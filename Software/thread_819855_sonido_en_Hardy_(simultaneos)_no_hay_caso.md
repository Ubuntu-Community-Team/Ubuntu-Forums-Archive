---
title: "sonido en Hardy (simultaneos) no hay caso"
date: 2008-06-05
forum: Software
---

### Post by atari130xe on 2008-06-05
Hace un tiempo posteé que tenia problemas con el audio (escuchar varias fuentes a la vez, ej. amarok, emesen, etc.), tenía habilitado el chip onboard del mother pero como era via USB lo saqué e instalé una placa PCI de las "comunes" (Genius Live 5.1 Value), funciona pero... me doy cuenta que sigue igual (poder escuchar varios sonidos a la vez), Googleé y la verdad que puse en práctica varias cosas de lo que encontré pero sigo con el mismo problema, alguien que haya pasado por lo mismo le encontró "la vuelta"? es raro pero tanto en la version 7.10 como en la 8.04 el mismo tema. Que extraño que eso no viene "pre-seteado" al instalarse y bueno si me dan una manito, agredecido como siempre :)

Probé con esto: [http://redavalon.blogspot.com/2007/03/multiples-sonidos-en-ubuntu.html]("http://redavalon.blogspot.com/2007/03/multiples-sonidos-en-ubuntu.html") y nada :confused:

un lspci:
```
desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)

```

---

### Post by pol666 on 2008-06-05
Me imagino que estas usando Pulceaudio no?

Anda a Sistema/Preferencias/Sonidos y ahi selecciona todo use PULCEAUDIO... lo que me da la impresion es que estas usando ALSA con ESD en vez de Pulceaudio y ahi es el problema

---

### Post by lushnok on 2008-06-05
tengo varios problemas de este estilo, aun no pude resolver nada... pruebo con esto del pulse..

---

### Post by pol666 on 2008-06-05
en Gutsy se solucionaba editando el esd.conf aca con Pulceaudio se arreglo eso, igual el sonido 5.1 de Soundblaster sigue con problemas asi que bue eso solo... Fijate haciendo lo que te dije, tambien fijate que todos ls volumenes esten altos

---

### Post by atari130xe on 2008-06-06
Al menos a mi, el cambiar a Pulseaudio todo no me dá resultados, sigo con el mismo problema, si escucho Amarok, no escucho el sonido de otra cosa.

---

### Post by vk-cdg on 2008-06-06
A mi me pasa lo mismo. Tengo seteado PulseAudio como servidor de sonido, pero en cuanto escucho algo a través del navegador (youtube o algún tema embebido en alguna web) se pianta el resto. Por ejemplo, el Exaile no reproduce, no solo no sale sonido, sino que le doy play a un tema, y no avanza. Lo avanzo mano y queda donde lo dejé!

---

### Post by atari130xe on 2008-06-06
Sigo igual, lo raro es que mi placa de audio es full compatible con Linux (hasta trae un cd con controladores, que por supuesto no utilicé porque la reconoció al toque y con sonido) pero el tema es la mezcla de sonido (múltiples sonidos) no su funcionamiento en sí. Sé que es un problema de bastante gente porque lo leo en foros y más foros, pero bueno no sé la solucion por el momento.

---

### Post by sartrejp on 2008-06-06
Yo tuve el mismo problema al instalar ubuntu y al actualizarlo, siempre lo solucioné poniendo "autodetectar" en todo lo de audio y en cada aplicación específica (generalmente en herramientas o editar y opciones) elegía ALSA, y no he vuelto a tener ese problema.
Intentalo
Suerte

---

### Post by santius on 2008-06-07
Hola como estás?
Bueno te cuento que yo el problema lo solucioné habilitando la mezcla por software desde la configuración de Audio.

Espero que te sirva de algo este dato,

Saludos.

---

### Post by atari130xe on 2008-06-10
Gracias pero esta está tildado desde la instalación misma en mi caso y nada, no funca. La verdad que es bastante frustrante no poder solucionar eso, que raro que no hay muchos con ese problema :(

---

### Post by mikestrato on 2008-06-12
Yo tenia el mismo problema, y googleando un poco encontre este foro espero te sirva

[http://biestado.kraptor.com/2008/05/27/solucionar-problemas-de-audio-en-hardy-heron](http://biestado.kraptor.com/2008/05/27/solucionar-problemas-de-audio-en-hardy-heron)

saludos!

---

