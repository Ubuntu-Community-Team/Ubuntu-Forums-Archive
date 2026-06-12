---
title: "El sonido se entrecorta en Rhythmbox"
date: 2010-07-03
forum: Software
---

### Post by pinguinosaurio on 2010-07-03
Es dificil describir con palabras, sucede generalmente cuando hay una aplicación usando Internet (Firefox, Synpatic, Transmissión, etc.), pasa que cuando estoy escuchando un MP3 con normalidad de pronto el sonido se interrumpe un momento muy breve y luego continúa...

Este sería mi hardware:

lspci

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

En cuanto a la distribución, uso Ubuntu Lucid versión i386, algo que puedo agregar es que en Fedora Goddard esto no sucede :confused:
En el fichero /var/log/messages aparecen las siguientes lineas
Jul  3 16:37:06 infragilis-laptop pulseaudio[1179]: ratelimit.c: 468 events suppressed
Jul  3 16:37:57 infragilis-laptop pulseaudio[1179]: ratelimit.c: 105 events suppressed
Jul  3 16:38:52 infragilis-laptop pulseaudio[1179]: ratelimit.c: 105 events suppressed
Jul  3 16:40:04 infragilis-laptop pulseaudio[1179]: ratelimit.c: 670 events suppressed
Jul  3 16:41:03 infragilis-laptop pulseaudio[1179]: ratelimit.c: 467 events suppressed
Jul  3 16:48:24 infragilis-laptop pulseaudio[1179]: ratelimit.c: 187 events suppressed
Jul  3 16:49:13 infragilis-laptop pulseaudio[1179]: ratelimit.c: 190 events suppressed
Jul  3 16:51:07 infragilis-laptop pulseaudio[1179]: ratelimit.c: 646 events suppressed
Jul  3 16:58:15 infragilis-laptop pulseaudio[1179]: ratelimit.c: 479 events suppressed
Jul  3 16:59:08 infragilis-laptop pulseaudio[1179]: ratelimit.c: 1 events suppressed
Jul  3 17:04:58 infragilis-laptop pulseaudio[1179]: ratelimit.c: 1363 events suppressed
Jul  3 17:32:54 infragilis-laptop pulseaudio[1179]: ratelimit.c: 788 events suppressed
Jul  3 17:56:31 infragilis-laptop pulseaudio[1179]: ratelimit.c: 379 events suppressed

Talvéz tengan que ver con el problema, espero que me puedan ayudar, ya que el problema se arrastra desde varias versiones de esta distribución...

Gracias de antemano, saludos a la comunidad chilena de este foro

---

### Post by Fisaulerod on 2010-07-04
A mi me pasa lo mismo, y no sólo en Ubuntu, también en suse. Recuerdo que sólo hasta intrepid funcionó bien. 
Yo he podido reducir este problema bajándole el swappinness, pero el problema persiste. Quizás esté también relacionado con el mal rendimiento del video, que también, por lo menos a mí, se entrecorta, y creo no tener un mal computador.
Igual podrías usar por mientras otro reproductor como qmmp, audacious o decibel-audio-player.
Saludos.

---

