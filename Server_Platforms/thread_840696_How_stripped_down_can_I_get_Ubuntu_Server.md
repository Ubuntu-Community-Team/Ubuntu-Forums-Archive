---
title: "How stripped down can I get Ubuntu Server?"
date: 2008-06-25
forum: Server Platforms
---

### Post by zachtib on 2008-06-25
So, I'm trying to build sort of a poor-man's ESX, using a headless Linux Server and VMware Server 2.0.  I'm wondering how small can I get a headless Ubuntu Server installation, or would another distro be preferred for this kind of thing?

---

### Post by koenn on 2008-06-25
> **zachtib said:**
> So, I'm trying to build sort of a poor-man's ESX, using a headless Linux Server and VMware Server 2.0.  I'm wondering how small can I get a headless Ubuntu Server installation, or would another distro be preferred for this kind of thing?

you can start with either an Ubuntu server or Debian install CD or netinst / mini CD, run the installer in expert mode, and skip the part where the installer suggests you to install additional software (or de-select all proposed tasks). You'll end up with a fully functional operating system of approx. 300 MB. 

Then install VMware server and any package it requires.

---

### Post by zachtib on 2008-06-25
OK, I just tested the expert install out in a VM.  
I'm also looking for something similar to storage pools in ZFS, I think that LVM will accomplish this, right?

---

### Post by dominiquec on 2008-06-25
Consider using KVM virtualization.  It's part of Ubuntu 8.04 official repositories.  You can operate it as a headless machine ([https://help.ubuntu.com/8.04/serverguide/C/virtualization.html](https://help.ubuntu.com/8.04/serverguide/C/virtualization.html)).  In fact, I believe it is meant to operate headless.

There are problems with it ([http://ubuntuliving.blogspot.com/2008/06/grade-for-ubuntu-804s-virtualization.html](http://ubuntuliving.blogspot.com/2008/06/grade-for-ubuntu-804s-virtualization.html)) but if all you're planning to run is Ubuntu 8.04 guest machines, you should be fine.

---

### Post by zachtib on 2008-06-25
> **dominiquec said:**
> Consider using KVM virtualization.  It's part of Ubuntu 8.04 official repositories.  You can operate it as a headless machine ([https://help.ubuntu.com/8.04/serverguide/C/virtualization.html](https://help.ubuntu.com/8.04/serverguide/C/virtualization.html)).  In fact, I believe it is meant to operate headless.

There are problems with it ([http://ubuntuliving.blogspot.com/2008/06/grade-for-ubuntu-804s-virtualization.html](http://ubuntuliving.blogspot.com/2008/06/grade-for-ubuntu-804s-virtualization.html)) but if all you're planning to run is Ubuntu 8.04 guest machines, you should be fine.

Well, I'm just got VMware Server 2 set up with the web ui and everything...

Also, as a current VMware employee, I'll probably be using their products :P

---

### Post by jrusso2 on 2008-06-25
I would use Slackware then you can decide what to install or maybe Centos.

---

### Post by zachtib on 2008-06-25
> **jrusso2 said:**
> I would use Slackware then you can decide what to install or maybe Centos.

I just read about Ubuntu Jeos... it sounds like it's meant for VM guests, but would it be able to function as the host OS as well?  At < 300MB install footprint, it looks ideal for what I'm doing.

hmm, apparently not, but it'll work for my VMs

---

### Post by bloodniece on 2008-06-25
ESX rocks big time and was a track record worth trusting Ubuntu "Juice" might be worth looking into, but the curve becomes a knife in the wrong hands. ESX FTW!

I used to skate down Bardstown Rd about 20 years ago . . . lol

---

### Post by zachtib on 2008-06-26
Well, I've installed VMware Server 2.0b2 on my webserver, and it's pretty nice.  The Web UI is, IMO, better than on ESX 3.5.  The only thing I miss from ESX is the ability to clone VMs, which is kind of a big deal.

The reason for this is so I can clone a production server, turn it into a test server, and test updates and experimental software on the test server before putting them on my production server.

I may try to hack together a shell script to try and clone a running VM... I need to look into ESX 4.0...

I got an ubuntu installation down to 463MB by doing a netinstall.  I can probably strip it down more.  Minimal Ubuntu + VMware Server 2.0 might be a decent alternative to ESX.

---

### Post by Robstarusa on 2008-06-26
> **zachtib said:**
> Well, I've installed VMware Server 2.0b2 on my webserver, and it's pretty nice.  The Web UI is, IMO, better than on ESX 3.5.  The only thing I miss from ESX is the ability to clone VMs, which is kind of a big deal.

The reason for this is so I can clone a production server, turn it into a test server, and test updates and experimental software on the test server before putting them on my production server.

I may try to hack together a shell script to try and clone a running VM... I need to look into ESX 4.0...

I got an ubuntu installation down to 463MB by doing a netinstall.  I can probably strip it down more.  Minimal Ubuntu + VMware Server 2.0 might be a decent alternative to ESX.

What do you mean "clone vms"?  Can't you stop the vm, rsync it to a new directory & start it?  once it's started, change it's IP/name & you're done, right?

---

### Post by zachtib on 2008-06-26
> **Robstarusa said:**
> What do you mean "clone vms"?  Can't you stop the vm, rsync it to a new directory & start it?  once it's started, change it's IP/name & you're done, right?

right, but the idea is to clone a running VM, so there's no downtime.  I think I can get it working if I take a snapshot, then copy the snapshot over

---

### Post by koenn on 2008-06-26
> **zachtib said:**
> OK, I just tested the expert install out in a VM.  
I'm also looking for something similar to storage pools in ZFS, I think that LVM will accomplish this, right?
I don't know ZFS. LVM is a storage abstraction layer : you create volumes that are independent of the underlying disk / partition layout, i.e. you could span multiple disks or partitions with 1 logical volume, or add additional disks to an existing LV. You can mount such a volume, so you have 1 directory/mountpoint spanning multiple disks.

---

### Post by koenn on 2008-06-26
> **zachtib said:**
> 
I got an ubuntu installation down to 463MB by doing a netinstall.  I can probably strip it down more.  Minimal Ubuntu + VMware Server 2.0 might be a decent alternative to ESX.

I have a server with Debian installed the way I described, currently at 380 MB, including some stuff I added later on (squid, apt-proxy, dnsmasq, ....).
Pretty decent for a server OS, given todays disk sizes. 

If you do apt-clean and/or apt-autoclean, you remove the .deb files you downloaded , so that frees up some space.

---

### Post by koenn on 2008-06-26
> **zachtib said:**
> right, but the idea is to clone a running VM, so there's no downtime.  I think I can get it working if I take a snapshot, then copy the snapshot over

I thought that when you make a snapshot, it's the snapshot file that's being modified from then on, in stead of the disk (vmdk) file.
So you'd have to make a snapshot, then copy all files except the snapshot file (or kust the cmdk and assume you can re-create the others by creating a new vm with an existing disk)

However, i doubt it's gong to be that easy. I can't seam to read (cat, cp, dd, ....) any of the files of a running vm guest.

---

