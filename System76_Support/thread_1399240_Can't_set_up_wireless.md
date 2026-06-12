---
title: "Can't set up wireless"
date: 2010-02-05
forum: System76 Support
---

### Post by porlaizquierda on 2010-02-05
i use a system 76 starling netbook running 9.04. i did some security updates and it asked me to restart. when i did it wouldn't let me connect to wireless internet. the little light at the bottom that shows that wireless it connected doesn't even show up. it only asks me for VPN connections when i look at the wireless icon. what do i need to do?

---

### Post by Cabs21 on 2010-02-05
update your wireless drivers. SYSTEM>ADMINISTRATION>HARDWARE DRIVERS

you need to be connected to the internet for this to work so i suggest using a LAN cable to connect until the drivers are updated and then try connecting to wireless

also post the output of these codes once entered in terminal

```
ifconfig

iwconfig
```

---

### Post by porlaizquierda on 2010-02-05
when i get to hardware drivers it simply says:

No proprietary drivers are in use on this system.

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:26:9e:01:46:78  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:9eff:fe01:4678/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6585043 (6.5 MB)  TX bytes:1609481 (1.6 MB)
          Interrupt:253 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2272 (2.2 KB)  TX bytes:2272 (2.2 KB)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by Cabs21 on 2010-02-05
when you entered this into terminal did you have your computer connected to the internet?  It looks like you are connected but your wireless card is either turned off or not installed.  you will not find any drivers until you are connected to the internet.

---

### Post by porlaizquierda on 2010-02-05
i'm connected with ethernet. but the wireless is not working. it was working fine this morning until i did some sercurity updates with update manager.

---

### Post by Cabs21 on 2010-02-05
BUMP

That is very strange.  Sorry but this goes beyond my scoop.  If you can give more info then others might be able to help.

---

### Post by tlroche on 2010-02-05
Your problem may be due to System76 being down: see [this thread]("http://ubuntuforums.org/showthread.php?t=1399130") and replies.

---

### Post by porlaizquierda on 2010-02-05
that is really all the info i can give. i need someone to help.

---

### Post by thomasaaron on 2010-02-05
porlaizquierda,

Since you are running 9.04, I imagine that one of the updates you installed was a kernel update, and it broke the wireless.

Typically, you would just run the system76 driver and reboot to restore your wireless. However, at the moment it is not possible to run the System76 driver. 

The driver connects to our website to download the wireless driver, and our website it is down until probably Monday.

Please give me a call on Monday, and I'll help you get your wireless back up and running. I'm very sorry for the inconvenience.

---

### Post by porlaizquierda on 2010-02-05
is there any way i can revert back temporarily so i can use wireless?

---

### Post by Charlietje on 2010-02-05
can you post
```
ifconfig -a
```

with the -a option, it will show all available nics, up and down

also can you post 
```
lspci
```

---

### Post by porlaizquierda on 2010-02-05
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:9e:01:46:78  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:9eff:fe01:4678/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25683918 (25.6 MB)  TX bytes:6053546 (6.0 MB)
          Interrupt:253 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3156 (3.1 KB)  TX bytes:3156 (3.1 KB)

pan0      Link encap:Ethernet  HWaddr 66:77:37:e9:b3:8f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by porlaizquierda on 2010-02-07
the system 76 website has since come back. i updated the drivers and wifi is working again.

---

