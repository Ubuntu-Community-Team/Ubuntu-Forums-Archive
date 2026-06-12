---
title: "No Puedo Reproducir DVD Original"
date: 2009-03-30
forum: Software
---

### Post by rubioo on 2009-03-30
Hola, me compre el DVD de Arctic Monkeys At The Apollo y resulta que cuando lo voy a ver en la compu (porque estaban viendo una peli en el dvd), no lo puedo reproducir, ni con vlc ni totem. Cuando lo abro con vlc me sale esto:

> cristian@cristian-desktop:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/cristian/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f70000. Regions: 4

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed


 Y cuando lo abro con totem esto: y la pantalla de totem se queda negra:

> ** (totem:6923): DEBUG: Init of Python module
** (totem:6923): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:6923): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:6923): DEBUG: Creating Python plugin instance
** (totem:6923): DEBUG: Init of Python module
** (totem:6923): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:6923): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:6923): DEBUG: Creating Python plugin instance

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


 
 Aclaro que es el unico dvd que no puedo reproducir, ya que todos los que probe antes y despues los reproduce (totem y vlc) sin problemas.


        Gracias y Saludos!

---

### Post by pablo.s on 2009-03-30
Pregunta: ¿Tenés instalado el paquete libdvdcss2?
Este paquete te libera de casi todas las restricciones de zonas y
anticopia. Está en Medibuntu.
Saludos.

---

### Post by rubioo on 2009-03-30
Gracias pablo tenia que instalar ese paquete. Pero es normal que se vea asi? Cuando abro el dvd con el vlc no se ve muy bien, y cuando lo abro con el totem se ve algo parecido a cuadro por cuadro.

---

### Post by pablo.s on 2009-03-30
Y ahora como se ve? Si tiene restricción de zonas y
anticopia no se ve nada de nada, pero con el libdvdcss2
se ve bien?

---

### Post by rubioo on 2009-03-30
> **pablo.s said:**
> Y ahora como se ve? Si tiene restricción de zonas y
anticopia no se ve nada de nada, pero con el libdvdcss2
se ve bien?
:confused::confused::confused: ??

 No entiendo lo que me estas tratando de decir, si te referis a que si prefiero que se vea asi a que no se vea. La respuesta es obia, prefiero que se vea asi. Preguntaba solamtente si era normal que se vea asi

    Saludetes

---

### Post by Hei Ku on 2009-03-30
No, no es normal que se vea asi. Los DVDs se ven sin problemas. 

Tenes los efectos de escritorio activados (Compiz)?

---

### Post by rubioo on 2009-03-30
Si, tengo compiz activado. Pruebo desactivandolos y comento como fue.

   Gracias



 Probe desactivando compiz, pero se sigue viendo asi :S
 Alguien sabe que podria ser?

 
              Saludos!

---

### Post by rubioo on 2009-04-04
Ya encontre el motivo por el que no se veia bien, era que estaba ejecutandose xflux. Ahora que lo desactive se ve claramente mejor.
 Hay alguna manera para que no tenga que estar desactivandolo y activando cada ves que veo el dvd?


         Gracias y Saludos!

---

### Post by pablo.s on 2009-04-04
Contame que es xflux, que no lo registro.
¿Que nivel de importancia tiene en el caso?

---

### Post by rubioo on 2009-04-05
Aca tenes informacion de xflux [http://ubuntuforums.org/showthread.php?t=1090756]("http://ubuntuforums.org/showthread.php?t=1090756")
 El nivel que tiene es bastante algo, ya que cuando no lo estoy ejecutando se ve bastante mejor.

---

### Post by faktorqm on 2009-04-06
Comentario personal: Me parece malisimo ese programa, si me estoy rompiendo la vista o prendo la luz de la habitacion donde este o bajo el brillo del monitor con los botones o el OSD que traiga, ni cerca gasto un solo byte de mi memoria ram es un programa que hace lo mismo que el hardware.

Lo que me parece extraño es que intervenga en la velocidad de reproduccion, creo que no deberia meterse en eso. Estas usando motor xine para reproducir? salu2!

---

### Post by rubioo on 2009-04-06
Hola faktor, no estoy usando xine, uso el que viene por default

---

