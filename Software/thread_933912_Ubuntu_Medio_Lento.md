---
title: "Ubuntu Medio Lento"
date: 2008-09-29
forum: Software
---

### Post by papocha on 2008-09-29
Hola comunidad ubuntera 
tengo una duda con respecto al ubuntu y la instalacion de los drivers del mother.
tengo un: 

P4HT 3.20/3.20 GHZ 
NVIDIA GeForce FX5200 128mb
Novatech 512DDR2 
mother biostar P4MM800-ProM7

instale los drivers de la placa de video correctamente, los de sonido y placa de red los instalo el SO automaticamente, pero como que anda medio lento el SO, sake la opcion de graficos medios o niguno.
queria saber si puede ser ke no tenga los drivers del mother instalado
cuando compre la pc ase un tiempo venia con win xp / vista, me andubo bien, per me cambie y tengo la impresion de que el SO no me esta andando al maximo rendimiento, o los drivers del mother esten mal instalados y si fuese asi me gustaria saber como hacer para poder nstalar los correctos.
Al principio no estaba seguro, hasta ke empese a ver videos en ytbe y note que tenian como un pequeño frizeo al reproducirse solo pasa con el video y no con el audio.
gracias =)

---

### Post by ramiro_md on 2008-09-30
Primero bienvenido. Segundo, corrias Vista con 512 de ram ? :o.
En cuanto a  que te ande lento podrías ser más específico ?...te tarda en cargar ubuntu e iniciar gnome ?. O es qué tarda en abrirte aplicaciones, y demás ?. Un saludo.

PD: Lo de la mother olvidate xD
PD 2: Puede ser que estés usando ubuntu 64 bits ? suele tener problemas con flash (youtube).

---

### Post by papocha on 2008-09-30
> **ramiro_md said:**
> Primero bienvenido. Segundo, corrias Vista con 512 de ram ? :o.
En cuanto a  que te ande lento podrías ser más específico ?...te tarda en cargar ubuntu e iniciar gnome ?. O es qué tarda en abrirte aplicaciones, y demás ?. Un saludo.

PD: Lo de la mother olvidate xD
PD 2: Puede ser que estés usando ubuntu 64 bits ? suele tener problemas con flash (youtube).

a) cuando compre la pc me vino con vista, pero al toke instale XP
c) no de echo instale el flash-nonfree, pero es como ke me anda bien pero ahi partes de los videos ke los carga por frames como si me consumiera toda la memoria en ese instante pero solo el video no pasa con el audio puede ser porke tenga 512 ?
nunca tube ese problema antes con los otro SO
igual gracia por la buena onda =)

---

### Post by ramiro_md on 2008-09-30
No te preocupes por tus 512 de ram, van bien con ubuntu. Trata de reproducir el video una vez cargado del todo. Sino fijate en estos dos links

[http://dudas.wordpress.com/2007/01/20/instalar-flash-player-9/](http://dudas.wordpress.com/2007/01/20/instalar-flash-player-9/)

[http://www.guia-ubuntu.org/index.php?title=Firefox#Instalar_Flash](http://www.guia-ubuntu.org/index.php?title=Firefox#Instalar_Flash)*si usas firefox como navegador

Un saludo.

PD>Dinos si usas ubuntu 64 o 32 bits.

---

### Post by andrelo87 on 2008-09-30
si la verdad.. una ***** el tema de video en linux.. yo estoy pariendo con mi mx4000 en ubuntu.. no hay forma de que ande bien, ya probe envy, probe instalar desde los repositorios, trate bajando el driver de nvidia (todas las versiones) e instalandolo saliendo del entorno grafico y no hay forma.. 

no me gusta como me aparece la placa en el xorg.conf aparece algo asi como NVIDIA (generic) o algo asi.. no tendria qeu aparece no se.. NVIDIA GeForce mx4000?? o NV18  o no se algo distinto de generic.. bueno yo ahora no estoy en ubuntu estoy en el xp porque estoy podrido de ver en 640x480.. de ultima como hago para que quede como me deja el ubuntu despues de la instalacion.. porque ahi me aparecia como hasta 1440x no se cuanto.. pero no tenia aceleracion grafica.. y ahora qeu tengo aceleracion no puedo a mas de 640x480.. jaja.. cualquiera.. bueno si alguien sabe como ayudarme.. si quieren abro un post..

gracias desde ya..

PD: ya intente agregarle en el xorg.conf las otras resoluciones para poder elejir un a mas alta.. pero no funciono..

---

### Post by ramiro_md on 2008-09-30
Andrelo no la compliques con el envy. Es buen programa, pero hacela corta, te vas a sistema > administracion > controladores de harware y habilita la placa y sus controladores de ahi.

PD> el tema del video no es malo en LInux, solo que si nVidia liberaria los drivers para ayudar un poco al usuario libre, como lo ha hecho intel y ati, la cosa seria un poco mas linda.
PD2>se me acaba de desconfigurar el teclado (n).

---

### Post by papocha on 2008-09-30
> **ramiro_md said:**
> No te preocupes por tus 512 de ram, van bien con ubuntu. Trata de reproducir el video una vez cargado del todo. Sino fijate en estos dos links

[http://dudas.wordpress.com/2007/01/20/instalar-flash-player-9/](http://dudas.wordpress.com/2007/01/20/instalar-flash-player-9/)

[http://www.guia-ubuntu.org/index.php?title=Firefox#Instalar_Flash](http://www.guia-ubuntu.org/index.php?title=Firefox#Instalar_Flash)*si usas firefox como navegador

Un saludo.

PD>Dinos si usas ubuntu 64 o 32 bits.

Ya econtre el problema de la lentitud nose porque pero el ubuntu me consume demasiada memoria, y eso hace que ante lento el SO, y el ytbe.
los pricipales consumidores de memoria son , firefox, gnome-panel.
y cuando instalo algun programa con el gnome app install me consume un 120 porciento de la memoria

---

### Post by Mauro22 on 2008-09-30
> **papocha said:**
> ...me consume un 120 porciento de la memoria


120% ??? Como va a consumir mas de lo que tiene :confused:...


Si queres podes internet KDE que es un poco mas liviano o XFCE que todavia es mas liviano. Acordate que Gnome es el mas pesado.

---

### Post by niko_3100 on 2008-10-01
KDE el mas liviano? creo que es el mas pesado de todos, los programas en kde pesan mas que en gnome. Igual al margen podes probarlo igual que es muuy bueno al igual de gnome.
Fijate deshabilitando el tracker, en la opcion "sesiones" todo lo que diga tracker deshabilitalo, eso te indexa el disco cada ves que guardas o borras algun archivo por lo que siempre esta consumiendo memoria.

---

### Post by niko_3100 on 2008-10-01
KDE el mas liviano? creo que es el mas pesado de todos, los programas en kde pesan mas que en gnome. Igual al margen podes probarlo igual que es muuy bueno al igual de gnome.
Fijate deshabilitando el tracker, en la opcion "sesiones" todo lo que diga tracker deshabilitalo, eso te indexa el disco cada ves que guardas o borras algun archivo por lo que siempre esta consumiendo memoria.

---

### Post by guisheca on 2008-10-01
> **Mauro22 said:**
> 120% ??? Como va a consumir mas de lo que tiene :confused:...


Si queres podes internet KDE que es un poco mas liviano o XFCE que todavia es mas liviano. Acordate que Gnome es el mas pesado.

Al menos en la dimensión del universo en la que vivo se sabe perfectamente que KDE es el entorno que mas recursos consume de todos.
De onda lo digo, (ando medio contrera ultimamente, pero soy bueno :-) )

---

### Post by papocha on 2008-10-01
Solucionado! formatie reinstale todo sake los efectos especiales del gnome y me anda perfectamente.
=D

---

### Post by pol666 on 2008-10-01
como kDE consume menos xfce :| xD

---

### Post by leo_rockway on 2008-10-01
@niko_3100: Double Post FTW xD

El otro día alguien comentaba (creo que Hei Ku) que KDE apenas levanta es más pesado pero a medida que abrís aplicaciones te das cuenta que no es tan pesado como parece porque todas las aplicaciones comparten muchísimas cosas lo que en definitiva termina siendo un ahorro.

Eso de que KDE es __muuucho__ más pesado que Gnome es medio mito. Además Gnome está cada vez más achanchado.

Ya fue, me paso a Fluxbox* (?).


* Fluxbox es un golazo.

---

### Post by faktorqm on 2008-10-02
Ahora en 8.10 me voy a instalar Kubuntu, pero si va lento o muy lento, le tiro el enlightment o el fluxbox de una. La velocidad sobre todas las cosas!

---

### Post by ramiro_md on 2008-10-02
Kde 4.1 me inicia más rápidop que Gnome. EL 30 de octubre me pido kubuntu :D

---

### Post by Aspergillus on 2008-10-03
con 512 de ram yo no usaria gnome ni a palos, a mi con 1 gb ya se me achanchaba muchisimo asi que busque soluciones...Xfce esta muy bueno si te gusta tener iconos en el escritorio, barra de menus y todo eso a velocidad de saldo :P, pero si queres velocidad al extremo Fluxbox es LA gloria, tambien podrias probar Pekwm que es muy parecido a Fluxbox

---

### Post by guisheca on 2008-10-03
> **Aspergillus said:**
> con 512 de ram yo no usaria gnome ni a palos, a mi con 1 gb ya se me achanchaba muchisimo asi que busque soluciones...Xfce esta muy bueno si te gusta tener iconos en el escritorio, barra de menus y todo eso a velocidad de saldo :P, pero si queres velocidad al extremo Fluxbox es LA gloria, tambien podrias probar Pekwm que es muy parecido a Fluxbox

Me parece que estas exagerando un poco master, 512mb de ram está muy bien para gnome y con 1gb vuela con compiz y todo.
Todo bien si sos amante de la rapidez extrema, pero con 512 gnome funca que da miedo .
Yo tenía una máquina con 768mb de ram (256+512) con compiz activado (beryl en aquellos tiempos) y sin swap y te puedo asegurar que funcionaba de 10.
El problema creo que es con el ubuntu mas que nada, que ahora (8.04) está medio pesadito por los procesos que corre desde el inicio, como el indexado de archivos, el bluetoot y demás. Quizás si se desinstalan o desactivan del inicio esos procesos se hace mas fluido su funcionamiento. Pero en lo que a gnome respecta es un escritorio que corre muy bien en 512mb.
Saludos.

---

### Post by niko_3100 on 2008-10-03
Lo primeor que hago despues de instalar una version de ubuntu es deshabilitar el tracker, te alenta muuucho el disco y por consiguiente todo el funcionamiento de la memoria. Te indexa cada cosa que haces, escritura o lectura y se re siente porque el disco esta continuamente haciendo cosas..

---

### Post by pol666 on 2008-10-03
men, tengo un amigo con Ubuntu+Gnome en 256 de ram con una nvidia 5200.

Vuela.

---

