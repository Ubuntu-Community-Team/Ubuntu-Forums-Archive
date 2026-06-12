---
title: "problema de codecs o de la tarjeta de video?"
date: 2010-11-29
forum: Software
---

### Post by joseluis on 2010-11-29
Comento lo más claro que me puede salir, cualquier cosita pregunten.
Estoy grabando videos. Es una cam sony. Bue, la cuestión es que la cam graba en extensión .MTS.
Hasta ahi todo bien.
Ahora, cuando paso el video a la compu, se traba terriblemente el video, el sonido sigue (mas o menos) y el video se congela.
Subiendo el mismo archivo youtube, para probar, noto que no hay problemas, que el video y el audio corren perfectamente, sin siquiera convertirlo.
Además probé en convertirlo a .avi por ejemplo, y todo bien, NO HAY DEFECTO.
Entonces, ¿por qué no puedo ver directamente MTS en la pc? Uso Ubuntu 10.10 , pero también me pasa con el 10.04 que tengo en otro rigido.
aca va el lsmod:

Module                  Size  Used by
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  1 vfat
binfmt_misc             6599  1 
snd_hda_codec_realtek   217971  1 
nvidia               7088432  34 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
usblp                  10651  0 
parport_pc             26058  1 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  1 nvidia
k8temp                  3228  0 
i2c_nforce2             5179  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
8139too                19581  0 
usb_storage            40172  0 
8139cp                 16934  0 
forcedeth              49433  0 
sata_nv                19420  3 
pata_amd                8746  4 
mii                     4425  2 8139too,8139cp
floppy                 54311  0 

gracias

---

### Post by Wiredfixer on 2010-11-30
El lsmod esta muy completo, aun asi, seria bueno ver el modelo de la camara y como conectas este equipo a tu PC, asimismo, el programa que usas para editar los videos.

Ahora que, si es una camara que funciona como dispositivo USB, y los videos se guardan en MTS, pues la cuestion estara en encontrar un Codec para este tipo de formato, que por lo que se, no es un formato que se reproduzca en todos lados, mas bien, su proceso correcto es convertirlo a AVI y luego reproducir el resultado.

[http://ubuntuforums.org/showthread.php?t=864983](http://ubuntuforums.org/showthread.php?t=864983)
Ahi hay mas sobre tu caso, aun asi, pasa mas datos y veremos.

---

### Post by joseluis on 2010-11-30
La camara es una Sony HDR CX100, un balaso.
Pero por lo que vi en ese enlace, solo podría verse tranformando el video. Es decir, quizás pueda verlo en un TV (no tengo la posibilidad inmediata de hacerlo). La conexion es via USB.
Aclaro que al convertir de MTS a MPEG4 con OpenShot tengo grandes resultados, pero no se si no estoy perdiendo calidad en la conversión. 
Como decía, Youtube los transforma, los pude subir. Pero obvio que antes tendría que editarlo. Y para eso, como decía, uso OpenShot.
Lo que me queda es que ese formato, parece HAY QUE convertirlo, SI o SI para trabajarlo. No se lo puede trbajar como MTS.
Salvo.............probar con el MPlayer, que en el enlace que me pasaste lo nombra. Voy a verlo.
Gracias! sigo buscando. Si alguien tiene más información, bienvenida sea

---

### Post by gmunioz on 2010-11-30
Mira este sitio:

[http://karuppuswamy.com/wordpress/2010/06/07/how-to-convert-canon-mts-video-files-to-other-formats-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/07/how-to-convert-canon-mts-video-files-to-other-formats-in-ubuntu/)

---

### Post by joseluis on 2010-11-30
Exacto gmunioz, este es otro que uso, pero es lo mismo: no se puede visualizar .mts sino se convierte. Eso es lo que veo. Este que pressentás lo uso mucho para convertir, y es genial, por lo veloz y lo eficaz. 
Entonces, **conclusión**: **no se puede visualizar MTS si no es convertido a otro formato.**

---

### Post by Wiredfixer on 2010-12-01
Asi es, ya que el formato de alguna manera es un formato cerrado... yo creo que se trata de un AVI HD con alguna codificacion nadamas, el software de la camara se encarga de descodificarlo...

Ahora dices, Subes el MTS a youtube y lo despliega sin errores?

---

### Post by gmunioz on 2010-12-01
Los archivos.mts corresponden a AVCHD (Advanced Video Codec High Definition)
Este es un formato de grabación de alta definición privativo, de propiedad de Sony y Panasonic. 
Puede emplear diversos formatos de almacenamiento, incluyendo discos miniDVD (DVD grabables de 80 mm.), discos duros, y tarjetas de memoria SD y Memory Stick Pro.
Usa la compresión de vídeo MPEG-4 AVC (H.264), publicitada 
como un método de compresión más eficiente.
El audio puede ser codificado en 5.1 AC-3 ó 7.1 linear PCM. Como flujo de transporte se emplea MPEG-2. Sony asegura que el formato tiene un tiempo total de almacenamiento en un MiniDVD de unos 20 minutos de vídeo de alta definición empleando bitrates "medios". 
Este formato es el que usan los bluray y naturalmente no se  podrá ver en un aparato DVD. 
El reproductor aconsejado por Sony y Panasonic es el software propietario que corre en Windows unicamente, el Sony Motion Picture Browser (MPB)

---

### Post by joseluis on 2010-12-02
excelente detalle gmunioz, gracias!!!!
noto, entonces, que este formato privativo queda reducido, como siempre a un sistema.
¿le puedo sacar "jugo" en ubuntu sin necesidad de pasar por PMB? 
¿el formato que decís sería el que yo debería codificar para sacar mejor calidad en HD?
No voy a grabar en blue ray, pero ..... ¿podría buscar una compresión que se acerque tanto para hacer un disco como para ver en la compu?

gracias gmunioz si podés contestar estas dudas.

---

### Post by gmunioz on 2010-12-02
Para ver archivos.mts en Ubuntu
Debes tener en tu ordenador un procesador y tarjeta de video poderosos.
Luego instalas VLC y FFmpeg:

sudo apt-get install vlc ffmpeg

Abres VLC y te vas a Herramientas -- Preferencias y marcas en 
Mostar ajustes Todo
A la izquierda te vas a Entrada/Códecs -- amplias a otros Codecs -- amplias FFmpeg 
Lo configuras con los valores siguientes
Permitir trucos de velocidad
Omitir el filtro de bucle para decodificación H.264 marcar Todo
el resto por defecto

Si al reproducir se notan ciertas distorsiones con lineas horizontales en la imagen
en las configuraciones de Video -- Filtros  Desentrelazado elege un modo en Pantalla y Emitiendo.
Se suele usar Mezclar o Lineal en general.

Hay información en la red acerca de que una grabadora de Panasonic, la vw-bn1e-s  es capaz de grabar AVCHD en un DVD
y  permite reproducir el contenido conectando el grabador a 
la cámara y la cámara al televisor.

También existe un grabador de Sony pero sin la opción de reproducir, el VRD-MC5.

---

### Post by joseluis on 2010-12-02
> **Wiredfixer said:**
> 

Ahora dices, Subes el MTS a youtube y lo despliega sin errores?

Si exactamente

---

### Post by joseluis on 2010-12-02
> **gmunioz said:**
> Para ver archivos.mts en Ubuntu
Debes tener en tu ordenador un procesador y tarjeta de video poderosos.
Luego instalas VLC y FFmpeg:

sudo apt-get install vlc ffmpeg

Abres VLC y te vas a Herramientas -- Preferencias y marcas en 
Mostar ajustes Todo
A la izquierda te vas a Entrada/Códecs -- amplias a otros Codecs -- amplias FFmpeg 
Lo configuras con los valores siguientes
Permitir trucos de velocidad
Omitir el filtro de bucle para decodificación H.264 marcar Todo
el resto por defecto

Si al reproducir se notan ciertas distorsiones con lineas horizontales en la imagen
en las configuraciones de Video -- Filtros  Desentrelazado elege un modo en Pantalla y Emitiendo.
Se suele usar Mezclar o Lineal en general.

Hay información en la red acerca de que una grabadora de Panasonic, la vw-bn1e-s  es capaz de grabar AVCHD en un DVD
y  permite reproducir el contenido conectando el grabador a 
la cámara y la cámara al televisor.

También existe un grabador de Sony pero sin la opción de reproducir, el VRD-MC5.

bien! vamos mejor. Gracias!!! encuentro que se frena, pero evidentemente tiene que ver con eso que decís que necesitas una maquina poderosa. La mia es Athlon 3000+ 1.8G 2Gi de ram. Pero gracias de verdad

---

### Post by Wiredfixer on 2010-12-03
gmunioz vino a iluminarnos un poco...

Habra que ver ahora como youtube "convierte" esos archivos en un flv... 

Digamos que ya tienes la manera para verlos... y pues en la camara se ven fluidos porque solo eso hace la camara, en cambio, en tu PC tienes un monton de servicios que usan otras cosas aparte..

Funcionara en digamos.. una distro dedicada solo a ver video?  Habra que hacer la prueba...

---

