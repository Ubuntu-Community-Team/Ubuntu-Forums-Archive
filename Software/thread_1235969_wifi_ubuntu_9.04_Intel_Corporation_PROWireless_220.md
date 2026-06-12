---
title: "wifi ubuntu 9.04 Intel Corporation PRO/Wireless 2200BG"
date: 2009-08-09
forum: Software
---

### Post by Jaim on 2009-08-09
Hola, soy nuevo con Linux, y no se como hacer para poder conectarme a internet inalámbrico, el problema surgió así:

Instale el ubuntu en mi pc portátil, no tiene sonido a si que busque en google como agregar sonido y encontré que actualizando los Drivers Alsa el problema se soluciona, a si que descargue e instale los drivers, y entonces cuando reinicie la computadora vi que ya no se conectaba a internet, cuando entro a win si tengo red pero en ubuntu no, solo me puedo conectar por un cable de ethernet.

Alguien me podría ayudar a resolver el problema, por favor.

---

### Post by Carlos C on 2009-08-10
Hola. Tienes que decirnos qué versión de Ubuntu usas, es un detalle importante. Luego tenemos que saber qué modelo de tarjeta de red tienes. Me parece que lo importante es solucionar el problema del wifi en este thread y luego ver en un thread diferente tu problema de audio. Para saber qué modelo de tarjeta tienes debes escribir en el terminal:
```
lspci
```
y pegar acá lo que te muestre el sistema.
Saludos.

---

### Post by Jaim on 2009-08-10
La versión del ubuntu es 9.04, y lo que salio en la terminal:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
06:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:07.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

