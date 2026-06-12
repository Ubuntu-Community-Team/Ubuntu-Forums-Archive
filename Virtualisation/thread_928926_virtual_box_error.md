---
title: "virtual box error"
date: 2008-09-24
forum: Virtualisation
---

### Post by joey-elijah on 2008-09-24
Whenever i try to run Virtual box i get:

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

i have already gone into synaptic and installed the generic thingy for my kernel but still get no where.

Is this a simple fix? thanks!

---

### Post by Thelasko on 2008-09-24
Add yourself to the vboxusers group.

---

### Post by joey-elijah on 2008-09-25
errrrm.... where/how?

---

### Post by xebian on 2008-09-25
what it means is that you need to recompile the module for your new kernel.  Open a terminal, and execute this

```

sudo /etc/init.d/vboxdrv setup

```

---

### Post by Thelasko on 2008-09-25
> **joey-elijah said:**
> errrrm.... where/how?

[Try this.]("http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups#Modifying_an_Ubuntu_Linux_Group")

---

### Post by Therion on 2008-09-25
Best tutorial I've found on getting Virtual Box up and running under Ubuntu is [right here](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html).  I strongly suggest using the binary version of VB (versus the open source version you get in the repo, but that's up to you of course) that you can find [HERE](http://www.virtualbox.org/wiki/Downloads).  It's also the newest version of VB which includes about a TON of bug-fixes and some major updates.

---

### Post by joey-elijah on 2008-09-28
i've heard binary bites. Hmm. i'm all up for trying what's likely best. Getting this up and running would be awesome x lots.

i'll give the binary a try! thanks!

---

### Post by johnny5@5 on 2008-09-30
Another option too would be to download the guest modules for your kernel right from the synaptic package manager. Hope this might be of some help

---

