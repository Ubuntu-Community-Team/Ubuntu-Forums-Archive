---
title: "KVM networking question"
date: 2009-07-23
forum: Virtualisation
---

### Post by papertigers on 2009-07-23
I have a question idk if any of you could answer.  
I was wondering if it is possible to setup networking in such a way that traffic will come into the machine on eth0 and will pass through a virtual machine of a firewall such as pfsense or smoothwall.  

Say I have
Ubuntu server running KVM
Virtual machines:
1. pfsense
2. a file server
3. a web server

could i have something like that.

internet ----> KVM box --> to first vm (pfsene) and then have the file server and webserver connect through pfsense back to the kvm and out.

Thanks.

---

### Post by bodhi.zazen on 2009-07-23
Guest networking is a bit complex and here is a link to get you started :

[http://www.gnome.org/~markmc/qemu-networking.html](http://www.gnome.org/~markmc/qemu-networking.html)

personally I would find it easier to use iptables on the host, without pfsense on a separate guest.

You will have to configure pfsense (tow virtual network cards), boot the other guests, and then edit networking to use the pfsense as a gateway (edit /etc/networking/interfaces and set the pfsense box as the default gateway and edit /etc/resolv.conf).

---

