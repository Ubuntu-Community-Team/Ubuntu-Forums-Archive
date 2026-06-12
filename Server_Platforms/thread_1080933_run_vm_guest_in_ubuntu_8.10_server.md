---
title: "run vm guest in ubuntu 8.10 server"
date: 2009-02-25
forum: Server Platforms
---

### Post by freefall235 on 2009-02-25
Hey Everyone, 

I have just installed Ubuntu server at home, and have been playing around with it...

I have not installed any desktop environments, ie gnome, and i dont plan to...

however the server is essentially just a file, web, dhcp and dns server, so am thinking of using some virtualization software on it. 

I am probably going to use vmware server, as its a fairly old pc, and I dont think my CPU would meet reqs of KVM... (p4 2.8, 1.5gb DDR1 ram)

so, my question is, when I install vmware server, can I bring up a command to execute that server, and run it with keyboard and mouse, which seems strange to me, since there is no desktop env installed...

but just thought I would ask...

Cheers

---

### Post by TwiceOver on 2009-02-26
VMWare Server 2 has a web frontend.  Install VMWare Server2 on your Ubuntu Server then from another machine with a web browser you can connect to the box and create your virtual machines and install software.

Pretty slick little setup they got there now.

---

