---
title: "[SOLVED] Ventanas &quot;gelatinosas&quot; sin compiz. Posible?"
date: 2009-07-12
forum: Software
---

### Post by Mauro22 on 2009-07-12
Holas!!


Eso, actualmente estoy trabajando con metacity y composite para que tenga transparencias y pueda usar AWN.


Al desactivar compiz, gané muchisimo rendimiento... pero lo unico que extraño es el efecto de "gelatina" en las ventanas..


Es posible activar eso solo sin usar compiz??


Saludos!!

---

### Post by Hei Ku on 2009-07-12
No, es un plugin de Compiz. Aunque podrías activar Compiz, desactivar el resto de los efectos y dejar solo ese, a ver cómo anda.

---

### Post by Mauro22 on 2009-07-12
Gracias Hei Ku!


Lo hice (desactivar todo menos ese) y se me sigue colgando y cuando no se cuelga, pierdo rendimiento...


Parece que tengo que desistir de ese efecto..

---

### Post by granjero on 2009-07-15
si mal no recuerdo apenas instalé por primera vez ubuntu (8.04) con sólo ir a *Sistema>Preferencias>Apariencia>solapa de efectos visuales* y tildar efectos extra las ventanas gelatinosas ya andan!

eso es sin tener que instalar compiz si mal no recuerdo.

salud!

---

### Post by Hei Ku on 2009-07-15
Pero seguis usando Compiz. Solo que no te lo dice.

---

### Post by juancarlospaco on 2009-07-15
Lo curioso es que** si **hay un Metacity mejorado que tiene ventanas y menus gelatinosos,
sin Compiz, ni Emerald, usa OpenGL o no por Software, 
sin nVidia, ni ATI, hecho con una notebook muy austera,
pero nunca fue publicado empaquetado hasta ahora, 
se llama **[SIZE="3"]Luminocity[/SIZE]**, hay codigo fuente disponible,
esta en la web de desarrollo de Gnome.

Inclusive hay Videos:

[LIST]
[*]**[SIZE="3"][VIDEO1]("http://www.gnome.org/~seth/blog-images/monkey-hoot/WobblyWindows.ogg")[/SIZE]**
[*]**[SIZE="3"][VIDEO2]("http://www.gnome.org/~seth/blog-images/monkey-hoot/WobblyWindowsIntro.ogg")[/SIZE]**
[*]**[SIZE="3"][VIDEO3]("http://www.gnome.org/~seth/blog-images/monkey-hoot/MovieOfMovie.ogg")[/SIZE]**
[*]**[SIZE="3"][VIDEO4]("http://www.gnome.org/~seth/blog-images/monkey-hoot/TransparentWindows.ogg")[/SIZE]**
[/LIST]


Inclusive reproduce Video en tiempo real en una ventana deformada,
que se yo, quien te dice es parte de Gnome 3.0, y nos sorprenden.

En conclusion, es posible, como? no lo se...

*Se ve claramente que no es Compiz, grandes misterios del escritorio GNU...*

---

### Post by pablo.s on 2009-07-15
Ese era el proyecto original
antes de Beryl, antes de Compiz.
En GNOME 3.0 Metacity se pasa
a llamar Mutter.

---

### Post by Mauro22 on 2009-07-16
Gracias a los dos!!

Estuve buscando info sobre luminucity y mutter pero no encontre como instalarlos..

Voy a seguir buscando a ver que onda!

---

### Post by juancarlospaco on 2009-07-16
> **pablo.s said:**
> 
En GNOME 3.0 Metacity se pasa
a llamar Mutter.

Pero yo use Mutter en Gnome Shell y es exactamente igual a Metacity.

Tambien tenian un proyecto de una especie de Gestor de Ventanas pero para Marcos y Botones,
cada boton podia tener un borde personalizado, y los marcos tambien.

*Lo que yo quiero es un Gestor de ventanas que haga cosas como Luminocity o Metisse.*

:)

---

### Post by Mauro22 on 2009-07-17
Vamos de guatemala a guatepeor...


Ayer intenté activar compiz y no me deja... "No se han podido activar los efectos"


Alguien tiene un xorg de intel andando con compiz?? porque Glxgears andan bien, o sea que acceleracion tengo...



Saludos!

---

### Post by Mister X on 2009-07-17
yo lo tengo, pero en Intrepid, no se si te sirva...

---

### Post by Mauro22 on 2009-07-17
Pasa, igual tengo backup!!


=D gracias!

---

### Post by Mister X on 2009-07-17
intel X3100 en Intrepid

---

### Post by Mauro22 on 2009-07-17
Gracias Mister X


Les comento!


Ajuste el xorg.conf con el de Mister X y levantó el video pero igual a antes, no me deja activar los efectos.

Esto es la salida del comando:

```
mauro@mauro-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
```

Y se me van los bordes de las ventanas...
:S

Volviendo a metacity...

---

### Post by Mister X on 2009-07-17
la sacaste de la blacklist de compiz?

creo que era en /usr/bin/compiz

---

### Post by Mauro22 on 2009-07-17
nop, no hice nada de eso...


Lo raro es que hace muchooo andaba... :S

---

### Post by Mauro22 on 2009-07-18
Listo el pollo =D


Les comento:


1) Baje el script de aca [0]. Sirve para hacer un chequeo de porque no anda compiz y te ayuda a arreglarlo casi automaticamente.

2) Lo corri y me dijo que se estaba usando un composite y si queria desactivarlo para correr compiz.

3) Le dije que Si. Ejecute compiz y listo :D


Ojala le sirva a alguien, en especial el script que esta muy bueno.


[0] [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)



Marquenlo como SOLVED

---

### Post by matias_tati on 2009-07-18
> **Mauro22 said:**
> Listo el pollo =D


Les comento:


1) Baje el script de aca [0]. Sirve para hacer un chequeo de porque no anda compiz y te ayuda a arreglarlo casi automaticamente.

2) Lo corri y me dijo que se estaba usando un composite y si queria desactivarlo para correr compiz.

3) Le dije que Si. Ejecute compiz y listo :D


Ojala le sirva a alguien, en especial el script que esta muy bueno.


[0] [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)



Marquenlo como SOLVED

Esta me puede servir para resolver mi problema? A mi me desaparecieron efectos del compiz y no se por que.

---

### Post by Mauro22 on 2009-07-19
Si, bajate el script. 

En la página dice como ejecutarlo y hace un par de pruebas y te tira Ok o Fail. 


A mi me lo arregló solo.

---

### Post by matias_tati on 2009-07-19
> **Mauro22 said:**
> Si, bajate el script. 

En la página dice como ejecutarlo y hace un par de pruebas y te tira Ok o Fail. 


A mi me lo arregló solo.

Me ayudas? No se bien lo que es un script y de ingles casi nada.

---

### Post by Mauro22 on 2009-07-19
Claro!


Abri un ventana de consola y poné:


1) wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check

Con eso bajas el script a tu PC

2) chmod +x compiz-check

Con eso le das permiso de ejecución

3) ./compiz-check

Con eso lo ejecutas.



Poné lo que te salga a partir del punto 3. y vemos como seguimos!

---

### Post by matias_tati on 2009-07-19
Me da todo ok pero los efectos que me desaparecieron siguen sin aparecer

[IMG]http://img505.imageshack.us/img505/294/pantallazomatiasmatias.png[/IMG]

---

### Post by Mister X on 2009-07-19
pero no tenes andando ningun efecto??? 

o solamente desaparecieron algunos?

---

### Post by Mauro22 on 2009-07-19
Tenes estos paquetes instalados?


compiz-fusion-plugins-extra
compiz-fusion-plugins-main

---

### Post by matias_tati on 2009-07-19
Si los tengo y si me desaparecieron solo algunos efectos como por ejemplo el de quemar la ventana y el del avioncito de papel que se dobla. Ahi se ve que no tengo el plugin add-ons.

---

