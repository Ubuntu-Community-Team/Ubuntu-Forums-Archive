---
title: "configurar pulseaudio para upnp/dlna streaming"
date: 2010-02-21
forum: Software
---

### Post by joselitux on 2010-02-21
Hola

He visto que el nuevo Karmic, si tenemos pulseaudio instalado, existen unas opciones que al activarlas podemos hacer que nuestro sonido se retransmita a toda la red local via upnp/dlna, como cuando tienes un Daap activado por ejemplo en el rhythmbox.

Seria la caña poner una pelicula en el portatil, y que el audio sonara por mis altavoces de la PS3 o del Pinnacle Soundbridge, por poner dos ejemplos de dispositivos que pueden acceder a servidores upnp/dlna.

El caso es que por mas que activo dichas opciones, no logro ver resultado alguno.

¿alguien ha podido configurar pulseaudio para que se pueda oir el sonido del pc en cualquier dispositivo externo?

Esta es mi configuracion:

**sound Preferences**

> output > DLNA/upnp Streaming (stereo)

**paprefs**

-Tab Network access
click "make discoverable Pulseaudio network sound devices available locally" y lo mismo para "[...] Apple Airtunes"
-tab Network server
todas las opciones activadas
- tab Multicast RTP
activado "receiver", activado "sender" y seleccionado "send audio from local speakers"
-Tab simultaneous output
sin activar

**padevchooser**

- Default server: joselitux-pc
- Default sink: DLNA/upnp Streaming
- Default source: internal analog Stereo

gracias por la ayuda

---

### Post by alfplayer on 2010-02-21
Tengo funcionando audio remoto entre dos Ubuntu 9.10 pero usando el protocolo de PulseAudio (no es DLNA/UPnP).

Configuración:

**En el servidor**: activo la primer opción en "Network Server" y sus dos subopciones.

**En el cliente**: activo la primer opción en "Network Access", y con padevchooser una vez que son detectados el servidor o el sink remoto los selecciono.

Para estar seguro que las configuraciones tengan efecto se puede reiniciar Ubuntu.

Además, deben estar bien configurados los niveles de volumen en Ubuntu. Esto se puede configurar con el comando alsamixer (hay que tener cuidado porque se pueden desconfigurar después de reiniciar Ubuntu).

---

### Post by joselitux on 2010-02-22
En cierta medida está relacionado con lo que pregunto. Ciertamente tu solucion no es para uPnp (una ps3 concretamente), pero aun así no entiendo lo que quieres decir.

---

### Post by alfplayer on 2010-02-22
> **joselitux said:**
> En cierta medida está relacionado con lo que pregunto. Ciertamente tu solucion no es para uPnp (una ps3 concretamente), pero aun así no entiendo lo que quieres decir.

No resuelve el problema, pero creo que puede ayudar.

---

### Post by llove on 2010-02-22
Hola, mediatomb tal vez te sirva por lo que veo, te paso link de unos howto y del mediatomb

[http://mediatomb.cc](http://mediatomb.cc)

[http://www.dekazeta.net/topic/69307-comparte-archivos-entre-ubuntu-y-playstation-3-con-mediatomb/](http://www.dekazeta.net/topic/69307-comparte-archivos-entre-ubuntu-y-playstation-3-con-mediatomb/)

[http://ubunturoot.wordpress.com/2008/08/04/ubuntu-como-servidor-multimedia-para-ps3-y-otros/](http://ubunturoot.wordpress.com/2008/08/04/ubuntu-como-servidor-multimedia-para-ps3-y-otros/)

espero que te sirva. 
Saludos

---

### Post by joselitux on 2010-02-23
Creo que no me he expresado bien.

No necesito un servidor multimedia. Ya tengo uno, se llama Firefly (mt-daapd), y funciona como mediatomb, es decir, que indexa la biblioteca de medios y los expone para su consumo por cualquier dispositivo compatible con upnp/dlna.

Pero eso no es lo que necesito.

Necesito que el sonido que sale por los altavoces se retransmita al mismo tiempo via upnp/daap, que es precisamente lo que permite pulseaudio según he visto en sus opciones de configuración. Pero hasta hora no he logrado configurarlo correctamente.

Lo que me estais diciendo está relacionado pero no tiene nada que ver.

---

