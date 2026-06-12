---
title: "[SOLVED] Capturar TV con Mplayer?"
date: 2008-07-23
forum: Software
---

### Post by FlyerDie on 2008-07-23
Luego de lidiar un rato largo con otra  capturadora (en este caso una ENLTV-FM de Encore) ya que me la detectaba como GENERIC, la pude hacer funcionar con:

```
sudo modprobe saa7134 card=3
```

Configure por tvtime y me quedo funcionando HHAARMOSO. Queda solucionar un peque;o detalle que me queda siempre sonando la television por mas que cierre el programa...:confused:

Pero este seria un tema menor a lo que realmente me interesa, ya que esta maquina no la uso para otra cosa mas que grabar radio de internet y testing de cosas no multimedia (salvo lo que viene ahora).

Quisiera poder capturar TV, y se que con mplayer se puede...pero cuando corro:

```
mplayer tv:// on:driver=v4l:width=640:height=480:norm=palnc -vo xv
```

me el video como fuera de sintonia y no tengo opcion de cambiar ni de canal ni de mejorar la imagen.
Algo similar me habia pasado con el tvtime, pero cambie en la cofiguracion de:

*channel management / change frequency table / cable (por default en vez de venir cable viene broadcast)*

Y ahi empece a ver los canales perfectamente y en colores...
Pero en el mplayer me esta pasando lo mismo pero no se como llegar a esa parte de la configuracion como primera instancia, ya que el objetivo es poder capturar algun programa de tv :)

Como siempre, mil gracias a quien me de una manito :KS

---

### Post by tzulberti on 2008-07-23
Yo usaba el siguiente comando con el mencoder:
mencoder -tv  driiver=v4l2:width=640:height=480:norm=pal_nc:input=1:chanlist=us_cable:channel=43
-ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac
mp3lame -lameopts cbr:br=128 -endpos 30 -o outfile.mpg tv://

Es para grabar pero el mplayer no debe ser muy diferente...

Ahora no tengo mas la placa, pero lo que recuerdo es que aunque la imagen se veia bien, no tenia sonido...

---

### Post by FlyerDie on 2008-07-23
> **tzulberti said:**
> Yo usaba el siguiente comando con el mencoder:
mencoder -tv  driiver=v4l2:width=640:height=480:norm=pal_nc:input=1:chanlist=us_cable:channel=43
-ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac
mp3lame -lameopts cbr:br=128 -endpos 30 -o outfile.mpg tv://

Es para grabar pero el mplayer no debe ser muy diferente...

Ahora no tengo mas la placa, pero lo que recuerdo es que aunque la imagen se veia bien, no tenia sonido...

creo que pegaste en el blanco con el tema **chanlist=us_cable:channel=43**

Ya que ahi interpreto que estas usando cable (como lo que pongo yo en el tvtime) y le estas especificando el canal a ver :)

Estuve probando en algun momento el mencoder, pero creo que me alcahueteaba un bolonqui con algun codec (algo relativamente menor al caso). Pero por lo que recuerdo no era una linea con la info que vos pasaste sino una mas austera.

Cuando llegue a casa hago la prueba con esto que me pasas y de paso ver el tema ese del codec que seguramente salte denuevo :lolflag:.

Saludos y gracias!

---

### Post by FlyerDie on 2008-07-23
Tuve que hacer un pequenio toque a lo que me pasaste, pero igual sigo con un tema:


```
$ mencoder -tv driver=v4l2:width=640:height=480:norm=pal_nc:input=0:chanlist=us_cable:channel=43 -ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac mp3lame -lameopts cbr:br=128 -endpos 30 -o outfile.avi tv://
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 1600+ (Family: 6, Model: 6, Stepping: 2)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: LifeView/Typhoon FlyVIDEO2000
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = PAL; 5 = PAL-BG; 6 = PAL-H; 7 = PAL-I; 8 = PAL-DK; 9 = PAL-M; 10 = PAL-N; 11 = PAL-Nc; 12 = PAL-60; 13 = SECAM; 14 = SECAM-B; 15 = SECAM-G; 16 = SECAM-H; 17 = SECAM-DK; 18 = SECAM-L; 19 = SECAM-Lc;
 inputs: 0 = Television; 1 = Composite1; 2 = Composite2; 3 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : MONO
tv.c: norm_from_string(pal_nc): Bogus norm parameter, setting default.
**Unable to find selected channel list! (us_cable)**
Segmentation fault
```

De donde saco ese channel list?
Si se lo quito y pongo el canal se ve como si no utilizara antena...osea, selecciono uno de los canales de aire como el 11 o 13 y se ve con lluvia, medio desfazado (me refiero al archivo avi que fue capturando).
Es como que no usa la sintonizacion de canales...

---

### Post by Mauro22 on 2008-07-26
Pense que te habia respondido:

Yo para grabar uso mencoder:

```
mencoder -tv driver=v4l2:width=640:height=480:amode=1:device=/dev/video0 tv:// -o SALIDA.avi -oac lavc -ovc lavc
```Donde tv:// tendria que ir seguido del canal que queres grabar que se pueda ver en tvtime, yo no uso numero de canal porque solo tengo 1 (el 3 que es una imagen-espejo del deco de directv)

Despues, para comprimirlo esto:

```
mencoder ENTRADA.avi -o SALIDA.avi -ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac mp3lame -lameopts cbr:br=128
```Que es practicamente igual al tuyo solo que lo hago aparte porque por ahora no me sirve comprimir, dado que he logrado 10, 15 mb de diferencia.


TIP: Si en el 1 codigo dejas tv:// asi nomas, te va a grabar el canal sintonizado de tvtime automaticamente.

---

### Post by FlyerDie on 2008-07-28
Mauro, mil gracias por tu respuesta y disculpa que recien ahora contesto..es que no estuve con la pc estos dias.

Te comento, ponga canal o no en tv *tomando el que veo en tvtime, lo veo en blanco y negro (imagen tvtime1.png) cosa que en tvtime si la veo en color... (color.png)
Probe cambiendole la norma pero tampoco sirvio ya que probe con 0 que es NTSC, 11 pal/Nc, 10 pal/n y nada...:(

[I]EDIT: perdon..otras cosas que me olvidaba...en tvtime si tengo el 12 es canal 13...pero si pongo el 12 en forma forzada en el mencoder me toma TN...osea, como que no esta tomando correctamente lo mismo que en tvtime tengo configurado.
Otra cosa es que no captura el sonido, solo video.[/I]

---

### Post by leo_rockway on 2008-07-29
Esto es lo que me funcionó a mí tanto para mencoder como para mplayer (funcionan con sonido, color y todo): -tv norm=PAL-Nc:chanlist=us-cable tv://#
# es el número de canal que vos quieras.

Con poner la norma y el chanlist en mi caso fue suficiente.

##Fijate que es us-cable y no us_cable.##

---

### Post by FlyerDie on 2008-07-29
> **leo_rockway said:**
> Esto es lo que me funcionó a mí tanto para mencoder como para mplayer (funcionan con sonido, color y todo): -tv norm=PAL-Nc:chanlist=us-cable tv://#
# es el número de canal que vos quieras.

Con poner la norma y el chanlist en mi caso fue suficiente.

##Fijate que es us-cable y no us_cable.##

BINGO...!
ahora el video perfecto..pero el sonido tuve que tomarlo del MIC porque por lo visto del LINE IN no me estaba tomando el sonido para capturar pero si para poder escucharlo...:confused: pero realmente no me calienta, fue solo cambiar el plug de lugar :)

Ahora me surge otra consulta... antes como tenia  -endpos 30 solo me capturaba 30 segundos y el mencoder cortaba solito, ahora com oquiero capturar por un tiempo indefinido, no encontre otra manera de cortar al mencoder mas que hacerle un kill :( (si si..soy un cabeza)...cual es el comando de escape que tiene el mencoder? el mplayer es darle 2 veces a ESC, pero aca no es lo mismo.

Igualmente este es un tema 'cosmetico' ya que el problema principal ya esta solucionado, pero me gustaria saberlo..:lolflag:

Saludos y mil gracias!

---

### Post by Mauro22 on 2008-07-29
Para el mencoder, no se si tiene comando, para salir, pero con Control C cierra..

---

### Post by eldragon on 2008-07-29
para que no quede sonando la tv todo el tiempo: yo hice el siguiente script para ejecutar tvtime;
```

#!/bin/bash
amixer -c 0 set Line unmute cap
tvtime
amixer -c 0 set Line mute

```

guardalo en /usr/bin
y hacele chmod a+x para poder ejecutarlo.

cuando lo ejecutas. desmutea line el linein de la tarj de sonido.
ejecuta tvtime, y cuando sale tvtime, lo vuelve a mutear.

---

### Post by FlyerDie on 2008-07-29
Mauro, el control c, no me mata el proceso, sino que stopea el job (el proceso sigue cargado y consumiendo recursos)
Igual, como dije antes es cosmetico lo mio, y no me molesta hacer un kill.
Y lo del script esta muy piola dragon ;) voy a ver si hago algo asi.

gracias nuevamente!

---

### Post by leo_rockway on 2008-07-29
No sé si este script amerita su propio thread, así que se los dejo acá.
Yo sabía que tenía que haber una forma de hacer streaming de TV por LAN así que no paré hasta lograrlo. El script no es mio, yo solo lo modifiqué; lo saqué de una página para ver tele desde la EeePC [0]

```

#!/bin/sh
CHANNEL=${1:-TV1}
ssh -c blowfish -x -l USER SERVER \
"rm -f /tmp/tmp.tmp
 mkfifo /tmp/tmp.tmp
 /usr/bin/mencoder tv://${CHANNEL} \
          -vf pp=lb \
          -tv driver=v4l2:norm=PAL-Nc:chanlist=us-cable:audiorate=32000:adevice=/dev/dsp1:width=640:height=480:immediatemode=0 \
          -ovc lavc=1 \
          -lavcopts vcodec=mpeg4:vbitrate=2000 \
          -oac mp3lame \
          -lameopts vbr=1:br=32 \
          -srate 32000 \
          -o /tmp/tmp.tmp > /dev/null 2>&1 &
cat /tmp/tmp.tmp" | \
mplayer - -cache 128 -framedrop -vf scale=640:480 -vo xv
```

Hay que modificar USER y SERVER por lo que corresponda.
Suponiendo que el archivo se llama tv.sh, el uso sería ./tv.sh # (donde # es el número de canal).

Básicamente se está encodeando con mencoder y usando un pipe y conectando por ssh para hacer streaming con mplayer.

Cuando se termina de ver un canal hay que conectarse al servidor y matar el proceso de mencoder para poder volver a ver la tele usando este script.

Si tienen alguna pregunta me lo comentan y veo si puedo ayudarlos.

[0] [http://forum.eeeuser.com/viewtopic.php?id=23642](http://forum.eeeuser.com/viewtopic.php?id=23642)

---

### Post by Mauro22 on 2008-07-29
Siguien el tema:

Hay alguna forma de ver mientras se graba?  O sea, como hace mi placa en windows? o trato de usar wine con el programa privativo??

---

### Post by leo_rockway on 2008-07-29
¿Ver otro canal o ver lo mismo que estás grabando?

Si queres ver lo que estás grabando una variación del script que dejé me imaginó que funcionaría: es decir, encodear con mencoder y reproducir con mplayer. En el caso del script que dejé yo, no se está grabando nada sino sólo enviando por tubería, pero el concepto me parece que sería el mismo. Yo no veo tele en directo por LAN, veo un video que está siendo capturado con mencoder (de hecho tengo unos 3 segundos de delay entre lo que está pasando en la tele y lo que yo veo en mi laptop / cliente).

EDIT: el problema que le encuentro es que mplayer reproduce sólo lo que hay hasta el momento en que se lo ejecuta y no sigue leyendo el archivo a medida que crece. Sería cuestión de investigarlo...

---

### Post by Mauro22 on 2008-07-29
Cuando pongo a grabar con mencoder el tvtime muestra "sin señal" pero esta siendo grabada...

No se si puedo ver otro canal ya que tengo un solo (el 3) que me hace de un "canal espejo" del deco de directv.


La que me queda es prender la tv y verlo ahi. Pero me agarran ganas de hacer zapping etc y eso queda todo grabado :S:S:lolflag:

---

### Post by eldragon on 2008-07-29
en vez de tanta vuelta, por que no instalan el myth-backend que camina de lo lindo.

yo usaba tvtime para ver tele porque nunca me calente por poder grabar, pero me compre una notebook y para ver tv desde ahi tambien, instale mythtv, y veo tv inalambrica desde la notebook. graba mientras veo, lo dejo grabando....programo, e incluso uso tv_grab_ar para bajar la info de multicanal. algo muy bueno para programar television

---

### Post by Mauro22 on 2008-07-29
Probe mythtv y anda bien...

Pero soy medio kamikaze y me gusta saber como funcionan las cosas y adaptarlas a lo que quiero...

Ejemplo: Tengo todo hecho el script para grabar tv y/o programar grabaciones con tvtime... todo automatico.

---

### Post by leo_rockway on 2008-07-29
> **Mauro22 said:**
> 
Pero soy medio kamikaze y me gusta saber como funcionan las cosas y adaptarlas a lo que quiero...

Jaja, exacto...
Ademas quería probar ver tele desde la DS :lolflag: (ascii ftw).

---

### Post by FlyerDie on 2008-07-29
> **Mauro22 said:**
> 
Pero soy medio kamikaze y me gusta saber como funcionan las cosas y adaptarlas a lo que quiero...

Ejemplo: Tengo todo hecho el script para grabar tv y/o programar grabaciones con tvtime... todo automatico.

Lo mismo me pasa a mi..me gusta ver como funcionan las cosas, aunque no quita que un poco de facilismo no viene mal, pero me gusta la idea de crear scripts para grabar cuando quiero :)

---

### Post by FlyerDie on 2008-07-30
> **eldragon said:**
> e incluso uso tv_grab_ar para bajar la info de multicanal. algo muy bueno para programar television

Estuve viendo esto, y resulta que corro lo siguiente:

sudo tv_grab_ar --configure

me agrega todos los canales, luego:

sudo tv_grab_ar | tv_sort > programacion.xml

como para que me los tome el tvtime, pero puede ser que el tv_grab_ar tenga mal organizados los canales?

Pregunto esto porque vi que hay un script hecho por alguien de argenteam pero no entiendo como ejecutarlo, ya que tv_grab_ar me viene ya con el xmltv...:confused:

---

### Post by FlyerDie on 2008-07-31
me autorespondo :lolflag:
ya solucione el tema del xmltv, y veo los canales con la informacion sacada de multicanal :)

ahora les paso un tip que encontre, ya que las capturas me las hacia con el interlaced y generaba esas rayitas feas en la imagen, agregandole lo siguiente (en este caso en el comando veran que estoy capturando canal 14 y durante 60 segundos):

```
$ mencoder -tv driver=v4l2:width=640:height=480:norm=PAL-Nc:chanlist=us-cable **-vf pp=md** -ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac mp3lame -lameopts cbr:br=128 -endpos 60 -o outfile.avi tv://14

```

el **-vf pp=md** es lo que hace corregir el interlace y que sse capture FERPECTO :)

Genchi, disculpen si soy muy reiterativo en esto, pero calculo que a alguno que tenga interes en capturar programas de TV le puede servir..si alguien tiene algun otro tip para mejorar las capturas, bienvenido!!!

Saludos!

---

### Post by leo_rockway on 2008-08-01
> **FlyerDie said:**
> 
ya solucione el tema del xmltv, y veo los canales con la informacion sacada de multicanal :)

¿Podés contar como hiciste lo de tv_grab_ar? ¡Yo ni siquiera sabía que existía eso!

EDIT:
> **eldragon said:**
> para que no quede sonando la tv todo el tiempo: yo hice el siguiente script para ejecutar tvtime;
```

#!/bin/bash
amixer -c 0 set Line unmute cap
tvtime
amixer -c 0 set Line mute

```

```
$ amixer -c 0 set Line mute
amixer: Invalid command!
```

Y sin embargo 'Line toggle' me funciona... medio raro.

---

### Post by Mauro22 on 2008-08-01
[QUOTE="Mauro22 pensando"]Lo que se me ocurre para ver y grabar a la vez es:

* Empezar a grabar y digamos unos 60, 70 segundos mas tarde, abrir el archivo con lo que se va grabando. 

Lo veriamos con un delay pero veriamos al fin (ademas de pausar, ir para atras y delante)

Cuando tenga tiempo lo pruebo...

AHORA:

Perjudicaria en algo al archivo estar siendo leido y escrito a la vez??[/QUOTE]

2 problemas:

* Tvtime corta el video pero no el audio, al momento de ir viendo lo grabado tenemos de fondo el audio "en vivo" + el grabado
* La calidad de video es malisima..

---

### Post by leo_rockway on 2008-08-01
> **Mauro22 said:**
> 
* Tvtime corta el video pero no el audio, al momento de ir viendo lo grabado tenemos de fondo el audio "en vivo" + el grabado


Le podés poner Mute a Line y listo.

---

### Post by Mauro22 on 2008-08-01
Deja de grabar el audio en lo que esta siendo grabado...


Acordate que es ver y grabar

:)

---

### Post by leo_rockway on 2008-08-01
Yo si le pongo mute a Line se deja de escuchar en el servidor pero se sigue grabando y lo escucho en el cliente (esto lo hago por SSH con mencoder y mplayer, no lo probé localmente con el tvtime).

Para que se deje de grabar el audio lo que tengo que hacer es bajarle el volumen, pero con mute sigue grabando.

Lo que me pasó al intentar hacer esto localmente es que si yo ponía a grabar algo con mencoder y lo ponía a reproducir con mplayer, mplayer sólo me reproducía el contenido del archivo hasta ese momento y no lo que se grababa después. Es decir, si yo empezaba a grabar y 1 minuto despues le daba play al mplayer, mplayer me reproducía solamente 1 minuto y no seguía con lo demás que había capturado mencoder. Igualmente tampoco me fijé mucho este tema.

---

### Post by Hei Ku on 2008-08-02
El problema con que te muestre solo el contenido del archivo hasta que lo abriste debe tener que ver con la forma en que abre el archivo. O sea, hay dos maneras de abrirlo. La primera es que abre el archivo y se guarda una imagen en memoria. Esto es lo que hace en tu caso.
La segunda es que abre un handler nomas y va a buscar al archivo fisico cuando es necesario. Es mas lento, pero es lo que necesitas en tu caso, y realmente ni idea como hacerlo para ese script. :)

---

### Post by leo_rockway on 2008-08-02
Estaba aburrido así que hice un GUI para ver tele desde mi laptop. Desde el GUI cambio de canal: el backend por detrás se encarga de matar a mplayer y mencoder y de volverlos a llamar. Tardo 5 segundos en cambiar de canal :P

Es un hack muy feo, pero si a alguien le interesa verlo me dice y lo subo a algún lado.

---

### Post by gap1981 on 2008-08-15
> **leo_rockway said:**
> Estaba aburrido así que hice un GUI para ver tele desde mi laptop. Desde el GUI cambio de canal: el backend por detrás se encarga de matar a mplayer y mencoder y de volverlos a llamar. Tardo 5 segundos en cambiar de canal :P

Es un hack muy feo, pero si a alguien le interesa verlo me dice y lo subo a algún lado.


me interesa... salutess

---

### Post by leo_rockway on 2008-08-26
Voy a intentar pasar a Python lo más que pueda (ie, traducirlo de bash) y lo cuelgo en mi servidor. Cuando este listo dejo la dirección por acá.

---

### Post by sbruno on 2008-11-27
Gente, perdón por revivir esto tan viejo, pero quisiera saber en qué quedó esto de la interfaz gráfica en python.
Yo estuve jugando a hacer algo así para capturar con mencoder en estos días, y buscando en internet para ver si alguien había hecho algo parecido, esto fue lo mas cercano que encontré. Si hay algo implementado me gustaría ver el código.

Yo les dejo lo que hice por si alguien lo quiere probar. Tiene para modificar los parámetros de mencoder que yo uso, pero se le pueden agregar más.

[http://code.google.com/p/mtvcgui/](http://code.google.com/p/mtvcgui/)

---

