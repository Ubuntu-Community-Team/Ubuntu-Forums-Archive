---
title: "problema con archivo wav"
date: 2008-09-04
forum: Software
---

### Post by faktorqm on 2008-09-04
Hola, tengo un pequeño problema con un archivo wav, y la verdad que ya es la segunda vez que me pasa y ya estoy cansado. Dejo grabando la radio con el siguiente comando

```
mplayer mms://delplata.telecomdatacenter.com.ar/delplata -ao pcm:file=/media/cuatro/tempradio.wav -vc dummy -vo null
```

y cuando me levanto al otro dia encuentro un archivo .wav de 4.1gb, pero cuando lo abro todos los reproductores y/o editores (vlc, totem, el mismisimo mplayer, audacity) me dice que la duracion es de 10:28, o sea diez minutos veintiocho segundos. La vez pasada me lo corto a los 24 minutos, asi que es aleatorio.
La cosa es que la vez pasada lo quise recuperar y lo termine borrando el archivo. (me mande una yo...) Ahora quiero evitar eso.

1) ¿se puede "reparar" un archivo .wav? si es asi, ¿con que programa?
2) ¿no me conviene tirarlo a un .ogg por ejemplo para que sea un archivo de streaming y no de archivo la proxima? ¿mplayer lo hace?
3) Conocen algún otro programa que grabe streaming de internet a un archivo? (el vlc creo que lo hace, voy a investigar)
4) ¿Como le bajo la calidad al streaming? por que como verán ocupa bastante, o sea, no me calientan 4gb por que tengo 400gb en total, pero si se puede y es relativamente facil... por ahora lo estoy pasando a mp3 con el siguiente comando:

```
lame -m s /media/cuatro/tempradio.wav -o /home/faktorqm/radio_del_plata/radio_$(date +"%Y%m%d").mp3
```

Desde ya muchas gracias a todos. Salu2!!

---

### Post by leo_rockway on 2008-09-05
Yo te muestro lo que tengo para la R&P. Lo probé solo una vez, pero funcionó bien

```

#!/bin/sh
NOW=$(date +"%b-%d-%y")
/usr/bin/mplayer "mms://200.59.146.10/rockandpop-ba" -af lavcresample=44100 -cache 32 -ao pcm:file="/tmp/mystream.wav" -vc dummy -vo null ;
/usr/bin/oggenc /tmp/mystream.wav -o "/home/leo/rock/CualEs - $NOW.ogg" -b 160 ;
rm /tmp/mystream.wav
```

EDIT: así como está el script, me generó un ogg de 170mb por 03:20:18 de audio. Cadencia promedio 119kbps, stereo, cadencia nominal 160kbps, frecuencia de muestreo 44100Hz (esto porque lo baje con el mplayer, la radio está en 48000Hz)

---

### Post by faktorqm on 2008-09-05
ok gracias, pero tenes lo mismo que yo... anoche por ejemplo me grabo 3 horas en 4,5gb... pero lo deje 7 grabando..... me tiene harto.
Te comento que lo de los 44100 y los 48000 son por el parametro que le estas pasando -af lavcresample=44100.
Yo en lugar del oggenc uso lame. me lo tira a mp3, pero ese no es el problema, yo lo que quiero es que lo guarde a ogg (sin comprimir, obviamente o como sea) y que despues si lo comprimo, entonces si tengo algun cuelgue en algun lugar del archivo de audio no se me corta como el wav, por que ya es de stream, si se corta por algun motivo, escuchare un ruidito o algo pero seguira reproducciendo... 
Ayer me lei el man del mplayer... y no lo termine! es el man mas grande que conozco jajaj salu2!

---

### Post by euzkoarima on 2008-09-05
Con el tema de repararlo, no se si lo hará, pero yo probaría con audacity.
Saludos.

---

### Post by faktorqm on 2008-09-05
Gracias euzko, ya lo probé y me abre el archivo mal tambien. (mal es que reconoce solo las 3 horas)

Estoy desconcertado con este asunto y encima quize hacer un programa en C para supuestamente repararlo (trabaje con una copia igual) pero lo termine haciendo bolsa. Luego intente cambiarle la longitud en el header y los reproductores se vuelven "locos" (locos es igual a: adelanto y se cuelga, adelanto y vuelve al inicio solo, adelanto y se deja de escuchar, voy al final y no pasa nada) y al fin y al cabo reproduce bien las 3 horas y nada mas. 
Encontre una opcion dentro del VLC que lo hace. Voy a intentar esta noche de vuelta, si no anda voy a releer la documentacion del mplayer y voy a sacar algo andando.
Flyerdie: ¿a vos no te pasa? gracias y salu2!!!

---

