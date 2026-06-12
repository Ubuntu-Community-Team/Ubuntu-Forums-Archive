---
title: "Problema al conectar camara digital!"
date: 2009-06-28
forum: Software
---

### Post by gaston89 on 2009-06-28
Hola, tengo un problema al conectar una "kodak easyshare c310". 
Luego de instalar el "gphoto2", al conectarla me salta un cartel que dice: "Error al inicializar la cámara: -60: No se pudo trabar el dispositivo"... dejando el icono de la camara en "Equipo" pero sin poder acceder a ella. Luego de desconectar la camara, frustrado por no poder bajar las fotos, el icono sigue en pantalla recordandome que no pude hacer nada!.

Nota: El S.O. es Ubuntu 9.04

Desde ya gracias.

---

### Post by juancarlospaco on 2009-06-28
Proba hacer lo mismo pero con **sudo**

---

### Post by gaston89 on 2009-06-30
dale voy a probarlo y te digo...

---

### Post by gaston89 on 2009-07-01
Lamento mucho la tardanza, pero hacer lo mismo con "sudo" es lo mismo...
sigo teniendo el problema...

el error es el siguiente:

Se ha producido un error en la biblioteca de entrada-salida ('No se pudo trabar el dispositivo'): La cámara ya está en uso.
*** Error (-60: «No se pudo trabar el dispositivo») *** 
--------

y cuando ejecuto el comando "--debug"  me muestra el siguiente listado de depuración:

0.000378 main(2): INCLUYA SIEMPRE LA SIGUIENTE LÍNEA CUANDO ENVÍE MENSAJES DE DEPURACIÓN A LA LISTA DE DISTRIBUCIÓN DE CORREO:
0.000501 main(2): gphoto2 2.4.0
0.000588 main(2): gphoto2 has been compiled with the following options:
0.000615 main(2):  + gcc (C compiler used)
0.000633 main(2):  + popt (mandatory, for handling command-line parameters)
0.000649 main(2):  + exif (for displaying EXIF information)
0.000664 main(2):  + cdk (for accessing configuration options)
0.000678 main(2):  + no aa (for displaying live previews)
0.000693 main(2):  + jpeg (for displaying live previews in JPEG format)
0.000708 main(2):  + readline (for easy navigation in the shell)
0.000736 main(2): libgphoto2 2.4.2
0.000765 main(2): libgphoto2 has been compiled with the following options:
0.000782 main(2):  + gcc (C compiler used)
0.000798 main(2):  + ltdl (for portable loading of camlibs)
0.000817 main(2):  + EXIF (for special handling of EXIF files)
0.000834 main(2): libgphoto2_port 0.8.0
0.000856 main(2): libgphoto2_port has been compiled with the following options:
0.000873 main(2):  + gcc (C compiler used)
0.000891 main(2):  + ltdl (for portable loading of camlibs)
0.000905 main(2):  + USB (libusb, for USB cameras)
0.000920 main(2):  + serial (for serial cameras)
0.000935 main(2):  + no resmgr (serial port access and locking)
0.000949 main(2):  + no baudboy (serial port locking)
0.000965 main(2):  + no ttylock (serial port locking)
0.000983 main(2):  + no lockdev (serial port locking)
0.001000 main(2): CAMLIBS env var not set, using compile-time default instead
0.001018 main(2): IOLIBS env var not set, using compile-time default instead
0.001065 setting/gphoto2-setting.c(2): Creating $HOME/.gphoto
0.001310 setting/gphoto2-setting.c(2): Loading settings from file "/home/gaston/.gphoto/settings"
0.001546 gp-camera(2): Freeing camera...
0.001595 gphoto2-port(2): Liberando puerto...
0.001623 libgphoto2/gphoto2-filesys.c(2): Clearing fscache LRU list...
0.001641 libgphoto2/gphoto2-filesys.c(2): fscache LRU list already empty
0.001662 gphoto2-filesystem(2): Internally deleting all folders from '/'...

espero q sirva de algo..
gracias

---

