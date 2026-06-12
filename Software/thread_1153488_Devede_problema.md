---
title: "Devede problema"
date: 2009-05-08
forum: Software
---

### Post by Applelnx on 2009-05-08
Hola me baje el Devede para crear DVD con menus etc. Todo bien hasta la parte de crearlo cuando me salta un problema con el Mencoder. Busque en google y parece que se trata de un problema con la nueva version del Mplayer. Lo unico que encontre es un fix que te hace un downgrade, publicado en la pagina [www.rastersoft.com](www.rastersoft.com), pero la pagina me aparece caida.

Alguno en una de esas casualidades tiene este fix (version 64 bits)
(un poco especifico, no?? :S). 

O saben como solucionarlo? Saludos

---

### Post by pablo.s on 2009-05-08
Podés especificar mas el problema?

Mensajes de error de la versión,
paquete en cuestión?

---

### Post by guillermolisi on 2009-05-09
> **Applelnx said:**
> Hola me baje el Devede para crear DVD con menus etc. Todo bien hasta la parte de crearlo cuando me salta un problema con el Mencoder. Busque en google y parece que se trata de un problema con la nueva version del Mplayer. Lo unico que encontre es un fix que te hace un downgrade, publicado en la pagina [www.rastersoft.com]("http://www.rastersoft.com"), pero la pagina me aparece caida.

Alguno en una de esas casualidades tiene este fix (version 64 bits)
(un poco especifico, no?? :S). 

O saben como solucionarlo? Saludos
Si vas a llevar a cabo tareas multimedia, mi consejo es que incluyas los repositorios y bajes codecs de medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

En ese link encontraras como agregar el repo e incorporar la firma digital para que no te rete por incauto el administrador de paquetes/actualizaciones.

---

### Post by Applelnx on 2009-05-09
Hola, gracias por responder. El fix que estaba buscando ya lo encontre pero no me soluciono nada. Al hacer un downgrade de mplayer y mencoder, el programa Devede no abria (necesita de estos dos para funcionar asi que supongo que no los reconocia).

El mensaje de error no especifica mucho, cuando esta creando el menu 1 se interrumpe y dice:

```
[B]Error
Ha fallado la conversion. Parece un error de Mencoder.[/B]
```

Me baje los codecs desde Medibuntu (los de w64codecs pero sigue con el mismo error). No se que podra ser...

PD: ayer probe con uno solo de los videos y funcionaba. Parece que hay uno que tiene problemas.

Los archivos de video estan en AVI, voy a probar pasar a MPEG y les aviso.

---

### Post by inigoalda on 2009-11-30
hola  nada mas empezar me tira el error,error de conversion parece un
problema de mencoder
alguna idea
gracias
inigo@inigo-laptop:~$ sudo devede
[sudo] password for inigo:
DeVeDe 3.15.0
Locale: es_ES.UTF-8
Using package-installed files
/home/inigo/
Entro en fonts
Salgo de fonts
/home/inigo/
Temp Directory is:  /var/tmp
home load:  /home/inigo/.devede
linea:  video_format:pal

linea:  temp_folder:/var/tmp/

linea:  multicore:2

linea:
Creating window /usr/share/devede/wdisk_type.ui
Creating window /usr/share/devede/wmain.ui
Launching program:  mplayer -loop 1 -identify -ao null -vo null -
frames 0 /usr/share/devede/silence.ogg
elemento:  /usr/bin
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote
control.
Longitud sonido: 38
Cores: 2
Launching program:  mplayer -loop 1 -identify -ao null -vo null -
frames 0 /usr/share/devede/silence.ogg
elemento:  /usr/bin
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote
control.
Longitud sonido: 38
Calculating size for disk :dvd
Calculating size for disk :dvd
Creating window /usr/share/devede/wfile.ui
Anado filtro
Anado filtro
Traceback (most recent call last):
  File "/usr/lib/devede/devede_main.py", line 607, in
on_add_chapter_clicked
    window=devede_newfiles.file_properties
(self.global_vars,title,-1,self.structure,self.refresh_all)
  File "/usr/lib/devede/devede_newfiles.py", line 548, in __init__
    self.set_widgets()
  File "/usr/lib/devede/devede_newfiles.py", line 1065, in set_widgets
    w.set_lower(128)
AttributeError: 'gtk.Adjustment' object has no attribute 'set_lower'
File changed to /home/inigo/Azureus Downloads/Enchufados a la red
(DVDRip) (EliteTorrent.net).avi
Launching program:  mplayer -loop 1 -identify -ao null -vo null -
frames 0 /home/inigo/Azureus Downloads/Enchufados a la red (DVDRip)
(EliteTorrent.net).avi
elemento:  /usr/bin
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote
control.
Launching program:  mplayer -loop 1 -identify -ao null -vo null -
frames 1 /home/inigo/Azureus Downloads/Enchufados a la red (DVDRip)
(EliteTorrent.net).avi
elemento:  /usr/bin
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote
control.
[mpeg4 @ 0x89d22c0]Invalid and inefficient vfw-avi packed B frames
detected
Traceback (most recent call last):
  File "/usr/lib/devede/devede_newfiles.py", line 876, in
on_moviefile_file_set
    self.set_widgets()
  File "/usr/lib/devede/devede_newfiles.py", line 1065, in set_widgets
    w.set_lower(128)
AttributeError: 'gtk.Adjustment' object has no attribute 'set_lower'
Calculating size for disk :dvd
Threads: 2
Creating window /usr/share/devede/wprogress.ui
Creating window /usr/share/devede/wfolder_dialog.ui
Creating window /usr/share/devede/wfolder_exists.ui
Path para borrar: /home/inigo/movie/movie
Checking /home/inigo/movie/
Free space in /home/inigo/movie/: 88299662
estatus  posix.statvfs_result(f_bsize=4096, f_frsize=4096,
f_blocks=27733834L, f_bfree=24100941L, f_bavail=22692142L,
f_files=7045120L, f_ffree=6830906L, f_favail=6830906L, f_flag=4096,
f_namemax=255)

Calculating size for disk :dvd
Free: 88299662
Needed: 5358.0
/home/inigo/movie/movie.cue not found
/home/inigo/movie/movie.bin not found
/home/inigo/movie/movie/ not found
/home/inigo/movie/movie.iso not found
delete menu temp
delete menu
Deleting movie_??_??.mpg
/home/inigo/movie/movie.xml not found
Borro principal
Menu PAL: True
Menu1 0 0
Uso /usr/share/devede/backgrounds/default_bg.png
0.325
Paint_bg 0 title text:
0.325
Paint_bg 1 title text:
0.325
Paint_bg 3 title text:
Creating menus
Lanzo ['mencoder', '-srate', '48000', '-af', 'lavcresample=48000', '-
oac', 'lavc', '-ovc', 'lavc', '-of', 'mpeg', '-mpegopts',
'format=dvd:tsaf', '-ofps', '25', '-vf', 'scale=720:576,harddup', '-
lavcopts',
'threads=2:vcodec=mpeg2video:sc_threshold=1000000000:cgop:trell:mbd=2:vstrict=0:vrc_maxrate=7000:vrc_buf_size=1835:vbitrate=1000:keyint=12:acodec=ac3:abitrate=128:aspect=4/3',
'-o', '/home/inigo/movie/movie_menu_0.mpg', '-audiofile', '/usr/share/
devede/silence.ogg', '-mf', 'type=png:fps=1/38', 'mf:///home/inigo/
movie/movie_menu0_bg.png']
Launching program:  mencoder -srate 48000 -af lavcresample=48000 -oac
lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -ofps 25 -vf
scale=720:576,harddup -lavcopts
threads=2:vcodec=mpeg2video:sc_threshold=1000000000:cgop:trell:mbd=2:vstrict=0:vrc_maxrate=7000:vrc_buf_size=1835:vbitrate=1000:keyint=12:acodec=ac3:abitrate=128:aspect=4/3
-o /home/inigo/movie/movie_menu_0.mpg -audiofile /usr/share/devede/
silence.ogg -mf type=png:fps=1/38 mf:///home/inigo/movie/movie_menu0_bg.png
elemento:  /usr/bin
Unsupported PixelFormat -1
MEncoder SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: /home/inigo/movie/movie_menu0_bg.png*
[mf] number of files: 1 (4)
VIDEO:  [MPNG]  0x0  24bpp  0.026 fps    0.0 kbps ( 0.0 kbyte/s)
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
[V] filefmt:65536  fourcc:0x474E504D  size:0x0  fps:0.026
ftime:=38.0000
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
Pos:  38.0s      1f ( 0%)  0.10fps Trem:   0min   0mb  A-V:0.000
[484:0]
[ac3 @ 0xa16a3b0]No channel layout specified. The encoder will guess
the layout, Flushing video frames.
Launch: spumux "/home/inigo/movie/movie_menu_0.xml"
Launching shell program: spumux "/home/inigo/movie/movie_menu_0.xml" <
"/home/inigo/movie/movie_menu_0.mpg" > "/home/inigo/movie/
movie_menu2_0.mpg"

delete menu temp
Addbars True resx_o 576 resy_o 320
resx_i 576 resy_i 432
Launching program:  mencoder -oac lavc -aid 1 -ovc lavc -of mpeg -
mpegopts format=dvd:tsaf -ofps 25 -vf
expand=576:432:0:56,scale=720:576,harddup -lavcopts
threads=2:vcodec=mpeg2video:trell:mbd=0:sc_threshold=1000000000:cgop:vstrict=0:vrc_maxrate=0:vrc_buf_size=1835:vbitrate=0:keyint=15:acodec=ac3:abitrate=0:aspect=4/3
-o /home/inigo/movie/movie_01_01.mpg /home/inigo/Azureus Downloads/
Enchufados a la red (DVDRip) (EliteTorrent.net).avi
elemento:  /usr/bin
Creating window /usr/share/devede/werror_dialog.ui


y esto sele en consola como root

---

### Post by guillermolisi on 2009-11-30
Y por que ejecutas todo eso con sudo ?
Probaste de hacer lo mismo pero con tu usuario de siempre, sin sudo ?
Que sucede si corres sin sudo ?

---

### Post by nemodot on 2009-11-30
Si la página aparece caída algo que me sirve a mi para acceder es buscarla en google y entrar por la opción "En Caché". Es como que el buscador mantiene una copia de la ubicación en su servidor.

---

