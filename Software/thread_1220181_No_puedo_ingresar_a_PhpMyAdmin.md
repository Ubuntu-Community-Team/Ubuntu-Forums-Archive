---
title: "No puedo ingresar a PhpMyAdmin"
date: 2009-07-22
forum: Software
---

### Post by FB91 on 2009-07-22
Hace ya unos cuantos días que tengo instalado XAMPP para linux y me andubo perfecto, pero desde hace unos días que veo que cuando "lo inicio" poniendo en consola "sudo /opt/lampp/lampp start" me tira algunos errores como los siguientes:

```
Starting XAMPP for Linux 1.7.1...                                                                                    
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_gd2.dll' - C:\xampp\php\ext\/php_gd2.dll: cannot open shared object file: No such file or directory in Unknown on line 0                                 
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_gettext.dll' - C:\xampp\php\ext\/php_gettext.dll: cannot open shared object file: No such file or directory in Unknown on line 0                         
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_imap.dll' - C:\xampp\php\ext\/php_imap.dll: cannot open shared object file: No such file or directory in Unknown on line 0                               
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_mbstring.dll' - C:\xampp\php\ext\/php_mbstring.dll: cannot open shared object file: No such file or directory in Unknown on line 0                       
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_exif.dll' - C:\xampp\php\ext\/php_exif.dll: cannot open shared object file: No such file or directory in Unknown on line 0                               
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_mcrypt.dll' - C:\xampp\php\ext\/php_mcrypt.dll: cannot open shared object file: No such file or directory in Unknown on line 0                           
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_mime_magic.dll' - C:\xampp\php\ext\/php_mime_magic.dll: cannot open shared object file: No such file or directory in Unknown on line 0                   
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_ming.dll' - C:\xampp\php\ext\/php_ming.dll: cannot open shared object file: No such file or directory in Unknown on line 0                               
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_mssql.dll' - C:\xampp\php\ext\/php_mssql.dll: cannot open shared object file: No such file or directory in Unknown on line 0                             
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_mysql.dll' - C:\xampp\php\ext\/php_mysql.dll: cannot open shared object file: No such file or directory in Unknown on line 0                             
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_mysqli.dll' - C:\xampp\php\ext\/php_mysqli.dll: cannot open shared object file: No such file or directory in Unknown on line 0                           
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_pdf.dll' - C:\xampp\php\ext\/php_pdf.dll: cannot open shared object file: No such file or directory in Unknown on line 0                                 
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_pdo.dll' - C:\xampp\php\ext\/php_pdo.dll: cannot open shared object file: No such file or directory in Unknown on line 0                                 
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_pdo_mssql.dll' - C:\xampp\php\ext\/php_pdo_mssql.dll: cannot open shared object file: No such file or directory in Unknown on line 0                     
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_pdo_mysql.dll' - C:\xampp\php\ext\/php_pdo_mysql.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_pgsql.dll' - C:\xampp\php\ext\/php_pgsql.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_soap.dll' - C:\xampp\php\ext\/php_soap.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_sockets.dll' - C:\xampp\php\ext\/php_sockets.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_sqlite.dll' - C:\xampp\php\ext\/php_sqlite.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_xmlrpc.dll' - C:\xampp\php\ext\/php_xmlrpc.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_xsl.dll' - C:\xampp\php\ext\/php_xsl.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_zip.dll' - C:\xampp\php\ext\/php_zip.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_ps.dll' - C:\xampp\php\ext\/php_ps.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library 'C:\xampp\php\ext\/php_paradox.dll' - C:\xampp\php\ext\/php_paradox.dll: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  Cannot open 'C:\xampp\php\browscap\browscap.ini' for reading in Unknown on line 0
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
```El intérprete de PHP me funciona bien, pero el problema es cuando entro a PhpMyAdmin, me logueo y cuando clickeo en el botón de "Continuar" no entra :S

Alguna idea de que puede ser?

Gracias! :D

---

### Post by sergiom99 on 2009-07-22
Evidentemente tiene algun archivo de configuracion copiado de Windows.
Fijate que esta buscando cosas en 'C:\xampp\php'
Lo hiciste siguiendo algun tutorial o copiaste archivos de otro lado?

En Ubuntu no existe C:\xampp\php.
Fijate si este howto te ayuda a configurarlo: [http://ubuntu-ar.org/node/206](http://ubuntu-ar.org/node/206)

---

### Post by FB91 on 2009-07-22
Tengo en mi otra partición de windows instalado el XAMPP de Windows... lo raro es que siempre me andubo bien el phpmyadmin, supongo que hubo "algo" que cambió la configuración del mismo.

hay alguna manera de indicarle que no busque en C:\xampp... sino que busque en /opt/lampp... ?

Gracias por el howto !

---

### Post by FB91 on 2009-07-23
> **sergiom99 said:**
> Evidentemente tiene algun archivo de configuracion copiado de Windows.
Fijate que esta buscando cosas en 'C:\xampp\php'
Lo hiciste siguiendo algun tutorial o copiaste archivos de otro lado?

En Ubuntu no existe C:\xampp\php.
Fijate si este howto te ayuda a configurarlo: [http://ubuntu-ar.org/node/206](http://ubuntu-ar.org/node/206)

Hice el tutorial que me dijiste y lo único que no me funciona es el phpmyadmin... probé creando un archivo test.php (como dice el tutorial) y me lo muestra correctamente, el problema es que yendo a [http://localhost/phpmyadmin](http://localhost/phpmyadmin) no se ve nada, solo una pantalla en blanco :S

---

### Post by sergiom99 on 2009-07-23
desconozco phpmyadmin como para decirte donde esta el archivo de configuracion.
fijate si en /etc/php.../ hay algun .conf o .ini que tenga algo que apunte a c:\

Seguro te copiaste algo del XAMPP de Windows que carga esa configuracion.

---

### Post by guillermolisi on 2009-07-23
Estan, porque son varios, en
```
guille@guillepc:~$ ls -al **/etc/phpmyadmin**
total 40
drwxr-xr-x   2 root root     4096 2009-07-08 17:26 .
drwxr-xr-x 177 root root     8192 2009-07-22 20:05 ..
-rw-r--r--   1 root root      879 2009-02-03 00:17 apache.conf
-rw-r-----   1 root www-data  549 2009-07-08 17:26 config-db.php
-rw-r--r--   1 root root      168 2008-03-06 00:42 config.footer.inc.php
-rw-r--r--   1 root root      168 2008-03-06 00:42 config.header.inc.php
-rw-r--r--   1 root root     3358 2009-02-03 00:17 config.inc.php
-rw-r-----   1 root www-data    8 2008-07-29 14:48 htpasswd.setup
-rw-r--r--   1 root root      570 2009-02-03 00:17 lighttpd.conf
```
Fijate porque hay para Apache, para MySQL y para PHP.

Nota: No uso XAMPP

---

### Post by FB91 on 2009-07-23
Probé reinstalando el XAMPP para Linux y cuando lo inicio me da este error :

```
Starting XAMPP for Linux 1.7.1...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Error 1! Couldn't start Apache!
XAMPP: Starting diagnose...
tail: no se puede abrir «/opt/lampp/logs/apachestart.log» para lectura: No existe el fichero ó directorio
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum http://www.apachefriends.org/f/
XAMPP: Starting MySQL...
XAMPP: Couldn't start MySQL!
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
```

La verdad es que hice una ensalada importante con todo esto de las instalaciones xD tengo ganas de desinstalar por completo el XAMPP para Linux y también lo que me instaló [este tutorial]("http://ubuntu-ar.org/node/206") ... el único problema es que nose como hacerlo :)

---

### Post by FB91 on 2009-07-26
alguien me orienta un poco? la verdad que estoy medio mareado :S
estuve tocando bastante cosas que al final instalé de todo y sigue sin andar.

Les cuento por donde estoy parado:
al poner en el navegador [http://localhost/](http://localhost/) me muestra una pantalla que dice Index of y a continuación los archivos que tengo en el directorio /var/www[IMG]http://i31.tinypic.com/2cn8fwj.jpg[/IMG]
y cuando entro a [http://localhost/phpmyadmin](http://localhost/phpmyadmin) directamente no encuentra la página...
Supongo que anduve mezclando instalaciones o algo similar :S

Alguien sabe como se soluciona? tengo muchas ganas de probar unas cositas en php (recién estoy empezando) y esto me tiene muy trabado!

Gracias!

---

### Post by sergiom99 on 2009-07-26
supongo que solo te muestra eso porque no tenes ningun archivo que sea 'index.*'.
Lo importante es saber si al poner [http://localhost/test.php](http://localhost/test.php) ejecuta esa pagina o no.
Si muestra el contenido, es porque el Apache y el php de alguna manera estan funcionando.

Seguramente la config y parametrizacion del otro soft te van a poder ayudar mas en sus foros de soporte/wiki/etc.

---

### Post by FB91 on 2009-07-28
yendo a [http://localhost/test.php](http://localhost/test.php) me muestra la pantalla con todos los datos de php... por lo que veo el intérprete php va bien... la cosa es el phpmyadmin :S

gracias por la ayuda ! seguiré leyendo sobre este tema a ver si le encuentro la vuelta ;)

---

