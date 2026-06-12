---
title: "Parpadeo de google earth karmic 64 bit"
date: 2009-12-17
forum: Software
---

### Post by asterix77 on 2009-12-17
Acabo de bajar el .bin de google earth de su página oficial. Al instalarlo aparece lo siguiente

$ sudo chmod 777 GoogleEarthLinux.bin 
$ ./GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.1.3533.1731..............................................................
loki_setup: Valor del tamaño sospechoso para la opción option

/usr/lib/gio/modules/libgiogconf.so: clase ELF errónea: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: clase ELF errónea: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: clase ELF errónea: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
loki_setup: Valor del tamaño sospechoso para la opción option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...


Al ejecutarlo se abre y pregunta detalles acerca de la configuración propia inicial (solo la primera vez que se ejecuta). Al aparecer la tierra, se puede ver un parpadeo incesante, que realmente no deja realizar nada el el.

He desactivado los efectos de compiz, dejándo solo metacity, y nada.

*  Uso Karmic 64 bit
*  lspci entre otras cosas arroja
       01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

*   glxinfo arroja lo siguiente al principio

     name of display: :0.0
     display: :0  screen: 0
     direct rendering: Yes
     server glx vendor string: SGI
     server glx version string: 1.2
     ..........

*   5097 frames in 5.0 seconds
5283 frames in 5.0 seconds
5229 frames in 5.0 seconds
5277 frames in 5.0 seconds
5272 frames in 5.0 seconds
1298 frames in 5.0 seconds
436 frames in 5.0 seconds
437 frames in 5.0 seconds
437 frames in 5.0 seconds
435 frames in 5.0 seconds
418 frames in 5.0 seconds
4637 frames in 5.0 seconds
5342 frames in 5.0 seconds
5343 frames in 5.0 seconds
5411 frames in 5.0 seconds

Los valores más bajos (app 436), son los que se muestran cuando le doy pantalla completa a los engranajes (me tiende a parpadear un poco al maximizar).

Creo que a lo mejor el parpadeo son por los errores descritos al instalar la aplicación

¿se debe a eso?¿que significan esos errores?¿Se pueden solucionar?

Lo curioso es que esos archivos están en la ruta descrita.

Espero que me puedan ayudar, saludos

---

### Post by CdK1 on 2009-12-22
Ejecuta el google earth con metacity, y sigue estos pasos:

1.- Activa el modo seguro del programa: [FONT=courier new][/FONT]Menu  herramientas -> opciones -> modo de graficos -> Modo seguro activado

2.- Sino funciona, trata de usar el deb de los repositorios de medibuntu
3.- Sino, borra todo lo que hiciste anteriormente
4.- Actualiza y upgradea
5.- Verifica que tienes las librerias de compatibilidad de 32 bits:
                   
           - ia32-libs
           - lib32nss-mdns

[FONT=courier new][/FONT][FONT=courier new][/FONT][FONT=courier new][/FONT]6.- Baja GoogleEarthLinux.bin desde earth.google.com
7.- Dale permisos de ejecucion "chmod +x"
8.- Como root borra: [FONT=courier new]/opt/google-earth/libcrypto.so.XXX[/FONT]
__[FONT=courier new][/FONT]

---

### Post by asterix77 on 2009-12-24
CDk1 gracias por responder

Te comento que seguí todas las sugerencias, pero todo sigue igual. Instalé el binario, lo desinstalé, coloqué el de los repositorios, y nada.

Lo curioso es que cuando usaba intrepid, me funcionaba perfectamante en metacity, y ahora que mi aceleraci&#324; gráfica mejoró notablemente con karmic, me sucede esto.

Curioso.


Saludos

---

### Post by CdK1 on 2010-01-01
Te recomiendo que leas este hilo...

[http://ubuntuforums.org/showthread.php?t=1353158](http://ubuntuforums.org/showthread.php?t=1353158)

---

