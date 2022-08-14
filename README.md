Установка LEMP стэка и wp на чистый сервер (Ubuntu)
=========

Роль для настройки веб-сервера
------------

Устанавливает php-пакеты, mysql и nginx(вместе с конфигурацией), также проводит mysql-secure-instalation и создает бд/юзера для wordpress

Требования
------------

Inventory для хоста, на котором будет разворачиваться LEMP стек

Переменные
--------------

group_vars: ansible_host, ansible_user, ansible_password, ansible_sudo_pass
vars(main.yml): В этом файле описаны все пакеты для установки, также имя пользователя и пароль для wordpress db и имя проекта(исп. в конфигурации nginx)

Проверить соединение можне командой:
<sudo ansible ИМЯ_ХОСТА -i hosts -m ping -b >

Пример использования роли
----------------

Для использования роли достаточно в папке с inventory создать playbook(side.yml) со сл, содержанием:
<
- name: Nginx Setup
  hosts: NginxHost4
  become: yes
  gather_facts: yes
  roles:
      - InstallWebServer
 >

Запуск плейбука с ролью
----------------

Запуск происходит командой:
<sudo ansible-playbook -i hosts side.yml >