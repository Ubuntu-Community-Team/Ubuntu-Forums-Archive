---
title: "1 GB RAM VPS with ubuntu 16.04 , mariadb10, php7 and apache2 keeps swapping"
date: 2017-07-28
forum: Server Platforms
---

### Post by rgilaard on 2017-07-28
Dear all, I have my ubuntu 16.04 VPS to host my wordpress production site but unfortunately the system keeps using swap although my vm.swappiness is set to 5.

 sudo free -m
              total        used        free      shared  buff/cache   available
Mem:            991         230         120          34         641         551
Swap:           511           2         509


On this system I have:
[LIST]
[*]apache2
[*]php7
[*]mariadb10
[/LIST]
I configured apache2 with php-fpm so the memory consumption is the best.
I also configured fail2ban to ban those bruteforcers.

vi /etc/mysql/mariadb.conf.d/50-server.cnf shows: 

bind-address            = 127.0.0.1

#
# * Fine Tuning
#
key_buffer_size         = 4M
max_allowed_packet      = 8M
thread_stack            = 128K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10

#
# * Query Cache Configuration
#
query_cache_limit       = 512K
query_cache_size        = 4M

vi /etc/php/7.0/fpm/pool.d/www.conf has the following settings:

pm.start_servers = 1
pm.min_spare_servers = 1
pm.max_spare_servers = 2

uname -a shows:
Linux 4.4.0-87-generic #110-Ubuntu SMP Tue Jul 18 12:55:35 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

sudo dpkg -l | grep php
ii  libapache2-mod-php7.0              7.0.18-0ubuntu0.16.04.1                    amd64        server-side, HTML-embedded scripting language (Apache 2 module)
ii  php-common                         1:35ubuntu6                                all          Common files for PHP packages
ii  php-imagick                        3.4.0~rc6-1ubuntu3                         amd64        Provides a wrapper to the ImageMagick library
ii  php-pear                           1:1.10.1+submodules+notgz-6                all          PEAR Base System
ii  php-xml                            1:7.0+35ubuntu6                            all          DOM, SimpleXML, WDDX, XML, and XSL module for PHP [default]
ii  php7.0                             7.0.18-0ubuntu0.16.04.1                    all          server-side, HTML-embedded scripting language (metapackage)
ii  php7.0-cli                         7.0.18-0ubuntu0.16.04.1                    amd64        command-line interpreter for the PHP scripting language
ii  php7.0-common                      7.0.18-0ubuntu0.16.04.1                    amd64        documentation, examples and common module for PHP
ii  php7.0-curl                        7.0.18-0ubuntu0.16.04.1                    amd64        CURL module for PHP
ii  php7.0-fpm                         7.0.18-0ubuntu0.16.04.1                    amd64        server-side, HTML-embedded scripting language (FPM-CGI binary)
ii  php7.0-gd                          7.0.18-0ubuntu0.16.04.1                    amd64        GD module for PHP
ii  php7.0-imap                        7.0.18-0ubuntu0.16.04.1                    amd64        IMAP module for PHP
ii  php7.0-intl                        7.0.18-0ubuntu0.16.04.1                    amd64        Internationalisation module for PHP
ii  php7.0-json                        7.0.18-0ubuntu0.16.04.1                    amd64        JSON module for PHP
ii  php7.0-mcrypt                      7.0.18-0ubuntu0.16.04.1                    amd64        libmcrypt module for PHP
ii  php7.0-mysql                       7.0.18-0ubuntu0.16.04.1                    amd64        MySQL module for PHP
ii  php7.0-opcache                     7.0.18-0ubuntu0.16.04.1                    amd64        Zend OpCache module for PHP
ii  php7.0-pspell                      7.0.18-0ubuntu0.16.04.1                    amd64        pspell module for PHP
ii  php7.0-readline                    7.0.18-0ubuntu0.16.04.1                    amd64        readline module for PHP
ii  php7.0-recode                      7.0.18-0ubuntu0.16.04.1                    amd64        recode module for PHP
ii  php7.0-snmp                        7.0.18-0ubuntu0.16.04.1                    amd64        SNMP module for PHP
ii  php7.0-sqlite3                     7.0.18-0ubuntu0.16.04.1                    amd64        SQLite3 module for PHP
ii  php7.0-tidy                        7.0.18-0ubuntu0.16.04.1                    amd64        tidy module for PHP
ii  php7.0-xml                         7.0.18-0ubuntu0.16.04.1                    amd64        DOM, SimpleXML, WDDX, XML, and XSL module for PHP
ii  php7.0-xmlrpc                      7.0.18-0ubuntu0.16.04.1                    amd64        XMLRPC-EPI module for PHP
ii  php7.0-xsl                         7.0.18-0ubuntu0.16.04.1                    all          XSL module for PHP (dummy)


sudo dpkg -l | grep mariadb
ii  mariadb-client                     10.0.29-0ubuntu0.16.04.1                   all          MariaDB database client (metapackage depending on the latest version)
ii  mariadb-client-10.0                10.0.29-0ubuntu0.16.04.1                   amd64        MariaDB database client binaries
ii  mariadb-client-core-10.0           10.0.29-0ubuntu0.16.04.1                   amd64        MariaDB database core client binaries
ii  mariadb-common                     10.0.29-0ubuntu0.16.04.1                   all          MariaDB common metapackage
ii  mariadb-server                     10.0.29-0ubuntu0.16.04.1                   all          MariaDB database server (metapackage depending on the latest version)
ii  mariadb-server-10.0                10.0.29-0ubuntu0.16.04.1                   amd64        MariaDB database server binaries
ii  mariadb-server-core-10.0           10.0.29-0ubuntu0.16.04.1                   amd64        MariaDB database core server files

sudo dpkg -l | grep apache
ii  apache2                            2.4.18-2ubuntu3.4                          amd64        Apache HTTP Server
ii  apache2-bin                        2.4.18-2ubuntu3.4                          amd64        Apache HTTP Server (modules and other binary files)
ii  apache2-data                       2.4.18-2ubuntu3.4                          all          Apache HTTP Server (common files)
ii  apache2-utils                      2.4.18-2ubuntu3.4                          amd64        Apache HTTP Server (utility programs for web servers)
ii  libapache2-mod-fastcgi             2.4.7~0910052141-1.2                       amd64        Apache 2 FastCGI module for long-running CGI scripts
ii  libapache2-mod-php7.0              7.0.18-0ubuntu0.16.04.1                    amd64        server-side, HTML-embedded scripting language (Apache 2 module)

sudo apachectl -M
Loaded Modules:
 core_module (static)
 so_module (static)
 watchdog_module (static)
 http_module (static)
 log_config_module (static)
 logio_module (static)
 version_module (static)
 unixd_module (static)
 access_compat_module (shared)
 actions_module (shared)
 alias_module (shared)
 auth_basic_module (shared)
 authn_core_module (shared)
 authn_file_module (shared)
 authz_core_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 fastcgi_module (shared)
 filter_module (shared)
 mime_module (shared)
 mpm_prefork_module (shared)
 negotiation_module (shared)
 proxy_module (shared)
 proxy_fcgi_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 status_module (shared)

All loaded modules for apache do worry me a bit but I can't think that would be the reason for swapping.

Can someone help me investigate what is happening?
If the solution is that I should split the webserver/php7 from the database server part, so be it but I would like to get to the bottom of this as on the web people have succeeded in setting up a server like this which performs good on less hardware. This VPS got a SSD drive.

With kind regards,
Django

---

