---
title: "Como ver Tv en Ubuntu?"
date: 2010-08-31
forum: Software
---

### Post by diegol3d on 2010-08-31
Hola chicos. Poseo Ubuntu 10.04 y me gustaria saber si puedo ver la  TV en este hermoso mundo. Poseo una sintonizadora de TV  Compro  VideoMate TV Gold+ II. estuve leyendo y se me complica mucho, ya que soy  novato y para mi es muy nuevo todo. lei que habia que editar unas  lineas pero la verdad que no se como es. Para ir ganando tiempo les  comento que instale el TVTIME y no toma ninguna señal. Con el comando  "lspci -nn" me sale:


 04:05.0 Multimedia controller [0480]: Philips Semiconductors  SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev 10)


 Espero que me puedan dar una mano, aunque sea para decirme que es imposible. Saludos.

---

### Post by Applelnx on 2010-09-01
Hola diego, proba haciendo lo siguiente:

$ sudo rmmod saa7134
$ sudo modprobe saa7134 card=62

Con eso lo que haces es primero sacar el modulo que Ubuntu cargo por defecto, y despues cargas el modulo indicandole que modelo de tarjeta es (segun la siguiente lista [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134))

Un comentario aparte. A mi no me funcionaba nada hasta que le saque los efectos de escritorio. Avisa como te fue.

Saludos

---

### Post by mama21mama on 2010-09-01
Hola, yo tenia una mas o menos igual chip saa7130 y me andaba con [esta config]("http://mamalibre.eshost.com.ar/?q=content/tv-tuner-pro-enltv-fm-con-chip-saa71304"). Espero te sirva, saludos.

---

### Post by diegol3d on 2010-09-02
Hola chicos, gracias por contestar. les cuento que hice las 2 formas que postean y no pasa naranja. 3 cosas:
1) ni idea como saco los efectos del escritorio
2) como dije antes no tengo señal de las 2 formas, o poniendo la linea de comando, o editando el archivos como lo dice ahi. pero cuando edito me aparece en blanco. solo pongo esa linea, es decir: no hay nada hasta que pongo la linea esa. esta bien?
3) lo ultimo: en la configuracion del TVTime no logro que me tome cable. Esto es: Gestion de canales - cambiar tabla de frecuencia - personalizada. porque no esta argentina. y cuando pongo escanear canal no hace nada. es imposible?

---

### Post by mama21mama on 2010-09-02
> **diegol3d said:**
> Hola chicos, gracias por contestar. les cuento que hice las 2 formas que postean y no pasa naranja. 3 cosas:
1) ni idea como saco los efectos del escritorio

**Boton derecho, allí hay una solapa...**

> 2) como dije antes no tengo señal de las 2 formas, o poniendo la linea de comando, o editando el archivos como lo dice ahi. pero cuando edito me aparece en blanco. solo pongo esa linea, es decir: no hay nada hasta que pongo la linea esa. esta bien?

**Si**

> 3) lo ultimo: en la configuracion del TVTime no logro que me tome cable. Esto es: Gestion de canales - cambiar tabla de frecuencia - personalizada. porque no esta argentina. y cuando pongo escanear canal no hace nada. es imposible?

**Proba con otro para ir descartando si es problema de config del tvtime**

---

### Post by diegol3d on 2010-09-02
La solapa que me decis no la encuentro. si hago mouse derecho en el escritorio no me sale esa opcion. Probe con todas y no agarra señal. Estoy al horno?
P-D: Cuando abro por primera vez el tvtime me lo abre sin problemas, pero cuando lo cierro y lo quiero abrir de nuevo no se ejecuta. fijandome en el comando me sale esto:

diego@diego-desktop:~$ tvtime
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /home/diego/.tvtime/tvtime.xml
/home/diego/.tvtime/stationlist.xml: No existing PAL-N station list "custom".
videoinput: Driver refuses to set norm: Argumento inválido

    Your capture card driver: saa7134 [Compro VideoMate TV Gold+II/PCI:0000:04:05.0/527]
    does not support full size studio-quality images required by tvtime.
    This is true for many low-quality webcams.  Please select a
    different video device for tvtime to use with the command line
    option --device.

Fallo de segmentación

---

### Post by josecuervo86 on 2010-09-02
Para quitar los efectos de escritorio hace lo siguiente: anda a **Sistema > Preferencias > Apariencia** y en la solapa **Efectos visuales** selecciona **ninguno**

Saludos!

---

### Post by Applelnx on 2010-09-03
Diego podrias postear que resultado te tira en la consola cuando pones:

$ sudo rmmod saa7134
$ sudo modprobe saa7134 card=62
$ tvtime

Un comentario al margen, tengo entendido que la norma argentina es PAL-Nc. Fijate si podes cambiarla.

---

### Post by diegol3d on 2010-09-03
Lo he hecho sin ningún resultado. He notado que en todos menos en pal-n (norma de argentina de cable) me deja setear "cable" , pero en pal-n no. ja! increible...
Como no Applelnx!

diego@diego-desktop:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
diego@diego-desktop:~$ sudo modprobe saa7134 card=62
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
diego@diego-desktop:~$ tvtime
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /home/diego/.tvtime/tvtime.xml

Edito: tenias razon, en argentina es PAL-Nc. Tengo imagen!!!
solo 2 cosas:
1) no tengo sonido :(
2) solo me escanea 20 canales: del 62 al 82
igual es un gran avance! si me ayudan a resolver esos 2 puntos soy gardel, lepera y los guitarristas

[[IMG]http://img831.imageshack.us/img831/4238/pantallazodk.th.png[/IMG]]("http://img831.imageshack.us/i/pantallazodk.png/")

[]("http://imageshack.us")

---

### Post by diegol3d on 2010-09-03
Edito 2: muchachos ya  tengo todos los canales! desisntale he instale de nuevo y tengo todos los canales!!! y el sonido lo resolví conectando directamente a la placa de TV. lastima que mediante el cable puente (placa a placa) no se escucha, ya que tengo que desenchufar el cable de mi placa X-Fi y enchufarlo a la placa de TV cada vez que quiero ver la TV, pero tampoco es la muerte de nadie, por lo menos tengo TV! 
Gracias a todos!!!

---

