---
title: "Backup a whole running server or pack it into a VM"
date: 2011-10-22
forum: Server Platforms
---

### Post by Zoxa on 2011-10-22
Hello,

I have a Ubuntu 10.04.1 64bit server. And it would be very handy now if I had a copy of it in a VM for testing.
My first try now was to get the job done with VMWare Converter but the latest server version for Linux (which is 4.0.1) doesn't work with 64 bit and it seems there is no workaround (you cannot login due to a missing lib32/security/pam_unix.so file [*link*]("http://communities.vmware.com/message/1412749")). And the VMWare Converter 5 is only available for Windows. It has a feature to convert Linux machines via remote SSH but unfortunately it doesn't work with RAID1 which my server has of course... There is also no workaround.

So now I was wondering if there is any other ubuntu server tool which can dump an image of a whole file system of a running server. Converting such an image into a VM would probably be easier than the direct way.
Or are there any other options?

I would be grateful for help!

---

### Post by vasile002 on 2011-10-23
the other option is to install the OS into the VM and migrate all the files/settings manually from the old one

---

### Post by SeijiSensei on 2011-10-23
rsync is the simplest method to copy over the files once you've got the VM image up and running.

---

### Post by koenn on 2011-10-23
there's a couple of things you can do as an alternative to a "P2V"

one is to set up a vanilla install of the same OS, then rsync all files from the production machine to the test machine. Linux is very file-oriented, so this just works.

There's a few caveats :
- you probably want some data to be unique, those will have to be modified by hand afterwards (IP addresses, hostname, ...). disks identified by GUIS '/etc/fstab, ...) will need tweaking too;
- you don't want runtime or hardware-specific files (/proc, /dev ) and you'll want to make sure that the kernel of your production system is compatible with the hardware of your test machine (for the latter, having both production and test on identical hypervisors helps)
- as rsync does file copy, this appoach will not clone your underlying disk infratsructure, you may have to handle that separately, and in advance.

example: if your src machine's filesystem is mounted from 2 partitions, you will not get the same arrangement on the dest system, unless it already had e similar disl/partition layout with the partitions mounted as on the src system, so the files will end up on the corresponding disks. 
Likewise for NFS mounts etc.

If tried this once, between 2 VM's. It worked. 
Notes here : [http://users.telenet.be/mydotcom/howto/linux/clone.htm](http://users.telenet.be/mydotcom/howto/linux/clone.htm)


--
Another appoach is to use dd to clone your disks, on the assumption that if you can boot a system from cloned disks, that system will be identical to the system you cloned from.

dd can do block-level copies so the mountpoint stuff might get easier but you might have to pay attention re. your RAID conf.

I'm not quite sure you can dd straight into a .vmdk file (maybe you should just giove it a try :) ), you might have to attach some .vmdk files to a VM that you dd to through a networked pipe. 

looks something like this:
```
dd if=/dev/something | ssh username@btestserver "dd of=/dev/whatever"
```

this might require some creativity in what you mount where and how to avoid having to dd from or to a mounted root filesystem
see also [http://karlherrick.com/dev/2008/09/12/dd-backups-over-ssh/](http://karlherrick.com/dev/2008/09/12/dd-backups-over-ssh/)


--
yet another approach : mimic the 1st in stall  as closely as posible, with tools to automate large parts of it (more work, but more flexibility)
[http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)

---

### Post by jesuspresley on 2011-10-29
I have a similar task here. Need to migrate my hosted Ubuntu 8.04 virtual server to a clean Ubuntu 10.04 install. I am not sure if the dd variant will work here. Is it possible to upgrade the 8.04 one, then copy the whole disk? 

As I basically need Apache with multiple domains (TYPO3 and Wordpress) and Ruby on Rails (Redmine) I think this whole task should be possible within 7 days?

---

### Post by koenn on 2011-10-29
> **jesuspresley said:**
>  Need to migrate my hosted Ubuntu 8.04 virtual server to a clean Ubuntu 10.04 install. 

Is it possible to upgrade the 8.04 one, then copy the whole disk? 

As I basically need Apache with multiple domains (TYPO3 and Wordpress) and Ruby on Rails (Redmine) I think this whole task should be possible within 7 days?

It's one thing to back up a server to a quasi-identical machine, or to convert a physical server to a vm; it's a completely different thing to upgrade a server or move it to a different OS version. 


For cases like yours, you'd install an OS + all the software you need, then try to migrate your configuration and data. That implies you know where your data is, and where your configurations deviate from the distribution defaults. 

That, in turn, is something you keep in mind while setting up a system - you know you'll probably be upgrading/migrating at some point, so you factor that in in the decisions you make when setting up your current system. 
It's also something you plan for : you keep track of where your data is and what configuration you customize, and you think about how to restore it (for migrations, but also for recovery etc.) 


Yes, you can just copy files into the new system. If you copy too much, you'll have  8.04 specific files on a 10.04 system. 
The copying will take far less than 7 days, debugging might well take a lot longer than that.

---

### Post by haqking on 2011-10-29
use clonezilla to clone your server to an image and then clone it back into a equal size or larger Virtual machine.

---

### Post by collisionystm on 2011-10-29
> **haqking said:**
> use clonezilla to clone your server to an image and then clone it back into a equal size or larger Virtual machine.

+1 

This is what I would do if Vmware would not work.

---

