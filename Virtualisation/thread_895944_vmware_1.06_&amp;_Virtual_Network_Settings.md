---
title: "vmware 1.06 &amp; Virtual Network Settings"
date: 2008-08-20
forum: Virtualisation
---

### Post by khalos on 2008-08-20
hi,

I have instaled ubuntu 8.04 with vmware server 1.06 and everything works fine. 
But now i change my network wired to wifi and my virtual machines cant connect to anywhere. 
I have to change in Virtual Network Settings on server from one adapter to another.
The question is: i havent this option on my vmware server, how can i change my settings?
I try to install this version of vmware server on XP with two network adapters and works great.

Thanks,
Nuno

---

### Post by fjgaude on 2008-08-20
I believe you have to power off the VM then you can go to settings and change them. You can't that when the VM is powered on.

---

### Post by khalos on 2008-08-21
I tried it, and i know that, the problem is i havent that option in vmware server.
It is some kind of limitation in linux/ubuntu?

thanks,
nuno

---

### Post by SecretCode on 2008-08-22
Just to be clear, are you saying you have VMware server running with Ubuntu as the **host**? And if go to host > virtual network settings > host virtual network mapping, you can't change the mapping for VMnet0?

---

