---
title: "Server installation problem"
date: 2008-10-31
forum: Server Platforms
---

### Post by KB1LQC on 2008-10-31
I am trying to install an Ubuntu Server edition on a PIII server I acquired.  I only know that it is a pIII 430 or so MHz with two 9GB SCSI drives and no internal CDROM.  I have hooked up a CD drive for installation and here is what happens.

I can do a normal install process for Desktop and Server edition.  However, when installing I make progress up until 75% of the base system is installed.  It the, gets stuck at "storing language" and does not seem to do anything.  I have tried different releases (7.10, 8.04, and 8.10) as well as an IDE drive which I was using in another computer running as a server, so it had a server edition already on it (wanted to start fresh).  Any ideas on what the problem is?  The server seems to be something that was built by parts from somewhere like newegg.com or something.  It's not a brand name labeled server.  If more information is needed please let me know!




Bryce
KB1LQC

---

### Post by KB1LQC on 2008-10-31
I got it to work by putting the hard drive in another computer and installing Server 8.10 on there.  I then switched the HDD to the server and it boots up but I chose not to configure the network on the other machine because it would get stuck when searching for mirrors.  Now I need to set-up the network on this computer but I can't seem to get it to configure correctly.  When I use teh ethernet device "eth0" I get an error about the device not existing.  Next I ran ifconfig and it told me that the two network devices present were "lo" and "vnet0".  I tried using vnet0 but so far I haven't been able to connect to the internet (I test by trying to update with apt-get).  Any suggestions?



Bryce

---

### Post by cariboo on 2008-10-31
Could you paste the output of:

```
sudo lshw -C network
```

In your next post. This will help determine if your network card is working.

JIm

---

### Post by KB1LQC on 2008-11-01
> **cariboo907 said:**
> Could you paste the output of:

```
sudo lshw -C network
```

In your next post. This will help determine if your network card is working.

JIm

Heres what I can see on the screen about the card I am using

```

description: Ethernet interface
physical id: 1
logical name: vnet0
serial: b2:0b:de:c5:2d:25
compatibilities: Ethernet physical
configuration: broadcase=yes driver=bridge driverversion=2.3 firmware=N/A
ip=192.168.122.1 link=yes multicast=yes

```

the ip address is confusing me because I am plugged into my schools ethernet jack (not my router) and should have an ip on the order of 129.XX.XX.XXX which is what my school seems to give out on these (going by by laptops IP).  My /etc/network/interfaces is configured

```

auto vnet0
iface vnet0 inet dhcp

```

---

