---
title: "Running VirtualBox as service without GUI"
date: 2012-05-03
forum: Server Platforms
---

### Post by YSS on 2012-05-03
Hello, Is it possible to run Virtualbox as a service in Ubuntu server 12.04 ? 

I want to install a server with Ubuntu server 12.04 64bit and run 2 windows servers under Oracle Virtualserver.

Is this possible ? Or do I have to install the GUI ? 

Thanks

---

### Post by Cheesemill on 2012-05-03
Yes it's possible:
[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.1-on-a-headless-ubuntu-11.10-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.1-on-a-headless-ubuntu-11.10-server)

Also if you want to create and administrate VM's using a web interface instead of having to use the VBoxManage commands take a look at phpvirtualbox:
[http://code.google.com/p/phpvirtualbox/](http://code.google.com/p/phpvirtualbox/)

---

### Post by elico on 2012-05-03
i wrote some simple interactive scripts to manage a headless vbox machines.
shutdown\start\restart
config network cards(internal,host,bridge)
configure vrde (RDP)
insert\eject cdrom(iso)
connect and disconnect HD images.

if someone wants them i will upload them.

---

### Post by YSS on 2012-05-03
Please do. 

Thanks!!

---

