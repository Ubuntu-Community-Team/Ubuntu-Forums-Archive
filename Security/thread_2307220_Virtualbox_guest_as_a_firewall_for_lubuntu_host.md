---
title: "Virtualbox guest as a firewall for lubuntu host"
date: 2015-12-22
forum: Security
---

### Post by HardTrickySecurity on 2015-12-22
Using virtualbox, I am trying to use Alpine linux (guest) as a firewall for my lubuntu (host). My physical network card (NIC) is eth0.


ISP WAN -> Alpine linux (guest) -> lubuntu (host) LAN


I am trying to get the ip from my ISP DHCP server but I had no success. I know that in virtualbox I have to use bridged adapter in eth0.
But in AlpineLinux (guest) do I have to create a vlan? Thats where I get confused.


ISP WAN <--(DHCP)--> Alpine linux (guest)


Links:


[http://timita.org/wordpress/2011/07/29/protect-your-windows-laptop-with-pfsense-and-virtualbox-part-1-preamble/](http://timita.org/wordpress/2011/07/29/protect-your-windows-laptop-with-pfsense-and-virtualbox-part-1-preamble/)
[http://www.instructables.com/id/How-To--Run-an-IPCop-Virtual-Machine-to-Protect-y/](http://www.instructables.com/id/How-To--Run-an-IPCop-Virtual-Machine-to-Protect-y/)
[http://brezular.com/2015/01/18/pfsense-virtualbox-appliance-as-personal-firewall-on-linux/](http://brezular.com/2015/01/18/pfsense-virtualbox-appliance-as-personal-firewall-on-linux/)

---

### Post by HardTrickySecurity on 2015-12-22
I was able to do this with two PCs like this:

ISP WAN --> Alpine linux firewall (PC1) --> Lubuntu LAN (PC2)

But now I am trying to do it with just one PC using virtualbox like this:

ISP WAN --> Alpine linux firewall (PC1) (Guest) --> Lubuntu LAN (PC1) (Host)

---

