---
title: "dual boot windows 2000 and ubuntu server"
date: 2008-12-31
forum: Server Platforms
---

### Post by lego12 on 2008-12-31
i want the computer im going to set up to automaticaly boot ubuntu server and when i want it to, boot win2k, what program should i use or how do i do this?

---

### Post by windependence on 2009-01-01
Install Windows 2000 first, then install Ubuntu. You will be given the option to keep your windoze 2000 installation when you install Ubuntu and there will be a boot menu installed so you can pick the OS you want to boot. 

A better suggestion would be to install the free VMware server and run your Windows machine in a VM session. That way, you would not have to reboot to get in to Windoze.

Just curious, what do you need Windoze 2000 for?

-Tim

---

### Post by Zack McCool on 2009-01-01
Especially as a server?  If you are starting from scratch, you'll be far better off with a Linux server.  File shares will be snappier, and you'll have far less likelihood of issues.

But, yes, if you really feel you want a Windows server, VMWare Server installed on Ubuntu Server will be a better option.  You won't have to reboot each time you want to use the Windows services...

---

### Post by theozzlives on 2009-01-01
I was under the impression that VMWare was like VirtualBox... GUI based.

---

### Post by windependence on 2009-01-01
> **theozzlives said:**
> I was under the impression that VMWare was like VirtualBox... GUI based.

It is, but it doesn't HAVE to be. It can be set up completely headless if you want with control from a remote machine or web GUI.

-Tim

---

### Post by Zack McCool on 2009-01-01
> **theozzlives said:**
> I was under the impression that VMWare was like VirtualBox... GUI based.

VMWare is not GUI based.  It has a browser-based interface for management, but it works completely independent of it.  For instance, you can set it to start VM's at specific intervals after a reboot.  They run without any visible interface.  AAMOF, for Windows guests, I usually use RDP to connect rather than the Web interface, as RDP is a bit faster.

I have 8 VM's on this machine.  When I reboot, 3 of them automatically start, in 5 minute intervals.  The other 5 only get started if I need them for something.

---

### Post by lego12 on 2009-01-01
th reason i need windows 2000 is because i dont have another valid xp cd-key, and for the wireless usb im going to use i need to use Ndiswrapper

---

### Post by theozzlives on 2009-01-01
> **lego12 said:**
> th reason i need windows 2000 is because i dont have another valid xp cd-key, and for the wireless usb im going to use i need to use Ndiswrapper

Microsnot will give you another key or re-activate yours if you call them and tell them what your doing. Be sure to say pleeeeeese.

---

