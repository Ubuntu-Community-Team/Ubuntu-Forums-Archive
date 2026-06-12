---
title: "Emulador PSX V111 no inicia en Ubuntu Jaunty"
date: 2009-06-08
forum: Software
---

### Post by atari130xe on 2009-06-08
Buenas...

Tengo un problema con el emulador de PlayStation One PSX v111, simplemente no arranca.
ejecutandolo desde la consola tira estos errores:

```
jose@jose-desktop:~$ psx
/home/jose/.themes/XPLuna/gtk-2.0/panel.rc:13: Imposible encontrar un archivo imagen en pixmap_path: «shadows/window-bg.png»
/home/jose/.themes/XPLuna/gtk-2.0/panel.rc:112: Imposible encontrar un archivo imagen en pixmap_path: «menubar/menubar-item.png»
/home/jose/.themes/XPLuna/gtk-2.0/panel.rc:115: Background image options specified without filename
/home/jose/.themes/XPLuna/gtk-2.0/panel.rc:13: Imposible encontrar un archivo imagen en pixmap_path: «shadows/window-bg.png»
/home/jose/.themes/XPLuna/gtk-2.0/panel.rc:112: Imposible encontrar un archivo imagen en pixmap_path: «menubar/menubar-item.png»
/home/jose/.themes/XPLuna/gtk-2.0/panel.rc:115: Background image options specified without filename
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'No existe el fichero ó directorio'
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No existe el fichero ó directorio
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No existe el fichero ó directorio
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No existe el fichero ó directorio
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No existe el fichero ó directorio
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
pSX: pcm_params.c:2259: snd_pcm_hw_refine: Afirmación `pcm && params' fallida.
/home/jose/.themes/XPLuna/gtk-2.0/panel.rc:13: Imposible encontrar un archivo imagen en pixmap_path: «shadows/window-bg.png»
/home/jose/.themes/XPLuna/gtk-2.0/panel.rc:112: Imposible encontrar un archivo imagen en pixmap_path: «menubar/menubar-item.png»
/home/jose/.themes/XPLuna/gtk-2.0/panel.rc:115: Background image options specified without filename
 * PulseAudio configured for per-user sessions
jose@jose-desktop:~$ 

```

Por lo que puedo entender, hay problemas con PulseAudio, juro que no es a propósito! jajaja, la verdad que PulseAudio no es amigo mio y comienzo a detestarlo, (Volvé ALSA te queremos!).

Si alguien tiene alguna pista sobre como hacerlo funcionar, se lo agredacería.
saludos!:D

---

