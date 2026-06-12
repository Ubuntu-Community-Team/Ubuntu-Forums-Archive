---
title: "Avi a dvd"
date: 2008-11-13
forum: Software
---

### Post by ramiro_md on 2008-11-13
Gente, tengo un problema de librerias, resulta que quiero convertir un video en formato avi (codec dvix) a dvd. 
EL programa que utilizo es el winff, tengo instalado mencoder y ffmpeg, aún así cuando quiero convertir el video winff me tira el siguiente error
"Unknown encoder 'mpeg2video'. Googleando un poco encontré que ese drama estaba ligado a dos librerias (libavcodec y mjpegtools). Las busqué por synaptic y noté que mjpegtools no estaba instalada, y en el caso de libacodecs habia 3 paquetes interesantes: 

-libavcodec51
-libavcodeccvs51 (para enconde/decode multimedia streams)
-libavcodeccvs51-dev. 

El primero estaba instalado, pero los otros dos no.
Decidí instalarlos y terminar con el problema de "encode" pero al querer instalar el libavcodeccvs51 me pedia desinstalar winff, vlc, ffmpeg entre otras cosas. No me pareció algo "sensato" hacerlo y proseguí a instalar el mjpegtools, donde hubo otro problema, al querer instalar me dice que las dependencias de este paquetes no son resolubles y que verifique si los repos requeridos estan agregados y activados.
Busqué por google algun repo para las dependencias de mjpegtools pero no encontré mucho, y con respecto a lo de libavcodec espero que alguien me recomiende algo que hacer así no hago algo mal, xq no me fio de tener que eliminar esos paquetes/programas que me pide eliminar.
Bueno, saludos y gracias por leer :)

---

### Post by euzkoarima on 2008-11-13
No puedo ayudarte (de ignorante no mas) mucho con tu pregunta. Lo que puedo decirte es que los paquetes ffmpeg, mencoder y los que tienen que ver con video en gral, los tengo instalados de medibuntu en lugar de los que están en los repositorios "normales". Se que están compilados con algunas opciones más. Quizás ayuden a solucionar tu problema.

Saludos.

---

### Post by luks911 on 2008-11-13
Estoy casi como euzkoarima... tener el repositorio de medibuntu no es mala idea. Para instalarlo en Intrepid:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Otra sugerencia es probar con devede. Sirve para lo que necesitás y lo tuve funcionando junto a vlc, por ejemplo, sin problemas.

Saludos

---

### Post by ramiro_md on 2008-11-14
Luks muy groso ese programa, lo instalé porque sigo con el mismo drama de paquetes aún teniendo las repos de mediubuntu.
Tengo un problema igualmente con el devede jejeje, cuando crea la imagen e intento reproducirla vlc me tira este error:

Fallo de reproducción:
DVDRead could not open the disk "media/Datos/0/movie.iso".
Tu entrada no puede abrirse:
VLC is unable to open the MRL 'dvd://media/Datos/0/movie.iso'. Check the log for details.

Tenés idea de que pueda ser ?. Un saludo.

---

### Post by luks911 on 2008-11-14
> **ramiro_md said:**
> Luks muy groso ese programa, lo instalé porque sigo con el mismo drama de paquetes aún teniendo las repos de mediubuntu.
Tengo un problema igualmente con el devede jejeje, cuando crea la imagen e intento reproducirla vlc me tira este error:

Fallo de reproducción:
DVDRead could not open the disk "media/Datos/0/movie.iso".
Tu entrada no puede abrirse:
VLC is unable to open the MRL 'dvd://media/Datos/0/movie.iso'. Check the log for details.

Tenés idea de que pueda ser ?. Un saludo.

Sí, lo que pasa es que tenés que montar la iso para que la pueda leer el vlc. Bah, alguna vez leí, no recuerdo dónde, que el vlc lee las iso directamente, sin necesidad de montarla. Pero hacae unos días probé y tuve el mismo error que vos. La solución es montarla. 
Para eso uso Gmountiso. También se puede hacer con 

```
sudo mount -t iso9660 -o loop imagen_iso punto_de_montaje
```

Saludos

PD: buscando un poco más veo que teóricamente el mplayer también lee las iso. En casa con mi Ubuntu pruebo. Igual, la montás y problema solucionado.

---

### Post by luks911 on 2008-11-14
Ahora ya en mi máquina con Ubuntu estuve probando y encontré un par de cosas.
1) Usando VLC (versión 0.9.4) sí abre la iso sin montar. Pero para eso hay que cargarla yendo a Medio > Abrir archivo , seleccionar en el menú desplegable "Todos los archivos", buscar la iso y seleccionarla. No obstante, tardó bastante en reconocerlo y si bien entré a la pantalla con al menú del DVD, no funciona. Y si trató de navegarlo/reproducirlo con el menú del VLC tampoco anda. No se cuelga, pero tampoco reproduce. 
el error que te dio a vos me lo devolvió cuando quise cargar la iso pero desde Medio > Abrir Disco > Explorar.
2) Con SMPlayer (mi reproductor favorito, que es una especie de interfz mejorada para el MPlayer) funcionó sin problemas. La iso la cargue con Abrir > Fichero , selecciono la iso. Se salteó la pantalla del menú pero empezó la reproducción al instante y podía navegar el DVD desde el menú del SMPlayer.

Conclusión: se puede cargar la iso sin montar. SMPlayer gana.

Saludos

---

### Post by ramiro_md on 2008-11-14
JOya, gracias por la data, salió andando nomás

---

