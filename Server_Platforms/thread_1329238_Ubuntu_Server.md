---
title: "Ubuntu Server"
date: 2009-11-17
forum: Server Platforms
---

### Post by SvEnX on 2009-11-17
Hello,

is it possible to install Windows virtual machine without GUI on Ubuntu Server, I would like to keep the server optimal and leave it without GUI? I mean that I don't like to install GUI on Ubuntu, for installing Windows.

---

### Post by smeerbartje on 2009-11-17
> **SvEnX said:**
> Hello,

is it possible to install Windows virtual machine without GUI on Ubuntu Server, I would like to keep the server optimal and leave it without GUI? I mean that I don't like to install GUI on Ubuntu, for installing Windows.

Yes, by using Vmware Server 2.0 you can use a web interface to manage your virtual machines. No GUI needed on the server.

---

### Post by SvEnX on 2009-11-17
> **smeerbartje said:**
> Yes, by using Vmware Server 2.0 you can use a web interface to manage your virtual machines. No GUI needed on the server.
Thanks for quick reply.

Is there a good HowTO around some were, setting up vmware with webui?

---

### Post by Lars Noodén on 2009-11-17
> **SvEnX said:**
> Thanks for quick reply.

Is there a good HowTO around some were

Be sure to look into qemu and virtualbox.  I find qemu much easier to deal with than any of them, but virtualbox has more options.  Both are open source.  

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[http://www.downloadsquad.com/2008/02/10/run-windows-in-a-virtual-machine-using-ubuntu-and-virtualbox/](http://www.downloadsquad.com/2008/02/10/run-windows-in-a-virtual-machine-using-ubuntu-and-virtualbox/)


[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

And like the howto say, consider wine if it is only one or two applications that you need.

---

### Post by SvEnX on 2009-11-17
Thanks! I'll look into them.

---

