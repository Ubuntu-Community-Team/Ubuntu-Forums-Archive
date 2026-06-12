---
title: "Cant upgrade Virtualbox on Ubuntu 14.04.1"
date: 2014-09-14
forum: Virtualisation
---

### Post by xeddog on 2014-09-14
I have Ubuntu 14.04.1 running Virtualbox 4.3.10-dfsg-1 that was installed from the repos.  I have started having problems with one of my vms (Utopic) and noticed that the current version of Virtualbox is now at 4.3.16.  I followed the instructions on the Virtualbox web page for adding the deb entry to my sources.list, but it still won't upgrade.   Synaptic still shows 4.3.10-dfsg-1 as the latest version, and if I try to install it using the Software manager it tells me that it will break currently installed package virtualbox. . .

So, my question is this.  If I use synaptic to remove (NOT completely remove) my currently installed 4.3.10-dfsg-1 version of VB, and then re-install the 4.3.16 deb from Oracle, will I lose all of my virtual machines or will they still be preserved?

Thanks,

Wayne

---

### Post by Slim Odds on 2014-09-14
Your virtual machines live in a folder called "VirtualBox VMs" in your home folder. Removing the VirtualBox programs does not delete that folder and, of course, you've got that folder adequately backed up, right?

---

### Post by xeddog on 2014-09-14
Thanks Slim.  That is what I was thinking but what about all of the settings that were changed in the virtualbox settings like the number of processors to use, network settings being changed to bridged mode, etc.  I assume that those will be lost?  Those aren't a big deal but just curious.   

Wayne

---

### Post by bashiergui on 2014-09-14
> **xeddog said:**
> Thanks Slim.  That is what I was thinking but what about all of the settings that were changed in the virtualbox settings like the number of processors to use, network settings being changed to bridged mode, etc.  I assume that those will be lost?  Those aren't a big deal but just curious.   

WayneThose setting live on each VM. So no you won't lose them.

---

