---
title: "How to install VMware Server on Ubuntu 10.04 64-bit?"
date: 2010-09-01
forum: Virtualisation
---

### Post by lightningfox on 2010-09-01
Hi

I am running Ubuntu 10.04 64-bit GNOME.

I want to install VMware Server.

I read the sticky above but it only tells how to install VMware Server on Ubuntu 9.04.


Please tell me how to install VMware server on Ubuntu 10.04 64-bit, or give me a link to a webpage that does.

---

### Post by Ryadt on 2010-09-02
Try this:

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by lightningfox on 2010-09-02
Hi 

I installed the 64 bit version of VMware server using the instructions on this page [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)
and it seems to have installed successfully, but VMware Server hasn't appeared in my Application menu and I can't figure out how to start VMware Server.

Please help me to start VMware Server.

---

### Post by Ryadt on 2010-09-03
Try:
[http://localhost:8222](http://localhost:8222)

---

### Post by lbrty on 2010-09-08
Have you tried installing/using VMware Player? The process is much simpler.

[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

---

### Post by dcstar on 2010-09-08
> **Ryadt said:**
> Try:
[http://localhost:8222](http://localhost:8222)

You cannot use Firefox 3.6 with VMware Server 2.x console, you have to manually install and use FF 3.5 to actually be able to open a VM console window.

You also have to patch the /etc/vmware/config file with the keycode line to allow CTRL-ALT-Delete to be send to a Windows VM.

Guess who has just set up VMware Server 2 on a 10.04 64-bit system......8-[

This has some detailed help:

[https://resalxh.wordpress.com/2010/06/02/vmware-server-2-0-2-on-ubuntu-10-04-lucid-lynx/](https://resalxh.wordpress.com/2010/06/02/vmware-server-2-0-2-on-ubuntu-10-04-lucid-lynx/)

---

### Post by lightningfox on 2010-09-21
Hi 

Thanks for your answers.

I got vmware server to work and now I can open and run my VMs.

---

