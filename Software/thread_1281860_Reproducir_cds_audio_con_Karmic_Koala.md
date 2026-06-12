---
title: "Reproducir cds audio con Karmic Koala"
date: 2009-10-03
forum: Software
---

### Post by jbubu on 2009-10-03
Este es mi primer post y lamentablemente es para preguntar sobre un problema con karmic koala.
Por algún motivo, los reproductores de cds (probé con rhythmbox, banshee y exaile) no me reproducen los cds de música aunque los reconocen. AL parecer falta un plugin dado que exaile pone

"Se requiere un complemento Fuente de CD de sonido para reproducir este flujo, pero no está instalado."

Estuve buscando en el synaptic  pero no encontré nada. Lo raro es que vlc si reconoce los cds y los reproduce. ¿Alguien sabe que puede ser?.Desde ya muchas gracias

Bubu

---

### Post by gmunioz on 2009-10-04
Hola jbu.....:

Instala desde synaptic los gstreamer

GStreamer es un framework multimedia libre multiplataforma 
escrito en el Lenguaje de programación C, usando la biblioteca GObject.

GStreamer permite crear aplicaciones multimedia, como vídeo, sonido,
codificación, etc. Por ejemplo, con GStreamer se puede reproducir 
música o realizar tareas más complejas como mezclar audio y vídeo.

---

### Post by jbubu on 2009-10-04
Antes que nada, muchas gracias por tu respuesta.
Ya están instalados los gstreamer y nada...
No tengo idea que es :(

---

### Post by guillermolisi on 2009-10-04
> **jbubu said:**
> Antes que nada, muchas gracias por tu respuesta.
Ya están instalados los gstreamer y nada...
No tengo idea que es :(
Podrias ser mas especifico con el "nada" ?

Nada es ni siquiera un mensaje de error o advertencia.

---

### Post by jbubu on 2009-10-06
Si, disculpen. Me aparece un mensaje de error en el exaile diciendo

"Se requiere un complemento Fuente de CD de sonido para reproducir este flujo, pero no está instalado."

Los Gstreamer están instalados. Lo raro es que VLC y Mplayer si reproduce los cds de audio. El rhythmbox ponía "error en la tubería" o algo así, honestamente lo desinstalé para ver si era el programa pero no.

El exaile, ejecutado de la consola pone

INFO    : Playing cdda://1#/dev/sr0
ERROR   : <gst.Message GstMessageError, gerror=(GstGError)NULL, debug=(string)"gstplaybasebin.c\(1691\):\ gen_source_element\ \(\):\ /GstPlayBin:player:\012No\ URI\ handler\ for\ cdda"; from player at 0x39c3c80> ['__class__', '__cmp__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__grefcount__', '__gstminiobject_init__', '__gtype__', '__hash__', '__init__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'copy', 'flags', 'parse_async_start', 'parse_buffering', 'parse_buffering_stats', 'parse_clock_lost', 'parse_clock_provide', 'parse_duration', 'parse_error', 'parse_info', 'parse_new_clock', 'parse_request_state', 'parse_segment_done', 'parse_segment_start', 'parse_state_changed', 'parse_step_done', 'parse_step_start', 'parse_stream_status', 'parse_structure_change', 'parse_tag', 'parse_tag_full', 'parse_warning', 'set_buffering_stats', 'set_seqnum', 'src', 'structure', 'timestamp', 'type']
WARNING : No covers found


abriendo con vlc y con banshee no aparece nada. El banshee pone cruces al lado de las pistas, pero no dice nada en la terminal

Espero haber sido más claro, un saludo y gracias

---

### Post by jbubu on 2009-10-10
Más aún, me di cuenta que tampoco me deja reproducir archivos APE con el mismo error. Instalé el Rhythmbox para ver y el error que me da es

No URI handler implemented for "cdda".

Muchas gracias por todo

---

### Post by pablo.s on 2009-10-10
> **jbubu said:**
> Más aún, me di cuenta que tampoco me deja reproducir archivos APE con el mismo error. Instalé el Rhythmbox para ver y el error que me da es

APE es un codec propietario.
Por ende hay muy pocas
implementaciones para poder
reproducirlo. Una de ellas es
la de un plug-in para XMMS.
Para Rhythmbox no creo que
haya soporte, siendo que maneja
los plug-ins de GStreamer.

Si te interesan los formatos de
compresión sin perdida, te puedo
recomendar FLAC, que es libre
y no tiene ningún requisito para
ser reproducido en ningún programa.

---

