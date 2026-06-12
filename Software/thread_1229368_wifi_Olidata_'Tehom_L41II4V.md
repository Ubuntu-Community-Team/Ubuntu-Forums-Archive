---
title: "wifi Olidata 'Tehom L41II4V"
date: 2009-08-02
forum: Software
---

### Post by nicolasis on 2009-08-02
:(
Hola a todos.
Necesito ayuda, ya no ody mas. e buscado en muchos foros y no encuentro una linea de solución para mi problema.
Tengo un laptop Olidata 'Tehom L41II4V' y estoy chato porque no encuentro solución para la red alambrica e inalambrica.
E intentado instalar el ndiswrapper pero no encuentra el paquete de este al final de la instalacion para poder instalar los drivers que sirven para windos.
No se si es problema de driver o de configuracion mistica de Ubuntu.
De verdad quiero dar el gran paso de cambiarme a Ubuntu, pero este es un gran 'pero' en el camino. no cacho como arreglar este inconveniente.
si alguien puede aydarme, se lo agradeceré.
 
tengo los siguientes datos pero no los publicare por el momento si es que no me los piden:
iwconfig
ifconfig
lspci
lsusb
 
 
 
gracias de todas maneras.

---

### Post by nicolasis on 2009-08-04
Hola... nadie sabe algo respecto al tema?
saludos

---

### Post by maxmoraga on 2009-08-04
Primero que nada trata de usar un mejor titulo para el thread ya que "Ayuda porfa, de verdad" es ambiguo y va en contra de las reglas de cualquier foro o almenos de la mayoria.

Respecto a tu problema podrías publicar el lspci para que vamos viendo que chip tienes.

Saludos. :D

---

### Post by nicolasis on 2009-08-04
[EMAIL="root@afis-laptop"]root@afis-laptop[/EMAIL]:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
06:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
06:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[EMAIL="root@afis-laptop"]root@afis-laptop[/EMAIL]:~#

---

### Post by nicolasis on 2009-08-04
gracias por responder. :P

---

### Post by nopersona on 2009-08-04
Mira, he tenido casi el mismo problema de wifi con el note de mi polola, que también es olidata (no recuerdo el modelo) no estoy en la casa ahora, cuando llegue veré si te puedo dar una mano.

---

### Post by Carlos C on 2009-08-05
Edité el título, ya que efectivamente iba contra las normas del foro. Te sugiero las leas antes de volver a postear:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Saludos.

---

