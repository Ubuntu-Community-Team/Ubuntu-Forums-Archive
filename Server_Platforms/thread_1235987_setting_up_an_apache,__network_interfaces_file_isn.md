---
title: "setting up an apache,  network interfaces file isnt doing what i want."
date: 2009-08-09
forum: Server Platforms
---

### Post by S0VERE1GN on 2009-08-09
I'm setting up an apache server to run my new website, and i can't get my network interfaces file to do what i want. here it is. 

auto lo eth0
iface lo inet loopback 
iface eth0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1


i want it to give me a static IP address, obviously.
what am i missing? thats the whole file from beginning to end. did i delete some shell script i didn't know about? any help would be great.

---

### Post by volkswagner on 2009-08-09
You should remove eth0 from the first line.  Possibly add a network line.

Here is mine

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.12
	netmask 255.255.255.128
	network 192.168.1.0
	gateway 192.168.1.1
```

After edit you should restart networking
```
sudo /etc/init.d/networking restart
```

---

### Post by S0VERE1GN on 2009-08-10
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          SIOCADDRT: File exists
Failed to bring up eth0.


uhm......i'm really lost.

---

### Post by S0VERE1GN on 2009-08-11
breakfast bump...anyone know how to fix this? i think a clean install is the answer...

---

### Post by R.Bucky on 2009-08-11
try using ```
ifup eth0
```

If not, try commenting out your current interface and applying the static address like Volkswagoner stated. This is my /etc/network/interfaces file

```
# The primary network interface
auto eth0
iface eth0 inet static
	address (your-internal-static-address)
	netmask 255.255.255.0
        gateway (your-router-address)
        up route add default gw (your-router-address)
```

Make sure that your addresses are correct. Sometimes it is just the little things that bite us!

---

### Post by Iowan on 2009-08-11
IMHO, it looks like what you have *should* work... what kind of errors are occuring? Results of **ifconfig?** You may need to define DNS servers in */etc/resolv.conf*

---

### Post by VipX1 on 2009-08-11
I leave DHCP on for eth0 and then reserve the i.p. address for the mac of eth0 in the DHCP server.

---

### Post by Iowan on 2009-08-11
I like the idea of a static lease - when the DHCP server is capable. I have one server set up that way, and am considering changing my network printer to DHCP static lease.

---

### Post by volkswagner on 2009-08-11
We may need to get back to basics.

Did you have this card working at all?

What card is it?  The following will lead you to the card properties.

```
lspci
```

You may want to set it to DHCP  to see if the config is the issue.

---

### Post by confusedstingray on 2009-08-12
are you trying to give you website a static ip so if you type 192.168.x.x your web site shows up. 

here is a copy of my servers interfaces file

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.104
        netmask 255.255.255.0
        network 192.168.1.0
       	broadcast 192.168.1.255
	gateway 192.168.1.2

auto eth0:0
iface eth0:0 inet static
        address 192.168.1.205
        netmask 255.255.255.0
        broadcast 192.168.1.255
	network 192.168.1.0

auto eth0:1
iface eth0:1 inet static
        address 192.168.1.200
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0

so this is setup that eth0 is my actual ip of the server 
 
eth0:0 is is a virtual ip that points to my web site 1
eth0:1 is is a virtual ip that points to my web site 2
and i have apache setup to act on these ip's
hope this is what you will look'n for

---

### Post by S0VERE1GN on 2009-08-12
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by cariboo on 2009-08-12
Are you using ubuntu desktop on your server by any chance? If so then you need to set up your static ip address using netwrk manager.

---

### Post by S0VERE1GN on 2009-08-12
yea i installed the LAMP on desktop edition.... so i use network manager? thanks!

---

