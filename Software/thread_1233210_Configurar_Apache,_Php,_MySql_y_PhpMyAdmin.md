---
title: "Configurar Apache, Php, MySql y PhpMyAdmin"
date: 2009-08-06
forum: Software
---

### Post by FB91 on 2009-08-06
Alguien me ayuda a configurar todo esto? desde hace bastante tengo ganas de hacer unas cuantas cosas en php y no puedo arreglar esto :S estube viendo unos cuantos posts en el foro pero ninguno me lo pudo solucionar lamentablemente.

Les cuento mi situación, que seguro a más de uno le paso... cuando voy a [http://localhost/test.php](http://localhost/test.php) me sale el cartelito para descargar el archivo, es decir, no me interpreta el php. 
[U]
NOTA:[/U] el archivo test.php contiene <?php echo phpinfo(); ?>

Gracias a todos

FB91

---

### Post by credobyte on 2009-08-06
In terminal ( it'll reinstall PHP and mod for Apache ):
```
sudo apt-get remove --purge php5 libapache2-mod-php5 && sudo apt-get install php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart

```For the future knowledge, please write in English ( Google translate isn't the right way to communicate with each other :D ).

---

### Post by FB91 on 2009-08-06
> **credobyte said:**
> In terminal ( it'll reinstall PHP and mod for Apache ):
```
sudo apt-get remove --purge php5 libapache2-mod-php5 && sudo apt-get install php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart

```For the future knowledge, please write in English ( Google translate isn't the right way to communicate with each other :D ).

hi credobyte I did what you told me but I still have the same problem... any idea?

(I wrote in Spanish because this is the forum for argentina :D)

Alguien me dice como configurar todo para que me quede bien?

Salu2!

---

### Post by credobyte on 2009-08-06
Weird. Apache seems to know what PHP means ( you can see it in your browser ), tough, it doesn't open it.

What if you change permissions ( might be screwed up for some unknown reason ) ?
```
sudo chmod 755 /var/www/index.php
```

---

### Post by FB91 on 2009-08-06
nothing happened :S
[LEFT]I think I have something misconfigured[/LEFT]

---

### Post by josecuervo86 on 2009-08-06
Tengo exactamente el mismo problema! Help :P

---

### Post by jjgomera on 2009-08-06
podrías poner por aqui el contenido del archivo /etc/apache2/mods-available/php5.conf,  comprueba también si la librería que indica el archivo /etc/apache2/mods-available/php5.load existe en tu sistema
pliiiiiiiiiiis :P

---

### Post by FB91 on 2009-08-06
> **jjgomera said:**
> podrías poner por aqui el contenido del archivo /etc/apache2/mods-available/php5.conf,  comprueba también si la librería que indica el archivo /etc/apache2/mods-available/php5.load existe en tu sistema
pliiiiiiiiiiis :P

el archivo php5.conf contiene lo siguiente:

```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```

Y la librería que indica el archivo php5.load existe, pero al intentar abrirle me sale este mensaje
```

gedit no ha podido detectar la codificación de caracteres.
Compruebe que no está intentando abrir un archivo binario.
Seleccione una codificación de caracteres desde el menú e intente de nuevo
```

P.D.: Que buen avatar que tenés !! xD

---

### Post by jjgomera on 2009-08-06
pues el problema no esta ahí, tienes en /etc/apache2/mods-enabled un archivo php5.conf que sea un enlace simbolico del archivo /etc/apache2/mods-available/php5.conf?

> **FB91 said:**
> P.D.: Que buen avatar que tenés !! xD

gracias, homer (homero) y tux en uno :D

---

### Post by FB91 on 2009-08-06
sisi tenés razón, el php5.conf de mod-enabled es un enlace simbólico al de mod-available, o por lo menos eso creo... en las propiedades del archivo dice: Enlace hacia documento de texto sencillo (text/plain) así que supongo que estás en lo cierto!

Sigo aquí esperando consejos!

Gracias!

---

### Post by jjgomera on 2009-08-06
vamos a forzar entonces la carga del modulo php5 en apache:

```
sudo a2enmod php5
```
 
Fuerza el reinicio de apache:

```
sudo /etc/init.d/apache2 force-reload
```

y prueba de nuevo a ver

---

### Post by FB91 on 2009-08-06
No se solucionó :S
Cuando puse en consola: **sudo a2enmod** 
un mensaje me dice:[B]
php5Module php5 already enabled[/B]

---

### Post by jjgomera on 2009-08-07
> **FB91 said:**
> No se solucionó :S
Cuando puse en consola: **sudo a2enmod** 
un mensaje me dice:[B]
php5Module php5 already enabled[/B]

prueba entonces a descargarlo primero:

```
sudo a2dismod php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
```

Si entras en localhost que te aparece abajo (donde pone la versión de apache y los módulos instalados)

si te aparece activo php, mira en el archivo /var/log/apache2/error.log a ver si encuentras algún error que haga referencia a php5

---

### Post by FB91 on 2009-08-07
Buenas noticias :D

Ayer hice lo que me dijiste (eso de sudo a2enmod php5 y reiniciar el apache) pero no me había dado resultado... así que apagué la pc y me fui a dormir :D hoy cuando la prendo fuí de nuevo a [http://localhost/test.php](http://localhost/test.php) y ya andaba!!!

Así que venimos bien... PHP ya funciona, ahora tengo que ver como es para hacer andar phpmyadmin... si voy a [http://localhost/phpmyadmin](http://localhost/phpmyadmin) me aparece una pantalla en blanco :S hice lo que dijo un tutorial de hacer un enlace simbólico a phpmyadmin a /var/www pero no funciona

Gracias jjgomera! me ayudaste muchísimo!!

---

### Post by FB91 on 2009-08-07
Estuve viendo muchos sitios sobre como configurar phpmyadmin ya que cuando accedo a él ([http://localhost/phpmyadmin](http://localhost/phpmyadmin)) se me vé una linda pantalla en blanco :D

La cosa es que sigo igual y ninguna guía me sirvió! les planteo aquí algunas dudas que tengo:


[LIST]
[*]El archivo config.inc.php lo tengo en dos lugares distintos, /etc/phpmyadmin y en /usr/share/phpmyadmin y nose cual de los 2 tengo que editar para que funcione correctamente.
[*]Nose si será algún problema de permisos, porque al enlace simbólico que tengo en /var/www hacia /usr/share/phpmyadmin le puse permisos 755. ( sudo chmod 755 /var/www/phpmyadmin )
[/LIST]
:popcorn:

---

### Post by jjgomera on 2009-08-11
prueba a reconfigurar phpmyadmin por si no hubieses elegido bien el servidor web que tienes instalado (apache2 supongo)

```
sudo dpkg-reconfigure phpmyadmin
```

---

### Post by FB91 on 2009-08-11
sigue igual... al principio me pregunto algo para que elija entre "socket unix" o "tcp/ip" yo seleccioné socket unix, esta bien?

gracias!

---

### Post by sergiom99 on 2009-08-11
Aca encontre varios recursos que te pueden orientar:
[http://www.ubuntugeek.com/howto-install-mysql-database-server-with-phpmyadmin-frontend.html](http://www.ubuntugeek.com/howto-install-mysql-database-server-with-phpmyadmin-frontend.html)
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)
[https://help.ubuntu.com/9.04/serverguide/C/phpmyadmin.html](https://help.ubuntu.com/9.04/serverguide/C/phpmyadmin.html)
[https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=(apache](https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=(apache))

MAS> 
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=phpmyadmin&sa=Search&cof=FORID:9#881](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=phpmyadmin&sa=Search&cof=FORID:9#881)

---

### Post by Panzzer on 2011-10-31
> **jjgomera said:**
> prueba entonces a descargarlo primero:

```
sudo a2dismod php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
```

Si entras en localhost que te aparece abajo (donde pone la versión de apache y los módulos instalados)

si te aparece activo php, mira en el archivo /var/log/apache2/error.log a ver si encuentras algún error que haga referencia a php5

Hola yo tengo un problema bastante similar el apache2 me da error 13, con lo aconsejado hasta ahora me sale el siguiente mensage
>  * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Cuando inicio el apache me sale:
> desktop:~$ /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

Estoy tratando de que desde esta pc se pueda acceder a una web, todavía no hecha mas que nada para poder utilizar el servicio de correo personalizado de gmail(el cual requiere que se cargue un código en el host de la pagina)
Recién empiezo con ubuntu :lolflag:, espero poder hacer esto jeje

---

### Post by euzkoarima on 2011-10-31
Quizás esto pueda servirte:

[URL="http://aslamnajeebdeen.com/blog/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu"]How to fix Apache – "Could not reliably determine the server’s fully qualified domain name, using 127.0.1.1 for ServerName" Error on Ubuntu
[/URL]

Saludos,
Eduardo

---

