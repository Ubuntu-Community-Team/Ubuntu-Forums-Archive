---
title: "Problema de Resolucion / quiero apuñalar el monitor"
date: 2010-03-16
forum: Software
---

### Post by juancho_777 on 2010-03-16
hola amigos!
paso a contarles un problema que tengo en la PC de mi novia...
tengo en dual boot WinXP y Kubuntu KK, con el kernel actualizado.
al iniciar kubuntu arranca en 800x600px de resolucion, lo que hace que toda la pantalla se vea exageradamente grande, y los jueguitos de facebook (adicción irremediable de mi novia) se ven todos fuera de margen y mucho mas grande que el tamaño del navegador. ahora bien voy a "preferencias de sistema" y configuro las opciones de pantalla para que funcione en 1024x768px, y ahi todas las ventanas parecen verse normal, con la única excepción que las letras están exageradamente pequeñas, por ejemplo en el Kmess es imposible leer la lista de contactos. ahora bien, yo necesito lograr que la pantalla este en 1024x768px y que además las letras esten en un tamaño normal para que se puedan leer. a esto se le suma el problema de que al reiniciar la PC vuelve a la resolucion de 800x600.
es un problema que realmente molesta muchisimo.
me pueden ayudar?, nose si es un problema de drivers o del xorg.conf (el cual no existe y no entiendo como crearlo correctamente)

aca les copio el lspci para que vean la placa de video

> melisa@melisa-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC
*Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)


desde ya muchisimas gracias gente!
un abrazo grande!

---

### Post by guillermolisi on 2010-03-16
Y de que monitor estamos hablando ? Es TRC o TFT/LED ? Marca, modelo ? Y si podes, resolucion maxima y frecuencias de refresh vertical y horizontal (se que tal vez sea mucho pedir, pero si no lo buscas vos lo tendremos que hacer los demas).

Hasta 1024x768 sabemos que funciona. Luego, el tamaño de las letras se puede ajustar para que no tenga esa desproporcion (si es que no fueron ajustadas antes y sea esto lo que produce ese efecto).

---

### Post by juancho_777 on 2010-03-16
Hola Guille!, gracias por molestarte.
perdon por no poner la info antes...

el monitor es un Samsung 750s 17" (CRT)
Resolución Máxima: 1280 x 1024 / 60Hz
Resolución Recomendada: 1024 x 768 / 85Hz
Frecuencia Horizontal: 30-70 KHz
Frecuencia Vertical: 50-160 Hz

en caso de que falte alguna característica mas del monitor, aca estan las especificaciones completas: [http://www.pcstats.com/articleview.cfm?articleid=530&page=2]("http://www.pcstats.com/articleview.cfm?articleid=530&page=2")

Las letras no las modifiqué en ningún momento, este problema de resolución está desde el primer momento que usé kubuntu en esa máquina.

Muchas Gracias.

---

### Post by guillermolisi on 2010-03-16
Ese Kubuntu esta actualizado al dia, es decir con todos los parches y KDE 4.4.1 ?

Te pregunto porque con esa placa Intel deberias poder lograr la maxima resolucion del monitor, a menos que la RAM de la maquina no sea suficiente como para que el BIOS le asigne mas memoria a la placa de video on board.

Se podria probar de modificar el /etc/X11/xorg.conf para que "sepa" que resolucion por defecto debe utilizar al inicio pero lo que mas me llama la atencion es ese detalle del tamaño de las letras (nada que no se pueda arreglar en KDE).

En el /etc/X11/xrog.conf deberia agregarse algo asi:
```
Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Samsung"
    Modelname    "Samsung SyncMaster 750(M)s(T)"
    Horizsync    30-70
    Vertrefresh    50-160
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
## "Configured Monitor" es el nombre que debe coincidir con la referencia declarada en
##  la seccion "Monitor"
    Monitor        "Configured Monitor"
## "Configured Video Device" es el nombre que debe coincidir con la referencia
## declarada en la seccion "Device"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    1024
        Modes        "1280x1024@60"    "1400x1050@60"    "1280x960@60"    "1152x864@75"    "1024x768@43"    "1024x768@60"    "1024x768@70"    "1024x768@75"    "1024x768@85"    "832x624@75"    "800x600@60"    "800x600@85"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@85"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection

```con esta configuracion hacia funcionar el mismo monitor que tenes con driver VESA a 1280x1024 desde Hardy en adelante.

---

### Post by juancho_777 on 2010-03-16
si, Kubuntu está actualizado al día; de RAM tiene 1Gb, asi que no debería haber ningún problema por ese lado.
gracias por la ayuda... pero no existe ningun xorg.conf; a lo mejor mi consulta es muy básica, pero ¿cómo genero un xorg.conf nuevo?... o si tenes uno completo para ponerme y que lo pueda copiar.

esta noche en casa de mi novia pruebo esto de modificar el xorg.conf y te cuento como me fue :)

Muchas Gracias!

---

### Post by guillermolisi on 2010-03-16
Adjunto uno completo del cual tome las partes de ejemplo asi no tenes que escribirlo desde cero.

---

