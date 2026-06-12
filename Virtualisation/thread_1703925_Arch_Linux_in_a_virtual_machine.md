---
title: "Arch Linux in a virtual machine"
date: 2011-03-09
forum: Virtualisation
---

### Post by MartyBuntu on 2011-03-09
So here's my current setup:

DISK 1 - 320GB disk with Ubuntu 10.04 formatted as ext3
DISK 2 - 320GB disk for drive imaging of DISK1 formatted as ext3
DISK 3 - 250GB disk strictly for MP3 storage formatted as ext3
DISK 4 - 160GB disk workspace for cutting and editing video and audio
               uncompressed, captured from Hauppauge capture card formatted
               as ext3


...so the question is this. I wish to experiment with Arch and install it through a virtual machine (VMware).

During the VMware setup, can I allocate all or part of **DISK 4** to the Arch install, or does VMware require all work to be done in the host OS's "home directory"?

Thanks.

---

### Post by Sef on 2011-03-09
Moved to Virtualization.

I would recommend trying the Arch Linux forums.

---

### Post by matt_symes on 2011-03-10
Hi

I had a situation not to dissimilar to yours in that i use VMWare and i wanted to keep my VM's on a different partition.

What i did was moved the vmware directory in my home directory to the partition and then created a symbolic link to that directory in my home folder. I then mounted this partition at start up. This has worked for me and maybe it will work for you.

For my Arch install i did not bother with VMWare but created a 10G partition to install it in.

Kind regards

---

### Post by MartyBuntu on 2011-03-10
> **matt_symes said:**
> Hi

I had a situation not to dissimilar to yours in that i use VMWare and i wanted to keep my VM's on a different partition.

What i did was moved the vmware directory in my home directory to the partition and then created a symbolic link to that directory in my home folder. I then mounted this partition at start up. This has worked for me and maybe it will work for you.


I'll look into this. Thank you.

> **matt_symes said:**
> 
For my Arch install i did not bother with VMWare but created a 10G partition to install it in.

Kind regards

Arch was just an idea, although I'd like to VM other things too...possibly BSD's, Puppy...I just wanted to know if VMware in Ubuntu can install in separate physical drives.

---

### Post by daniel_w93 on 2011-03-10
(Using VirtualBox 4.0.2 on Ubuntu 10.10)

I just realized that you use VMware...I don't really know it's setup but I'm sure there should be a similar way like in VirtulBox

Yes you can use any partition of your HDD that you'd like...given that it is mounted ofcourse.

When you create a new VM the setup asks you if you want to create a new virtual hard disk or use an existing one.

You have to choose create new hard disk.
The next setup dialog will be "Virtual Disk Location and Size"
For the location you can type the location of the partition that you want to use 
```
/media/name_of _the_partition
```

or choose from the drop down menu.

Just make sure that the partition you want to use is mounted.

---

### Post by MartyBuntu on 2011-03-10
Thank you for your help, but just to let you know, I'll be going with **virtualbox** instead of VMware.

I hadn't commited to anything up till now. An hour ago I installed virtualbox and plan on installing Arch and PC-BSD virtually.

My processor supports virtualization BTW. I hope it helps.
It's an Intel E6300 (the 2.8 Ghz version) and I have 4GB of RAM in the computer.

---

### Post by daniel_w93 on 2011-03-10
Yeah that should work out pretty good then.
I have 4Gb RAM as well and AMD-V support for my processor.
Works like a charm...I can even game in it.

---

### Post by matt_symes on 2011-03-11
Hi

If you are going to use VirtualBox and you want USB support get the PUEL version from their web site and not the version in the repos. 

Both VMWare and VirtualBox are excellent pieces of software. Your machine will handle them fine.

Kind regards

---

### Post by MartyBuntu on 2011-03-15
Okay...found out I can install virtual machines in other mounted physical drives. That's good to know. Debian install very nicely with Virtualbox!

---

