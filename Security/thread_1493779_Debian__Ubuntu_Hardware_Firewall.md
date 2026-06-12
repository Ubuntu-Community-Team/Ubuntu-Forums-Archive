---
title: "Debian / Ubuntu Hardware Firewall ?"
date: 2010-05-26
forum: Security
---

### Post by luceerose on 2010-05-26
I have a PC built & ready to go for use as a hardware firewall with 3 network nics.
I was intending to use Smoothwall Express with a Red/Green/Purple configuration.
The problem is Smoothwall, for some reason won't recognize my lan ports.
I've tried both i386 & 64-bit version and Smoothwall installer just won't complete.
So, my question is can I set up a firewall PC in the same manner with an Ubuntu or Debian installation ???

All computers on my network use Debian & Ubuntu so I'm comfortable enough with using either of those just need to know what packages to install & how to use iptables/firestarter, etc to designate all 3 network interfaces to the right job.
For those not familiar with the setup I'm describing (Red/Green/Purple);
Red = Internet connection, Green = LAN, Purple = is usually WAN but in my case it's another NIC to allow laptops, etc to connect to the internet but have no access to LAN.

---

### Post by Grenage on 2010-05-26
While I've not attempted it on a Debian system, I can recommend Pfsense;  It's a fork of the m0n0wall project.

---

### Post by luceerose on 2010-05-26
Thanks. I'm downloading pfsense now.
Couldn't hurt to try it.

---

### Post by Grenage on 2010-05-26
I ended up trying it when smoothwall wouldn't work with a smartarray.  I eventually got smoothwall working, but found pfsense to be just so much better.

---

### Post by cdenley on 2010-05-26
PFSense is great. It runs on FreeBSD, and uses OpenBSD's "packet filter" firewall. I'm not sure what linux kernel Smoothwall uses, but I think linux usually supports network cards before FreeBSD does.
[http://www.freebsd.org/releases/7.2R/hardware.html#ETHERNET](http://www.freebsd.org/releases/7.2R/hardware.html#ETHERNET)

---

