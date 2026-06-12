---
title: "Trabajar con videos RMVB"
date: 2009-08-07
forum: Software
---

### Post by sp33d3rs on 2009-08-07
Hola Amigos del foro
Me acuerdo del primer dia que entre aca, pidiendo ayuda para instalar ubuntu y windows en una máquina... jeje, que dias aquellos, hoy en cambio tengo un sistema operativo y una consola de videojuegos (linux y windows, claro esta)

Ok, ahora los molesto de nuevo.
Estoy descargando unos videos de internet y los quiero convertir en DVD.
Ahora, por partes, la reproduccion no es 100% en tiempo real, quizas unos segundos funciona minimamente mas lento, quizas en momentos funciona ok, el sonido tambien se ralentiza por segundos.... osea, no se reproduce "a full". Probado con varios reproductores, incluido mi amigo vlc.

Pero, aparte de eso, el tema esta en convertirlos a un dvd video. ¿Cómo, o con que software?

Si me pueden dar una mano, se los agradezco. Bye:D

---

### Post by jordilin on 2009-08-07
Prueba:
[http://mistelix.org/Main_Page](http://mistelix.org/Main_Page)

---

### Post by guillermolisi on 2009-08-07
[DeVeDe]("http://www.guia-ubuntu.org/index.php?title=DeVeDe"), que esta en los repositorios.

---

### Post by sp33d3rs on 2009-08-07
> **guillermolisi said:**
> [DeVeDe]("http://www.guia-ubuntu.org/index.php?title=DeVeDe"), que esta en los repositorios.
Nop, el DeVeDe no levanta los archivos rmvb... si no tira mensaje de error, se tilda intentando, gracias igual

---

### Post by sp33d3rs on 2009-08-07
> **guillermolisi said:**
> [DeVeDe]("http://www.guia-ubuntu.org/index.php?title=DeVeDe"), que esta en los repositorios.
Nop, el DeVeDe no levanta los archivos rmvb... si no tira mensaje de error, se tilda intentando, gracias igual

---

### Post by sp33d3rs on 2009-08-07
> **guillermolisi said:**
> [DeVeDe]("http://www.guia-ubuntu.org/index.php?title=DeVeDe"), que esta en los repositorios.
Nop, el DeVeDe no levanta los archivos rmvb... si no tira mensaje de error, se tilda intentando, gracias igual

---

### Post by sp33d3rs on 2009-08-07
> **guillermolisi said:**
> [DeVeDe]("http://www.guia-ubuntu.org/index.php?title=DeVeDe"), que esta en los repositorios.
Nop, el DeVeDe no levanta los archivos rmvb... si no tira mensaje de error, se tilda intentando, gracias igual

---

### Post by staar on 2009-08-07
jo, se colgó :-P

y si primero convertís el/los .rmvb a un formato/contenedor más amigable, como .avi (o el que te guste)? creo que vas a tener menos dramas (solo tené cuidado con los parámetros de conversión, para minimizar la pérdidad de calidad), podés usar mencoder o ffmpeg para ello...

saludos

---

### Post by guillermolisi on 2009-08-07
> **staar said:**
> jo, se colgó :-P

y si primero convertís el/los .rmvb a un formato/contenedor más amigable, como .avi (o el que te guste)? creo que vas a tener menos dramas (solo tené cuidado con los parámetros de conversión, para minimizar la pérdidad de calidad), podés usar mencoder o ffmpeg para ello...

saludos
En realidad estaba pensando en eso cuando recomende DeVeDe.

Es que sea cual sea el front-end que se use, en defintiva el back-end sera siempre el mismo con opciones configuradas segun cada caso a convertir.

---

### Post by sp33d3rs on 2009-08-07
> **staar said:**
> jo, se colgó :-P

y si primero convertís el/los .rmvb a un formato/contenedor más amigable, como .avi (o el que te guste)? creo que vas a tener menos dramas (solo tené cuidado con los parámetros de conversión, para minimizar la pérdidad de calidad), podés usar mencoder o ffmpeg para ello...

saludos

Sep, ta buena la idea.. ahora, dame una mano :confused:, yo en win manejaba el total video converted, son similares estos softwares.. tenes alguna configuracion, que por mas que "tarde" se obtenga un buen resultado para dvd (para que mantenga la calidad, claro esta)

---

### Post by josecuervo86 on 2009-08-07
proba poniendo esto en una terminal:

```
ffmpeg -i **videooriginal.rmvb** **videoconvertido.avi**
```

Primero obviamente movete a la carpeta donde esta el video

---

### Post by feche_mza on 2009-08-08
concuerdo con varias de las respuestas de los chicos, es mejor pasarlos a .avi y de ahi hacer el DVD.
Yo uso mencoder para pasarlos a .avi, y antes usaba devede, pero es una **** por que tarda cono 5 horas en hacerlo y te consume un montón de recursos, ahora estoy usando mandvd que también esta en los repositorios, los hace mas rápido y te da opciones mas copadas , como ponerle menús animados, con musica, varios subtítulos, (mas completito y mas estable digamos).
Y para pasarlos de rmbv a avi uso este comando, por consola y navegando hasta la carpeta del video
> mencoder -ffourcc DX50 archivo.rmvb -oac mp3lame -lameopts preset=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200 -ofps 25 -of avi -o archivo.avi

ya se ya se es una ****** larguísima, pero quedan con la misma calidad y lo transforma bastante rápido

---

### Post by guillermolisi on 2009-08-08
Se supone que independientemente del front end que se use, DeVeDe o ManDVD, el resultado en la linea de comando en una consola/terminal resulta en algo similar a lo que acabas de mostrar con mencoder. En el peor de los casos utilizar mencoder u otro utilitario de back end es cuestion de configuracion en el front end.

---

### Post by guillermolisi on 2009-08-10
Como muchas veces suele suceder, buscando un tema encontre otro.

Para llevar a cabo conversiones de rmvb [en este post hay una solucion]("http://ubuntuforums.org/showpost.php?p=5831808&postcount=15").

---

