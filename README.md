**Задача 1**
- Предоставьте ответ в виде ссылки на https://hub.docker.com/<username_repo>/custom-nginx/general
  Ответ: https://hub.docker.com/repository/docker/stbir/custom-nginx/general
**Задача 2**
  Запустите ваш образ custom-nginx:1.0.0 командой docker run в соответвии с требованиями:
имя контейнера "ФИО-custom-nginx-t2"
контейнер работает в фоне
контейнер опубликован на порту хост системы 127.0.0.1:8080
Не удаляя, переименуйте контейнер в "custom-nginx-t2"
Выполните команду date +"%d-%m-%Y %T.%N %Z" ; sleep 0.150 ; docker ps ; ss -tlpn | grep 127.0.0.1:8080  ; docker logs custom-nginx-t2 -n1 ; docker exec -it custom-nginx-t2 base64 /usr/share/nginx/html/index.html
Убедитесь с помощью curl или веб браузера, что индекс-страница доступна.
В качестве ответа приложите скриншоты консоли, где видно все введенные команды и их вывод.
Ответ:
  ![Task2](https://github.com/user-attachments/assets/e1c1f12f-67d7-4e7f-b394-6c3d70ad015f)
**Задача 3**
  Воспользуйтесь docker help или google, чтобы узнать как подключиться к стандартному потоку ввода/вывода/ошибок контейнера "custom-nginx-t2".
Подключитесь к контейнеру и нажмите комбинацию Ctrl-C.
Выполните docker ps -a и объясните своими словами почему контейнер остановился.
Ответ:
Так как ctrl+c это стандартный сигнал завершения процесса, то контейнер его и завершает. Для работы в фоне необходимо ставить ключ -d -it и тогда мы просто отключимся от него.
![Task3 1](https://github.com/user-attachments/assets/97e92cc5-cb01-4fb6-93a1-5ab7ae254e27)

Перезапустите контейнер
Зайдите в интерактивный терминал контейнера "custom-nginx-t2" с оболочкой bash.
Установите любимый текстовый редактор(vim, nano итд) с помощью apt-get.
Отредактируйте файл "/etc/nginx/conf.d/default.conf", заменив порт "listen 80" на "listen 81".
Запомните(!) и выполните команду nginx -s reload, а затем внутри контейнера curl http://127.0.0.1:80 ; curl http://127.0.0.1:81.
Выйдите из контейнера, набрав в консоли exit или Ctrl-D.
Проверьте вывод команд: ss -tlpn | grep 127.0.0.1:8080 , docker port custom-nginx-t2, curl http://127.0.0.1:8080. Кратко объясните суть возникшей проблемы.
Ответ: 
Потому что при запуске мы прокидывали 80 порт на наш 8080, а теперь изменили его на 81.
![Task3 2](https://github.com/user-attachments/assets/fdba723e-36f6-44bc-b16e-8173dfa78e81)
![Task3 3](https://github.com/user-attachments/assets/9cc24131-e2f8-4a87-9d39-f6b81f3dafca)
![Task3 4](https://github.com/user-attachments/assets/9c6425eb-6fa3-46bd-a7b8-a23651022c00)
![Task3 5](https://github.com/user-attachments/assets/9b27b151-e6e7-4cc4-a008-3534dd0146e1)

Это дополнительное, необязательное задание. Попробуйте самостоятельно исправить конфигурацию контейнера, используя доступные источники в интернете. Не изменяйте конфигурацию nginx и не удаляйте контейнер. Останавливать контейнер можно.
Ответ:
![Task3 6](https://github.com/user-attachments/assets/a522acbe-6702-4ce6-b444-0d9339a24170)

Удалите запущенный контейнер "custom-nginx-t2", не останавливая его.
Ответ:
![Task3 7](https://github.com/user-attachments/assets/9ec56d24-4d56-403a-ab71-b2b367ba854a)

**Задача 4**
Запустите первый контейнер из образа centos c любым тегом в фоновом режиме, подключив папку текущий рабочий каталог $(pwd) на хостовой машине в /data контейнера, используя ключ -v.
Запустите второй контейнер из образа debian в фоновом режиме, подключив текущий рабочий каталог $(pwd) в /data контейнера.
Подключитесь к первому контейнеру с помощью docker exec и создайте текстовый файл любого содержания в /data.
Добавьте ещё один файл в текущий каталог $(pwd) на хостовой машине.
Подключитесь во второй контейнер и отобразите листинг и содержание файлов в /data контейнера.
Ответ:
![Task4](https://github.com/user-attachments/assets/5c7eaf8c-b915-4151-bda6-b6d9eddc4143)

**Задача 5**
![Task 5 1](https://github.com/user-attachments/assets/3d736753-4728-4e6c-94b0-cb4d9ea4eb6b)
![Task5 2](https://github.com/user-attachments/assets/331e1abf-d7fe-48a2-a698-d8fb5e9f0b8d)
![Task5 3](https://github.com/user-attachments/assets/29ae74f2-f611-4536-8363-6c2ce4c02140)
![Task5 4](https://github.com/user-attachments/assets/17e86c68-fefa-475a-a592-f9352e236c6a)
![Task5 5](https://github.com/user-attachments/assets/23cf9147-ece1-4c7f-9271-0f9d22deb2f3)
![Task5 6](https://github.com/user-attachments/assets/64db99c9-0a5f-496c-ac63-5f2e36b2feb2)
Видим, что был обнаружен запущенный контецнер, но описание контейнера Portainer было в удалённом файле compose.yaml. можно удалить его с помощью флага --remove- orphans.
