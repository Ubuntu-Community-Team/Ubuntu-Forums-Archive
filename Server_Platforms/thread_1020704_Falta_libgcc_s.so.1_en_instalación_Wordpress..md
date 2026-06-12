---
title: "Falta libgcc_s.so.1 en instalación Wordpress."
date: 2008-12-24
forum: Server Platforms
---

### Post by danirolo7 on 2008-12-24
Muy buenas, más hoy en nochebuena, ojalá le hayas demostrado a tu familia que los quieres derrochando dinero, paso al lío:

Me he puesto a instalar WordPress local en mi Ubuntu Ultimate 2.0 64 bits(basado en Ubuntu 8.10 Intrepid Ibex). Primero seguí un tutorial en [PuntoGeek]("http://www.puntogeek.com/2007/01/26/instalar-wordpress-local-en-ubuntu/"), al llegar a poner [http://localhost/CARPETA/wp-admin/install.php](http://localhost/CARPETA/wp-admin/install.php) en la barra de direcciones, pues no supe sustituir "carpeta" por lo que me correspondía, así que simplemente desistí y me fui a por otro tutorial, esta vez en [CyberNautas]("http://www.cybernautas.es/articulos_linux/instalar-wordpress-en-ubuntu/") donde recomendaban el uso de Xampp, que traía de todo ya, pues dije, si tiene de todo, vamos a desinstalar los programas que instalé siguiento el otro tuto, no vaya a ser que haya problema, por eso hice un (lo sé, purge es mejor)"sudo aptitude remove apache2 php5 mysql-server-5.0 phpmyadmin" y dije que con eso bastaría, al remover mysql-server-5.0 me removió tambien kmail y akinode-server [akinode, creo], pensé que no habría mucho problema...en fín, copié Xampp a /opt e hice el "sudo /opt/lampp/lampp start" y me dice:

```

daniel@daniel-laptop:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
libgcc_s.so.1 must be installed for pthread_cancel to work
Aborted
libgcc_s.so.1 must be installed for pthread_cancel to work
Aborted
libgcc_s.so.1 must be installed for pthread_cancel to work
libgcc_s.so.1 must be installed for pthread_cancel to work
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
daniel@daniel-laptop:~$ libgcc_s.so.1 must be installed for pthread_cancel to work

```

Según eso, se inicia pero hay un problema con el Libgcc_s.so.1, dice que no está instalado, pues me dije: hagamos un apt-file a ver en qué paquete está el archivito, hago "apt-file -x search libgcc_s.so.1" y sale:


```
gcc-snapshot: /usr/lib/gcc-snapshot/lib/libgcc_s.so.1
gcc-snapshot: /usr/lib/gcc-snapshot/lib32/libgcc_s.so.1
lib32gcc1: /usr/lib32/libgcc_s.so.1
lib32gcc1-dbg: /usr/lib/debug/usr/lib32/libgcc_s.so.1
libgcc1: /lib/libgcc_s.so.1
libgcc1-dbg: /usr/lib/debug/lib/libgcc_s.so.1
ppu-gcc: /usr/lib/cell/toolchain/lib/gcc/ppu/4.1.1/32/libgcc_s.so.1
ppu-gcc: /usr/lib/cell/toolchain/lib/gcc/ppu/4.1.1/libgcc_s.so.1
```


¿Qué paquete debo instalar?(si es cuestión de ese paquete, aunque me suena más un problema con MySQL-Server)¿Cómo puedo dejar en cero la instalación de los paquetes que he instalado? Que quede como si no hubiera hecho nada...

He intentado reinstalando mysql-server y removiéndolo con aptitude purge para quitar ficheros de configuración, vuelvo a iniciar Xampp con "sudo /opt/lampp/lampp restart" y me dice lo mismo, que me falta el libgcc_s.so.1. No sé qué más puedo intentar, he buscado pero parece que nadie es tan tonto como yo en las páginas indexadas por Google.

En fin, muchísimas gracias a los que habéis llegado hasta aquí en la lectura y muchísimas más a los que posteen una posible solución. Concretando: ¿Cómo puedo dejar todo como si no hubiese pasado nada? ¿Cómo instalo el Xampp sin problemas? o mejor aún ¿Cómo instalo el WordPress?

PD: por cierto, en [http://localhost/xampp](http://localhost/xampp) en la pestaña seguridad me sale "desconocido" en la tercera y cuarta categoría, las que tienen que ver con MySQL. Y al hacer click en phpMyAdmin en el menú de herramientas, sale [esto]("http://i701.photobucket.com/albums/ww17/danirolo7/php.png")

Muchas gracias por haberos tragado esta chapa. ¡Salud!

---

### Post by eduardozamudio on 2010-05-26
Hi, i've the same problem. After doing and ubuntu upgrade from 9.10 to 10.4, LAMPP starts giving this notice: "libgcc_s.so.1 must be installed for pthread_cancel to work"

I've search on synaptics, and i found two installed gcc versions (gcc-4.4 and gcc-4.2).
After uninstall gcc-4.2 the notice doesn't appear anymore, and mysql starts working perfectly.

(sorry to reply an old post, but i think this could help others)

---

