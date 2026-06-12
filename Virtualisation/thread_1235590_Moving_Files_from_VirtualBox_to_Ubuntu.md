---
title: "Moving Files from VirtualBox to Ubuntu"
date: 2009-08-09
forum: Virtualisation
---

### Post by chome4 on 2009-08-09
If I want to see an 'opening' to the Ubuntu platform from within VirtualBox, how is this done? I can download files within a VirtualBox session but don't know how to see the file in Ubuntu.

---

### Post by Richardarkless on 2009-08-09
The only possible way I can see would be to create a sharing folder between ubuntu and your vm

I dunno if it is possible to mount the virtual hard drive and wouldn't know where to start as I have been wanting to mount them ever since I began to use virtualbox

Richard

---

### Post by benerivo on 2009-08-09
@Richard - Have you tried this...(i haven't as i haven't really got a need for it)
[http://muralipiyer.blogspot.com/2008/02/mounting-virtualbox-vdi-disk-authentic.html](http://muralipiyer.blogspot.com/2008/02/mounting-virtualbox-vdi-disk-authentic.html)

EDIT - Only for use on a fixed size disk image.

---

### Post by RegentLynx on 2009-08-09
It's actually quite easy to set up Shared Folders in Virtual Box but it does involve downloading the "Guest Editions" module. Details and instructions can be found in the Virtual Box Manual at;
[http://www.virtualbox.org/manual/UserManual.html#id2507347](http://www.virtualbox.org/manual/UserManual.html#id2507347)

---

### Post by ugm6hr on 2009-08-09
How have you set up networking in your VirtualBox?

In the settings page, the default is NAT, which puts your VM in a different network to the host (presumably Ubuntu).  This allows you to access the internet via your host->router, but not the host network directly.

I used "Host Interface" which essentially puts the VM on the same network as all your other computers (and host).  This allows you to access the VM with the IP address (as a web-host etc), but should also allow file-sharing.

PS: I'm not a VM expert, but have recently been messing around with a VirtualBox Ubuntu server setup.  Hence my advice may not be 100% accurate...  I used the Jaunty repo virtualbox-ose

---

### Post by jocampo on 2009-08-10
> **chome4 said:**
> If I want to see an 'opening' to the Ubuntu platform from within VirtualBox, how is this done? I can download files within a VirtualBox session but don't know how to see the file in Ubuntu.

It's easy :-) ....in fact, was doing that as a mini Project this weekend at home...

1st, setup your VM network card as Bridged (DO NOT USE NAT). Bridged will create a virtual network card with its own IP address. This will allow your VM to connect and talk to your Host. 

Once done, you have several choices:

1. You can simple right click and create a Linux share folder. Maybe will ask you to download some files and setup Samba for you.
2. If you are creative (that's what I did) setup NFS on your Host. Once done, you can invoke or read/write inside your host from your Linux virtual machine. You can even map via autofs or fstab the Host share directory and move anything you download into your VM to the host.

---

