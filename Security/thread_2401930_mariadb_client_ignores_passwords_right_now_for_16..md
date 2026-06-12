---
title: "mariadb client ignores passwords right now for 16.04"
date: 2018-09-24
forum: Security
---

### Post by whistl2 on 2018-09-24
I installed mariadb on my host, I'm up to date on patches, and am so glad I'm only using the localhost IP network to offer my mysql database 3306 port to my blog web server, because tonight I discovered my mariadb server will accept absolutely any password for any account. I've run the mysql_secure_installation, and my mysql database users table is correct. The software is failing to reject users logging in as root with "**** you" as password (and I swear that's not the password I set).

I sure hope this is just me messing something up.  Please prove me wrong. Please.

root@whistl:/etc/inspircd# cat /etc/os-release
NAME="Ubuntu"
VERSION="16.04.5 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.5 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial
root@whistl:/etc/inspircd# dpkg -l | grep -E 'mysql|maria'
ii  libdbd-mysql-perl                4.033-1ubuntu0.1                           amd64        Perl5 database interface to the MySQL database
ii  libmysqlclient20:amd64           5.7.23-0ubuntu0.16.04.1                    amd64        MySQL database client library
ii  mariadb-client                   10.0.36-0ubuntu0.16.04.1                   all          MariaDB database client (metapackage depending on the latest version)
ii  mariadb-client-10.0              10.0.36-0ubuntu0.16.04.1                   amd64        MariaDB database client binaries
ii  mariadb-client-core-10.0         10.0.36-0ubuntu0.16.04.1                   amd64        MariaDB database core client binaries
ii  mariadb-common                   10.0.36-0ubuntu0.16.04.1                   all          MariaDB common metapackage
ii  mariadb-server                   10.0.36-0ubuntu0.16.04.1                   all          MariaDB database server (metapackage depending on the latest version)
ii  mariadb-server-10.0              10.0.36-0ubuntu0.16.04.1                   amd64        MariaDB database server binaries
ii  mariadb-server-core-10.0         10.0.36-0ubuntu0.16.04.1                   amd64        MariaDB database core server files
ii  mysql-common                     5.7.23-0ubuntu0.16.04.1                    all          MySQL database common files, e.g. /etc/mysql/my.cnf
ii  php-mysql                        1:7.0+35ubuntu6.1                          all          MySQL module for PHP [default]
ii  php7.0-mysql                     7.0.32-0ubuntu0.16.04.1                    amd64        MySQL module for PHP
root@whistl:/etc/inspircd# mysql -u root -p
Enter password: (I promise, I did not enter the mysql root account real password)
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 10101
Server version: 10.0.36-MariaDB-0ubuntu0.16.04.1 Ubuntu 16.04

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [mysql]> select * from user where User="root";
+-----------+------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+------------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+-------------+-----------------------+------------------+---------+
| Host      | User | Password                                  | Select_priv | Insert_priv | Update_priv | Delete_priv | Create_priv | Drop_priv | Reload_priv | Shutdown_priv | Process_priv | File_priv | Grant_priv | References_priv | Index_priv | Alter_priv | Show_db_priv | Super_priv | Create_tmp_table_priv | Lock_tables_priv | Execute_priv | Repl_slave_priv | Repl_client_priv | Create_view_priv | Show_view_priv | Create_routine_priv | Alter_routine_priv | Create_user_priv | Event_priv | Trigger_priv | Create_tablespace_priv | ssl_type | ssl_cipher | x509_issuer | x509_subject | max_questions | max_updates | max_connections | max_user_connections | plugin      | authentication_string | password_expired | is_role |
+-----------+------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+------------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+-------------+-----------------------+------------------+---------+
| localhost | root | *0DC2081C6D26C2A826D598A4292FD53D62744A92 | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            | Y                      |          |            |             |              |             0 |           0 |               0 |                    0 | unix_socket |                       | N                | N       |
+-----------+------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+------------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+-------------+-----------------------+------------------+---------+
1 row in set (0.00 sec)

MariaDB [mysql]> 

This is really messed up.

Patrick Wolfe (@whistl034)
Sr Linux Admin

---

### Post by whistl2 on 2018-09-24
Right, I managed, to exclude the following from the middle of my cut&paste (while trying to edit out all the typos)

MariaDB [(none)]> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

---

