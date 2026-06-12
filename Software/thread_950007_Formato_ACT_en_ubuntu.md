---
title: "Formato ACT en ubuntu"
date: 2008-10-16
forum: Software
---

### Post by guisheca on 2008-10-16
Quisiera saber si alguien tiene alguna info sobre como escuchar audio en formato ACT en ubuntu. Hasta ahora pude saber que es un formato de audio propietario destinado para mp4, pero no se como escucharlo en la pc o convertirlo a otro formato.
Son audios grabados con un mp4, grabaciones de una cátedra de la facultad de mi novia, y bueno ella no sabía y en un principio grabó las clases en ese formato. Ahora ya cambió el formato de grabación a wav, pero les quedaron varias clases grabadas en ACT.
Para otros SO al parecer existen conversores pero no parecen funcionar.
En fin, si alguien sabe de alguna solución para este problema estaría agradecido.
Saludos.

---

### Post by faktorqm on 2008-10-17
Programa asi como de programa no encontre nada.... SoundConverter vi por ahi pero no soporta ese formato, no se si lo soporta gstreamer.
Otra cosa que podes hacer es fijarte con el VLC (pero no tiene conversor me parece...)
Otra que se me ocurrio son los repos de medibuntu, el paquete w32 codecs y compañia (desde ya t aviso q no son libres...) podes ver eso tambien. Salu2!

---

### Post by guisheca on 2008-10-17
No hay caso che, que formato de ****** lo que voy a hacer es tratar de grabar la grabación (valga la redundancia) con audacity y ahí si guardarlo en un formato decente.
Saludos y gracias por comentar al menos ya que estaba quedando solito mi post jejeje.

---

### Post by juanman on 2008-10-18
ACT es un formato propietario, poco usado... Creo q no hay ningun reproductor nativo para Linux ni un conversor libre...
Pero podes probar con el Sound Convert Tool [http://www.geocities.com/sound_converter/]("http://www.geocities.com/sound_converter/"), es un freeware para win q trae un conversor a wav. Dentro del zip q te bajas desde esa pagina, viene el Apx_dec.exe, q parece funcionar con wine. No encontre los ACT q tenia, asi q no lo pude probar, pero deberia funcionar asi (estando ubicado en el directorio donde descomprimiste el zip):
```
wine Apx_dec.exe archivo.act archivo.wav
```
Con eso, se deberia convertir el archivo ACT a wav, q es mas manejable...

Probalo y conta como te fue...
Saludos

---

### Post by guisheca on 2008-10-20
Perdón que me colgué con la entrada esta. Al final no pasó nada con el comando que me pasaste juanman, al hacerlo me genera un archivo .wav vacío, es decir, de 0 bytes. Intenté hacerlo en win (desde simbolo de sistema) y tampoco pasó nada.
En todas las ocaciones puse los .act en la misma carpeta donde está el conversor.
Muchas gracias de todas formas.
Saludos!!

---

### Post by acdm86 on 2008-10-21
Probaste en [http://media-convert.com/conversion/?](http://media-convert.com/conversion/?)

---

### Post by sebastianabate on 2008-10-21
Una vez (y sólo una vez, con un solo archivo) convertí uno de estos malditos bastardos con el VLC.
Lo que hice fue configurar el VLC para que la salida sea a un archivo WAV

[IMG]http://imagebin.ca/img/wY6Go2.png[/IMG]

Andá probando con distintos formatos de salida (output format) y con los canales (seguro que es mono, o sea 1) y después abrís el archivo ACT y le das play.

El tema es que tarda en convertirlo lo que dure la grabación, porque genera el wav a medida que reproduce el archivo (en mi caso era una conferencia que había grabado una amiga que duraba como 45 minutos). Vos no escuchás nada mientras lo genera.

NOTA: Al principio escribí "y sólo una vez, con un solo archivo" porque cuando lo traté de hacer nuevamente con otro archivo ACT generado con otro reproductor MP3 no funcionó (el vlc no lo reconocía como archivo multimedia). Por lo que YMMV.
[IMG]http://imagebin.ca/view/wY6Go2.html[/IMG]

---

### Post by guisheca on 2008-10-21
> **acdm86 said:**
> Probaste en [http://media-convert.com/conversion/?](http://media-convert.com/conversion/?)
No soporta act che :(

sebastianabate: hasta ahora no pude lograr nada pero voy a intentar hasta agotar las posibilidades.

Gracias a todos.
Saludos.

---

