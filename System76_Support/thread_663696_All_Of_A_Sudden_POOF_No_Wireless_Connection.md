---
title: "All Of A Sudden POOF No Wireless Connection"
date: 2008-01-10
forum: System76 Support
---

### Post by thecomputerdoc on 2008-01-10
Yeah all of a sudden I lost my wireless connection, in fact I don't seem to have a logical name for it. Here's the results of a couple of inquires:

~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network DISABLED      
       description: Ethernet interface 
       product: NetLink BCM5787M Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth4 
       version: 02 
       serial: 00:1b:38:2a:e2:2f 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=tg3 driverversion=3.77 latency=0 module=tg3 multicast=yes 
  *-network 
       description: Network controller 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=ipw3945 latency=0 module=ipw3945 


~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6004 (5.8 KB)  TX bytes:6004 (5.8 KB) 

Does any One Know What I Can Do To Resolve This Issue... HELP

---

### Post by thomasaaron on 2008-01-10
It's always a good idea to let us know computer model you are using, as well as which version of Ubutnu you are running.

Does it have a wireless switch?

White Darter -- above the keyboard on the left
Newer Gazelles, Servals, Pangolins -- leading edge of computer, left hand side

If you have your wireless switch on, is the wireless led lit?
If so, try this:

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).

---

### Post by thecomputerdoc on 2008-01-10
My System is as follows:

Serval Performance
- Operating System Ubuntu 7.10 (Gutsy Gibbon) Linux
- Grapics: NVidia 512 MB GeForce 8600M GT
- Networking Ethernet (LAN) WiFi
- Wireless 802.1 abg
- Built-In Web Cam
- Processor Core 2 Duo T7700 2.4 GHz 800 MHz FSB 4 MB L2
- Memory 4 GB - 2 x 2 GB DDR2 667 MHZ
- Hard Drive 80 GB 7200 RPM SATA
- Optical Drive CD-RW / DVD-RW
- Wireless 802.11 abg
- Bluetooth Bluetooth

I've tries various things including looking at the networking system properties, trying a few commands from the terminal and it all indicates that I don't have a wireless connection at all.

HELP

---

### Post by thecomputerdoc on 2008-01-10
I run lshw and one of the PCI bridges includes:

Network controller 
/0/100/1c.5/0 
product: PRO/Wireless 3945ABG Network Connection 
vendor: Intel Corporation 
bus info: pci@0000:0c:00.0 
version: 02 
width: 32 bits 
clock: 33MHz 
capabilities: 
	bus mastering, 
	PCI capabilities listing 
configuration: 
	driver: ipw3945 
	latency: 0 
	module: ipw3945

---

### Post by thomasaaron on 2008-01-10
OK. So it sees your wireless card. That's a good sign.

Please confirm that your wireless switch (leading edge of your computer on the left side) is toggled to the right.

Please confirm that you have checked your /etc/network/interfaces file per the instructions above.

---

### Post by ubutufan on 2008-01-10
Hi thecomputerdoc
It would help to know the output of iwconfig. Please list it

---

### Post by thecomputerdoc on 2008-01-10
Wow I feel like a real dummy. I didn't have my switch set properly... I'm such a fool. Thanks Everyone for your help. My problem is solved.

---

### Post by thomasaaron on 2008-01-10
Don't sweat it.

The reason I knew to suggest it is that I've done it several times myself.
If you're a dummy for doing once, I must be a complete idiot.

Best,
T

---

