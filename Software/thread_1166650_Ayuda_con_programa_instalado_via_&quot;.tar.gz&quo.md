---
title: "Ayuda con programa instalado via &quot;.tar.gz&quot;"
date: 2009-05-21
forum: Software
---

### Post by r@fitiiixxx on 2009-05-21
Hola comunidad:

les vengo a echar 2 problemas que no son graves pero son muy molestos...
__________________________________________
el 1°
ante todo: mi Sist Op es UBUNTU 9.04 Jaunty Jackalope con GNOME... creo que la ver. 2.22 porque es la que viene con ubuntu no?
CompizFusion + Emerald

bueno si me falta algo mas me avisan que les tiro la data e? ;)
bueh.. la cosa es asi:

Ante ayer me baje el DJL: A linux Games Manager. 
Acá lo vi por primera ves [http://www.drollthings.com/?p=2311](http://www.drollthings.com/?p=2311)
explicacion mas linuxera: Viene a ser 1 cliente de repositorios pero solo de juegos
explicacion mas windowsera: Es como un Steam para linux pero de codigo libre (creo) y con jueguitos gratis y SIN CRACK :)

la cuestion es que lo instalé via .tar.gz y bueno... yo en realidad soy superno0b y me mandé a hacer cosas que no devería, pero bueh... lo echo echo está y ahora instalé este soft... el cual no me andaba bien.. tenia muchos fallos. se colgaba... se quedaba en proceso zombie si le hacia click en la ventanita... y bueno... bajaba lento... en fin, lo queria tanto como a un virus :)
asi que dije ahora lo desinstalo.. y fui a añadir y quitar programas y.. y... T_T nooo estabaaaa
obio si lo instale desde el source...
osea... se instala ejecutando 1 script que ya YA se los paso...
```
#!/bin/sh

cd `dirname $0`/djl
python -O djl.py $*
```
yo le mandé doble click... y ahora no lo puedo sacar... para colmo... estube leyendo en el foro de como se buscaría donde se instaló el tema es que fui eliminando todas las carpetas manualmente... mejor dicho las que encontré tiradas por ahi con el nombre "djl" o los jueguitos que me habia bajado... y con el comando whereis... no sale carpeta alguna :B... el tema es que.. en el panel de GNOME pongo Aplicaciones > Juegos > "y aca me aparece el acceso directo o lo que sea del djl... y no lo puedo sacar T_T"
>si le ago click sale esto: > Ha ocurrido un error al cambiar al directorio «/home/nicolas/Escritorio/djl/djl»·(No existe el fichero ó directorio)
todavia tengo el .tar.gz pero no se que mas hacer...
y busque bastante por google y en foros... no hay muchos post de como desinstalar .tar.gz ... osea si hay algunos... pero todos dicen
"miraa adentro del .tar.gz en el README dice como desinstalarlo, casi siempre es asi..."

bueno me kbe que a mi me jodieron :) porque no me vino eso.. dice 1 monton de guebadas de para que sirve y porq es bueno y genial pero no dice nada de como desinstalarlo... = borre algunas carpetas asi que deve estar medio fallado el soft jeje... la cuestion cuanto antes me lo saque mejor... y si me pueden tirar 1 mano se lo re agradecería (o_-)

nota: como no entiendo donde buscar donde se instalan las cosas.. porque todavia no entiendo donde se guardan las cosas cuando las instalo, puede ser que hay carpetas que me esté saltando y me olvide de sacarlas... pero bueh.. algun dia voy a entender donde se guarda todo :P
me ayudan?? C:
_________________________________________________________
el 2°: a mi me gusta viciar... pero tmb me gusta un escritorio con cubo 3D y emerald y todoh loh chiche :D
pero no puedo! cada ves que quiero jugar un juego se me traba... y ctrl+alt+f2 para modo consola... entro y no me sirve el comando PS porque no me lista los procesos.. osea prové con todas las extenciones...
pero no funcionó. ensima como no tengo ni idea del uso de la consola... me costó aprender a cerrar sesion desde ahí, antes reiniciaba la pc :S
ahora por lo menos solo cierro sesion... pero el juegito me dura 2 min... y se que es por culpa de compiz
 :( compiz malo! no mentiiira :$ es hermoso :D
pero no me deja jugar Q_Q y nesesiiitoo juuugarr :E jajaja
la cuestion... no hay algun script para desabilitar el compiz mientras juego, y luego volverlo a habilitar TAL CUAL lo habia dejado?
aclaro que esto me acabo de acordar... y no me puse a buscar mucho.. ahora busco algo y si encuentro la sol tmb la posteo...
pero bueno eso na mas... si me pueden tirar 1 cablin seria genial 
_________________________________________________________________
pido disculpas por mi no0bidad y bueno... con el tiempo algun día no sea tan pelotudon y no meteré mano donde no se... por ahora tengo 1 icono que lo quiero rajar a patadas jeje
bueno gracias de antemano y salu2

---

### Post by staar on 2009-05-22
por lo poco que entiendo del script, te diría que ese programa no se 'instala', corre desde el directorio donde descomprimiste el .tar.gz (similar a algunas aplicaciones hechas en java) según el acceso del menú, /home/nicolas/Escritorio/djl/ asi que con solo borrar ese directorio, ya lo tendrías 'desinstalado'...

para borrar el acceso del menú, click derecho sobre el menú > Editar menu, vas hasta donde está el acceso, y lo borrás :-P:-D

saludos

---

### Post by r@fitiiixxx on 2009-05-22
> **staar said:**
> por lo poco que entiendo del script, te diría que ese programa no se 'instala', corre desde el directorio donde descomprimiste el .tar.gz (similar a algunas aplicaciones hechas en java) según el acceso del menú, /home/nicolas/Escritorio/djl/ asi que con solo borrar ese directorio, ya lo tendrías 'desinstalado'...

para borrar el acceso del menú, click derecho sobre el menú > Editar menu, vas hasta donde está el acceso, y lo borrás :-P:-D

saludos

eje grax por ponerle onda :D

pero no me funcionó :( dado que no está tal carpeta en escritorio porque la borré... osea ese mensaje me sale porque me falta esa carpeta porq se la borré asi a lo gaucho jeje
y tmb dije que era 1 script que me fabricó carpetas... osea tenia 1 carpeta en /home/nicolas/.djl y a esa tmb la mande al recicle bin y dsps a vaciar el recicle bin XD
todo culpa del script (?) jaja
y lo de borrar el icono... SOS 1 MAESTROOOOO KPO JEJEEEEEEEEEEEEE Y LO SAKÉ A LA MIE... NOMASSSSSS :D 
ahora me faltaria saber si me falto algo por sacar... y si no ya ta jeje viteh :P
--------------------
chee soy muy pelotudon... tu firma dice escuchen su disco duro... y yo le puse.... jajajajaja... que cuernos es eso? me asusté pense que habia roto a ubuntu jajajajaja

===========================================================
encontré la solucion para cualquier persona que no quiera tocar scripts o prefiera el uso del maus antes que usar la shell bash para desactivar y activar compiz sin que se te borre la config... que tanto me costo el efecto GENIE de MAC :D
e aquí el [Compiz-Switch (pag oficial)]("http://forlong.blogage.de/entries/pages/Compiz-Switch")
que sirve para la cartera de la dama y el bolsillo del caballero xD
desactiva y activa compiz... y no borra la config :B
espero q a alguien le sirva... bueno suerte ;)

---

### Post by staar on 2009-05-22
si ya la borraste, el programa ya está desinstaldo, lo bajé para corroborar, y corre desde donde lo descomprimis, y en el primer uso te crea una carpeta oculta con las configuraciones en el /home (eso lo hacen prácticamente todos los programas) y te permite crear un ícono en el menú, si ya borraste esas tres cosas, ya está, eso es todo (este programa sería algo así como los 'portables' con los que tanto joden ahora en Ventanas)

lo de mi firma, es solo el poder de la terminal :-D:-D, solo le pasas a aplay, un programa básico para reproducir sonidos, el contenido de tu disco duro, pelado, byte por byte, sería como poner el plato del HD en un tocadiscos :-D:-D

saludos

---

### Post by juancarlospaco on 2009-05-22
1) DJL no se instala en el sistema, corre desde tu carpeta personal, 
esta en una carpeta oculta en tu carpeta personal, se llama .djl la carpeta creo, borrala y ya esta.

2) A los juegos que se te traban, hacele un acceso directo nuevo y ponele:

killall gnome-screensaver ; ejecutabledeljuegoaca

Es que en realidad muchos juegos no avisan al demonio del screensaver que estan a pantalla completa,
y el screensaver luego de ver que no se mueve el puntero intenta iniciarse, colgando el juego.

---

### Post by r@fitiiixxx on 2009-05-22
Wuaw gracias gente :D la verdad me re sirvio lo que me dijeron... ahora pongo en practica eso del kill-gnome screensaver a ver que onda... jeje
osea que ya lo borré al programita.. bueno que bueno

la verdad mil gracias a todos :) y suerte...

):P

---

### Post by r@fitiiixxx on 2009-05-22
che lo de kill allgnome-screensaver en el launcher no me funciona... no me lo toma.. :S

te recuerdo que el Urban Terror 4.1 es el unico juego que tengo y juego.. y no es un paquete .deb ... por hay es por eso no?

sea como sea con el compiz swicth ando bien
pero me molesta tener q agregar 1 barra abajo porq tengo el Gnome Do y lo tengo q sacar y poner algo para ver las cosas! jaja
y bueno.. asi que si me podes datear mejor de este acceso directo seria copadaso :)

salu2

---

