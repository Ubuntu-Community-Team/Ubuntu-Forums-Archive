---
title: "Problema con VLC"
date: 2009-02-06
forum: Software
---

### Post by rubioo on 2009-02-06
Hola gente, resulta que escuchando a los arctic monkeys con el vlc y probando las opciones del ecualizador, al seleccionar la opcion pop se cierra el vlc :S queria saber si a ustedes les pasa esto y como solucionarlo, o como reportar el bug.

 Gracias y saludos

---

### Post by SLA_leandrin on 2009-02-06
Yo te diría que lo largues desde la consola

```
vlc
```

y pruebes ahí, asi podes leer el error que te larga, y postearlo aquí.
ahí veremos que es lo q pasa.

---

### Post by rubioo on 2009-02-06
Hola, me sale esto: 

 > VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "es"
[00000001] main libvlc: Ejecutar vlc con el interfaz por defecto. Usa 'cvlc' para usar vlc sin interfaz.
*** buffer overflow detected ***: vlc terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7ef6548]
/lib/tls/i686/cmov/libc.so.6[0xb7ef4670]
/lib/tls/i686/cmov/libc.so.6[0xb7ef3d68]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0xc8)[0xb7e69a18]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0xf4a)[0xb7e3c8da]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xa4)[0xb7ef3e14]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xb7ef3d5d]
/usr/lib/vlc/audio_filter/libequalizer_plugin.so[0xaeb7979c]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:02 8005942    /usr/bin/vlc
0804a000-0804b000 r--p 00001000 08:02 8005942    /usr/bin/vlc
0804b000-0804c000 rw-p 00002000 08:02 8005942    /usr/bin/vlc
09895000-09b03000 rw-p 09895000 00:00 0          [heap]
ad8cc000-ad8d5000 r-xp 00000000 08:02 8004723    /usr/lib/liba52-0.7.4.so
ad8d5000-ad8d6000 rw-p 00008000 08:02 8004723    /usr/lib/liba52-0.7.4.so
ad8d6000-ad8d7000 rw-p ad8d6000 00:00 0 
ad8d7000-ad8f0000 r-xp 00000000 08:02 8005933    /usr/lib/libdca.so.0.0.0
ad8f0000-ad8f1000 r--p 00018000 08:02 8005933    /usr/lib/libdca.so.0.0.0
ad8f1000-ad8fe000 rw-p 00019000 08:02 8005933    /usr/lib/libdca.so.0.0.0
ad8fe000-ad914000 r-xp 00000000 08:02 8005239    /usr/lib/libmad.so.0.2.1
ad914000-ad915000 r--p 00015000 08:02 8005239    /usr/lib/libmad.so.0.2.1
ad915000-ad916000 rw-p 00016000 08:02 8005239    /usr/lib/libmad.so.0.2.1
ad91d000-ad923000 r-xp 00000000 08:02 8520291    /usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
ad923000-ad924000 r--p 00005000 08:02 8520291    /usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
ad924000-ad925000 rw-p 00006000 08:02 8520291    /usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
ad925000-ad926000 ---p ad925000 00:00 0 
ad926000-ae126000 rw-p ad926000 00:00 0 
ae126000-ae127000 ---p ae126000 00:00 0 
ae127000-ae927000 rw-p ae127000 00:00 0 
ae927000-aeb28000 rw-s 00000000 00:15 21104      /dev/shm/pulse-shm-4266101744
aeb28000-aeb76000 r-xp 00000000 08:02 8004374    /usr/lib/libpulse.so.0.4.1
aeb76000-aeb77000 r--p 0004d000 08:02 8004374    /usr/lib/libpulse.so.0.4.1
aeb77000-aeb78000 rw-p 0004e000 08:02 8004374    /usr/lib/libpulse.so.0.4.1
aeb78000-aeb7b000 r-xp 00000000 08:02 8520297    /usr/lib/vlc/audio_filter/libequalizer_plugin.so
aeb7b000-aeb7c000 ---p 00003000 08:02 8520297    /usr/lib/vlc/audio_filter/libequalizer_plugin.so
aeb7c000-aeb7d000 r--p 00003000 08:02 8520297    /usr/lib/vlc/audio_filter/libequalizer_plugin.so
aeb7d000-aeb7e000 rw-p 00004000 08:02 8520297    /usr/lib/vlc/audio_filter/libequalizer_plugin.so
aeb7e000-aeb80000 r-xp 00000000 08:02 8520284    /usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
aeb80000-aeb81000 r--p 00001000 08:02 8520284    /usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
aeb81000-aeb82000 rw-p 00002000 08:02 8520284    /usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
aeb82000-aeb85000 r-xp 00000000 08:02 8520290    /usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
aeb85000-aeb86000 r--p 00002000 08:02 8520290    /usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
aeb86000-aeb87000 rw-p 00003000 08:02 8520290    /usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
aeb87000-aeb88000 ---p aeb87000 00:00 0 
aeb88000-af388000 rw-p aeb88000 00:00 0 
af388000-af3c3000 r-xp 00000000 08:02 8005265    /usr/lib/libfaad.so.0.0.0
af3c3000-af3c4000 ---p 0003b000 08:02 8005265    /usr/lib/libfaad.so.0.0.0
af3c4000-af3c5000 r--p 0003b000 08:02 8005265    /usr/lib/libfaad.so.0.0.0
af3c5000-af3c8000 rw-p 0003c000 08:02 8005265    /usr/lib/libfaad.so.0.0.0
af3c8000-af3de000 r-xp 00000000 08:02 8005241    /usr/lib/libmpeg2.so.0.0.0
af3de000-af3df000 r--p 00015000 08:02 8005241    /usr/lib/libmpeg2.so.0.0.0
af3df000-af3e0000 rw-p 00016000 08:02 8005241    /usr/lib/libmpeg2.so.0.0.0
af3e0000-af3e2000 rw-p af3e0000 00:00 0 
af3e2000-af3e4000 r-xp 00000000 08:02 8520288    /usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
af3e4000-af3e5000 r--p 00001000 08:02 8520288    /usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
af3e5000-af3e6000 rw-p 00002000 08:02 8520288    /usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
af3e6000-af3e8000 r-xp 00000000 08:02 8520302    /usr/lib/vlc/audio_mixer/libfloat32_mixer_plugin.so
af3e8000-af3e9000 r--p 00001000 08:02 8520302    /usr/lib/vlc/audio_mixer/libfloat32_mixer_plugin.so
af3e9000-af3ea000 rw-p 00002000 08:02 8520302    /usr/lib/vlc/audio_mixer/libfloat32_mixer_plugin.so
af3ea000-af3ef000 r-xp 00000000 08:02 8020433    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
af3ef000-af3f0000 r--p 00004000 08:02 8020433    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
af3f0000-af3f1000 rw-p 00005000 08:02 8020433    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
af3f1000-af446000 r-xp 00000000 08:02 8006923    /usr/lib/liboil-0.3.so.0.3.0
af446000-af447000 r--p 00054000 08:02 8006923    /usr/lib/liboil-0.3.so.0.3.0
af447000-af45e000 rw-p 00055000 08:02 8006923    /usr/lib/liboil-0.3.so.0.3.0
af45e000-af460000 rw-p af45e000 00:00 0 
af460000-af4cd000 r-xp 00000000 08:02 8007045    /usr/lib/libschroedinger-1.0.so.0.1.0
af4cd000-af4ce000 r--p 0006d000 08:02 8007045    /usr/lib/libschroedinger-1.0.so.0.1.0
af4ce000-af4cf000 rw-p 0006e000 08:02 8007045    /usr/lib/libschroedinger-1.0.so.0.1.0
af4cf000-af4d0000 rw-p af4cf000 00:00 0 
af4d1000-af4d4000 r-xp 00000000 08:02 8896554    /lib/libcap.so.1.10
af4d4000-af4d5000 rw-p 00002000 08:02 8896554    /lib/libcap.so.1.10
af4d5000-af4d8000 r-xp 00000000 08:02 8520321    /usr/lib/vlc/codec/libfaad_plugin.so
af4d8000-af4d9000 r--p 00002000 08:02 8520321    /usr/lib/vlc/codec/libfaad_plugin.so
af4d9000-af4da000 rw-p 00003000 08:02 8520321    /usr/lib/vlc/codec/libfaad_plugin.so
af4da000-af4dd000 r-xp 00000000 08:02 8520324    /usr/lib/vlc/codec/liblibmpeg2_plugin.so
af4dd000-af4de000 r--p 00002000 08:02 8520324    /usr/lib/vlc/codec/liblibmpeg2_plugin.so
af4de000-af4df000 rw-p 00003000 08:02 8520324    /usr/lib/vlc/codec/liblibmpeg2_plugin.so
af4df000-af546000 r-xp 00000000 08:02 8007099    /usr/lib/libtag.so.1.5.0
af546000-af547000 r--p 00067000 08:02 8007099    /usr/lib/libtag.so.1.5.0
af547000-af548000 rw-p 00068000 08:02 8007099    /usr/lib/libtag.so.1.5.0
af54a000-af54c000 r-xp 00000000 08:02 8520329    /usr/lib/vlc/codec/libschroedinger_plugin.so
af54c000-af54d000 r--p 00001000 08:02 8520329    /usr/lib/vlc/codec/libschroedinger_plugin.so
af54d000-af54e000 rw-p 00002000 08:02 8520329    /usr/lib/vlc/codec/libschroedinger_plugin.so
af54e000-af551000 r-xp 00000000 08:02 8520322    /usr/lib/vlc/codec/libfake_plugin.so
af551000-af552000 r--p 00002000 08:02 8520322    /usr/lib/vlc/codec/libfake_plugin.so
af552000-af553000 rw-p 00003000 08:02 8520322    /usr/lib/vlc/codec/libfake_plugin.so
af553000-af555000 r-xp 00000000 08:02 8520327    /usr/lib/vlc/codec/libpng_plugin.so
af555000-af556000 r--p 00001000 08:02 8520327    /usr/lib/vlc/codec/libpng_plugin.so
af556000-af557000 rw-p 00002000 08:02 8520327    /usr/lib/vlc/codec/libpng_plugin.so
af557000-af55f000 r-xp 00000000 08:02 8527936    /usr/lib/vlc/meta_engine/libtaglib_plugin.so
af55f000-af560000 r--p 00007000 08:02 8527936    /usr/lib/vlc/meta_engine/libtaglib_plugin.so
af560000-af561000 rw-p 00008000 08:02 8527936    /usr/lib/vlc/meta_engine/libtaglib_plugin.so
af561000-af564000 r-xp 00000000 08:02 8520326    /usr/lib/vlc/codec/libmpeg_audio_plugin.so
af564000-af565000 r--p 00002000 08:02 8520326    /usr/lib/vlc/codec/libmpeg_audio_plugin.so
af565000-af566000 rw-p 00003000 08:02 8520326    /usr/lib/vlc/codec/libmpeg_audio_plugin.so
af566000-af569000 r-xp 00000000 08:02 8520319    /usr/lib/vlc/codec/libdts_plugin.so
af569000-af56a000 r--p 00002000 08:02 8520319    /usr/lib/vlc/codec/libdts_plugin.so
af56a000-af56b000 rw-p 00003000 08:02 8520319    /usr/lib/vlc/codec/libdts_plugin.so
af56b000-af56f000 r-xp 00000000 08:02 8527969    /usr/lib/vlc/packetizer/libpacketizer_mpeg4video_plugin.so
af56f000-af570000 r--p 00003000 08:02 8527969    /usr/lib/vlc/packetizer/libpacketizer_mpeg4video_plugin.so
af570000-af571000 rw-p 00004000 08:02 8527969    /usr/lib/vlc/packetizer/libpacketizer_mpeg4video_plugin.so
af571000-af577000 r-xp 00000000 08:02 8527970    /usr/lib/vlc/packetizer/libpacketizer_mpeg4audio_plugin.so
af577000-af578000 r--p 00005000 08:02 8527970    /usr/lib/vlc/packetizer/libpacketizer_mpeg4audio_plugin.so
af578000-af579000 rw-p 00006000 08:02 8527970    /usr/lib/vlc/packetizer/libpacketizer_mpeg4audio_plugin.so
af579000-af57c000 r-xp 00000000 08:02 8527972    /usr/lib/vlc/packetizer/libpacketizer_vc1_plugin.so
af57c000-af57d000 r--p 00002000 08:02 8527972    /usr/lib/vlc/packetizer/libpacketizer_vc1_plugin.Cancelado


---

### Post by faktorqm on 2009-02-09
A mi no me pasa che! que ubuntu estas usando? salu2!

---

### Post by rubioo on 2009-02-09
Hola faktor uso ubuntu 8.10. Que raro que a vos no te pase :S

---

### Post by faktorqm on 2009-02-09
ahhh yo uso 8.04, y la version de vlc es 0.8.6e. 
en el foro dice que usas 8.04, cambialo ;) salu2!

---

### Post by sebastianabate on 2009-02-10
Sí, confirmado, a mi me hace lo mismo y únicamente con POP, todos los demás presets funcionan sin problema. Yo uso Ubuntu 8.10 de 64 bits.

---

### Post by rubioo on 2009-02-10
Si, me olvide de especificar que era de 64 bits, la versión de VLC es 0.9.4. Pero en ubuntu de 32 bits, tambien pasa esto?

---

### Post by Air23 on 2009-02-10
> **rubioo said:**
> Si, me olvide de especificar que era de 64 bits, la versión de VLC es 0.9.4. Pero en ubuntu de 32 bits, tambien pasa esto?

Si, en intrepid de 32 bits para lo mismo

---

### Post by sebastianabate on 2009-02-13
> **rubioo said:**
> Si, me olvide de especificar que era de 64 bits, la versión de VLC es 0.9.4. Pero en ubuntu de 32 bits, tambien pasa esto?

Pero en el post donde ponés la salida de consola que te tira estás usando uno compilado para 32 bits

> [00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu'En uno de 64 la línea se ve así

> [00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu'De todas forma el error se presenta en las dos plataformas, pero me parece que tendrías que revisar por qué tenés instalada la versión de 32 bits en un sistema de 64.

---

### Post by rubioo on 2009-02-13
Hola, yo lo descargue desde synaptic. Pero para estar seguro, ¿cómo me fijo que versión tengo y como instalo la de 64 bits?

       Gracias y saludos

---

### Post by sebastianabate on 2009-02-16
Si lo descargaste con synaptic te tiene que haber instalado la versión para tu arquitectura.

Estás seguro que tenés instalado Ubuntu de 64 bits? qué te devuelve el comando
```
uname -m
```En mi máquina (Intrepid de 64 bits) me devuelve
```
x86_64
```

---

### Post by rubioo on 2009-02-16
Hola sebastian, tenias razón. Lo que paso es que tenía el cd de ubuntu 8.04 de 64 bits, pero instale el de ubuntu 8.10 (que era de 32 bits). Disculpa mi ignorancia pero puedo pasarme de 32 a 64 o tengo que instalar todo de nuevo.


       Gracias y saludos

---

### Post by sebastianabate on 2009-02-18
Tenés que instalar todo de nuevo, pero podés mantener las configuraciones. Yo hice eso mismo con Ubuntu 8.04 y no tuve problema. Lo que tuve que hacer es backapear mi home y /etc (y unos directorios de /var/lib, porque tenía una base de datos MySQL y estaba probando un groupware que guardaba alguna data allí, pero por regla general con el home y /etc alcanza)

Una vez backapeado todo lo que querés mantener, reinstalás la versión de 64 bits, volvés a instalar todos los paquetes no standard que agregaste, actalizás todo y después sobreescribís el home nuevo con el del backup, y lo mismo con /etc (si tenés varios usuarios en el sistema asegurate de crearlos en el mismo orden en el que los habías creado originalmente, para evitar problemas con los permisos y los uid)

Ahora la pregunta del millón: ¿Por qué querés instalar la versión de 64 bits?
Te pregunto esto porque cuando yo hice ese cambio fue para poder virtualizar un RHEL de 64 bits porque necesitaba hacer unas pruebas, pero con la versión 2.1 de Virtualbox esto ya no es necesario, porque puede correr un Guest de 64 bits en un Host de 32 (siempre y cuando el procesador sea de 64 bits).

Me parece que hoy en día no tiene grandes beneficios usar una distribución de 64 bits para un uso personal (salvo el acceso a más de 3 GB de memoria, y si tenemos en cuenta que muchos mothers no tan viejos no soportan más de 2 GB, ni siquiera esta es una buena razón), y por el contrario, te trae algunos contratiempos (y noten que digo contratiempos y no problemas); por ejemplo el plugin de flash 10 de 64 bits está en alpha (a mi me pasa que no puedo ver los videos de Clarín, o cuando cierro Firefox mientras estoy navegando por una página con mucho flash, como youtube, queda corriendo su proceso sin cerrarse del todo), o [DJL]("http://www.djl-linux.org/") (un especie de Steam pero para Linux) que sólo instala jegos para 32 bits.

No digo que Ubuntu de 64 bits no sirva (yo lo uso diariamente y estoy más que contento), pero creo que si no es por una razón bien justificada te convendría seguir con la versión de 32 bits.

---

### Post by rubioo on 2009-02-18
Ya me parecia que tendria que instalar todo de nuevo. Pero no tengo una razon especifica para instalarlo, solamente era para 'aprovechar' mi hardware, como mi compu soporta 64 bits. Pero por ahora entonces voy a seguir con 32.


   Gracias y saludos !

---

