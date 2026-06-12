---
title: "Installing Vista from HP Recovery DVD?"
date: 2008-03-23
forum: Virtualisation
---

### Post by Jugney on 2008-03-23
Hi all,

I have an HP laptop that came with Vista and a few months ago wiped it and just went with Ubuntu. However, Im finding there are still a few times I need to use Windows (and when WINE doesnt work). 

I have the HP recovery DVD which will return the laptop to factory condition. Is it safe to use this to install Vista through VirtualBox? I imagine it won't touch my Ubuntu, but I want to make sure!

Thanks,
Jugney

---

### Post by SpenceMakesSense on 2008-03-23
well the problem you might get is that it doesnt install to a partition but just your entire hardrive, which then you might want to reinstall vista with a regualr disc and not a recover disc, which after that you would need to reinstall grub, which is easy ;D

---

### Post by Existentialist on 2008-03-23
I installed xp in virtualbox with an hp recovery cd without any issues.  As long as it is bootable media it should work.  As long as you are not booting the computer from the drive, and only mount it in virtualbox, it wont touch your ubuntu install since it is not visible to the virtual drive.

---

### Post by Jugney on 2008-03-23
Hi there,

Thanks for the reply - this is what I thought. So now when I try to boot in VirtualBox from the recovery disks, after a few minutes I get this message:

"Error

This PC is not supported by the System Recovery Disks

You will not be able to recover this system with these disks."

Any thoughts on this? I deleted my HP recovery partition when I deleted windows, however from reading other forums people seem to think this isnt the problem.

Jugney

---

### Post by SpenceMakesSense on 2008-03-24
>>>accidently posted twice(not a good day for me huh?)

---

### Post by SpenceMakesSense on 2008-03-24
oops sorry didn't read the whole thing, didn't notice you were attempting a virtual box install (sorry)

VirtualBox really has nothing to do with whats on your actually hardrive unless your sharing folders, which you havent gotten it installed yet so that wouldn't be a problem yet.

From what it looks like the Recovery discs are looking for the specific hardware inside the computer(like a certain motherboard) Which in virtual box it all the hardware is "virtual" hardware so its called something like vbox graphics card ect. So there is most likely no way of getting it to install via virtual machine. It assumes you rtrying to get people free windows most likely(whats wrong with people sharing OS's??)

You may be able to check the specs of the computer and make them match in the virtual machine. For instance telling it to have 512 ram which is how much ram your computer has. Along with the graphics card. 

Other than that sounds just like a M$ thing to pull and not let you install them unless you have the same exact hardware.

---

### Post by dcstar on 2008-03-24
> **Jugney said:**
> Hi there,

Thanks for the reply - this is what I thought. So now when I try to boot in VirtualBox from the recovery disks, after a few minutes I get this message:

"Error

This PC is not supported by the System Recovery Disks

You will not be able to recover this system with these disks."

Any thoughts on this? I deleted my HP recovery partition when I deleted windows, however from reading other forums people seem to think this isnt the problem.

Jugney

To prevent copying fraud, these disks are set to only install on specific hardware, and a VM is not that hardware.

You can use them to wipe your system and install the default Windows, then you can copy that install to a VM (if your VM system has those tools, like VMware has).

---

### Post by Existentialist on 2008-03-24
What you really pay for when buying windows is your license.  The license will work for any install of that same version of windows (ie. home premium, ultimate).  So if you obtained an install cd of the same version your laptop came with, you could use your key for the install (works with xp, somebody correct me if this changed with vista).  Of course I am not advocating any illegal way of doing this, and installing and running multiple copies of windows simultaneously with the same key is a violation of copyrights.

---

### Post by Jugney on 2008-03-29
Hi everyone,

THanks for the responses. I ended up torrenting a copy of Vista Home Premium online (the same version my laptop came with) and installing it in VB using my license key. It worked perfectly, and I feel there's no legality issue because I have a valid license and am only running one version on my computer. (Plus their EULA now allows virtualized usage of Home Premium, though I would have done it anyway...)

Thanks for your help! Now I'm just working on getting remote access to a Mac to work...If any of you can help please stop on by that thread: 
[http://ubuntuforums.org/showthread.php?t=733396&highlight=jugney](http://ubuntuforums.org/showthread.php?t=733396&highlight=jugney)

Jugney

---

