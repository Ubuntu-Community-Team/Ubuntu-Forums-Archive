---
title: "Cómo aprovechar hardware con VLC"
date: 2011-06-27
forum: Software
---

### Post by losoollenos on 2011-06-27
Hola cómo andan tod@s, espero todo bien.
La cuestión es si será posible que algun reproductor aproveche mejor el equipo para lograr reproducir videos en HD, cosa que sí me está andando en el xp.
Probé con los restricted-extras, con VLC (habilitándole la aceleración por hardware) y los HD salen muy mal. En el Monitor de recursos veo que me utiliza un núcleo al 100% y los otros 3 entre 10 y 30 % (es una netbook con atom n-550, creo que en realidad son dos núcleos y dos en espejo o algo así).
Se podrá configurar para aprovechar más el micro?, en el xp utiliza los cuatro núcleos entre el 50 y el 60 %, sobra máquina y se reproduce fluidamente.

Muchas gracias a tod@s y hasta pronto !!!!

---

### Post by biale on 2011-06-27
Bajo Lucid? Se podría ver la manera de mejorar de version de VLC. O bien con PPA o probando la versión "Linux-portable"

---

### Post by losoollenos on 2011-06-27
No perdón, tengo que actualizarlo.....estoy con Natty y la última versión de Vlc, 1.1.10.

Gracias y saludos !!

---

### Post by biale on 2011-06-28
Entonces el tema pasa por otro lado. Para HD se necesita procesador + placa de video y si por algún motivo no se esta utilizando bien la aceleración de la placa de video hay un mayor esfuerzo para el procesador. Fijate que recursos de CPU esta usando WXP y eso te puede dar una pauta.

Hasta donde se VLC tiene codecs propios: tambien lo estas usando bajo WXP?

De todas maneras y hasta donde lei, el tema de la aceleración de la placa de video y la potencia de cpu son mas importantes que la optimización del codec

---

### Post by losoollenos on 2011-06-29
En el xp tira más o menos entre 50 y 60 % de cada núcleo, por lo menos asi muestra el administrador de tareas.

Ahi estoy usando el reproductor Media Player Home Cinema con el codec Coreavc h264. 

No se si es posible usar eso mismo en Ubuntu, quizás con wine tendria que probar, pero el codec lleva serial, no se.....

---

### Post by biale on 2011-06-30
Me parece que el problema pasa por la aceleracion de la placa de video (hasta adonde la usa?) y no por el codec. Pero eso es algo dificil de arreglar a mi nivel de conocimientos.

La idea pasaría mas por cambiar de container y/o de nivel de resolucion en el codec. h-264 es un codec de ultra-compresion, si mal no recuerdo 2 a 1. Hay un esfuerzo para descomprimir y otro para renderizar.

Como HD viene rápido, sería hasta un tema interesante para compartir. Onda "Que HW/SW estas usando para HD?. Yo casi me excluyo porque con un Intel i7 + tarjeta Nvidea sería lógico que no tuviera problemas. Los 4 cores/ 8 threads trabajan muy balanceados.

---

### Post by losoollenos on 2011-06-30
No tengo problemas en pasar los datos que decís, con mucho gusto, sólo que ni idea de cómo hacerlo !!!!

O sea, hasta dónde usa la placa de video (es la intel 3150, típica de netbook)........????, que HW/SW estoy usando.......??????.

Lo que sí veo, es que el micro(que no es que sea potente) está muy subutilizado, o eso creo.

---

### Post by biale on 2011-07-01
Hay tareas que deben ser realizadas si o si con un solo procesador, donde llego al 100% no da para mas. Mi punto es que probablemente Win este utilizando mejor el HW existente y por lo tanto ese nucleo trabaje menos.

Yo también observo que un nucleo trabaja entre un 15% a un 20% mas que el resto, pero no pasa del 60%

En tren de probar, podes bajarte algun trailer 1280 x 720 (no 1080).

---

### Post by losoollenos on 2011-07-01
Che qué es, más o menos, el HW/SW ??? 

Los videos en 720 los tira, ahora estoy mirando en el Monitor y también hay un núcleo, que no es siempre el mismo, que "se toma el mayor laburo", lo usa un 80 %, los otros entre 20 y 30 %.

Así y todo es el reproductor que mejor me anda en Ubuntu.

Saludos

---

### Post by biale on 2011-07-03
HW: Procesador/RAM  y placa de video.
SW: Versión del sistema operativo y reproductor.

Entonces insisto en que para mi o no esta usando bien la aceleración de la placa de video o por algún otro motivo no es eficiente el procesado de CPU. Aunque no lo pude ubicar hay un thread reciente que mas o menos trata lo mismo.

Todavia existe la posibilidad de convertirlos a AVI, o sea cambiar solo de container. Si recuerdo bien el software sugerido en el thread era "EKD"

---

### Post by losoollenos on 2011-07-04
Bueno lo mejor que pude lograr es con mplayer, instalando tantos codecs que ya no se con cual o cómo fue que anduvo. Anduvo con algunos hd en 1080 usando entre 80 a 90 % de los supuestos cuatro cores, parejos. En otros había una reproducción de video lenta, ahora con los codecs, sólo reproduce audio ????

En el tema de los codecs pareciera más difícil que en windows saber cuál necesita cada tipo de archivo, en este problema pasé desde los extra-restrictivos a los non-free-codecs de medibuntu junto al w32codecs, ffmpeg y vdpau, h264 y otros que ni me acuerdo.

Todavía me quedó afuera el coreavc-for-linux, este ya no es tan sencillo, no lo pude hacer andar.

Saludos !!!

---

### Post by biale on 2011-07-06
Con Nvidia/ vdpau y sobre la aceleracion de video aqui hay algo:

[http://linuxforums.org.uk/linux-tips-tricks/enable-nvidia-vdpau-video-decode-acceleration-in-ubuntu/](http://linuxforums.org.uk/linux-tips-tricks/enable-nvidia-vdpau-video-decode-acceleration-in-ubuntu/)

[http://www.ubuntu-es.org/node/139259?page=1](http://www.ubuntu-es.org/node/139259?page=1)

Pero no recuerdo haber tenido que hacer algo especial para instalar la libvdpau1

---

### Post by losoollenos on 2011-07-06
No, este netbook viene con la intel 3150 (integrada).
Pude averiguar que lo que hizo posible reproducir esos archivos es el Mplayer que instalás agregando este repo: **sudo add-apt-repository ppa:ripps818/coreavc **

Ya con eso no hace falta ningún otro codec, muy interesnte este reproductor. Además en la página del mismo vi que existen codecs adicionales, pero no entendí nada todavía.

Y éste archivo sigo sin poder reproducir con video, sólo sale audio aunque instale todos los codecs que mencionaba más arriba, sabés cuál me estaría faltando?, te paso las características del video porque el audio sí lo reprduce:

General
ID                               : 16 (0x10)
Formato                          : MPEG-TS
Tamaño del archivo               : 170MB
Duración                         : 3min.
Tasa de bits total               : 7 487Kbps

Video
ID                               : 326 (0x146)
ID Menú                          : 12106 (0x2F4A)
Formato                          : AVC
Formato/Info                     : Advanced Video Codec
Formato del perfil               : Main@L4.0
Ajustes del formato, CABAC       : Si
Ajustes del formato, RefFrames   : 4marcos
ID Códec                         : 27
Duración                         : 3min.
Tasa de bits                     : 6 729Kbps
Ancho                            : 1 920pixeles
Alto                             : 1 080pixeles
Relación de aspecto              : 16:9
Velocidad de cuadro              : 25,000fps
ColorSpace                       : YUV
ChromaSubsampling                : 4:2:0
BitDepth/String                  : 8bits
Tipo de exploración              : Entrelazado
Orden de la exploración          : Campo superior primero
Bits/(Pixel*cuadro)              : 0.130
Tamaño de pista                  : 153MB (90%)
colour_primaries                 : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
transfer_characteristics         : BT.709-5, BT.1361
matrix_coefficients              : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Saludos !!!!

---

