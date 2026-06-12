---
title: "problema de audio ubuntu 9.04 elitebook 6930"
date: 2009-08-11
forum: Software
---

### Post by krasef on 2009-08-11
hola instale por primera vez ubuntu 9.04 el dia de ayer instalo bien se ve genial y todo,esta bien rapido en todo conforme,pero el problema es que no tengo sonido es buscado por todos lados una solucion y llege a este foro ojala me puedan ayudar.Mi equipo es un elitebook 6930 y esta particionado en 2 SO una particion de 100 giga con window vista, y la otra con Ubuntu de 150 giga.

les dejo esto para que puedan sacar informacion:
diaf@diaf-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 0

navegando por internet he encontrado soluciones, se las he puesto todas @.@las que encontre y ninguna a funcionado.si nesesitan otra informacion me avisan.

---

### Post by josecuervo86 on 2009-08-12
Fijate poniendo esto en una terminal

```
alsamixer
```

Te va a abrir una consola, trata de fijarte si no hay nada en mute

---

### Post by CdK1 on 2009-08-12
sudo apt-get install alsa-base alsa-utils alsa-oss pulseaudio
sudo reboot

---

