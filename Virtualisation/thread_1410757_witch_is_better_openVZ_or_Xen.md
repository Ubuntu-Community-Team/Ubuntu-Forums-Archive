---
title: "witch is better openVZ or Xen"
date: 2010-02-19
forum: Virtualisation
---

### Post by appie oulkady on 2010-02-19
[COLOR=black][FONT=Verdana]Hey guys,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I want to install an Ubuntu web server on a virtual machine.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I did some research on openVZ and Xen, but i couldn't make up my mind whether to use openVZ or Xen. I hope you guys can give me some advise and help me out here.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]greets [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Appie Oulkady[/FONT][/COLOR]

---

### Post by chakoshi on 2010-02-21
[http://ubuntuforums.org/showthread.php?p=8860871](http://ubuntuforums.org/showthread.php?p=8860871)

I suggest you try kvm!

---

### Post by lahmanwokard on 2010-03-02
We vote for Xen we are running small VPS hosting company and I can say xen is the best virtuazliation ever we added [http://hostbillapp.com](http://hostbillapp.com) to vps provisioning and we are reall happy for that.

---

### Post by bodhi.zazen on 2010-03-03
> **appie oulkady said:**
> [COLOR=black][FONT=Verdana]Hey guys,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I want to install an Ubuntu web server on a virtual machine.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I did some research on openVZ and Xen, but i couldn't make up my mind whether to use openVZ or Xen. I hope you guys can give me some advise and help me out here.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]greets [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Appie Oulkady[/FONT][/COLOR]

The "problem" you will have with OpenVZ and Xen is getting the host node up and running.

Linux is moving to LXC , but IMO it is not up to par yet ...

I suggest you look a Proxmox :

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

Proxmox is Debian with OpenVZ + KVM + a Web interface for management of the guests.

The other option IMO is Centos + either Xen or Openvz.

For Xen on Ubuntu see :

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

