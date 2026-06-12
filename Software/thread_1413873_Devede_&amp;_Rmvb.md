---
title: "Devede &amp; Rmvb"
date: 2010-02-23
forum: Software
---

### Post by NickCis on 2010-02-23
Hola, tengo que hacer un dvd con videos rmvb. Instale la version mas nueva del devede con el deb de su propia pagina.
El resto de las depedencias instaladas desde los repositorios de ubuntu (el repo de medibuntu esta activado).
Tengo ubuntu 9.10.

El problema es que cuando esta haciendo el iso del dvd (en el principio):
Devuelve el error de "Ha Fallado la conversion. Parece un problema de mencoder", y no puedo hacer el iso del dvd.

Muchas gracias =P.

Dejo la salida de consola:

```

newpc@newpc:~/Descargas/Trois Coleurs$ devede
DeVeDe 3.16.3
Locale: es_AR.UTF-8
Using package-installed files
/home/newpc/
Entro en fonts
Salgo de fonts
/home/newpc/
Temp Directory is:  /var/tmp
home load:  /home/newpc/.devede
linea:  video_format:pal

linea:  temp_folder:/var/tmp/

linea:  multicore:1

linea:  final_folder:/home/newpc

linea:  sub_language:EN (ENGLISH)

linea:  sub_codepage:ISO-8859-1

linea:  
Creating window /usr/share/devede/wdisk_type.ui
Creating window /usr/share/devede/wmain.ui
Launching program:  mplayer -loop 1 -identify -ao null -vo null -frames 0 /usr/share/devede/silence.ogg
elemento:  /usr/bin
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Longitud sonido: 38
Cores: 1
Launching program:  mplayer -loop 1 -identify -ao null -vo null -frames 0 /usr/share/devede/silence.ogg
elemento:  /usr/bin
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Longitud sonido: 38
Calculating size for disk :dvd
Calculating size for disk :dvd
Creating window /usr/share/devede/wloadconfig.ui
/usr/lib/devede/devede_loadsave.py:63: GtkWarning: gtk_widget_grab_default: assertion `GTK_WIDGET_CAN_DEFAULT (widget)' failed
  window.show()
Launching program:  mplayer -loop 1 -identify -ao null -vo null -frames 0 /usr/share/devede/silence.ogg
elemento:  /usr/bin
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Calculating size for disk :dvd
Calculating size for disk :dvd
Con menu: True
Threads: 1
Creating window /usr/share/devede/wprogress.ui
Creating window /usr/share/devede/wfolder_dialog.ui
Creating window /usr/share/devede/wfolder_exists.ui
Path para borrar: /home/newpc/TROIS_COLEURS/TROIS_COLEURS
Checking /home/newpc/TROIS_COLEURS/
Free space in /home/newpc/TROIS_COLEURS/: 28134745
estatus  posix.statvfs_result(f_bsize=4096, f_frsize=4096, f_blocks=13899536L, f_bfree=7936408L, f_bavail=7230352L, f_files=3530752L, f_ffree=3308972L, f_favail=3308972L, f_flag=0, f_namemax=255) 

Calculating size for disk :dvd
Free: 28134745
Needed: 3862950.0
/home/newpc/TROIS_COLEURS/TROIS_COLEURS.cue not found
/home/newpc/TROIS_COLEURS/TROIS_COLEURS.bin not found
/home/newpc/TROIS_COLEURS/TROIS_COLEURS/ not found
/home/newpc/TROIS_COLEURS/TROIS_COLEURS.iso not found
delete menu temp
delete menu
Deleting TROIS_COLEURS_??_??.mpg
Trying to delete /home/newpc/TROIS_COLEURS/TROIS_COLEURS_01_01.mpg
Deleting TROIS_COLEURS.log
/home/newpc/TROIS_COLEURS/TROIS_COLEURS.log not found
/home/newpc/TROIS_COLEURS/TROIS_COLEURS.xml not found
Borro principal
Menu PAL: True
Menu1 0 0
Uso /home/newpc/Descargas/Trois Coleurs/Trilogy_dvdcover_high.jpg
0.275
0.325
0.375
Paint_bg 0 title text: 
0.275
0.325
0.375
Paint_bg 1 title text: 
0.275
0.325
0.375
Paint_bg 3 title text: 
Creating menus
Lanzo ['mencoder', '-srate', '48000', '-af', 'lavcresample=48000', '-oac', 'lavc', '-ovc', 'lavc', '-of', 'mpeg', '-mpegopts', 'format=dvd:tsaf', '-ofps', '25', '-vf', 'scale=720:576,harddup', '-lavcopts', 'vcodec=mpeg2video:sc_threshold=1000000000:cgop:trell:mbd=2:vstrict=0:vrc_maxrate=7000:vrc_buf_size=1835:vbitrate=1000:keyint=12:acodec=ac3:abitrate=128:aspect=4/3', '-o', '/home/newpc/TROIS_COLEURS/TROIS_COLEURS_menu_0.mpg', '-audiofile', '/usr/share/devede/silence.ogg', '-mf', 'type=png:fps=1/38', 'mf:///home/newpc/TROIS_COLEURS/TROIS_COLEURS_menu0_bg.png']
Launching program:  mencoder -srate 48000 -af lavcresample=48000 -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -ofps 25 -vf scale=720:576,harddup -lavcopts vcodec=mpeg2video:sc_threshold=1000000000:cgop:trell:mbd=2:vstrict=0:vrc_maxrate=7000:vrc_buf_size=1835:vbitrate=1000:keyint=12:acodec=ac3:abitrate=128:aspect=4/3 -o /home/newpc/TROIS_COLEURS/TROIS_COLEURS_menu_0.mpg -audiofile /usr/share/devede/silence.ogg -mf type=png:fps=1/38 mf:///home/newpc/TROIS_COLEURS/TROIS_COLEURS_menu0_bg.png
elemento:  /usr/bin
Unsupported PixelFormat -1
MEncoder SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: /home/newpc/TROIS_COLEURS/TROIS_COLEURS_menu0_bg.png*
[mf] number of files: 1 (4)
VIDEO:  [MPNG]  0x0  24bpp  0.026 fps    0.0 kbps ( 0.0 kbyte/s)
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
[V] filefmt:65536  fourcc:0x474E504D  size:0x0  fps:0.026  ftime:=38.0000
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 8000->192000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
PACKET SIZE: 2048 bytes, deltascr: 43885
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=720 h=576]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffpng] vfm: ffmpeg (FFmpeg PNG)
==========================================================================
VDec: vo config request - 720 x 576 (preferred colorspace: BGRA)
VDec: using BGRA as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (720x576 fourcc=3267706d [mpg2])
[VE_LAVC] High quality encoding selected (non-realtime)!
Writing header...
INITV: 0.200, 0.160, fps: 25.000
Pos:  38.0s      1f ( 0%)  0.05fps Trem:   0min   0mb  A-V:0.000 [1047:0]
Limiting audio preload to 0.4s.
Flushing video frames.
Launch: spumux "/home/newpc/TROIS_COLEURS/TROIS_COLEURS_menu_0.xml"
Launching shell program: spumux "/home/newpc/TROIS_COLEURS/TROIS_COLEURS_menu_0.xml" < "/home/newpc/TROIS_COLEURS/TROIS_COLEURS_menu_0.mpg" > "/home/newpc/TROIS_COLEURS/TROIS_COLEURS_menu2_0.mpg"

delete menu temp
Segundos 0
Addbars True resx_o 720 resy_o 408
resx_i 720 resy_i 540
Launching program:  mencoder -srate 48000 -af lavcresample=48000 -oac lavc -aid 0 -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -ofps 25 -vf expand=720:540:0:66,scale=720:576,harddup -lavcopts vcodec=mpeg2video:trell:mbd=2:sc_threshold=1000000000:cgop:vstrict=0:vrc_maxrate=3108:vrc_buf_size=1835:vbitrate=1554:keyint=12:acodec=ac3:abitrate=224:aspect=4/3 -o /home/newpc/TROIS_COLEURS/TROIS_COLEURS_01_01.mpg /home/newpc/Descargas/Trois Coleurs/Trois Couleurs - Bleu (Krzysztof Kieslowski, 1993).rmvb
elemento:  /usr/bin
Error loading dll
Creating window /usr/share/devede/werror_dialog.ui

```

---

### Post by NickCis on 2010-02-23
Supongo que es un problema del Mplayer (mencoder), tampoco puedo reproducir videos rmvb con el Mplayer,, Busque como solucionarlo (eso de copiar los essentials codecs bajados de la pagina de Mplayer pero tampoco funciono).
Tengo activados los repositorios de Medibuntu e instalados los paquetes w32codecs libdvdcss2 non-free-codecs y ubuntu-restricted-extrass.

Alguna ayuda?

Saludos.

EDIT:
Ya encontre la linea qe delata el problema:
```

ERROR: Could not open required DirectShow codec drvc.dll.

```

Parece qe con los essentials de Mplayer no tengo todas las dll necesarias para reproducir los videos. Alguien sabe de donde puedo conseguir los codecs para rmvb?

Hice lo de esta pagina: [http://mipclibre.wordpress.com/2009/08/01/crear-dvd-en-linux-con-devede-instalando-mplayer-con-soporte-para-rmvb/](http://mipclibre.wordpress.com/2009/08/01/crear-dvd-en-linux-con-devede-instalando-mplayer-con-soporte-para-rmvb/) y sigo sin solucion =S

Tras mucho rezar, ahora el mplayer reproduce los rmvb, pero el devede no me deja trabajar con ellos. (Devede me sigue devolviendo lo mismo qe en el primer post =S)

---

### Post by guillermolisi on 2010-02-23
> **NickCis said:**
> Supongo que es un problema del Mplayer (mencoder), tampoco puedo reproducir videos rmvb con el Mplayer,, Busque como solucionarlo (eso de copiar los essentials codecs bajados de la pagina de Mplayer pero tampoco funciono).
Tengo activados los repositorios de Medibuntu e instalados los paquetes w32codecs libdvdcss2 non-free-codecs y ubuntu-restricted-extrass.

Alguna ayuda?

Saludos.

EDIT:
Ya encontre la linea qe delata el problema:
```

ERROR: Could not open required DirectShow codec drvc.dll.

```Parece qe con los essentials de Mplayer no tengo todas las dll necesarias para reproducir los videos. Alguien sabe de donde puedo conseguir los codecs para rmvb?

Hice lo de esta pagina: [http://mipclibre.wordpress.com/2009/08/01/crear-dvd-en-linux-con-devede-instalando-mplayer-con-soporte-para-rmvb/](http://mipclibre.wordpress.com/2009/08/01/crear-dvd-en-linux-con-devede-instalando-mplayer-con-soporte-para-rmvb/) y sigo sin solucion =S

Tras mucho rezar, ahora el mplayer reproduce los rmvb, pero el devede no me deja trabajar con ellos. (Devede me sigue devolviendo lo mismo qe en el primer post =S)
Hasta hace unos meses atras, DeVeDe no resolvia bien o directamente no resolvia el formato rmvb.

En este subforo hay dos o tres hilos que hablan directa o indirectamente de ello, todos referidos al formato en cuestion.

---

### Post by NickCis on 2010-02-24
Ahh,, por qe me baje la version mas nueva de Devede ( [http://www.rastersoft.com/programas/devede_es.html#download_section](http://www.rastersoft.com/programas/devede_es.html#download_section) ) que supuestamente ya soporta,, Devede dice qe el error esta relacionado al mencoder, pero la verdad ni idea =S..

Las soluciones provistas eran pasar el rmvb a avi y ahi usar el devede. Crei que ya habia sido solucionado el problema de rmvb con devede ya que Devede desde su version 3.15.0 ya soporta rmvb
 
```

# Version 3.15.0 (2009-11-27)
# Añadido -loop 1 en los comandos de mplayer para evitar problemas cuando el usuario tiene un fichero mplayer.config
# Modificada la distribución de la ventana principal para adaptarse mejor a pantallas panorámicas
# Añadido soporte de OGG/Vorbis para el sonido de fondo de los menús
# Añadidos nuevos fondos para los menús (Gracias a Ben)
# Soporte de la extensión RMVB
# El icono del botón de previsualización desaparece si la configuración global indica que no se deben pintar iconos
# Al utilizar Resolución por defecto en DivX, no se toca ni el tamaño, ni la relación de aspecto, ni se añaden barras
# Actualizada la traducción a francés
# Actualizada la traducción a gallego
# Traducción a chino tradicional
# Soporte de nombres de ficheros que contengan comillas (Gracias a Christian)
# Permite dividir en dos una película tanto en SVCD como en CVD, no sólo en VCD

```

Gracias igualmente =P, voy a ver que puedo hacer =P

---

### Post by NickCis on 2010-02-24
Volvi para atras, ahora el Mplayer ya no me reproduce rmvb.

Recapitulo el escenario: Ubuntu 9.10.
Mplayer, libcss2, ubuntu-restricted-extras, libstdc++6 (se recomendaba instalar libstdc++5 pero no existia), non-free-codecs, w32codecs. Y los essential codecs de la pagina de mplayer instalados en /usr/lib/codecs, un link simbolico de /usr/lib/win32 y /usr/local/lib/win32 a /usr/lib/codecs. (Todo instalado desde los repos de ubuntu con Medibuntu activado)

Y la ultima version de devede instalado con el deb de la pagina de devede.

Adjunto salida de terminal (el archivo adjunto tiene la salida de terminal con verbose).
Estas sin "-v":
```

newpc@newpc:~/Descargas/Trois Coleurs$ mplayer "Trois coleurs - Blue (Krzysztof Kieslowski, 1993).rmvb"
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Trois coleurs - Blue (Krzysztof Kieslowski, 1993).rmvb.
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV30]  720x408  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 comment: 
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
[VO_XV] Could not grab port 355.
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drvc.dll, /usr/lib/codecs/drvc.dll, /usr/lib/win32/drvc.dll, /usr/local/lib/win32/drvc.dll
Error loading dll
ERROR: Could not open required DirectShow codec drvc.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drv33260.dll, /usr/lib/codecs/drv33260.dll, /usr/lib/win32/drv33260.dll, /usr/local/lib/win32/drv33260.dll
Error loading dll
ERROR: Could not open required DirectShow codec drv33260.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.bundle/Contents/MacOS/drvc, /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc, /usr/lib/win32/drvc.bundle/Contents/MacOS/drvc, /usr/local/lib/win32/drvc.bundle/Contents/MacOS/drvc
Error loading dll
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: libstdc++.so.5: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.so, /usr/lib/codecs/drvc.so, /usr/lib/win32/drvc.so, /usr/local/lib/win32/drvc.so
Error loading dll
ERROR: Could not open required DirectShow codec drvc.so.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Selected video codec: [rv30] vfm: realvid (Linux RealPlayer 8 RV30)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.1 kbit/4.54% (ratio: 8010->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 408 (preferred colorspace: Planar I420)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 1.76:1 - prescaling to correct movie aspect.
VO: [xv] 720x408 => 720x408 Planar I420 
A:   0.3 V:   0.2 A-V:  0.072 ct: -0.003   5/  5 ??% ??% ??,?% 3 0 

MPlayer interrupted by signal 11 in module: decode_video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]
newpc@newpc:~/Descargas/Trois Coleurs$ 

```

Alguna idea?

---

### Post by NickCis on 2010-02-24
Problema aparentemente solucionado bajando drvc.dll ([http://www.dlldll.com/getdll/1582.html](http://www.dlldll.com/getdll/1582.html)) y poniendolo en /usr/lib/codecs.

En este momento esta haciendo el dvd, despues cuento que pasa =P.

Saludos.

Edit: Si, se soluciono de esta manera.. Pude crear el iso del dvd y anda perfectamente =P.

---

