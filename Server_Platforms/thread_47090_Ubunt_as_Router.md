---
title: "Ubunt as Router"
date: 2005-07-07
forum: Server Platforms
---

### Post by ozzie123 on 2005-07-07
Hello guys,

I wanted to make my PC as a router for my network. Is it possible to do this with Ubuntu (and secure enough). Is there a HOWTO about it?

Thanks

---

### Post by lothar_m on 2005-07-07
although i'm hardly an expert on this matter i do believe that you can use any linux distribution to do this but it's not for everyone.

I sugest you search the web for linux distros specially designed for that purpose.

---

### Post by alastair on 2005-07-07
When you say "router", you just mean routing network packets to different destinations/interfaces? Any Linux system can do this - this is what "route" does (manipulate kernel routing tables), or at a lower level, the "ip" command.

Ubuntu should be fine for this.

---

### Post by gruepig on 2005-07-08
Yes, you can do this.  For a HOWTO, see [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/).  In brief, you need to:

[list=1]
[*]have kernel support for packet filtering and masquerading (I haven't checked but this may be in Ubuntu's default kernel)
[*]have two ethernet interfaces configured (/etc/network/interfaces)
[*]turn on forwarding (/etc/network/options: ip_forward=yes)
[*]configure iptables forwarding firewall policy
[/list]

---

### Post by relix42 on 2005-07-08
[QUOTE=ozzie123]Hello guys,

I wanted to make my PC as a router for my network. Is it possible to do this with Ubuntu (and secure enough). Is there a HOWTO about it?

Thanks[/QUOTE]
 These are all good ideas, however, if you provided an example of what you are trying to do, we could be more specific in helping you.  (i.e. simple packet forwarding doesn't require IP tables - firewalling/NATing/mangling/tagging/logging requires IP Tables)

---

### Post by Daicogra on 2005-07-11
Special Linux-Router-Distro: [http://www.ipcop.org/](http://www.ipcop.org/)

---

### Post by ozzie123 on 2005-07-12
[QUOTE=relix42]These are all good ideas, however, if you provided an example of what you are trying to do, we could be more specific in helping you.  (i.e. simple packet forwarding doesn't require IP tables - firewalling/NATing/mangling/tagging/logging requires IP Tables)[/QUOTE]

Here's what I'm actually trying to do.

One of my computer is connected to the internet via an ADSL Modem which in turn connects with my PC using a LAN card. Currently that PC has 2 LAN card, one for the ADSL modem and the other one is for an access point.

I wanted to make all of the computer at my house (which all have a wireless LAN card) can access the internet, using the first computer as a router/server/firewall.

Is this possible?

---

### Post by az on 2005-07-12
You can do that with firestarter.  It is a graphical interface to Network Address Translation (masquerading) as well as firewalling.

Firestarter is in universe.

---

### Post by Rick Z on 2007-10-18
Hi Everyone,

I have a ubuntu setup without gui.  How could I setup my ubuntu box as router?  Please help!

---

