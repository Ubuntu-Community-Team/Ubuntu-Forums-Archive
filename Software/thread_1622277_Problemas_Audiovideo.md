---
title: "Problemas Audio/video"
date: 2010-11-15
forum: Software
---

### Post by mr_sangrin on 2010-11-15
Gente,
Tengo el Siguiente problema con todos los reproductores de ubuntu 10.10

Los Mp3's se escuchan entrecortados y el Videos Flash (youtube,etc) se visualisan y escuchan correctamente como 10 segundos luego de eso comienzan a verse entrecortados y el audio totalmente desincronizado de las imagenes..

Instale lo siguiente pero el problema persiste. Alguna Idea?

l.- sudo aptitude -y install non-free-codecs
2.- sudo apt-get install ubuntu-restricted-extras

---

### Post by RafaelG on 2010-11-18
Disculpa, que Computador es? y bueno si colocas tu lspci podriamos saber tambien cual es tu tarjeta de audio y video.

Saludos!

---

### Post by mr_sangrin on 2010-11-22
> **RafaelG said:**
> Disculpa, que Computador es? y bueno si colocas tu lspci podriamos saber tambien cual es tu tarjeta de audio y video.

Saludos!

El computador es un samsung r430.
Sigo con el problema la salida de lspci que obtengo es:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

---

### Post by mr_sangrin on 2010-11-24
Alo?

Alguien, que me heche una ayudadita, me tiene realmente chato, el no poder ver videos ni escuchar musica.. asi que sia alguien tiene alguna idea please!

---

