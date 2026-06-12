---
title: "Problema audio Gnome"
date: 2009-09-15
forum: Software
---

### Post by ramiro_md on 2009-09-15
Gente ando con un problema bastante denso. Resulta que no puedo hacer que ande el audio en las aplicaciones de Gnome tales como Totem y Rhythmbox y también otras como VLC.
Problemas de ALSA no creo que sea porque lo instale y configure de lo más bien mediante synaptic y alsaconf. Y aplicaciones como Amarok y Smplayer me reproducen mp3 y el audio de las pelis lo más tranquilo.
EL tema es que no me son imprescindibles las aplicaciones que no funcionan del todo bien, porque uso Amarok para mp3 y Smplayer para videos, pero las cosas tienen que andar siempre !.
Ya no sé que puede ser, instalé todo lo que sabía que debía instalar y más también. Todo lo relacionado a audio que encontré por synaptic lo instalé por si las dudas y el problema no se soluciona.
A continuación dejo una lista de todo el paqueterio que tengo instalado para que ustedes me digan si me puede llegar a faltar algo o no...les aclaro que estoy usando Debian Squeeze.

> - Gstreamer0.10-alsa
- Gstreamer0.10-esd
- Gstreamer0.10-ffmpeg
- Gstreamer0.10-fluendo-mp3
- Gstreamer0.10-gnomevfs
- Gstreamer0.10-lame
- Gstreamer0.10-nice
- Gstreamer0.10-pitfdll
- Gstreamer0.10-plugins-bad
- Gstreamer0.10-plugins-base
- Gstreamer0.10-plugins-good
- Gstreamer0.10-plugins-ugly
- Gstreamer0.10-plugins-bad
- Gstreamer0.10-tools
- Gstreamer0.10-x
- Lame
- Ffmpeg
- Win32codecs
- Totem-gstreamer
- libmp3lame0
- libdvdnav4
- libdvdread3
- libdvdcss2
- avifile-divx-plugin
- ibfaad2-0
- libmp4v2-0
- libfaac0

Un saludo y gracias !.

---

### Post by guillermolisi on 2009-09-15
No usas PulseAudio ?

---

### Post by ramiro_md on 2009-09-15
Que yo sepa, no. Usé toda la vida ALSA. Es más aconsejable PulseAudio ?

---

### Post by guillermolisi on 2009-09-15
> **ramiro_md said:**
> Que yo sepa, no. Usé toda la vida ALSA. Es más aconsejable PulseAudio ?
Los comentarios que tuve de quienes lo usan en JJ son alentadores. Incluso Pablo.s hizo un tutorial muy bueno que esta aqui, en el foro.

Si actualmente no te funciona bien lo relacionado con audio, que podrias perder por probar con PulseAudio ? Siguiendo el tuto deberias llegar a buen termino.

---

### Post by Hei Ku on 2009-09-15
tenes el paquete de pulseaudio instalado o no?

Y eso de que las cosas tienen que andar siempre, a veces depende de "quien" les meta mano. ;)

---

### Post by pablo.s on 2009-09-15
Tutorial [aqui]("http://ubuntuforums.org/showpost.php?p=7522891&postcount=1").

---

### Post by ramiro_md on 2009-09-16
> **Hei Ku said:**
> Y eso de que las cosas tienen que andar siempre, a veces depende de "quien" les meta mano. ;)
Pienso exactamente igual, entonces decidí limpiar todo y arrancar de 0. 

Formatie, volví a instalar Squeeze, seguí los pasos de [esta]("http://man-es.debianchile.org/alsa.html") guía para configurar ALSA, me instalé el Rhythmbox y salió andando todo lo más bien :D.
Pero esto no acaba acá, hoy ala mañana me levanto y empiezo a instalar algunas cositas fundamentales para internet como Java y Flash (desde los repositorios) una vez instalados dije, bueno veamos algunos videillos de youtube para probar, y es ahí donde todo empezó a andar mal nuevamente :S.
Los videos se reproducian sin sonido y Rhythmbox me daba el siguiente mensaje de error:
> Tanto el elemento autoaudiosink como alsasink no están funcionando.
Me fijé si tenía los módulos cargados y me devolvió todo como estaba ayer por la noche cuando funcionaba perfecto.
> snd_hda_codec_realtek   178472  1 
snd_hda_intel          22192  0 
snd_hda_codec          63580  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            32232  0 
snd_mixer_oss          12368  1 snd_pcm_oss
snd_usb_audio          72088  0 
snd_pcm                62420  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_usb_audio
snd_usb_lib            13528  1 snd_usb_audio
snd_seq_midi            5688  0 
snd_seq_midi_event      6212  1 snd_seq_midi
snd_seq                42436  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            18596  2 snd_usb_lib,snd_seq_midi
snd_timer              17436  2 snd_pcm,snd_seq
snd_seq_device          6136  3 snd_seq_midi,snd_seq,snd_rawmidi
snd_hwdep               6120  2 snd_hda_codec,snd_usb_audio
snd                    49060  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device,snd_hwdep
snd_page_alloc          8180  2 snd_hda_intel,snd_pcm

Entré al gstreamer-properties y el "pitido" que hacia al probar ALSA con mi placa ya no lo hace más :S.
Leyendo el tuto de Pablo vi que los paquetes libflashsupport y flashplugin-nonfree-extrasound traían algunos dramas, verifiqué si tenía alguno instalado y así era, tenia el flashplugin-nonfree-extrasound.
Lo desinstale para ver si solucionaba algo pero no pasó nada com oera de esperar je.
Aún no he instalado pulseaudio porque quiero solucionar el tema de ALSA, luego de que arregle ese tema instalaré pulseaudio para ver si soluciono lo del audio youtube.
Un saludo, y gracias por todo !.

---

### Post by ramiro_md on 2009-09-18
El problema era de Rhythmbox únicamente. Ahora estoy usando Listen y va de 10.
Un saludo.

---

### Post by pablo.s on 2009-09-18
No te enojes, pero según mi
punto de vista si el problema
lo tenías con Rhythmbox y no
lo tenés porque usas Listen,
eso no califica como [SOLVED]
porque es un placebo.
Pero si a vos te sirve todo bien...

---

### Post by guillermolisi on 2009-09-18
> **pablo.s said:**
> No te enojes, pero según mi
punto de vista si el problema
lo tenías con Rhythmbox y no
lo tenés porque usas Listen,
eso no califica como [SOLVED]
porque es un placebo.
Pero si a vos te sirve todo bien...
Coincido. Es equivalente a "ya esta, reinstale y anduvo" pero nunca se sabe el origen del sintoma, ademas de la causa que suele estar entre la silla y el teclado :)

---

