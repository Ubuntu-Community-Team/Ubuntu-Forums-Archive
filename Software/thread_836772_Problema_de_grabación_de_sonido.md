---
title: "Problema de grabación de sonido"
date: 2008-06-21
forum: Software
---

### Post by Moonlit Knight on 2008-06-21
Hola ¿qué tal? Tengo un inconveniente para grabar con la guitarra elctrica en Ubuntu Hardy Heron.

Resulta que es así tengo la placa de sonido onboard:

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

Y aplay -l tira esto:

**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC861 Analog [ALC861 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


Tuve que recompilar alsa porque no me tomaba el alsamixer al parecer es este bug: 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382)

Después de recompilar pude acceder a alsamixer y ahí logré configurar para que tome el micrófono de adelante de la pc, toco y escucho lo que toco por los parlantes el tema es que no anda la captura porque abro el gnome-sound-recorder le asigno para que tome la salida de capture (la cual en alsamixer está seteada para que tome el front mic) y no graba nada... 

Lo mismo me pasó con qjackctl y creox... 

Por lo que yo veo la señal del micrófono va directo a los parlantes y no entra a ninguna aplicación (eso es lo que me da a entender).

Probé el LiveCD de Feisty Fawn y funcionó de maravilla sin tener que tocar nada. Pero en Gutsy no me funcionó...

Saludos y espero que puedan ayudarme. Realmente quiero grabar cosas en Ubuntu no quiero volver a tocar el windows. :(

---

### Post by Hei Ku on 2008-06-21
Tenes Gutsy o Hardy? Por lo que entendí todavía no actualizaste

---

### Post by Tosh78 on 2008-06-22
Probaste con Audacity?

---

### Post by Moonlit Knight on 2008-06-29
Tengo Hardy...

Disculpen por mi ausencia.

Agregu que cuando voy a Sistema -> Preferencias -> Sondio

Y en captura pongo probar. 

Me abre una caja de diálogo con este error:

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat ...

---

### Post by juanman on 2008-06-29
Parece q es un problema de Gnome (no solo afecta a Ubuntu)...
Un flaco de [este post]("http://ubuntuforums.org/showthread.php?t=634290") lo "solucionó" (con comillas, xq el cartel de error le sigue saltando) con:

1) Right click the speaker on panel, choose "Open Volume Control"
2) Click "Options" tab. If you don't see the options tab, edit preferences and enable "Digital input source", this will make it appear.
3) Change the "Digital Input Source" to "Digital Mic 1" from "Analog Inputs".

To set the mic volume, edit the preferences and enable "digital". A "Recording" tab appears. Move the slider up for the Digital setting. Use the sound recorder to test your sound levels.

No te lo traduzco xq sabes ingles, y yo lo voy a traducir mal :P
Si no funca segui preguntando, q no te llegue a encontrar otra vez en windows eh :lolflag:

---

### Post by Moonlit Knight on 2008-06-30
En Recording tengo el slide Digital pero no me aparece en nigún lado para seleccionar Digital input source. 

Por ahí eso varía según las options que se ponen en 

/etc/modprobe.d/alsa-base

Por lo pronto yo tengo puesto:

options snd-hda-intel model=auto

Probé con todas las que figuraban para el codec de mi placa, y con ninguna me apareció lo que vos decís.

Espero poder solucionarlo, parece que afecta a muchos.

Saludos

---

