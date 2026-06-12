---
title: "Raspberry pi as home network firewall"
date: 2012-06-15
forum: Server Platforms
---

### Post by ads2996 on 2012-06-15
Hi,

I am currently in the process of redesigning my home network. Putting cat6 Ethernet cable in and i had the thought of using the raspberry pi as a low power firewall gir my network. Then using another one as a dhcp server, router and wap for the network as my curent wireless router is extremly flakey and often crashes. All i was wonder is if raspberry pi is capable and if ubuntu server edition could be used for this purpose.

---

### Post by spynappels on 2012-06-15
Well, you currently will not be able to install Ubuntu Server edition as the specific arm architecture of the RPi is not supported.

It would be possible to do this with the Debian image available, but it is more difficult with just a single network port. The network port is also only 100Mbps (Fast Ethernet) so if you have a fast Internet connection, it could end up throttling your connection.

---

### Post by ads2996 on 2012-06-15
> **spynappels said:**
> Well, you currently will not be able to install Ubuntu Server edition as the specific arm architecture of the RPi is not supported.

It would be possible to do this with the Debian image available, but it is more difficult with just a single network port. The network port is also only 100Mbps (Fast Ethernet) so if you have a fast Internet connection, it could end up throttling your connection.

couldnt you use a usb ethernet port as the secound one. Also my internet is only 2mbs anyway so the speed isnt a probelm

---

### Post by spynappels on 2012-06-15
In that case you can just use what you have without a USB Ethernet adapter (which may not be supported in any case).

What you can do is have an aliased ip address on the main interface which means you have 2 IP addresses on a single interface. You'd use one for the WAN and one for the LAN. Do a Google on Debian IP Alias

Whatever you decide, you will not be able to do it on Ubuntu, you'll have to use a Debian image which can be downloaded from the Raspberry Pi website, or one of the other distros on there. Debian is most like Ubuntu though.

---

### Post by ads2996 on 2012-06-15
Is Ubuntu based of debian?

---

### Post by rubylaser on 2012-06-15
> **ads2996 said:**
> Is Ubuntu based of debian?

Yes it is.

Personally, I'd try as spynappels has done and use the Raspberry Pi for an Openelec XBMC device, and pickup a cheap and compatible device for DD-WRT for my firewall, but that's just me :)

---

### Post by ads2996 on 2012-06-15
> **rubylaser said:**
> Yes it is.

Personally, I'd try as spynappels has done and use the Raspberry Pi for an Openelec XBMC device, and pickup a cheap and compatible device for DD-WRT for my firewall, but that's just me :)
  What is dd-wrt?

---

### Post by rubylaser on 2012-06-15
Google is your friend :) [DD-WRT]("http://www.dd-wrt.com/site/index")

---

