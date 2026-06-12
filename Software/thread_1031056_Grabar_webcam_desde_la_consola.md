---
title: "Grabar webcam desde la consola?"
date: 2009-01-05
forum: Software
---

### Post by sartrejp on 2009-01-05
Alguien sabe como puedo grabar videos desde la webcam usando la terminal? Mi intención  es que en determinadas horas, se grabe un video y se guarde en un archivo.
La webcam la pude usar con cheese y con amsn, pero no con camorama (y con wxcam -que cumple funciones que me interesan - se divide la pantalla en 4 y los colores se distosionan) y tampoco pude con VLC.

La cámara es una GE con chipset microdia y está en /dev/video0

Desde ya se agradece

(a los moderadores, no sabía si poner el post en software o en hardware, y por eso está acá)

---

### Post by sergiom99 on 2009-01-05
Podes probar con ZoneMinder.
[http://www.zoneminder.com/](http://www.zoneminder.com/)

Tambien con mencoder:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Suerte!

---

### Post by jclevien on 2009-01-05
Si, es posible.

No lo probé, pero podés exportar el contenido de la cámara en un framebuffer, con x11vnc ([http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-rawfb](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-rawfb)).

Luego fácilmente grabás el framebuffer con cualquier utilitario de grabación RFB, como por ejemplo este: [http://www.unixuser.org/~euske/vnc2swf/](http://www.unixuser.org/~euske/vnc2swf/)

Naturalmente, quizás te convenga ajustar algunos parámetros, como por ejemplo el frame rate (cuantos cuadros por unidad de tiempo deseas), brillo, contraste, etc. Eso se especifica directamente en el x11vnc, fijate el help con los parámetros, está explicado.

Espero haber sido util.

Saludos.


Juan

---

### Post by sartrejp on 2009-01-05
Estoy leyendo tus links jclevien.

Respecto a mencoder tengo el siguiente error:
Si pongo $ mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0 -ovc lavc -o webcam.avi
me da el siguiente error:

MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ (Family: 15, Model: 107, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: USB camera
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = sonixb;
 Current input: 0
 Current format: unknown (0x30313953)
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
Exepción de coma flotante

si pongo v4l en vez de v4l2 sale
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ (Family: 15,
Model: 107, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: USB camera
 Capabilites: capture
 Device type: 1
 Supported sizes: 48x32 => 352x288
 Inputs: 1
 0: sonixb:  (tuner:0, norm:pal)
Using input 'sonixb'
Selected input hasn't got a tuner!
[V] filefmt:9  fourcc:0x32315659  size:320x240  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (320x240 fourcc=34504d46 [FMP4])
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.

ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not
writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not
writing vprp header.
Pos:   0.1s      3f ( 0%)  2.25fps Trem:   0min   0mb  A-V:0.000 [0:0]
77 duplicate frame(s)!
Pos:   3.3s      6f ( 0%)  1.69fps Trem:   0min   0mb  A-V:0.000 [1465:0]
Skipping frame!
Pos:   3.3s      7f ( 0%)  1.98fps Trem:   0min   0mb  A-V:0.000 [1465:0]
ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument
Pos:   3.5s     11f ( 0%)  2.40fps Trem:   0min   0mb  A-V:0.000 [2050:0]
77 duplicate frame(s)!
Pos:   6.6s     13f ( 0%)  1.90fps Trem:   0min   0mb  A-V:0.000 [1236:0]
Skipping frame!
Pos:   6.6s     14f ( 0%)  2.04fps Trem:   0min   0mb  A-V:0.000 [1236:0]
Skipping frame!
Pos:   6.6s     15f ( 0%)  2.19fps Trem:   0min   0mb  A-V:0.000 [1236:0]
ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument
Pos:   6.7s     17f ( 0%)  2.15fps Trem:   0min   0mb  A-V:0.000 [1380:0]
1 duplicate frame(s)!
Pos:   6.8s     19f ( 0%)  2.39fps Trem:   0min   0mb  A-V:0.000 [1472:0]
75 duplicate frame(s)!
Pos:   9.9s     21f ( 0%)  2.07fps Trem:   0min   0mb  A-V:0.000 [1111:0]
Skipping frame!
Pos:   9.9s     22f ( 0%)  2.17fps Trem:   0min   0mb  A-V:0.000 [1111:0]
Skipping frame!
Pos:   9.9s     23f ( 0%)  2.27fps Trem:   0min   0mb  A-V:0.000 [1111:0]
ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument
Pos:  10.0s     24f ( 0%)  2.14fps Trem:   0min   0mb  A-V:0.000 [1156:0]
1 duplicate frame(s)!
Pos:  10.0s     25f ( 0%)  2.22fps Trem:   0min   0mb  A-V:0.000 [1194:0]
1 duplicate frame(s)!
Pos:  10.1s     26f ( 0%)  2.31fps Trem:   0min   0mb  A-V:0.000 [1221:0]
1 duplicate frame(s)!
Pos:  10.2s     27f ( 0%)  2.40fps Trem:   0min   0mb  A-V:0.000 [1246:0]
74 duplicate frame(s)!
Pos:  13.2s     29f ( 0%)  2.15fps Trem:   0min   0mb  A-V:0.000 [1026:0]
Skipping frame!
Pos:  13.2s     30f ( 0%)  2.23fps Trem:   0min   0mb  A-V:0.000 [1026:0]
Skipping frame!
^Cs:  13.2s     31f ( 0%)  2.30fps Trem:   0min   0mb  A-V:0.000 [1026:0]
ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument

ioctl mcapture failed: Invalid argument
Pos:  13.3s     32f ( 0%)  2.19fps Trem:   0min   0mb  A-V:0.000 [1057:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not
writing vprp header.

Video stream: 1057.136 kbit/s  (132141 B/s)  size: 1754845 bytes
13.280 secs  32 frames
 MJP: returning!



Saben que significa???

Cuando intento instalar zoneminder me dice que falta libavcodec1d (que no esta para Intrepid, lo encontré, y al intentar instalarlo me falta liavutil1d que no lo pude encontrar -y no se si termina ahí)

---

### Post by sartrejp on 2009-01-07
Me di por vencido con mencoder y vlc, con el único programa que funciona la webcam es con cheese. ¿Sabe alguno como indicar desde la consola que grabe? La idea es ponerla a grabar a determinada hora con cron o at, pero no se como indicarlo sino es desde el entorno gráfico.

---

### Post by Hei Ku on 2009-01-07
Probá con "dcop cheese"

Si implementa dcop, lo podes manejar asi. Eso te va a tirar las funciones habilitadas.

---

### Post by sartrejp on 2009-01-07
No che, me tira "No such application: 'cheese'" 
(primero tuve que lanzar dcopserver porque sino me decía que no se podía conectar)

---

### Post by sergiom99 on 2009-01-08
tenes instalado cheese?

---

### Post by sartrejp on 2009-01-08
Jajaja si, lo tengo. Lo extraño es que no aparece en el menu aplicaciones, pero desde la terminal lo lanzo escribiendo cheese, precisamente por eso me extraña el mensaje.

---

