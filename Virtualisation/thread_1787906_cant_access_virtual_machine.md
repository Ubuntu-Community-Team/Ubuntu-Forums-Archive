---
title: "cant access virtual machine"
date: 2011-06-21
forum: Virtualisation
---

### Post by bigmonmulgrew on 2011-06-21
Hi all
Ive recently setup a ubuntu guest on a ubuntu host. Both 11.04.
The guest is a lamp server.
I set all this up following the ubuntu server guide.
Following an issue with the guest configuration i cant access it via ssh to make changes. I dont even get a logon prompt.
So i need another way to access the guest pc.

Im guessing there is a way to access it directly from the host pc, which i have both physical and ssh access to.

Alternatively is there a way to access the files on the guest pc to correct the configuration issue. The vhd was not encrypted so there has to be a way to read it.

---

### Post by Toz on 2011-06-21
If the drive (vhd) is still intact, you could create another vm (or boot a live CD in a vm), attach and mount this drive as a secondary drive and access it from there.

---

### Post by bigmonmulgrew on 2011-06-22
> **Toz said:**
> If the drive (vhd) is still intact, you could create another vm (or boot a live CD in a vm), attach and mount this drive as a secondary drive and access it from there.

Thats a brilliant idea. thanks a lot. 
It took me a while to work out how to create a vm properly but i saved it in a script so i could use it as a template.
This should make it easy to create a clone of the first vpc (without all the setup ive done since of course)

A few questions though.
Will i be able to mount and modify the first vpcs hard drive while it is still running?
How do i mount the vhd from the first pc to the second?

---

### Post by Toz on 2011-06-22
> **bigmonmulgrew said:**
> Will i be able to mount and modify the first vpcs hard drive while it is still running?
If by "first vpc hard drive" you mean the vhd from the ubuntu guest, then no - you will have to mount it as a secondary drive when it is not running on the original vm. You had stated in your original post that the guest pc no longer displays a login prompt and ssh doesn't work. I assumed the guest vm was dead. Have you tried booting the guest vm in recovery mode?

> How do i mount the vhd from the first pc to the second?
Depending on the vm product that you are using, there should be a section in the settings/configuration that will allow you to attach the drive. Once attached and with the new vm running, you can use the mount command to mount the drive and access it.

---

### Post by bigmonmulgrew on 2011-06-22
How do I boot a guest in recovery mode?

---

### Post by bigmonmulgrew on 2011-06-22
For clarity here is the script I used to create the vm in the first place. sensetive info removed/changed of course

```

#!/bin/bash
#Script to generate the Mulgrew Enterprises
# Web Server Virtual Machine template.

sudo ubuntu-vm-builder kvm natty \
--flavour virtual \
--domain mewebserver \
--dest mewebserver \
--arch amd64 \
-o \
--hostname mewebserver \
--mem 256 \
--rootsize 20480 \
--swapsize 2048 \
--name 'Mulgrew' \
--user user \
--pass password \
--bridge br0 \
--ip 192.168.0.201 \
--mask 255.255.255.0 \
--net 192.168.0.0 \
--bcast 192.168.0.255 \
--gw 192.168.0.10 \
--dns 192.168.0.10 \
--components main,universe \
--addpkg acpid \
--addpkg vim \
--addpkg openssh-server \
--addpkg avahi-daemon \
--libvirt qemu:///system ;


```

---

### Post by Toz on 2011-06-22
I was under the impression that you were using either Vmware or Virtualbox, but you are actually using kernel-based virtual machines. Unfortunately, I don't have any experience with this type of vm. 

However, I did a quick search on google and came across this website [http://equivocation.org/node/107]("http://equivocation.org/node/107") that discusses how to access the contents of these types (kvm) of drives. Perhaps this can be of some assistance.

---

### Post by bigmonmulgrew on 2011-06-22
thanks toz. I tried this after I killed the vpc for the second time. Unfortunately when scanning the file for partitions all it came up with was "control" which it cant mount.
I'm now in the process of rebuilding the vm for the 3rd time and this time I will regularly be backing up the vms vhd.
Which is really what I should have been doing in the first place.
I'd still like to know why I'm unable to access it from the host (except via ssh) and why it keeps dying when I apply some security but as long as its working I'll concentrate on more pressing matters and return to this issue next week.
cheers
-dave

---

