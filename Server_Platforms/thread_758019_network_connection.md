---
title: "network connection"
date: 2008-04-17
forum: Server Platforms
---

### Post by dtsreprise on 2008-04-17
I am running 7.10 server. I have no network connection. I am using a 3Com Etherlink III network card. In the desktop version I added the following lines to /etc/modules to have the card recognized:

   3c509
   alias eth0 3c509

I did this on the server version to no avail. ifconfig shows 127.0.0.1 for the inet address with a mask of 255.0.0.0. Can I manually configure an IP address for the machine? Any better solutions? Thanks in advance!

---

### Post by ScorpKing on 2008-04-17
you can edit /etc/network/interfaces and add

auto eth0
iface eth0 inet static
        address 192.168.1.1
        network 192.168.1.0
        broadcast 192.168.1.255
        netmask 255.255.255.0

for eth0. look at man interfaces for complete options. the network device is handled by udev in /etc/udev/rules.d/

Hope it works

---

