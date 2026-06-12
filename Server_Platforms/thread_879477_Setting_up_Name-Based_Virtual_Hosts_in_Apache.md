---
title: "Setting up Name-Based Virtual Hosts in Apache"
date: 2008-08-04
forum: Server Platforms
---

### Post by dr.wong on 2008-08-04
Hey everyone!

So I'm pretty new to Linux and I've chosen Ubuntu Desktop to be a LAMP server for my family's intranet with a few web apps such as php calendars etc...

The reason I've chosen Desktop and not Server is that someone needs to use the machine on a daily basis.

I am using a wireless router for all of the computers in my home and the Ubuntu machine is hard wired to the router. The ubuntu machine requires internet access.

The problem is that I have to set the Ubuntu machine's IP to static so that all of the other computers can find the intranet host, if I set it to DHCP, then the IP changes all the time and no one knows where to go to get to the intranet. If the ubuntu machine is using a static IP, it doesn't seem to get internet..

I think the solution is to use DHCP and use name based virtual hosting but the problem I am encountering is that you need a static IP, not dynamic IP to do this!

Is this so?

Does anyone have a solution to this?

Thanks a alot!!!!!!!!!!

---

### Post by osjak on 2008-08-04
It sounds like your server doesn't know what to use as a gateway. Please post the output of this:
```
cat /etc/network/interfaces
```

---

### Post by dr.wong on 2008-08-04
I changed the settings back to static from dynamic and it looks like the internet is working now... hmmm.... I even restarted the machine but it's still fine!! Strange...

Anyway, I'm sitting at the linux machine now, here's the output you asked for :

&#65279;auto lo
iface lo inet loopback

iface eth0 inet static
address 10.0.1.194
netmask 255.255.255.0
gateway 10.0.1.1

auto eth0

Still, do you see any reason that it would suddenly forget how to connect to the net?

---

### Post by osjak on 2008-08-04
I'm glad it works for you now. No idea why it might had been broked before.

---

### Post by dr.wong on 2008-08-04
Thanks a lot.

Next time the internet dies (if it does!!), I'll post that cat command here again!

Have an awesome one! :)

---

