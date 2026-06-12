---
title: "Problema placa de red nforce 680i - Router Encore"
date: 2009-12-18
forum: Software
---

### Post by condes on 2009-12-18
[SIZE=3][FONT=Calibri]Soy principiante en Ubuntu. Tengo una placa de red Nforce 680i que se encuentra conectada a un router Encore. Sin embargo no puedo conectarme al router y en consecuencia, a internet. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Si utilizo una conexión automática, me dice que el cable de red está desconectado. Si lo hago manual, me indica que se logró conexión, pero no pasa nada. O sea, internet no anda. Tampoco puedo conectarme al 191.168.1.1[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Para aclarar, la placa de red, tiene dos salidas de red. Lo que complica más las cosas. Y al final no sé si es un problema de configuración o de Hardware. Ya probé el ifconfig. Y parecería que detecta las placas. Pero tengo mis dudas. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Si alguien tiene alguna idea estaría agradecida. [/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Saludos [/FONT][/SIZE]

---

### Post by Carlos C on 2009-12-20
Parece que esa placa tiene problemas con versiones de BIOS antiguas. ¿Puedes decirnos que versión de BIOS tienes?

---

### Post by condes on 2009-12-20
Sí. Tipo de BIOS: Phoenix Award (02/07/07)
 
Creo que el ID es: 02/07/2007-C55XEMCP55PXE-StrikerE-00
 
 
Sitio Web:
 
[http://www.phoenix.com/en/OEM-ODM/products/default.htm](http://www.phoenix.com/en/OEM-ODM/products/default.htm)
 
SALUDOS

---

### Post by Carlos C on 2009-12-20
Lo que necesitas saber es la versión de tu BIOS, al parecer existe un bug en las versiones inferiores a la P23. Verifica entrando al BIOS cuando prendas el computador. Si la versión es muy antigua descarga una para tu modelo exacto, porque la verdad es que no estoy seguro que este sea tu modelo exacto:

[https://www.evga.com/forums/tm.aspx?m=204](https://www.evga.com/forums/tm.aspx?m=204)

Saludos.

---

### Post by condes on 2009-12-20
Model: StrikerE
Version: ASUS StrikerExtreme ACPI BIOS Revision 0901
Chipset: C55XEMCP55PXE
Date: 02/07/07
BIOS Type Award
 
Esto es todo lo que puedo sacar del manual.
 
Saludos

---

### Post by condes on 2009-12-20
Los datos que aparecen en el Bios de nvidia son:
 
P413
G86
Version: 60.86.4a.00.00
 
SALUDOS

---

### Post by Carlos C on 2009-12-21
¿Tu versión de Ubuntu cuál es?
Veamos qué te muestra el comando:
```
ifconfig
```
También:
```
ip -s route| grep default
```
también:
```
lspci
```
y por último dinos qué contiene tu archivo "/etc/network/interfaces". Cuando te conectas de manera manual ¿cómo lo haces?

---

### Post by condes on 2009-12-21
**Un ifconfig da lo siguiente:**
 
 
 
javier@javier-desktop:~$ ifconfig
 
eth0 
Link encap:Ethernet direcciÃ³nHW 00:1a:92:c2:87:d2 
direcciÃ³n inet6: fe80::21a:92ff:fec2:87d2/64 Alcance:VÃnculo
ARRIBA DIFUSIÃ"N CORRIENDO MULTICAST MTU:1500 MÃ©trica:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:3606 (3.6 KB)
InterrupciÃ³n:245 DirecciÃ³n base: 0x8000 
 
 
eth1
Link encap:Ethernet direcciÃ³nHW 00:1a:92:c2:90:ce 
ARRIBA DIFUSIÃ"N MULTICAST MTU:1500 MÃ©trica:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
InterrupciÃ³n:246 DirecciÃ³n base: 0xe000 
 
lo
 Link encap:Bucle local 
inet direcciÃ³n:127.0.0.1 MÃ¡scara:255.0.0.0
direcciÃ³n inet6: ::1/128 Alcance:AnfitriÃ³n
ARRIBA LOOPBACK CORRIENDO MTU:16436 MÃ©trica:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
 
 
**O sea que la placa está siendo detectada. **
**Pero cuando ponemos ifconfig 127.0.0.1 da:**
 
javier@javier-desktop:~$ ifcong 127.0.0.1
bash: ifcong: orden no encontrada
[EMAIL="javier@javier-desktop:~$"]javier@javier-desktop:~$[/EMAIL] 
 
**Lo que significa que la placa no está emitiendo señal. **

---

### Post by condes on 2009-12-21
**Un lspci da:**
 
 
 
 
javier@javier-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
08:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
 
 
**El otro comando que me pusiste no lo conocía. Lo escribí pero no hizo nada.**

---

### Post by moreback on 2009-12-21
¿Revisaste que el cable estuviera bueno?

Veo que tienes conectada una sola interfaz, la eth0, la eth1 aparece desconectada. ¿Y si te conectas en la otra boca?

¿Tienes las dos placas configuradas en Network-Manager (icono en el área de notificación)?

¿Tienes configurado DHCP en tu router para que te asigne direcciones IP automáticamente?

Por favor aclárame estas dudas.

Saludos.

PD: 127.0.0.1 es una dirección local, no está relacionada con la tarjeta de red.

---

### Post by Carlos C on 2009-12-21
Prueba lo siguiente, en el terminal escribes:
```
sudo gedit /etc/modprobe.d/options
```
Cuando se abra el archivo agregas la siguiente linea:
```
options forcedeth msi=0 msix=0
```
Luego guardas los cambios y cierras el archivo. A continuación escribe:
```
update-initramfs -u
```
y reinicias. Si no se soluciona el problema es cosa de borrar la linea que escribiste en tu archivo "options" y volver a ejecutar el último comando.

Saludos.

---

### Post by condes on 2009-12-22
> **moreback said:**
> ¿Revisaste que el cable estuviera bueno?
 
Veo que tienes conectada una sola interfaz, la eth0, la eth1 aparece desconectada. ¿Y si te conectas en la otra boca?
 
¿Tienes las dos placas configuradas en Network-Manager (icono en el área de notificación)?
 
¿Tienes configurado DHCP en tu router para que te asigne direcciones IP automáticamente?
 
Por favor aclárame estas dudas.
 
Saludos.
 
PD: 127.0.0.1 es una dirección local, no está relacionada con la tarjeta de red.
 
 
El cable de red es imposible que esté desconectado. Porque en otra partición tengo instalado windows y no hay problema.
 
Eth0 y eht1 ya las probe mil veces. No pasa nada. El Eh1 lo detecta también cuando lo instalo. Pasa que lo borré. 
 
El router ya lo probé en otra compu y anda lo mas bien. Ubuntu lo detecta. 
 
No entendí lo de Network Manager
 
También probé conectarlo manualmente de mil maneras. Pero no anda tampoco. O sea, es claro que no detecta la placa de red. O que la detecta mal. O que algo hace con la placa de red que no está bien.

---

### Post by condes on 2009-12-22
> **Carlos C said:**
> Prueba lo siguiente, en el terminal escribes:
```
sudo gedit /etc/modprobe.d/options
```Cuando se abra el archivo agregas la siguiente linea:
```
options forcedeth msi=0 msix=0
```Luego guardas los cambios y cierras el archivo. A continuación escribe:
```
update-initramfs -u
```y reinicias. Si no se soluciona el problema es cosa de borrar la linea que escribiste en tu archivo "options" y volver a ejecutar el último comando.

Saludos.


Sos un genio. Puse el código y ahora funciona. Podes decirme que siginfica ese código?

SALUDOS Y LA VERDAD MUY AGRADECIDO

---

### Post by CdK1 on 2009-12-22
**O sea que la placa está siendo detectada. **
**Pero cuando ponemos ifconfig 127.0.0.1 da:**
 
javier@javier-desktop:~$ ifcong 127.0.0.1
bash: ifcong: orden no encontrada
javier@javier-desktop:~$ 
 
[B]Lo que significa que la placa no está emitiendo señal.

Yo lo veo claro...
[/B]

---

### Post by alex_mayorga on 2009-12-22
> **CdK1 said:**
> 
javier@javier-desktop:~$ ifcong 127.0.0.1


Debe ser ifconfig ¿no?

---

### Post by CdK1 on 2009-12-22
Claro...

---

### Post by Carlos C on 2009-12-22
> **condes said:**
> Sos un genio. Puse el código y ahora funciona. Podes decirme que siginfica ese código?

SALUDOS Y LA VERDAD MUY AGRADECIDO

Parece que es un bug conocido de las nVidia MCP55:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836)

Como vi que seguía dándose en Jaunty te sugerí que lo intentaras:

[http://ubuntuforums.org/showthread.php?p=7454665#post7454665](http://ubuntuforums.org/showthread.php?p=7454665#post7454665)


Saludos.

---

