---
title: "DHCP Server and DHCP Client Simultaneously"
date: 2010-08-04
forum: Server Platforms
---

### Post by BeardedChimp on 2010-08-04
I have an embedded device for which I've created an html configuration page. This page allows you to set static IPs, dhcp, and can scan for wireless devices.

My problem is that in order to access the device it requires that it runs as a dhcp server otherwise people are not assigned an IP and so can not access the embedded devices static IP. (This config page is for the laymen and so they are not the type who are able to set up their own static IPs).

One of the potential options is to have the device connect to the network on eth0 acting as a dhcp client. However this prevents me from running a dhcp server.

One solution I can think of is running a dhcp server only if it doesn't detect another dhcp server running on the network. However I have no idea how this could be setup. Anyone know?

If anyone else knows more about networking so as to allow an idiot to be able to type [http://thisismydevice/](http://thisismydevice/) without requiring some form of dhcp running I would love to hear.

Cheers.

---

### Post by YesWeCan on 2010-08-05
Erm. A little more info may be required. If the "embedded device" has a static IP address then you should be able to access it from any other device that is on the same subnet. You should not have to have the embedded device dish out IP addresses. On your regular dhcp server you'll need to tell it to assign the embedded device's IP as a static IP so that it doesn't try to assign this IP to any other device.
The suggestion you make that the embedded device won't allow another device to talk to it on its static IP unless the embedded device has given the device its IP via dhcp doesn't make sense to me.

---

### Post by BeardedChimp on 2010-08-10
Sorry, I don't think I explained myself properly.
> If the "embedded device" has a static IP address then you should be able to access it from any other device that is on the same subnet.

This is the crux of the problem, unless the embedded board acts as a dhcp server, any laptops connected to it are not provided a subnet and so won't connect to the board when given its ip.

I'll lay out the problem more succinctly.

I have an embedded board that streams on to the internet. It has both ethernet and wireless access. The board has no display and so the only way to configure it is to plug a laptop into it and use the web interface I created. The web interface allows you to view networks in range and to connect to them. It also allows you to set a static IP for the ethernet, or to use DHCP.

The problem is that the devices needs to be able to use either ethernet or wireless to connect to the internet. If it uses ethernet then I obviously cannot run a dhcp server on it.

So what I essentially need is for people to be able to plug into it and be able to type either:
[http://mydevice](http://mydevice) (this is optimal)
or
[http://192.168.1.100](http://192.168.1.100) (its static IP)

However I cannot work out how to do this without dhcp

Cheers.

---

### Post by koenn on 2010-08-10
> **BeardedChimp said:**
> 
The problem is that the devices needs to be able to use either ethernet or wireless to connect to the internet. If it uses ethernet then I obviously cannot run a dhcp server on it.
why not ?

and why don't you just let some other host be dhcp server ?

---

### Post by BeardedChimp on 2010-08-16
I can't run a dhcp server and a dhcp client simultaneously as the dhcp server will interfere with other networks it is plugged into.

> and why don't you just let some other host be dhcp server ?

Because often the device will be used in places that do not have ethernet access. In which case the only way to connect it to their wireless is through an interface.

---

