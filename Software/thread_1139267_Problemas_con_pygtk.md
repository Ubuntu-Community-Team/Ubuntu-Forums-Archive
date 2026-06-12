---
title: "Problemas con pygtk"
date: 2009-04-26
forum: Software
---

### Post by josecuervo86 on 2009-04-26
Hola a todos!

Hay un módulo que se llama pygtk que me esta trayendo un par de problemas. Ya se que cambio de nombre (o al menos eso me dijieron) pero el tema es que antes en Intrepid no podía hacer funcionar screenlets por que requería ese módulo. Ahora en Jaunty no puedo hacer andar ni Totem ni rhythmbox porque al ejecutarlos desde consola me tiran el error diciendo que requieren ese bendito modulo.

La pregunta es: hay alguna forma de importarlo?

---

### Post by pablo.s on 2009-04-26
> **josecuervo86 said:**
> hay alguna forma de importarlo?

**[COLOR=Green]sudo apt-get install python-gnome2-extras[/COLOR]**

---

### Post by josecuervo86 on 2009-04-26
Pablo, me dice que ya lo tengo. Es muy raro esto. Hasta la actualización me andaban Totem y Rhythmbox a pesar de necesitarlo, pero ahora misteriosamente ellos tambien se niegan a abrir. Trate de compilarlo desde la fuente, pero debe necesitar alguna dependencia asique voy a seguir buscando.

Igual se agradecen nuevas sugerencias

---

### Post by pablo.s on 2009-04-26
Igual Cuervo, ni Totem ni Rhythmbox necesitan
de PyGTK, me resulta extrañisimo que te lo pida...

Podés pegar el mensaje de error, para analizarlo?

---

### Post by josecuervo86 on 2009-04-26
** (totem:14222): WARNING **: Could not import pygtk
ImportError: No module named pygtk
Fallo de segmentación
josecuervo86@josecuervo86-desktop:~$ 

(rhythmbox:14226): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Fallo de segmentación

Te puse lo último que tira, porque antes pone esto en ambos, que para mi no tiene nada que ver:

/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:84: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:85: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:207: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:238: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:251: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:277: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:307: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:331: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

O_o

---

### Post by pablo.s on 2009-04-26
Lo ultimo que te pone es una queja sobre
la compatibilidad del tema Murrine, casi
siempre se queja.

Guarda que ahi te está dando fallo de 
segmentación después de lo de PyGTK, 
que es más importante, asi que yo por
mi parte descarto que sea la causa, y me
fijaria si no hay algun conflicto con...
ya sabes que desactivar y fijate si sigue
dando el fallo.

---

### Post by josecuervo86 on 2009-04-26
jajaja, dale, ahora pruebo y te digo

---

### Post by josecuervo86 on 2009-04-26
Todo igual, es bastante raro, lo reconozco. Voy a ver si hay reportado algun bug en launchpad y vulevo

---

### Post by josecuervo86 on 2009-04-26
The exact same thing (?)

> Binary package hint: totem

Description: Ubuntu 9.04
Release: 9.04

totem:
  Installed: 2.26.1-0ubuntu5
  Candidate: 2.26.1-0ubuntu5
  Version table:
 *** 2.26.1-0ubuntu5 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
        100 /var/lib/dpkg/status

Well, I expect it to work and open up.

What happened instead is it crashes and the output it gives me in the console is this...

** (totem:21700): WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault

I have pygtk installed though according to Synaptic so I don't see what the problem is. I've tried reinstalling it and reinstalling totem and nothing changes...

Reportadisimo

---

### Post by pablo.s on 2009-04-26
Che pero a mi me funciona de periias

Instalado desde la Alternate.

---

### Post by josecuervo86 on 2009-04-27
Yo actualize desde Ineternet :S....Voy a hacerle un seguimiento al bug a ver que pasa. Lo raro es que este problema de pygtk ya me lo tiraba screenlets antes, y supuestamente ya lo tengo!!!

---

### Post by josecuervo86 on 2009-05-10
Solucionado!

El problema se debia a una instalación erronea de python. Lo unico que tuve que hacer fue borrar todos los archivos que empezaban con "python" de mi /usr/local/bin y el problema se soluciono :D

---

