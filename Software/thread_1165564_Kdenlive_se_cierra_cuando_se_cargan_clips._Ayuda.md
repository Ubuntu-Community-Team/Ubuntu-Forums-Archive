---
title: "Kdenlive se cierra cuando se cargan clips. Ayuda"
date: 2009-05-20
forum: Software
---

### Post by guillermon on 2009-05-20
Hola, nuevamente pidiendo ayuda... Estoy empezando a usar Kdenlive, ya que leí que es un buen programa para editar videos y fotos desde software libre. Ocurre que una vez cargado los clips, cuando los traigo a la línea de tiempo, a la segunda vez se cierra (no apenas lo abro, que parece ser un  problema bastante frecuente). No encuentro en google una solución... Dejo un pantallazo del cartel que me sale, y el detalle del error. Desde ya gracias

Guillermo
```
Esta traza inversa parece inútil.
Probablemente se deba a que sus paquetes están generados de forma que eviten la creación de trazas inversas adecuados, o la pila se ha corrompido seriamente durante el fallo de la aplicación.

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb5d3f700 (LWP 11264)]
[New Thread 0xad8d1b90 (LWP 11540)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f99430 in __kernel_vsyscall ()
[Current thread is 0 (LWP 11264)]

Thread 2 (Thread 0xad8d1b90 (LWP 11540)):
#0  0xb7f99430 in __kernel_vsyscall ()
#1  0xb66287a6 in nanosleep () from /lib/tls/i686/cmov/libc.so.6
#2  0xb66285be in sleep () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7d9e8b2 in ?? () from /usr/lib/libkdeui.so.5
#4  0xb7d9f274 in KCrash::defaultCrashHandler () from /usr/lib/libkdeui.so.5
#5  <signal handler called>
#6  0xae13f650 in ?? ()
#7  0xb666d49e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb5d3f700 (LWP 11264)):
#0  0xb7f99430 in __kernel_vsyscall ()
#1  0xb6571be7 in pthread_join () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb3d0b39e in ?? () from /usr/lib/mlt/libmltsdl.so
#0  0xb7f99430 in __kernel_vsyscall ()

```

---

### Post by Hei Ku on 2009-05-20
Estaría bueno que lo ejecutes desde una terminal, a ver si tira algún mensaje mas informativo. Ese stacktrace no sirve de mucho, como dice ahí.

---

### Post by guillermon on 2009-05-21
> **Hei Ku said:**
> Estaría bueno que lo ejecutes desde una terminal, a ver si tira algún mensaje mas informativo. Ese stacktrace no sirve de mucho, como dice ahí.

Hola Hei Ku, he ejecutado desde el terminal como me sugieres. Para mi sorpresa, esta vez no se cuelga cuando paso las fotos a la línea de tiempo; pero ocurre algo nuevo: no se ven las mismas en el proyecto (no en el monitor del clip). Me he sacado la duda randerizando el proyecto, y se ve la pantalla negra y se escucha la música. Y también observé que no carga los videos; en mi caso son .mov; así que cuando lo cargué manualmente a uno se cerró como antes (cargué todas las fotos y supuestamente los videos con un script). Allí apareció el mismo aviso gráfico, pero en el terminal apareció esto último:
```
Crash: Application 'kdenlive' crashing...
sock_file=/home/guille/.kde/socket-guille-desktop/kdeinit4__0
kdeinit4: preparing to launch /usr/lib/kde4/libexec/drkonqi
kdenlive(3709) MyThread::run: for  0   28300   true

```

   Antes decían muchas cosas, mientras se abre el programa, y mientras se cargan cada foto. Te aclaro además, que lo hice varias veces, para ver qué pasaba, y lo mismo. Avisame si hay algo que observar. Desde ya gracias! Hasta pronto
Guillermo

---

### Post by pablo.s on 2009-05-21
> **guillermon said:**
> Y también observé que no carga los videos; en mi caso son .mov; así que cuando lo cargué manualmente a uno se cerró como antes (cargué todas las fotos y supuestamente los videos con un script).

Algunos codecs de cámaras de
fotos no le gustan a la mayoria
de los programas de video en
Linux. Fijate las propiedades
del video y ahi te dice que codec
está usando.
Por lo general cuando tienen que
procesar algunos de esos codecs
de audio (por ejemplo el Quicktime
que codifican las cámaras Kodak 
previas al HD 720p) los programas 
abortan la ejecución. Una solución 
al problema es desde el sistema
operativo privativo pasarlas por
Avidemux y codificarlas como
H264 + MP3 y ahi si editarlas en
el programa que utilices.

---

### Post by guillermon on 2009-05-23
> **pablo.s said:**
> Algunos codecs de cámaras de
fotos no le gustan a la mayoria
de los programas de video en
Linux. Fijate las propiedades
del video y ahi te dice que codec
está usando.
  Hola pablo, me he fijado como dices, y tienes razón, en tipo de archivo dice: "vídeo QuickTime (video/quicktime)". Pero me desorienta que, si mal no recuerdo, cuando tenía HH, lo había usado sin problemas, con los mismos videos. ¿y esto de que si lo ejecuto de modo gráfico se cierra solo, y cuando lo ejecuto desde consola no, pero que procesa las imágenes (cuando si lo hace cuando lo hago de modo gráfico (antes que se cierre), y más aún cuando nada de esto pasó en la versión de ubuntu anterior? La verdad que desde que estoy con JJ tengo varios problemillas de este tipo. Estoy empezando a considerar un retorno...
  Y otra cosa que estoy pensando es en probar Cinelerra antes de darme por vencido...

---

