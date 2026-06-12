---
title: "OpenVZ + VirtualBox on Hardy"
date: 2008-06-04
forum: Virtualisation
---

### Post by Tombar.uy on 2008-06-04
Hi folks!

im new to virtualization and kernels, so i may be really wrong on some of my assumptions^^ please apologize me :D

I am currently running openVZ on Hardy using 2.6.24-6-fza-686 kernel and now i need to virtualize a windows XP for testing purposes, i used to run a winxp with virtualbox before installing openVz.

I have  already install virtualbox but when i try to start a virtualxp image i have, it fails and tells me to install virtualbox-ose-modules-generic, i was about to when i see there is a virtualbox-ose-modules-2.6.24-17-openvz and i wonder which kernel module should i install? can someone point me which one i need to install?

also i wonder if there is a 2.6.24.17 kernel with openvz "modules" in it available for hardy? should i install it and then try with the virtualbox-ose-modules-2.6.24-17-openvz?

is there another virtualization platform i could use to run winXP on it easily? im use to virtualbox and it really rocks! but im open to try another platform and solve my drama :D

Regards Martin

Ps: Please aplogize for my english but im not a native english speaker.

---

### Post by bradmkjr on 2008-06-04
I don't think you are going to be able to run virtualbox inside of openvz. Where it may be possible, but because of the kernel requirements of virtual box most likely the two of them won't play nicely together.

I haven't worked with Openvz for a while now, so things maybe better supported, but my experience was that it was better to put Openvz inside of a full virtual machine, such as virtual box or vmware server.

Good luck, and be careful, please don't test out this amount of virtualization on a production system, because there is always a chance you may crash hard and not be able to boot if kernel files get over written.

Good Luck,
Bradford Knowlton
[http://x86v.com](http://x86v.com)

---

### Post by Tombar.uy on 2008-06-06
I think you didnt understand my current setup :S

i run hardy with 2.6.24-6-fza-686 kernel and with Xs (xfce) , inside hardy i run openVz and 2 VE (debian and centos) and now i also want to run virtualbox for WindowsXP

now im going to try new kernels and install:

linux-headers-2.6.24-17-openvz
linux-image-2.6.24-17-openvz 
virtualbox-ose-modules-2.6.24-17-openvz 


i will report later my findings :D

---

### Post by starfry on 2009-03-07
Hello,

Just download and install that latest VirtualBox (get it from virtualbox.org). It should just work, as long as you do this **AFTER** installing openVZ.

If you do it the other way round (i.e. install VirtualBox then openVZ) then you will need to rebuild the VirtualBox kernel drivers like this:

```

$ sudo apt-get install linux-headers-$(uname -r)
$ sudo /etc/init.d/vboxdrv setup

```

---

