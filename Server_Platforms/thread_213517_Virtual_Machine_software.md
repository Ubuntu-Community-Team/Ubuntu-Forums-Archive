---
title: "Virtual Machine software"
date: 2006-07-11
forum: Server Platforms
---

### Post by wifiabc on 2006-07-11
Which VM software works well on an ubuntu server?

---

### Post by Thund3rstruck on 2006-07-11
I use VMWare server and it works fantastic...

---

### Post by Martin.Snyder on 2006-07-11
wifiabc,

I saw that VMWare server needs to link to some of the X11 libraries.  Does it actually require X11 to run, or do you just need the libraries?

Also, do you know what the minimal "apt-get install" that one would need to run to be able to complete the VMWare server install.  I tried following the instructions in this guide:
[https://help.ubuntu.com/community/VMware_Guide:_Installing_VMware_Server_on_Ubuntu_6.06_LTS_amd64](https://help.ubuntu.com/community/VMware_Guide:_Installing_VMware_Server_on_Ubuntu_6.06_LTS_amd64)

Eventually I ended up failing with a series of link errors.  I am running the 32-bit x86 Ubuntu though, and not the amd64 version mentioned in that piece.

- Martin

---

### Post by scxtt on 2006-07-11
downloading VMware server from VMware.com and running the install Perl script inside works just fine w/ ubuntu (i've done it 2x w/o negative results) - the only potential issue is making sure you have the proper kernel headers in order to compile it ... as for it 'requiring' X11 to run, yeah - i'd imagine it does - unless you're not running X11 now and want a VM that doesn't run X11 ... if that's the case, i'd recommend getting the player and looking for an appliance that doesn't use X11 ... tho i don't really see the point of running VM's on a host w/o X ...

---

### Post by Martin.Snyder on 2006-07-11
scxtt,

Here's what I was thinking:

VMWare allows you to install the "console" part on any machine on the network to remotely administer one or more VMWare servers.  I've done this before in a windows environment and it works fine.  The VMWare Console behaves exactly the same whether its running on the VMWare Server machine or a remote machine.

It seemed to me that it might be possible  that VMWare server could run happily without X installed at all, so long as you never intended to run the console on that machine.

That's where the question was coming from.  I concede that it might very well be an unsupported configuration.

- Martin

---

