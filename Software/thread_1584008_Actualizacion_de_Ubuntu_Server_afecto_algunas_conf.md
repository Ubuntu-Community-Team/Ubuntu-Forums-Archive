---
title: "Actualizacion de Ubuntu Server afecto algunas configuraciones."
date: 2010-09-28
forum: Software
---

### Post by Wiredfixer on 2010-09-28
Pues bien, mi problema es el siguiente:

Desde hace un buen rato, ya tenia yo instalado un servidor para gestion, en el cual tengo lo siguiente:

- Repositorio APT personalizado para Desktops
- Puppet para Gestion remota e instalaciones
- OCS Inventory
- GLPI Para Complementar OCS.
- Webmin para gestion del server

Despues de un Update, mis configuraciones de GLPI y OCS Inventory se dañaron y sucedio lo siguiente:

- OCS Inventory no se encuentra (desaparecio!! /ocsreports 404)
- GLPI no accesaba correctamente desde el navegador (descargaba el PHP en lugar de abrirlo)
-
Asi que empeze a reorganizar todo, Mi Repositorio, Webmin y Puppet funcionaban correctamente, asi que los errores se debian concretamente a los modulos PHP y Perl.

Ahorita funciona my apt, GLPI esta Levantada de nuevo pero OCS no se deja instalar, al aplicarlo desde los repositorios me dice esto:

ERROR: Module perl does not exist!

Reinstale Perl completo con todos sus requerimientos (previa desinstalacion) y todo funciono en teoria, Reinstale OCS Inventory desde los repos y pues dice que funciona OK, pero al tratar de accesar desde un cliente me marca un error 500... Y al tratar de acceder al sitio en el servidor, pues me dice que no existe...

 No se a que se deba, he reinstalado lo que segun yo esta mal, pero creo que hay problemas extra pero no los he podido localizar.

 Saben de alguien que haya tenido el mismo problema? desgraciadamente no vi que fue lo que se actualizo y no hayo un log concreto para ver que fue lo que cambio mis configuraciones de manera tan drastica.

 Saludos!

---

### Post by guillermolisi on 2010-09-28
Fijate como esta el contenido de /etc/apache2/conf.d

Tengo una maquina con OCS funcionando aun despues de las actualizaciones y con este contenido (relativo a OCS, el resto no cuenta):

```
guille@ubuntu804server:~$ ls -al /etc/apache2/conf.d
total 36
drwxr-xr-x 2 root root  4096 2010-09-22 06:42 .
drwxr-xr-x 7 root root  4096 2010-09-22 06:42 ..
-rw-r--r-- 1 root root   269 2008-02-02 01:57 charset
lrwxrwxrwx 1 root root    45 2010-06-12 13:09 javascript-common.conf -> /etc/javascript-common/javascript-common.conf
-rw-r--r-- 1 root root  3296 2010-04-13 16:27 localized-error-pages
lrwxrwxrwx 1 root root    23 2010-06-12 14:27 munin -> ../../munin/apache.conf
lrwxrwxrwx 1 root root    25 2010-06-12 20:20 nagios3.conf -> /etc/nagios3/apache2.conf
[COLOR="Blue"]-rw-r--r-- 1 root root  2095 2010-06-24 23:37 ocsinventory-reports.conf[/COLOR]
lrwxrwxrwx 1 root root    28 2008-04-20 18:17 phpmyadmin.conf -> ../../phpmyadmin/apache.conf
-rw-r--r-- 1 root root  1481 2010-04-13 16:27 security
[COLOR="blue"]-rw-r--r-- 1 root root 11093 2010-06-24 23:28 z-ocsinventory-server.conf[/COLOR]
```
Revisa si los permisos, owner y group de los archivos de OCS estan correctos, tambien.

---

### Post by juancarlospaco on 2010-09-28
Siempre tene el /etc en una Tarball

reintalas programa y pisas las config

---

### Post by Wiredfixer on 2010-09-29
Esto esta en mi Apache

```
drwxr-xr-x 2 root root 4.0K 2010-09-28 10:32 .
drwxr-xr-x 7 root root 4.0K 2010-09-27 16:04 ..
-rw-r--r-- 1 root root  269 2010-08-18 21:19 charset
-rw-r--r-- 1 root root 3.3K 2010-08-18 21:19 localized-error-pages
lrwxrwxrwx 1 root root   35 2010-09-28 10:28 ocsinventory.conf -> /etc/ocsinventory/ocsinventory.conf
lrwxrwxrwx 1 root root   33 2010-09-28 10:32 ocsreports.conf -> /etc/ocsinventory/ocsreports.conf
-rw-r--r-- 1 root root 1.5K 2010-08-18 21:19 security

```

Es horrible, es todo un desorden esto, pude haber hecho esto de las configuraciones, pero creo que se debe a que muchos archivos cambiaron de lugar, ahora no tengo idea por donde empezar a organizar todo.

Hay alguna manera de "resetear" todo esto? es decir, reinstalar todo de manera normal, en realidad no me importan mucho las configuraciones, lo malo es que despues de desinstalar y reinstalar, en teoria deberian funcionar.

 Ahora ya no operan correctamente, y eso es lo que me altera un poco, puedo empezar todo de nuevo, el problema es que el servidor no lo tengo fisicamente en mi sede, esta en otro pais :S

---

### Post by Wiredfixer on 2010-09-29
Tengo el Log de errores de apache, aqui lo pongo:

```
ocsinventory-server: Can't load SOAP::Transport::HTTP* - Web service will be unavailable
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/msql.so' - /usr/lib/php5/20090626+lfs/msql.so: cannot o$
[Wed Sep 29 15:54:23 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.1 configured -- $
[Wed Sep 29 15:54:26 2010] [notice] Graceful restart requested, doing restart
ocsinventory-server: Can't load SOAP::Transport::HTTP* - Web service will be unavailable
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/msql.so' - /usr/lib/php5/20090626+lfs/msql.so: cannot o$
[Wed Sep 29 15:54:26 2010] [notice] Apache/2.2.14 (Ubuntu) mod_fcgid/2.3.4 PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.$
[Wed Sep 29 15:54:26 2010] [notice] child pid 4175 exit signal Segmentation fault (11)
[Wed Sep 29 15:54:26 2010] [notice] child pid 4176 exit signal Segmentation fault (11)
[Wed Sep 29 15:54:26 2010] [notice] child pid 4177 exit signal Segmentation fault (11)
[Wed Sep 29 15:54:27 2010] [notice] child pid 4178 exit signal Segmentation fault (11)
[Wed Sep 29 15:54:27 2010] [notice] child pid 4179 exit signal Segmentation fault (11)
[Wed Sep 29 15:54:28 2010] [notice] child pid 4252 exit signal Segmentation fault (11)
[Wed Sep 29 15:54:29 2010] [notice] child pid 4332 exit signal Segmentation fault (11)
[Wed Sep 29 15:54:29 2010] [notice] Graceful restart requested, doing restart
ocsinventory-server: Can't load SOAP::Transport::HTTP* - Web service will be unavailable
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/msql.so' - /usr/lib/php5/20090626+lfs/msql.so: cannot o$
[Wed Sep 29 15:54:30 2010] [notice] Apache/2.2.14 (Ubuntu) mod_fcgid/2.3.4 PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.$
[Wed Sep 29 15:54:30 2010] [notice] child pid 4585 exit signal Segmentation fault (11)
[Wed Sep 29 15:54:30 2010] [notice] child pid 4623 exit signal Segmentation fault (11)
[Wed Sep 29 15:55:10 2010] [notice] SIGHUP received.  Attempting to restart
ocsinventory-server: Can't load SOAP::Transport::HTTP* - Web service will be unavailable
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/msql.so' - /usr/lib/php5/20090626+lfs/msql.so: cannot o$
[Wed Sep 29 15:55:11 2010] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Wed Sep 29 15:55:11 2010] [notice] Apache/2.2.14 (Ubuntu) mod_fcgid/2.3.4 PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch mod_ssl/2.2.14 OpenSSL/0.9$

```

AQui aparentemente tengo problemas (o sigo) con PHP, Perl y otras cosas que no identifico....

---

### Post by guillermolisi on 2010-09-29
Por lo que interpreto del log, tenes problemas con modulos de Mysql y Perl. Revisa las versiones porque es probable que una buena parte del conflicto venga por eso.

Cuando actualice de 8.04.4 a 10.04 tuve que remover completamente OCS (y sus dependencias y links simbolicos) para volver a instalar desde la version de los repositorios (mas moderna que la que estaba usando) ya que tuve problemas con las versiones de modulos Perl que no dejaban que Apache inicie correctamente. La instalacion de OCS que tenia la hice "a mano", no utilice la version de los repos en esa oportunidad.

Verifica que MySQL este funcionando correctamente, sino OCS no levantara nunca.

---

### Post by Wiredfixer on 2010-09-29
Pues de hecho voy a remover todo LAMP, ya que mi problema se esta dando por ahi.

Curiosamente, este servidor empezo siendo un 9.04 (no se porque no se fueron por un LTS) de ahi actualize hasta 10.04 y todo funcion bien, hasta que realize la ultima actualizacion que fue el dia 24 de este mes.

En realidad no importa mucho la informacion ni las DB, ya que todo es parte de un sistema de Inventarios, los equipos desktop ya tienen instalados los agentes asi que solo seria de realizar los cambios en el servidor.

Precisamente pense eso mismo, que seria una cuestion entre MySql y Perl, en un Principio, mod_perl no lo detectaba como ya lo comente y luego me aparecen varios errores en el log de apache.

 Espero que con *tasksel* y retirar todo LAMP y BASE me funcione bien despues de reinstalar.

 Hay alguna manera de dejar el sistema como nuevo? Por ahora estoy configurando todo por SSH y me gustaria instalar en Limpio todo LAMP y Perl, a ver si es posible.

 Gracias :D, regreso con mas datos.

---

### Post by Wiredfixer on 2010-09-29
Revisando los logs de APT, encontre lo siguiente, segun yo, son las entradas de los updates:

```
Log started: 2010-09-21  11:01:24
Log ended: 2010-09-21  11:01:27

Log started: 2010-09-23  17:27:41
Selecting previously deselected package libapache2-mod-php5.
(Reading database ... ^M(Reading database ... 5%^M(Reading database ... 10%^M(Reading database ... 15%^M(Reading database ... 20%^M(Reading d$
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.3.2-1ubuntu4.5_i386.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.3.2-1ubuntu4.5_all.deb) ...
Selecting previously deselected package php5-gd.
Unpacking php5-gd (from .../php5-gd_5.3.2-1ubuntu4.5_i386.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.3.2-1ubuntu4.5_i386.deb) ...
Selecting previously deselected package ocsinventory-reports.
Unpacking ocsinventory-reports (from .../ocsinventory-reports_1.02.1-2_all.deb) ...
Setting up libapache2-mod-php5 (5.3.2-1ubuntu4.5) ...
 * Reloading web server config apache2       ^[[80G ^M^[[74G[ OK ]

Setting up php5 (5.3.2-1ubuntu4.5) ...
Setting up php5-gd (5.3.2-1ubuntu4.5) ...
Setting up php5-mysql (5.3.2-1ubuntu4.5) ...
Setting up ocsinventory-reports (1.02.1-2) ...
Module php5 already enabled
Module rewrite already enabled

Log ended: 2010-09-23  17:27:49

Log started: 2010-09-23  17:28:27
(Reading database ... ^M(Reading database ... 5%^M(Reading database ... 10%^M(Reading database ... 15%^M(Reading database ... 20%^M(Reading d$
Removing ocsinventory-reports ...
 * Reloading web server config apache2       ^[[80G ^M^[[74G[ OK ]
Removing ocsinventory-server ...
^[[?1049h^[[1;25r^[[4l^[[?25l^[[m^[(B^[[37m^[[40m^[[1;25r^[[H^[[2J^[[1;1H^[[1m^[[37m^[[44m^[[K
^[[K

```

Ahi fue donde empezo mi problema..

---

### Post by guillermolisi on 2010-09-29
Supongamos que cuando actualizaste se removio OCS-inventory-reports, lo volviste a instalar ? Desde donde ? Que version ?

---

### Post by Wiredfixer on 2010-09-30
Reinstale OCS Inventory desde los repos de Ubuntu Oficiales, las versiones:

- ocsinventory-reports 1.02.1-2
- ocsinventory-server 1.02.1-2

Que version de OCS Recomiendas?

Realize una purga de mi OS usando tasksel, deseleccionado LAMP y todo lo demas y dejando solo Basic Server y OpenSSH, reinstalo todo y aparentemente funciona ok, me voy a los logs de apache y aparece esto:

> [Thu Sep 30 09:00:20 2010] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Thu Sep 30 09:00:21 2010] [notice] Graceful restart requested, doing restart
[Thu Sep 30 09:00:21 2010] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Thu Sep 30 09:06:09 2010] [error] [client 10.190.65.87] File does not exist: /var/www/ocsreports
[Thu Sep 30 09:06:09 2010] [error] [client 10.190.65.87] File does not exist: /var/www/favicon.ico
[Thu Sep 30 09:06:11 2010] [error] [client 10.190.65.87] File does not exist: /var/www/favicon.ico
[Thu Sep 30 09:06:12 2010] [error] [client 10.190.65.87] File does not exist: /var/www/favicon.ico
[Thu Sep 30 09:12:19 2010] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/gd.so' - /usr/lib/php5/20090626+lfs/gd.so: cannot o$
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/imagick.so' - /usr/lib/php5/20090626+lfs/imagick.so$
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/imap.so' - /usr/lib/php5/20090626+lfs/imap.so: cann$
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mcrypt.so' - /usr/lib/php5/20090626+lfs/mcrypt.so: $
[Thu Sep 30 09:12:20 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operatio$
[Thu Sep 30 09:13:21 2010] [error] [client 10.190.65.87] File does not exist: /var/www/ocsreports
[Thu Sep 30 09:26:22 2010] [notice] Graceful restart requested, doing restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imap.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/imagick.so' - /usr/lib/php5/20090626+lfs/imagick.so$
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/imap.so' - /usr/lib/php5/20090626+lfs/imap.so: cann$
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mcrypt.so' - /usr/lib/php5/20090626+lfs/mcrypt.so: $
[Thu Sep 30 09:26:22 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operatio$
[Thu Sep 30 09:29:21 2010] [error] [client 10.190.65.87] File does not exist: /var/www/ocsreports


Ahi es donde no entiendo que pasa, segun veo los "PHP deprecated" acuden a ficheros que no existen en esa carpeta, de ahi me voy a las librerias que no cargan, y obviamente, /ocsreports que no existe, ya que lo reinstale y aparentemente no crea el directorio porque faltan algunas cosas.

Y Por Cierto, despues de la actualizacion ya no me aparecio el resumen del Server cada que acceso por SSH, no es gran cosa ya que a veces lo gestiono con webmin, pero aqui regularmente me dice si hay updates de manera mas rapida.

---

### Post by guillermolisi on 2010-09-30
La ultima estable es la 1.3.2 y la anterior, en el site del proyecto es la 1.2.3.

Si la que instalaste funciona bien, deja esa. Sino, bajate el tarball de la ultima e instalala a mano. En su documentacion explican bien como hacerlo.

---

### Post by Wiredfixer on 2010-09-30
Eso hare, mi unico problema aun es que me sigue enviando esos errores de php:

```
PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/imagick.so'
```

Y Similares...

---

### Post by Wiredfixer on 2010-09-30
La cuestion de los "Deprecated" se repara asi

cd /etc/php5/cli/conf.d
sudo perl -pi.bk -e 's/(\s*)#/\1;/' *ini
sudo mkdir bk
sudo mv *.bk bk

esto es por un bug : [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/573436](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/573436)

Lo que no he podido resolver aun, es lo de los modulos... alguna idea?

---

### Post by Wiredfixer on 2010-10-04
Pues Bien, despues de estar un rato luchando con el server, quedo funcionando.

Principalmente los fallos fueron:

- Apache2 No se actualizo correctamente, se corrigieron algunas instalaciones de modulos y opero correctamente.
- Asimismo, se tuvo que reinstalar Perl y sus dependencias.
- Se corrigieron rutas de configuracion de PHP, funciona OK.
- Se actualizo la version de OCS inventory por la Version mas nueva y estable.

 Basicamente esos fueron los puntos revisados, si alguien tiene dudas o los mismos problemas, que revise primero estos errores.

 Creo que lo damos como resuelto.

---

