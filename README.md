Ansible Role: OpenMCU
------------

Эта роль установит сервер видеоконференции OpenMCU версии 4.1.8 на CentOS 7.

Requirements
------------

None.

Role Variables
--------------

Доступные переменные перечислены ниже вместе со значениями по умолчанию (см. `defaults/main.yml`). Флаг включает применение кастомных настроек сервера (openmcu.ini, layout.conf, members.conf):
  - openmcu_copy_custom_settings: true

Настройка учетных данных администратора и оператора сервера видеоконференции:
  - openmcu_web_admin_user: admin
  - openmcu_web_admin_password:
  - openmcu_web_conf_user: guin
  - openmcu_web_conf_password: guin

Настройка диапазона udp-портов для media-трафика от сервера видеоконференции к клиентам.
  - openmcu_rtp_base_port: 7000
  - openmcu_rtp_max_port: 7999

Dependencies
------------

Также необходимо открыть следующие порты в firewall
  - port: 1420/tcp
  - port: 1554/tcp
  - port: 1719-1721/tcp
  - port: 5060-5061/tcp
  - port: 30000-39000/tcp
  - port: 1719-1721/udp
  - port: 5060-5061/udp
  - port: {{ openmcu_rtp_base_port }}-{{ openmcu_rtp_max_port }}/udp

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - openmcu

License
-------

BSD

Author Information
------------------

Chubik Sergey, chubik@ekaterinburg.fsin.uis.
