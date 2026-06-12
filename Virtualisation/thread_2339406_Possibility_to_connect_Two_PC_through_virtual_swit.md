---
title: "Possibility to connect Two PC through virtual switch"
date: 2016-10-08
forum: Virtualisation
---

### Post by mistblinde on 2016-10-08
[TABLE]
[TR]
[TD="class: votecell"][CENTER]
[/CENTER]
[/TD]
[TD="class: postcell"]Hi!

I want to connect two of my PC through OVS which I would like to install on my computer, here you are a picture how it look like:
[IMG]https://s17.postimg.org/y4oatlanz/How_It_Look_Like.png[/IMG]

I want to install two NIC (HP Intel Pro 1000 CT GbE Card), install this two NIC on my second PC, then install on this second PC OVS (under Ubuntu) and connect from port of first NIC to my first computer and from port of second NIC to third computer.

Is this possible?

Thanks in advance!
[/TD]
[/TR]
[/TABLE]

---

### Post by TheFu on 2016-10-08
Yes. Don't know what OVS is exactly (lots of abbreviates for those 3 letters), but if PC2 is configured as a router, this is trivial.

---

### Post by mistblinde on 2016-10-08
By OVS I mean Open Virtual Switch :)

---

### Post by TheFu on 2016-10-08
[http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)
OVS isn't needed. I guess you can use it, but for connections that aren't 10G, really isn't needed.

---

### Post by mistblinde on 2016-10-08
I know but I have to test some different virtual switches(Open vSwitch, Lagopus, etc) in that environment and I have to configure it as you see in my picture and I need to know that this is possible :)

---

### Post by SeijiSensei on 2016-10-08
One thing to remember is that, by default, Ubuntu does not permit forwarding of packets across network interfaces.  You need to uncomment the "net.ipv4.ip_forward=1" directive in /etc/sysctl.conf.

---

### Post by mistblinde on 2016-10-09
Thank you for all!! :)

---

