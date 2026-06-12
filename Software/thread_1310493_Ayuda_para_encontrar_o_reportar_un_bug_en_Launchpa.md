---
title: "Ayuda para encontrar o reportar un bug en Launchpad.net"
date: 2009-11-01
forum: Software
---

### Post by DrKenobi on 2009-11-01
Hola. Encontre un bug pero no se que paquete es el que deberia reportar o buscar para sumarme a la lista de afectador por el bug. Despues de leer [https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs") sigo sin saber como hacer.

Como pueden ver en las capturas de pantalla, las **notificaciones** y el **System Monitor** no se pueden ver. Esto solo pasa si los **System-->Preferences-->Appearance-->Visual Effects** estan en **NONE**. Si esta selecionado **NORMAL** o **EXTRA** el problema no aparece.

Otra cosa que me pasa es que hay veces que no me deja cambiar los efectos. Restarteo y el problema se va. Pero esto lo vere en otro momento.

Gracias!

---

### Post by staar on 2009-11-01
ambas aplicaciones tienen soporte para transparencias (en el system monitor se activan cuando usas un tema gtk basado en murrine con soporte ARGB), que placa de video tenés y que drivers estás usando?

saludos

---

### Post by DrKenobi on 2009-11-01
Segun [World Wide QuickSpecs]("http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML") la placa q tiene mi laptop es *ATI Mobility Radeon 7500 Graphics Controller with 32 MB of DDR video RAM*

Como averiguo que driver estoy usando?

---

### Post by guillermolisi on 2009-11-01
> **DrKenobi said:**
> Segun [World Wide QuickSpecs]("http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML") la placa q tiene mi laptop es *ATI Mobility Radeon 7500 Graphics Controller with 32 MB of DDR video RAM*

Como averiguo que driver estoy usando?
Y segun la salida de "lspci" ?

---

### Post by DrKenobi on 2009-11-01
> **guillermolisi said:**
> Y segun la salida de "lspci" ?

Segun "lspci":

> joaquin@compaq:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:06.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
joaquin@compaq:~$

*Creo* que dice lo mismo.

---

### Post by guillermolisi on 2009-11-02
> **DrKenobi said:**
> Segun "lspci":



*Creo* que dice lo mismo.
Ok. Si, pero lo mas importante es como la reconoce Ubuntu mas alla del modelo que diga ser en la caja u otros avisos.

Y ahora viene la parte de los drivers ya que para algunas placas ATI van bien los libres y para otras van bien los privativos (cosa que aun no logre memorizar).

---

### Post by DrKenobi on 2009-11-02
> **guillermolisi said:**
> Ok. Si, pero lo mas importante es como la reconoce Ubuntu mas alla del modelo que diga ser en la caja u otros avisos.

Y ahora viene la parte de los drivers ya que para algunas placas ATI van bien los libres y para otras van bien los privativos (cosa que aun no logre memorizar).

Me fije en **System-->Administration-->Hardware Drivers** y no dice nada de drivers privativos (creo que este es lugar donde debia fijarme).

Esta es la primera vez que me aparece un error de este tipo. Yo creo que la placa siempre anduvo con los drivers libres (me anduvo todo bien con 8.10, 9.04 y no con 9.10).

---

### Post by staar on 2009-11-02
> **guillermolisi said:**
> Y ahora viene la parte de los drivers ya que para algunas placas ATI van bien los libres y para otras van bien los privativos (cosa que aun no logre memorizar).

para esta placa, van los drivers libres, ya que tiene sus años (las placas más viejas usan los drivers libres, las más nuevas, las HD 4xxx, los privativos, aunque se está avanzando mucho en los libres para estas últimas)

para reportar el bug, creo que te ganaron de mano :-P [https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/426582]("https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/426582") y [https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/416001]("https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/416001")

saludos

---

### Post by DrKenobi on 2009-11-02
> **staar said:**
> para esta placa, van los drivers libres, ya que tiene sus años (las placas más viejas usan los drivers libres, las más nuevas, las HD 4xxx, los privativos, aunque se está avanzando mucho en los libres para estas últimas)

para reportar el bug, creo que te ganaron de mano :-P [https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/426582]("https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/426582") y [https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/416001]("https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/416001")

saludos

Sip, me ganaron. Pero al menos me sumo a la lista de afectados por el bug.

Gracias por la ayuda!

---

