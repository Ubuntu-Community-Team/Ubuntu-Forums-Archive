---
title: "ubuntu remote access"
date: 2011-02-28
forum: Server Platforms
---

### Post by mpratt on 2011-02-28
Hi,
I am trying to set up and run server 10.10 so that I can use it to host a virtual machine running windows server 2008. I installed ubuntu 10.10 server, and was wanting to use virtualbox, but was not sure how to configure it in text only mode, so I installed ubuntu-desktop on the machine. The problem I have now is that when I leave my machine alone for lets say several hours or more, then i try to log back in, but the monitor will not turn on and I can't get putty access. When I didn't have the desktop installed I never had this problem. so my 2 questions are - either how do I remove the desktop - or how do I get it to work. second what is the best way to set up virtualbox, or if there is a better program, in text only mode?
 
Any help is appreciated
Mike

---

### Post by mpratt on 2011-03-01
Update- I have installed ubuntu 10.04 server - running just fine in text mode, here is my setup.
 
2 ide drives sda and sdb
1 sata drive sdc - this is the drive I installed the operating system on, so I did a manuall install of grub onto sdc, don't know if that is going to make any difference in my issue.
I need some information on installing the desktop environment on the server, and any suggestions as to why it does not respond in gui mode after sitting for several hours or longer.
 
thanks,
Mike

---

### Post by arrrghhh on 2011-03-01
If you want a GUI, run ubuntu-desktop.  It comes with a GUI, and can run all the same services as ubuntu-server does.

The whole point of the server distro is to be lean and mean, and have little to update but the necessary stuff.  Don't try to fit a round peg into a square hole, just go to the desktop edition if you need a GUI.

I don't mean install the ubuntu-desktop package on top of server.  I mean, install ubuntu-desktop, the desktop edition of Ubuntu.

---

### Post by mpratt on 2011-03-01
> **arrrghhh said:**
> If you want a GUI, run ubuntu-desktop. It comes with a GUI, and can run all the same services as ubuntu-server does.
 
The whole point of the server distro is to be lean and mean, and have little to update but the necessary stuff. Don't try to fit a round peg into a square hole, just go to the desktop edition if you need a GUI.
 
I don't mean install the ubuntu-desktop package on top of server. I mean, install ubuntu-desktop, the desktop edition of Ubuntu.
 
yes, but can the desktop run apache or dns?

---

### Post by HermanAB on 2011-03-01
Howdy,

Linux is Linux is Linux...

Yes you can run any server you want on regular Ubuntu.  There isn't really any big difference between the server and desktop versions of Ubuntu.  Desktop Ubuntu just has more packages installed and the kernel is configured slightly differently to make the desktop more responsive to the keyboard and mouse.

---

### Post by arrrghhh on 2011-03-01
> **mpratt said:**
> yes, but can the desktop run apache or dns?

Indeed, I already said that... HermanAB reiterated it.

[quote=arrrghhh]**and can run all the same services as ubuntu-server does.**[/quote]

---

