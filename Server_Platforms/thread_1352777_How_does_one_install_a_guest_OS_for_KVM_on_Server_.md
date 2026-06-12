---
title: "How does one install a guest OS for KVM on Server 9.10?"
date: 2009-12-12
forum: Server Platforms
---

### Post by lumix on 2009-12-12
After 4 hours of googling I quit.  I've seen references to python-virtinst which doesn't exist according to apt-get (on server AND desktop); and I get the directFB error that is oh-so talked about yet still a mystery to me when I try to use the kvm command.

Let's start from scratch:

I have a shiny new 9.10 64-bit server.  I want a guest OS on it.  How do I do this?

---

### Post by Druke on 2009-12-12
here you go! -> [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

you'll have alot more help asking in the [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum.

If you need expanded help beyond that, let me know.

Also, when you get to the networking part, theres some outdated info. I'm going to publish a wordpress tutorial later today on getting  everything ready right up to ubuntu-vm-builder.

btw if you use ubuntu-vm-builder, [I updated the script for generating the switches.]("http://thebwt.ath.cx/wp-uploads/2009/12/ubuntu-vm-builder-Parameter-Generator.html") (the current version doesn't have karmic or intrepid in the list.)

---

