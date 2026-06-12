---
title: "Ubuntu Server Boot Error"
date: 2016-03-15
forum: Server Platforms
---

### Post by Brandon_Wilson on 2016-03-15
[COLOR=#111111][FONT=Ubuntu]Yesterday a power failure caused our VMWare ESXi server to shutdown. After the host came back online this Ubuntu server did. I get this error message right after the boot selection menu. I have tried booting into recovery mode from the advanced menu but I get the same result. What other options do I have to resolve this? This is our home to our MySQL database and of course there are no recent backups.

[/FONT][/COLOR][IMG]http://i.stack.imgur.com/PbfXL.png[/IMG]

---

### Post by darkod on 2016-03-15
This doesn't say much. Is it possible the messages are part of vmware and not ubuntu? Are all other vmware VMs working correctly?

Also, have you tried booting the VM with the desktop live iso in live mode and trying to run a fsck on the root partition?

---

### Post by wellsilva-email on 2016-03-15
Brandon, Hello,

Seems like some OS file(s) got corrupted so, you will need to rebuild your Linux installation. Inside a VM you won't have a hardware problem.  I don't know your current level of Linux knowledge  but, usually, you will be able to access your old files and recover them to a new machine.

Without a backup from  both your system files and your database, you will take more time to recover from this failure.

I would say to you to follow these steps to a clean new install avoiding the destruction of your data:
 - dissociate your current hard drives from the vm
 - associate new ones with equal size
 - install the same ubuntu version, install vmware tools and apply upgrades if you did after your installation ( usually it's OK to do it anyway). 
 - associate the disks again and mount the filesystem in a directory. e.g.: /mnt/disk1,  /mnt/disk2  ... /mnt/disk(n)
 - now you have access to your old configuration files, so you can copy them, both for database and the OS
 - copy your database data files to the new disks. By default, if you didn't put in different partittions, they're are under (mount point of old disk)/var/lib/mysql

This is a general strategy and that you can try to get your database back. At least you will have the configuration and this old backup you've mentioned.

After this, consider to have incremental backups and to add a slave node to avoid this long restore process ( and less worries ).

Hope to have helped, let us know if you need anything else.

---

### Post by wellsilva-email on 2016-03-15
> **darkod said:**
> This doesn't say much. Is it possible the messages are part of vmware and not ubuntu? Are all other vmware VMs working correctly?

Also, have you tried booting the VM with the desktop live iso in live mode and trying to run a fsck on the root partition?

Yeah, boot from ubuntu cdrom and try this first, before trying the recovery procedure. 

It can save you many times.

---

### Post by Brandon_Wilson on 2016-03-15
I have booted into ISO image and which option should I choose? I tried the recover failed system and fsck command but it states that it doesn't exist. I am not an advanced Ubuntu user, I only know a few things.

---

### Post by darkod on 2016-03-15
If you boot the desktop ISO when it asks you if you want to Try Ubuntu or Install Ubuntu, select Try and let it load live mode. Note, we are talking about the desktop ISO, not server. The server has no live mode.

I don't know what you mean by "recover failed system". The recovery mode entry in the grub boot menu? Anyway, to run fsck the partition has to be unmounted, so you have to be running from live mode ISO.

---

### Post by Brandon_Wilson on 2016-03-15
This is a server ubuntu, any advice for the server version.

---

### Post by darkod on 2016-03-15
I understand what we are talking about Brandon, but you are missing my point... There is nothing saying you can't take the ubuntu desktop CD and boot in Try mode (not install) a server machine and try to fix it. In fact, that is one of the options that you have when the server is unbootable.

So, download the desktop iso, make a cd or usb with it, boot it into Try mode, open terminal and you can work from there. It will be able to see the HDDs in the machine so you can run the filesystem checks... And many more things...

PS. In your case because this is a VM, you can attach the iso as cd-rom and set the VM to boot from cd-rom first. That way it will boot from the iso and you can work...

---

