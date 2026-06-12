---
title: "Unstable Internet connection"
date: 2013-01-17
forum: Server Platforms
---

### Post by viktorjano on 2013-01-17
I want to ask why Ubuntu Server 12.04 is very unstable concerning its connection to Internet. Once I am starting it has Internet connection, than reboot it, and all of a sudden it can not connect. I really dont understand. If someone else faces this kind of problems please write down. Thanx

---

### Post by sandyd on 2013-01-17
We will need some information in order to help you diagnose the issue.

What kind of network is the server connected to? DHCP/Static Addressing/Server at Datacenter?

Also, post the output of
```

lspci
ifconfig
```

---

### Post by d4m1r on 2013-01-17
Laptop or desktop? Wireless or wired connection?

Need a lot more info but it sounds like user error so far...

---

### Post by viktorjano on 2013-01-22
Hi! 
Here is the *ifconfig* output:

eth0      Link encap:Ethernet  HWaddr 00:19:66:44:1e:2b  
          inet addr:192.168.0.128  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe44:1e2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1633632 (1.6 MB)  TX bytes:192532 (192.5 KB)
          Interrupt:40 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)

I am in a dhcp environment. 
And *lspci* output:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
05:00.0 VGA compatible controller: NVIDIA Corporation G73 [GeForce 7300 GT] (rev a1)

This time I didn't have any problem with Internet. I've just started the Ubuntu and started Mozzila... But still on the status bar in the right upper corner of the desktop, when I click the network icon, the wired network menu is inactive. 
Thanx

---

### Post by spynappels on 2013-01-22
Are you running server edition, or desktop edition?

If server edition with a desktop installed on top, Network manager is probably interfering with the config in /etc/network/interfaces

Can you confirm your setup?

---

### Post by viktorjano on 2013-02-05
Yes, it is a server distro with a desktop installed on top... So what do I do next... This time for example I started Ubuntu and there was active Internet connection...

---

### Post by spynappels on 2013-02-05
As you are using it as a server, I presume you want it to have a static IP address and control the networking from /etc/network/interfaces so if this is correct, you will need to uninstall network manager
```
sudo apt-get purge network-manager
```
and probably the Gnome Applet too to avoid annoying error messages
```
sudo apt-get purge nm-applet
```

You will also need to edit the /etc/network/interfaces file to reflect your desired setup.

---

