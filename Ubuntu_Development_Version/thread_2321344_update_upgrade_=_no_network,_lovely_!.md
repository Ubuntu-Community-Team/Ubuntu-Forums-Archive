---
title: "update /upgrade = no network, lovely !"
date: 2016-04-22
forum: Ubuntu Development Version
---

### Post by valereguerin on 2016-04-22
yesterday i :KSupdate/upgrade :KSmy system (16.04) and when i reboot my hardware doesn't works, no eth , marvellous !

recovery, boot another kernel, the same ! 
```

sudo ifdown -a
sudo ifup -a
```

always nothing....

i said today is a great day !

if i haven't another wifi key , :KSno network ....:KSor loose 2/3/6 hours for looking for the problem is...
```

freeman@Sniper-one:~$ inxi -b
System:    Host: Sniper-one Kernel: 4.4.0-6-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.4 Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2794 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.18.3 drivers: ati,vesa (unloaded: fbdev,radeon)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: D-Link System DGE-528T Gigabit Ethernet Adapter
           driver: r8169
           Card-2: Realtek RTL8187 Wireless Adapter driver: rtl8187
Drives:    HDD Total Size: 4871.0GB (14.8% used)
Info:      Processes: 346 Uptime: 1:47 Memory: 2607.0/7853.0MB
           Client: Shell (bash) inxi: 2.2.35 

```

this hardware tree day ago works fine, update/upgrade=hardware  is out ! FANTASTIC !
```
*-network
                description: Ethernet interface
                produit: DGE-528T Gigabit Ethernet Adapter
                fabriquant: D-Link System Inc
                identifiant matériel: 0
                information bus: pci@0000:08:00.0
                nom logique: enp8s0
                version: 10
                numéro de série: 6c:19:8f:99:82:bb
                taille: 10Mbit/s
                capacité: 1Gbit/s
                bits: 32 bits
                horloge: 66MHz
                fonctionnalités: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s

```
it said cable unplugged ! but my Toshiba-machine connect it ! and my cable is correctly plugged  !

My Kernel 4.5 rc  THE SAME !.....

---

### Post by ventrical on 2016-04-22
Same thing here with unity. However .. I checked my ethernet cable and it had slipped out of the socket because I did something to the mic jack :) . It is working now :0

Regards..

---

### Post by valereguerin on 2016-04-22
i had control that point ! twice and the "Ethernet-cable" with another computer works fine....

[http://hpics.li/9deee60](http://hpics.li/9deee60)

[[IMG]http://img15.hostingpics.net/pics/690082PBreseau1604.png[/IMG]](http://www.hostingpics.net/viewer.php?id=690082PBreseau1604.png)

---

### Post by ventrical on 2016-04-22
I sometime have to turn on the wifi manually. If I am using labtop der is sometimes switch that can be pressed to turn on wifi because update can reset network card.

regards..

---

### Post by ventrical on 2016-04-22
> **valereguerin said:**
> i had control that point ! twice and the "Ethernet-cable" with another computer works fine....

[http://hpics.li/9deee60](http://hpics.li/9deee60)

[[IMG]http://img15.hostingpics.net/pics/690082PBreseau1604.png[/IMG]]("http://www.hostingpics.net/viewer.php?id=690082PBreseau1604.png")

ahhh.. ok . sometimes I delete old connection and create new one and that usually helps.

---

### Post by valereguerin on 2016-04-22
i had tried that too, but i want to know :

[B][COLOR=#000000]why my card 1 woks fine tree days ago, and with no kernel change ; today won't work !

[/COLOR][/B][COLOR=#000000]i will boot on 14.04 and i see if my hadware card network 1, works....

```
freeman@Sniper-one:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13)
00:02.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 [8086:3409] (rev 13)
00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13)
00:10.0 PIC [0800]: Intel Corporation 7500/5520/5500/X58 Physical and Link Layer Registers Port 0 [8086:3425] (rev 13)
00:10.1 PIC [0800]: Intel Corporation 7500/5520/5500/X58 Routing and Protocol Layer Registers Port 0 [8086:3426] (rev 13)
00:11.0 PIC [0800]: Intel Corporation 7500/5520/5500 Physical and Link Layer Registers Port 1 [8086:3427] (rev 13)
00:11.1 PIC [0800]: Intel Corporation 7500/5520/5500 Routing & Protocol Layer Register Port 1 [8086:3428] (rev 13)
00:13.0 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller [8086:342d] (rev 13)
00:14.0 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13)
00:14.1 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13)
00:14.2 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13)
00:15.0 PIC [0800]: Intel Corporation 7500/5520/5500/X58 Trusted Execution Technology Registers [8086:342f] (rev 13)
00:1a.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1d.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
01:00.0 IDE interface [0101]: Marvell Technology Group Ltd. Device [1b4b:918a] (rev 10)
02:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] [1002:679a]
03:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series] [1002:aaa0]
05:00.0 Audio device [0403]: Creative Labs EMU20k2 [X-Fi Titanium Series] [1102:000b] (rev 03)
06:00.0 SATA controller [0106]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 03)
06:00.1 IDE interface [0101]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 03)
07:00.0 Power PC [0b20]: Freescale Semiconductor Inc MPC8308 [1957:c006] (rev 10)
08:00.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
3f:00.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers [8086:2c41] (rev 05)
3f:00.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder [8086:2c01] (rev 05)
3f:02.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QPI Link 0 [8086:2c10] (rev 05)
3f:02.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 [8086:2c11] (rev 05)
3f:03.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller [8086:2c18] (rev 05)
3f:03.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder [8086:2c19] (rev 05)
3f:03.4 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers [8086:2c1c] (rev 05)
3f:04.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers [8086:2c20] (rev 05)
3f:04.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers [8086:2c21] (rev 05)
3f:04.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers [8086:2c22] (rev 05)
3f:04.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2c23] (rev 05)
3f:05.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers [8086:2c28] (rev 05)
3f:05.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers [8086:2c29] (rev 05)
3f:05.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers [8086:2c2a] (rev 05)
3f:05.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2c2b] (rev 05)
3f:06.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers [8086:2c30] (rev 05)
3f:06.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers [8086:2c31] (rev 05)
3f:06.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers [8086:2c32] (rev 05)
3f:06.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers [8086:2c33] (rev 05)
freeman@Sniper-one:~$ sudo lshw -C network
[sudo] Mot de passe de freeman : 
  *-usb:2                 
       description: Interface réseau sans fil
       produit: USB2.0 WLAN Adapter
       fabriquant: Wireless Manufacturer
       identifiant matériel: 5
       information bus: usb@1:5
       nom logique: wlx00e04c84a720
       version: 2.00
       numéro de série: 00:e0:4c:84:a7:20
       fonctionnalités: usb-2.00 ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=4.5.0-040500rc7-generic firmware=N/A ip=192.168.0.28 link=yes maxpower=500mA multicast=yes speed=480Mbit/s wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       produit: DGE-528T Gigabit Ethernet Adapter
       fabriquant: D-Link System Inc
       identifiant matériel: 0
       information bus: pci@0000:08:00.0
       nom logique: enp8s0
       version: 10
       numéro de série: 6c:19:8f:99:82:bb
       taille: 10Mbit/s
       capacité: 1Gbit/s
       bits: 32 bits
       horloge: 66MHz
       fonctionnalités: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       ressources: irq:16 portE/S:ce00(taille=256) mémoire:fb9ff000-fb9ff0ff mémoire:fb900000-fb91ffff

```
[/COLOR]

---

### Post by Rustan on 2016-04-22
I think that the problem in network-manager 1.1.93-0ubuntu4 ... I have also problems after updating

---

### Post by valereguerin on 2016-04-27
i have two wifi usb network card works fine with my old ubuntusssssss, and this morning : 

no network ! yesterday yes but today no, it's not possible !

just one : free wifi, and i can't connect it, go into the machine, the hands in the...... ! 

great public OS ?........................................................;;;.;... not yet........

i fight with 14.04 LTS too,.... often ! just 12.04 works like a charm !

11.04 was perfect, since it s problems after problems, hoursssss the hand in the machine for it works correctly ! just correctly ! and  arrive updates,  fglrx problems grub problems usb problems ......

i spend my times with ubuntu !  i Have a Life !!!!! too !

Since two years, every update : usb problems, network problem ......for developpement version it's ok i choose it ;  

but LTS   NO !!!!! no !!!! NO !! AND NO  ! the first three month ok but not all the time pb pb pb pb pb pb pb pb pb  it's enough !


you 'll never a great public OS like that !

the recovery mode works when he want, how you want windows users choose to spend their time into a machine for use it !



if i haven't 3 computers and 6 OS and Live CD "7", i never choose UBUNTU ! TODAY ! because one update can dead your system and you loose one day(reinstall), again.....two times in one years and half  and i save it two times too with the recovery mode....UPDATE/upgrade ! not coool, 

if you change important things in the system put BE CARREFUL on the top of the update ! new KERNEL NEW XORG NEW GRUB NEW WAYLAND/MIR . i think it's a minimum to do for a great public OS ....!

---

