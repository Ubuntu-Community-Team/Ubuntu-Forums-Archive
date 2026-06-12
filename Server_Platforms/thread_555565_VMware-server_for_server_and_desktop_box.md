---
title: "VMware-server for server and desktop box"
date: 2007-09-20
forum: Server Platforms
---

### Post by xadium on 2007-09-20
Hi

I have a machine which is probably just about capable of running two virtualised environments.  It is headed with a relatively good gfx card/sound card etc.

Essentially I want to host two virtual machines under a lean Linux install, one which will be a virtual headless LAMP stack and the other which will my desktop machine.  The idea being that I can reboot/break the desktop machine and not impact the virtual server.

Is this a sensible proposal?  Am I going to get crappy performance from the virtual desktop.  Can I get my machine to effectively be the virtual desktop without having having to use X11 on the host to connect to the console to connect to X11 on the guest?  I want to boot the host, have the two virtual machines start and then my machine to become the desktop (transparently would be lovely)

Cheers to anyone who has some suggestions on this.

Ali

---

### Post by Brazen on 2007-09-20
Unfortunately, the VMWare Console is going to require x11 on the machine in order to run.  You could use one of the super lightweight window managers on the host, such as fluxbox or icewm.

You might be much happier though, just getting the cheapest computer off ebay (sub $100) and sticking it in a closet/attic/basement/etc and using that as your server.

---

### Post by dendrobates on 2007-09-20
vmware-server will do this very well.  You should use bridged networking and not NAT, or you will not be able to access the guest vm.

It is also worth mentioning that you can use a remote vmware console to access you client vm's.  You still need x to install it, but it doesn't need to remain running.

---

### Post by ruibernardo on 2007-09-20
I've found this "fresh" thread in "General Help": [Installing VirtualBox on 7.04 Server edition for VRDP use]("http://ubuntuforums.org/showthread.php?p=3399702#post3399702"). It explains how to install virtualbox (not vmware) in Ubuntu Server to use it with RDP. It could be an alternative to the option of installing a desktop environment in Ubuntu Server to use vmware-server.

But looking at that tutorial, I remember of trying a web interface for vmware-server back in Dapper. Now I'm using the vmware package from the commercial canonical repos on Feisty, and I can't find it here on my computer, but I took a look at wmware website and I've found it (it's the [Management Interface]("http://register.vmware.com/content/download.html")). 

I really didn't use it much, so I can't be more precise about what it can or can't do but, could it avoid a desktop environment on Ubuntu Server?

---

