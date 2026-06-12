---
title: "No encuentro section en nano"
date: 2009-06-09
forum: Software
---

### Post by pablocerg on 2009-06-09
Hola a todos!

Estoy devuelta y a un paso de poder usar ubuntu, estoy ansioso.

segui los pasos que staar me dio por mi problema del monitor

[http://ubuntuforums.org/showthread.php?t=1179778](http://ubuntuforums.org/showthread.php?t=1179778)

Cuando me da "OUT OF RANGE" entro a ctrl+alt+f1, pongo mi usuario y contraseña y despues "sudo nano /etc/x11/xorf.conf"

Bueno cuando entro a este editor no se como encontrar la section "monitor" que necesito modificar. Expliquenme como tengo que hacer, gracias.

---

### Post by Hei Ku on 2009-06-09
Con las flechas hacia abajo, hasta que encuentres la seccion.

---

### Post by pablo.s on 2009-06-09
Te la hago mas simple:
en lugar de poner

**[COLOR=DarkGreen]sudo nano /etc/x11/xorg.conf[/COLOR]**

poné

**[COLOR=DarkGreen]sudo gedit /etc/x11/xorg.conf[/COLOR]**

después presioná CTRL + F y
escribi monitor.

---

### Post by Hei Ku on 2009-06-09
No va a poder usar gedit, porque no le carga bien el X. :$

---

### Post by pablo.s on 2009-06-09
Bueno, entonces consejo:

En nano, se graban las 
modificaciones con

[COLOR="DarkGreen"]**CTRL + O**[/COLOR]

y se sale con 

[COLOR="#006400"]**CTRL + X**[/COLOR]

con [COLOR="DarkGreen"]**CTRL + W**[/COLOR] se buscan
las palabras, por ejemplo: 
monitor

---

### Post by pablocerg on 2009-06-09
Una cosa mas cuando entro a nano /ect/x11/xorg.conf no veo ningun texto, esta mas abajo?

voy a usar ctrl+w cuando entre, ahora estoy haciendo unas cosas como en media hora voy a entrar a probar

---

### Post by pablocerg on 2009-06-09
Necesito una solución a ese problema, porque cuando entro a nano /etc/x11/xorg.conf no hay nada, ninguna línea escrita

pongo buscar y no encuentra nada :S

---

### Post by pablo.s on 2009-06-09
Umm. Probaste hacer

[COLOR="DarkGreen"]**sudo dpkg-reconfigure xserver-xorg -phigh**[/COLOR]

y ver si te reconstruye
el archivo xorg.conf?
Tu problema es muy facil
de arreglar, pero debemos
empezar por lo primero, que
es analizar el xorg.conf.

---

### Post by pablocerg on 2009-06-09
Ya voy a probar, si no vuelvo pronto es porque funcionó :)

gracias

---

### Post by pablocerg on 2009-06-09
puse sudo dpkg-reconfigure xserver-xorg -phigh

no recuerdo bien que dijo después, pero la cosa es que entré devuelta a nano y no funcionó

---

### Post by pablo.s on 2009-06-09
Probá si entra a la GUI.
¿Que tarjeta de video
tiene la maquina?

---

### Post by Mauro22 on 2009-06-09
La ruta es :


/etc/X11/xorg.conf


X11 no x11... si lo pones con minuscula, te va a crear un archivo vacio... porque el original esta en X11.

---

### Post by pablocerg on 2009-06-09
> **pablo.s said:**
> Probá si entra a la GUI.
¿Que tarjeta de video
tiene la maquina?

¿Cómo entro a la GUI?

Tengo NVIDIA 8400GS 512mb

---

### Post by pablocerg on 2009-06-09
> **Mauro22 said:**
> La ruta es :


/etc/X11/xorg.conf


X11 no x11... si lo pones con minuscula, te va a crear un archivo vacio... porque el original esta en X11.

Ouch!
Que tarado.

voy a probar, gracias. Que vergüenza

---

### Post by pablo.s on 2009-06-09
Pff, me arrodillo en
tres kilos de maiz...

Se me pasó a mi el error.

A la GUI entrás con

[COLOR="DarkGreen"]**startx**[/COLOR]

---

### Post by pablocerg on 2009-06-09
Ahora pude entrar y no tube problemas, veia todo y busque monitor, lo encontre y puse los datos que me dieron en este post

[http://ubuntuforums.org/showthread.php?t=1179778](http://ubuntuforums.org/showthread.php?t=1179778)

El problema de mi monitor no se solucionó, ¿Qué puedo hacer?

---

### Post by Mauro22 on 2009-06-09
Probaste hacer:


control + alt + + (control alt +)
control + alt + - (control alt -)

Para ir cambiando las resoluciones mientras te tira Out Of Range ?

---

### Post by pablocerg on 2009-06-09
> **Mauro22 said:**
> Probaste hacer:


control + alt + + (control alt +)
control + alt + - (control alt -)

Para ir cambiando las resoluciones mientras te tira Out Of Range ?

Voy a probar esto.

---

### Post by pablocerg on 2009-06-09
Siii estoy en ubuntu!!!

ahora estoy intentando instalar el driver de mi placa de video.

gracias.

Mi solución fue probar con ctrl+alt+ + y - hasta que ahora estoy en 1600x1200, veo medio mal pero ya voy a ver bien seguro, gracias

---

