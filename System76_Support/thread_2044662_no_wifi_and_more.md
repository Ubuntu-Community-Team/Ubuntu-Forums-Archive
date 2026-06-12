---
title: "no wifi and more"
date: 2012-08-19
forum: System76 Support
---

### Post by porlaizquierda on 2012-08-19
i had posted this perviously

[http://ubuntuforums.org/showthread.php?t=2044118](http://ubuntuforums.org/showthread.php?t=2044118)

i managed to get my computer to start, but every time it boots it gives me a choice of which mode to go in. how to i get rid of that.

also, there is no wifi. in the past all i had to do was get a wired connection, install updated system76 drivers and reboot. this time it is not working. when i try to install the drivers from terminal, i get this:


degobrah@system76-netbook:~$ sudo system76-driver
[sudo] password for degobrah: 
NOTE: 11.10 or later detected! Running GTK3 version.
NOTE: 11.10 or later detected! Running GTK3 version.
Traceback (most recent call last):
  File "/usr/bin/system76-driver", line 96, in <module>
    main()
  File "/usr/bin/system76-driver", line 77, in main
    os.environ['GDMSESSION'] == 'default'
  File "/usr/lib/python2.7/UserDict.py", line 23, in __getitem__
    raise KeyError(key)
KeyError: 'GDMSESSION'
degobrah@system76-netbook:~$ sudo system76-driver
NOTE: 11.10 or later detected! Running GTK3 version.
NOTE: 11.10 or later detected! Running GTK3 version.
Traceback (most recent call last):
  File "/usr/bin/system76-driver", line 96, in <module>
    main()
  File "/usr/bin/system76-driver", line 77, in main
    os.environ['GDMSESSION'] == 'default'
  File "/usr/lib/python2.7/UserDict.py", line 23, in __getitem__
    raise KeyError(key)
KeyError: 'GDMSESSION'


what is that? also, every time i hit restart on my computer the screen just goes black. i have to manually restart my computer. don't know what is going on. really starting to regret upgrading to 12.04.

Please. Any help!!

---

### Post by porlaizquierda on 2012-08-19
everything is going better, except that i still have no wifi. how do i get wifi back??

---

### Post by Bucky Ball on 2012-08-19
You did an upgrade from 10.04 or 11.10? They can be problematic and I personally avoid. Clean install for me. Could you supply the result of this from a terminal:

sudo lshw -C network

---

### Post by porlaizquierda on 2012-08-20
i did an install from 10.04. things are working fine now except for the wifi. here is what i got from terminal


  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:01:46:78
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.137 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:1000(size=256) memory:91010000-91010fff memory:91000000-9100ffff memory:91020000-9102ffff

---

### Post by Bucky Ball on 2012-08-20
Okay. Your wireless card is not showing up at all there. Try this:

```
lspci
```

... and post the result of that (down the bottom of the output you *should* see 'Network Controller' entry).

Have you done an update then checked 'Additional Drivers'? Anything disabled in there for wireless?

---

### Post by porlaizquierda on 2012-08-21
this is what i got:


degobrah@system76-netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by porlaizquierda on 2012-08-21
as for additional drivers, nothing is showing up

---

### Post by Carborundum on 2012-08-21
> **porlaizquierda said:**
> this is what i got:


degobrah@system76-netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
No wireless controller here either. Could you boot into a live session of 12.04 to see if the wireless works there?

---

### Post by porlaizquierda on 2012-08-21
and wifi works just fine with a live cd. i don't get it

---

### Post by porlaizquierda on 2012-08-21
we must have sent at the same time. yeah. wireless is fine on live cd

---

### Post by porlaizquierda on 2012-08-21
here is what i got from terminal in live cd:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by Carborundum on 2012-08-21
> **porlaizquierda said:**
> here is what i got from terminal in live cd:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
That's somewhat worrying. Which model Starling is this? Only the Star1 is listed as requiring extra drivers in12.04 on [knowledge76]("http://knowledge76.com/index.php/Category:Starling"), so if it's a later model this might indicate a broken wireless card. If it is the Star1, I would do a fresh install, followed by installing the System76 driver, just to be sure.

---

### Post by porlaizquierda on 2012-08-21
yep. a star1. is this the only possible solution? i really hate to have to do a clean install.

---

### Post by Carborundum on 2012-08-21
I just re-read your OP in this thread; am I understanding correctly that you can't get the System76 driver to start? If so, fixing that would hopefully solve the problem. Any particular reason you're using sudo rather than gksu? What happens if you try to run gksu system76-driver instead?

---

### Post by porlaizquierda on 2012-08-21
i get this:


degobrah@system76-netbook:~$ gksu system76-driver 
NOTE: 11.10 or later detected! Running GTK3 version.
NOTE: 11.10 or later detected! Running GTK3 version.
    main()
  File "/usr/bin/system76-driver", line 77, in main
    os.environ['GDMSESSION'] == 'default'
  File "/usr/lib/python2.7/UserDict.py", line 23, in __getitem__
    raise KeyError(key)
KeyError: 'GDMSESSION'

then it says that something is wrong and asks if i want to send an error report

---

### Post by Bucky Ball on 2012-08-21
Yea, weird, because the wireless card is not showing up in the LiveCD lspci, either, when it is apparently working.

---

### Post by Carborundum on 2012-08-22
> **porlaizquierda said:**
> i get this:


degobrah@system76-netbook:~$ gksu system76-driver 
NOTE: 11.10 or later detected! Running GTK3 version.
NOTE: 11.10 or later detected! Running GTK3 version.
    main()
  File "/usr/bin/system76-driver", line 77, in main
    os.environ['GDMSESSION'] == 'default'
  File "/usr/lib/python2.7/UserDict.py", line 23, in __getitem__
    raise KeyError(key)
KeyError: 'GDMSESSION'

then it says that something is wrong and asks if i want to send an error report
Not the most verbose error, but it seems to be confused about GDM, which was the display manager in 10.04 but has been replaced by LightDM in 12.04. Try running```
sudo dpkg-reconfigure lightdm
```and choose lightdm in the subsequent dialogue, then try again.

---

### Post by racingsnake on 2012-10-31
Hi - in case this might help: 

I have a Starling 1, and yesterday upgraded to LTS 12.04 (upgrade, not a complete reinstall). Wired connectivity came up fine (as auto eth0), but there was no sign of a wireless connection at all.

I remembered to download and run the latest System76 driver (3.2.1), but that also had no effect. The hardware 3g/wifi switch and Fn-F2 similarly had no effect.

After a lot of frustrating searching I finally found a post describing similar symptoms with LTS 12.04; this attributed the problem to a missing wireless module, rtl8187.

I made the change recommended in that post, and wireless function was restored. Here's a link to the post in question - I hope this helps!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/951613](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/951613)

PS - I really wish that one day I could upgrade Ubuntu releases, run the System76 driver and just have wireless work... <sigh>

---

### Post by Bucky Ball on 2012-10-31
[B][I]Thread Closed

Reason:[/I][/B] Died of old age ...

---

