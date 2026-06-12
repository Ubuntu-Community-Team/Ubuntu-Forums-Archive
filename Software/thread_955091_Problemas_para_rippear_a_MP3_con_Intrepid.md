---
title: "Problemas para rippear a MP3 con Intrepid"
date: 2008-10-21
forum: Software
---

### Post by Thalskarth on 2008-10-21
Hola buenas, aprovecho y te hago una pregunta:

como le decía a Kantier [en este otro post]("http://ubuntuforums.org/showpost.php?p=6008597&postcount=2"), estoy en Intrepid ibex y he instalado el Lame para poder rippear mis CD's.---

pero tanto en el Sound-Juicer como en el rythembox no me sale la opción de MP3, me da para ripear en .oga (.ogg, no se porque lo pone con 'a') y en .flac

Si voy a la configuración de los programas, si esta la opción MP3 para setearla, pero en la lista no sale para elegirla...

Me acuerdo que con Hardy, con solo instalar el LAME había funcionado... pero acá se ve que no anda...

Sabes como podría solucionarlo?? porque por un lado mi MP3 lee .ogg asi que no me hago tanto drama, pero el celular de mi hermano no y ya me esta volviendo loco con el tema 

O es un tema del Intrepid por ser beta?

Muchas gracias

---

### Post by faktorqm on 2008-10-23
y.. yo lo hago por linea de comandos... pero podrias probar con:

```
sudo apt-get install liblame0 lame lame-extras gstreamer0.10-lame libtwolame0 toolame twolame

```

Siempre tengo la mala costumbre de instalar 150000 codecs por que no se cual va. Si encontras una solucion mas profesional, bienvenido. Salu2!

---

### Post by Thalskarth on 2008-10-23
ahí funcionó! gracias, se ve que el lame que instalé no era el que necesitaban...

por cierto, me picó la curiosidad, como haces para ripear y encodear los CDs desde consola??

---

### Post by faktorqm on 2008-10-24
Tenia un script que lo hace, el tema es que molesta mucho con ID3, por que no puedo, o no se como "automatizarlos" para que aunque sea tome el nombre del tema, cuando voy a casa lo busco y te lo paso, hace mil años que no ripeo nada. Salu2!

---

