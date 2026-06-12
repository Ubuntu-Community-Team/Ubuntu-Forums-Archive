---
title: "Can't Access Ubuntu Server from outside VirtualBox"
date: 2009-04-06
forum: Virtualisation
---

### Post by justinmiller87 on 2009-04-06
So here's what is going on. I recently setup a Ubuntu 8.10 Server in a virtual machine using VirtualBox installed on XP and I'm currently trying to access it. I tried giving it a static IP with the scheme of my local network to no avail. When I did that, I lost all connectivity in the Server to access the Internet. I restored it back to dhcp and was at least able to get to the Internet. I want to be able to have a static IP, have access to the Internet, and be able to access the web server from outside the machine. Any suggestions? I'll post anything you need me to post.

Thanks,

Justin

---

### Post by dominiquec on 2009-04-06
Hi, Justin,

For your virtual machine, you have to set the network interface to "Host Interface."  You'll find this in the settings for the virtual machine, not in the guest operating system.  This will be in the network setting.  The default is NAT, which will not let you access the guest OS from outside.

I assume you're using the latest version of VirtualBox.  You should be, because in earlier versions it was a real pain to set up.

--Dom

---

### Post by justinmiller87 on 2009-04-06
Hey Dom,

I'm using Version 2.1.4 just downloaded today, so I hope it's updated. :)

It worked, thanks for the assistance.

---

