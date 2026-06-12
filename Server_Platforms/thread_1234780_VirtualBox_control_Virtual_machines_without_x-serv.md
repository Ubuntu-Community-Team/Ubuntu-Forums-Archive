---
title: "VirtualBox control Virtual machines without x-server"
date: 2009-08-08
forum: Server Platforms
---

### Post by masterpingvin on 2009-08-08
Hi!

Well i'm useing VirtualBox for a log time!

I installed my server, and in my server there is no x-server.
I dont need it. But if i vant to start a Virtual Machine Via SSH, i got some error.

So i tryed this first:
VirtualBox -startvm (name of the machine)
Result: Failed to open the X11 display!

Then i tryed in an other way:
VirtualBox -controlvm (name of the machine) start
Result: Failed to open the X11 display!

Bet how can i control machines Without x-server?

They already have Rdp5 remote desktop by VirtualBox, so i dont need the screen inn the host machine.

I need to start in a service!

Thanx: Masterpingvin

---

### Post by scorp123 on 2009-08-08
> **masterpingvin said:**
>  Bet how can i control machines Without x-server? VBoxHeadless --help
VBoxManage --help

---

### Post by tjwallace on 2009-08-08
[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-3.0-on-a-headless-ubuntu-9.04-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-3.0-on-a-headless-ubuntu-9.04-server)

---

