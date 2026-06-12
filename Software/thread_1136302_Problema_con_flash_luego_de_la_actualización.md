---
title: "Problema con flash luego de la actualización"
date: 2009-04-24
forum: Software
---

### Post by josecuervo86 on 2009-04-24
Hola a todos!

Despues de actualizar a JJ empecé a tener problemas con el plugin de flash, no se si sera un bug, pero la cosa es que los videos de paginas como Youtube no se reproducen, y si se llegan a reproducir el boton del sonido no anda por ejemplo. Otra cosa es que aparece siempre un simbolito de play sobre un fondo gris.

Alguien tiene alguna idea de como solucionarlo?? probe cambiando las librerias de flash para firefox pero sigue con el error

---

### Post by pablo.s on 2009-04-24
Fijate que hay una actualización
de Flash que salió hoy mismo.
Eso me lo hacia a mi cuando
todavia estaba en Alpha, pero
ahora anda perfecto.

---

### Post by josecuervo86 on 2009-04-25
Baje el paquete de flashplugin-nonfree y se me soluciono.  Igual ayer a la noche seguia andando mal, pero hoy cuando la prendio agarro de lo mas bien.

---

### Post by Apipote on 2009-04-25
La actualización que mencionan, es flash de 64 bits y está en los repositorios??

Gracias

---

### Post by josecuervo86 on 2009-04-25
Te comento, el flash se me volvia a "romper", asique me baje un paquete que se llama **flashplugin-installer** de aca [0]. Yo tengo 64bits, asique baje la de 64 y hasta ahora anda bien. Veremos mañana. 

[0][http://packages.ubuntu.com/jaunty/flashplugin-installer]("http://packages.ubuntu.com/jaunty/flashplugin-installer")

---

### Post by Apipote on 2009-04-25
A ver che. 
Yo la baje de adobe, cree una carpeta "plugins", en mozilla, y anda perfecto.

Lo tuyo no es con el ndiswrapper?

---

### Post by josecuervo86 on 2009-04-25
Sabes lo que pasa? que de la pagina de Adobe te da la opcion para 32 bits, asique obligatoriamente tengo que elegir un camino alternativo :s

---

### Post by Apipote on 2009-04-25
No. Esta la también la de 64 y a mi me anda muy bien.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Slds

---

### Post by josecuervo86 on 2009-04-25
> **Apipote said:**
> No. Esta la también la de 64 y a mi me anda muy bien.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Slds

Muchas gracias Api.. nunca habia visto esa pagina! ;)

---

### Post by tinoq3 on 2009-04-27
Gente, serían tan amables de listar los pluggins y códecs necesarios para visualizar sin problemas la mayoría de las webs y videos?

Instalé la versión 10 de flash para ubuntu 64 bits, y si bien puedo ver youtube, la primer imagen que veo es el cuadrado gris con un símbolo de "play" como si no lo tuviese instalado... espero se entienda. Muchas gracias.

---

### Post by staar on 2009-04-27
> cuadrado gris con un símbolo de "play"

eso no es el flash blocker? la extensión de firefox?...

saludos

---

### Post by tinoq3 on 2009-04-27
> **staar said:**
> eso no es el flash blocker? la extensión de firefox?...

saludos

No te sabría decir, en ese caso faltaría algun pluggin de firefox?

---

### Post by josecuervo86 on 2009-04-27
Mas bien, sobraría ;)

---

### Post by staar on 2009-04-28
> **tinoq3 said:**
> No te sabría decir, en ese caso faltaría algun pluggin de firefox?

fijate, creo (uso opera, asi que puede que le erre con los nombres), en Herramientas -> Agregados (o extensiones, no recuerdo) si tenes activado uno que se llama flash blocker o similar, si es así desactivalo...

saludos

---

### Post by tinoq3 on 2009-04-28
> **staar said:**
> fijate, creo (uso opera, asi que puede que le erre con los nombres), en Herramientas -> Agregados (o extensiones, no recuerdo) si tenes activado uno que se llama flash blocker o similar, si es así desactivalo...

saludos

Ok, gracias. mas tarde en casa lo pruebo.
Por lo que recuerdo la 1ra vez que abrí el firefox luego de instalar JJ me pidió agregar unos pluggins (incluido uno de flash). Pense que con eso iba a ser sufieciente...

---

### Post by guidito73 on 2009-04-29
Tuve un problema parecido después de hacer unas actualizaciones desde backports. Lo solucioné borrando flashplugins-nonfree desde synaptic y después instalando desde la página de adobe con un .deb que hay por ahí. (Dejaron el link en un comentario anterior si no me equivoco)

---

### Post by tinoq3 on 2009-04-29
Ya pude solucionarlo, muchas gracias.
Es como decían, tenía instalada la versión 9 y 10. Deshabilité la 9 y funciona perfecto ahora.

Habrá una forma prolija de eliminar ese plugin?

---

### Post by hictio on 2009-04-29
> **tinoq3 said:**
> Gente, serían tan amables de listar los pluggins y códecs necesarios para visualizar sin problemas la mayoría de las webs y videos?

Instalé la versión 10 de flash para ubuntu 64 bits, y si bien puedo ver youtube, la primer imagen que veo es el cuadrado gris con un símbolo de "play" como si no lo tuviese instalado... espero se entienda. Muchas gracias.

Yo también tengo Ubuntu de 64 bits, instalé este meta paquete 'ubuntu-restricted-extras'.
Para videos, te recomiendo que instales vlc, y para ver DVDs, tenés que instalar 'libdvdcss2'.
Instrucciones para los codecs de video, en esta página [Install Mplayer and Multimedia Codecs (libdvdcss2,w32codecs,w64codecs) in Ubuntu 9.04 (Jaunty)](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-904-jaunty.html)

---

### Post by Applelnx on 2009-06-11
Tengo un problema similar. No tengo sonido para los videos de Youtube en Kubuntu. Instale ubuntu-restricted-extras y ahora no tengo sonido en todo el sistema :S

puse **sudo lspci** y salio lo siguiente

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI ExpressFast Ethernet controller (rev 02)
```

En preferencias de multimedia me aparecen 3 dispositivos:
HDA ATI SB 
HDA ATI HDMI
PulseAudio

Cuando pongo prueba, en todos se escucha como una lluvia leve :S
No se por donde encarar, porque al parecer tratando de arreglar una cosa lo empeore :(

EDIT: el problema es mas complejo. Desinatale los drivers de ATI (que me congelaban el video) y ahora tengo sonidos del sistema pero solo de algunos programas (amarok, dragon player), el vlc por ejemplo no.

---

### Post by Applelnx on 2009-06-12
Reformulo mejor los sintomas del problema:

- No funciona el audio de ciertas aplicaciones (vlc, firefox, etc)
- Funciona solo para otras (sonido de arranque, amarok, dragon)
- Cuando estoy tratando de ver un video en youtube y por alguna razon se cuelga el Firefox (supongo que por el flash), se arruina el sonido de todo el sistema.

---

### Post by pablo.s on 2009-06-12
Podés probar con deshabilitar
PulseAudio

---

### Post by Applelnx on 2009-06-12
Perdon si es muy basico, pero como lo deshabilito? Mis busquedas en Google fueron infructuosas :s

---

### Post by pablo.s on 2009-06-12
En el menú Sistema ->
Preferencias -> Sonido.

Música y Peliculas:
elegí ALSA

Eventos de Sonido:
elegí ALSA

AudioConferencia:
elegí ALSA

---

### Post by Applelnx on 2009-06-12
No tengo el alsa :s

Estoy en kubuntu y me cambio bastante:

[ATTACH]117417[/ATTACH]

---

### Post by pablo.s on 2009-06-12
Le paso la posta a
quien pueda ayudarte.
KDE no es lo mio.
Saludos.

---

### Post by Applelnx on 2009-06-12
Muchas gracias igual Pablo ;)

---

### Post by Hei Ku on 2009-06-12
Te fijaste en KMix que tengas todo al maximo?

Que pasa si arrancas en Amarok? Te tira un error diciendo que no encuentra salida de sonido o no dice nada y solo no anda?

---

### Post by Applelnx on 2009-06-12
:oops::oops::oops::oops::oops:

El PCM estaba a minimo nivel. Y el HDA ATI HDMI estaba silenciado... ups :(
(aclaro que nunca lo cambie, como para no quedar tan mal :s)

Gracias Hei Ku ;)

---

