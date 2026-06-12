---
title: "Lightweight host os for virtualization ?"
date: 2008-08-15
forum: Virtualisation
---

### Post by erland on 2008-08-15
Does anyone have a good recommendation from a lightweight os to use as host for multiple virtual machines.

I'm currently running a fullblown Ubuntu Server with a few VMWare virtual machines but I also run a number of server applications directly on the Ubuntu Server. To make the maintenance a bit easier so I can upgrade the OS for one application at the time I would like to change this so I basically run no server applications on the host OS and instead have virtual machines for each related set of applications. 

Is there a good recommendation on a lightweight os to use as the host os ?

Should I just go with a standard Ubuntu Server with with no extra applications installed or is there a better solution which use less resources ?

I currently use VMWare for the virtual machines, but I've been thinking about changing that to VirtualBox or KVM. I'm currently running one Windows XP and two Ubuntu JEOS as guests, this will probabably increase so I will be running a few more Ubuntu guests.

So, does anyone have any recommendation regarding what to use as the host os ?

---

### Post by chungy on 2008-08-15
I've set up CentOS and Xen before, and it works very well, and IMO it wasn't too hard to install.

---

### Post by EmmEff on 2008-08-15
How about the new, free ESXi?  Can't get much smaller than that...

Failing that, KVM is supposed to offer better performance than VMware Server but good luck with the network settings.  I have had a lot of difficulty getting VDE to work properly and offer the same types of network configurations that VMware has.

---

