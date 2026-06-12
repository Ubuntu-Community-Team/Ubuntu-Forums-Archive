---
title: "Resolucion pantalla Kubuntu"
date: 2009-12-21
forum: Software
---

### Post by Mustaine666 on 2009-12-21
BUeno les comento.. yo utilizo la resolución 1024x768 .. en un monitor tubo de 15 pulgadas (4:3) .. y resulta que cuando inicio kubuntu inicia en 800x600 .. y cada vez que reinicio tengo que configurarlo.. en 1024x768 .. hay alguna forma de que inicie  en 1024x768?? ..


desde ya muchas gracias!

---

### Post by guillermolisi on 2009-12-21
Que version de Kubuntu usas ?

Configuraste algo en el archivo /etc/X11/xorg.conf o esta original ?

---

### Post by Mustaine666 on 2009-12-22
uso kubuntu Karmic Koala.. el archivo esta original

---

### Post by CdK1 on 2009-12-22
Debes crear tú propio /etc/X11/xorg.conf para darle la resolución que quieras...

sudo [COLOR=#000099]dpkg-reconfigure xserver-xorg[/COLOR]

---

### Post by Mustaine666 on 2009-12-24
y como se hace eso?

---

### Post by guillermolisi on 2009-12-24
> **Mustaine666 said:**
> y como se hace eso?
Editando el archivo mencionado con algun editor de texto plano, tipo nano, gEdit, Kate, etc.
Te muestro como lo estoy usando en una de las PCs con Kubuntu 9.10 y palca nVidia 6200 para que no me pase ese efecto que mencionas (muestro las secciones mas relevantes):
```
Section "Monitor"
        Identifier     "Samsung"
        VendorName     "Samsung"
        ModelName      "Samsung SyncMaster 794MB/794MBplus/798MB"
        HorizSync       30.0 - 70.0
        VertRefresh     50.0 - 160.0
        Gamma           1
        ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
        ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
        ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
        ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
        ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
        ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
        ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
        ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
        ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
        ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
        ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
        ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
        ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
        ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
        ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
        ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Screen"
        Identifier     "Default Screen"
        Device         "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
        Monitor        "Samsung"
        Option         "NoLogo" "True"
        DefaultDepth    24
       [COLOR=RoyalBlue] SubSection "Display"
                Virtual     1280 1024
                Depth       24[/COLOR]
                Modes      "1280x1024@60" "1400x1050@60" "1280x960@60" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
        EndSubSection
EndSection

Section "Screen"
        Identifier     "screen1"
        Device         "device1"
        Monitor        "monitor1"
        DefaultDepth    24
        Option         "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth       24
                Modes      "640x480@60" "640x480@72" "640x480@75" "640x480@85"
 "800x600@56" "800x600@72" "800x600@75" "800x600@85" "800x600@60" "832x624@75" "1024x768@85" "1024x768@75" "1024x768@70" "1024x768@60" "1024x768@43" "1152x864@75" "1280x960@60" "1280x1024@60" "1400x1050@60"
        EndSubSection
EndSection
```Los valores en las variables HorizSync y VertRefresh corresponden a la marca y modelo de monitor mencionados. Tenes que revisar las caracteristicas del tuyo y colocar los correspondientes para lograr un funcionamiento adecuado.

En este caso y por lo marcado en color azul, siempre que inicio la maquina el escritorio KDE la resolucion es de 1280x1024

---

### Post by Mustaine666 on 2009-12-24
no esta el archivo xorg.conf en la ruta indicada.. :confused: 

y no lo encuentro. que puede ser?

---

### Post by guillermolisi on 2009-12-24
> **Mustaine666 said:**
> no esta el archivo xorg.conf en la ruta indicada.. :confused: 

y no lo encuentro. que puede ser?
En el post #4 tenes una forma de generarlo, lo hiciste ?

---

### Post by Mustaine666 on 2009-12-24
> **guillermolisi said:**
> En el post #4 tenes una forma de generarlo, lo hiciste ?

.


no puedo crear ni borrar nada en  /etc/X11/ 

tampoco pegar.. ni copiar

---

### Post by guillermolisi on 2009-12-24
> **Mustaine666 said:**
> .


no puedo crear ni borrar nada en  /etc/X11/ 

tampoco pegar.. ni copiar
Ni siquiera usando "sudo" ?

Mostranos la salida de ```
ls -al /etc/X11
``` asi vemos los permisos.

---

### Post by NickCis on 2009-12-24
Tenes que iniciar en el modo de recuperacion, (viste que en el grub tenes varias opciones, bue, la segunda) y ahi te da un menu para distintas opciones para iniciar. Elegi la qe te da salida a root con red, netroot creo q era o algo asi.

Ahi, ejecutamos el siguiente comando:
```
Xorg -configure
```

Esto te genera el xorg en la carpeta /root llamado xorg.conf.new
Este archivo lo editas a tu gusto.
Para forzar la resolucion tenes qe agregar/modificar los valores HorizSync y VertRefresh de la seccion "Monitor"(Son las tasas de refresco y son necesarias para forzar la resolucion). Un ej:
```

Section "Monitor"
        Identifier   "Configured Monitor"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    30-107
        VertRefresh  48-120
EndSection

```

Y la resolucion la forzas en la seccion "Screen"(en modes, tenes qe poner la resolucion qe qeres qe sea, acordate qe tiene qe estar soportada por tu placa), te paso un ejemplo:
```

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth 24
        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1024x768"
        EndSubSection
EndSection

```.

Esto lo copiamos a donde debe estar con el siguiente comando:
```
cp xorg.conf.new /etc/X11/xorg.conf
```
Y listo, al reiniciar tendria qe estar funcionando de no ser asi. Para volver la configuracion como estaba antes, iniciar devuelta en este modo y borrar el archivo qe creamos:
```
rm  /etc/X11/xorg.conf
```

Fuente: [http://www.ubuntu-es.org/?q=node/120319#comment-347394](http://www.ubuntu-es.org/?q=node/120319#comment-347394)

Saludos y suerte =P.
P.D.: La explicacion de esto, es qe las nuevas verciones de Xorg, ya no nececitan mas el archivo de configuracion, es opcional, si existe lo usan, pero de no ser asi, carga una configuracion.

---

### Post by Mustaine666 on 2009-12-25
```

drwxr-xr-x   9 root root  4096 2009-12-06 20:20 .
drwxr-xr-x 132 root root 12288 2009-12-25 15:31 ..
drwxr-xr-x   2 root root  4096 2009-10-28 18:39 app-defaults
drwxr-xr-x   2 root root  4096 2009-10-28 18:40 cursors
-rw-r--r--   1 root root    13 2009-10-28 18:41 default-display-manager
drwxr-xr-x   6 root root  4096 2009-10-28 18:37 fonts
-rw-r--r--   1 root root 17394 2009-06-22 19:57 rgb.txt
lrwxrwxrwx   1 root root    13 2009-11-30 21:00 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2009-10-28 18:39 xinit
drwxr-xr-x   2 root root  4096 2009-10-28 18:33 xkb
drwxr-xr-x   2 root root  4096 2009-12-06 20:20 Xresources
-rwxr-xr-x   1 root root  3730 2008-06-24 23:05 Xsession
drwxr-xr-x   2 root root  4096 2009-12-06 20:20 Xsession.d
-rw-r--r--   1 root root   265 2008-06-24 23:05 Xsession.options
-rw-r--r--   1 root root    13 2009-08-24 21:37 XvMCConfig
-rw-------   1 root root   601 2009-10-28 18:33 Xwrapper.config

```

esa es la salida de  ls -al /etc/X11

---

### Post by guillermolisi on 2009-12-25
> **Mustaine666 said:**
> ```

drwxr-xr-x   9 root root  4096 2009-12-06 20:20 .
drwxr-xr-x 132 root root 12288 2009-12-25 15:31 ..
drwxr-xr-x   2 root root  4096 2009-10-28 18:39 app-defaults
drwxr-xr-x   2 root root  4096 2009-10-28 18:40 cursors
-rw-r--r--   1 root root    13 2009-10-28 18:41 default-display-manager
drwxr-xr-x   6 root root  4096 2009-10-28 18:37 fonts
-rw-r--r--   1 root root 17394 2009-06-22 19:57 rgb.txt
lrwxrwxrwx   1 root root    13 2009-11-30 21:00 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2009-10-28 18:39 xinit
drwxr-xr-x   2 root root  4096 2009-10-28 18:33 xkb
drwxr-xr-x   2 root root  4096 2009-12-06 20:20 Xresources
-rwxr-xr-x   1 root root  3730 2008-06-24 23:05 Xsession
drwxr-xr-x   2 root root  4096 2009-12-06 20:20 Xsession.d
-rw-r--r--   1 root root   265 2008-06-24 23:05 Xsession.options
-rw-r--r--   1 root root    13 2009-08-24 21:37 XvMCConfig
-rw-------   1 root root   601 2009-10-28 18:33 Xwrapper.config

```esa es la salida de  ls -al /etc/X11
Esta todo bien asi que tranquilamente deberias poder generar el archivo xorg.conf con lo que te han sugerido en el post #4.
Tambien podrias crearlo vacio con ```
sudo touch /etc/X11/xorg.conf
``` luego deberias poder editarlo (siempre usando sudo).

---

