---
title: "Virtual Box - Kernel driver not installed"
date: 2010-06-09
forum: Virtualisation
---

### Post by forza.stiinta on 2010-06-09
Hello!

I am having this issue. It used to work fine, but this morning I updated virtualbox and when I start the virtual machine I get this error:

```

Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

I executed the suggested command, it does fix the problem, i.e. it starts the virtual machine and all runs fine. But when I restart the computer, I get this error again. Basically, I have to run vboxdrv setup each time I turn on the computer...

Any suggestions?

---

### Post by TransitMan on 2010-06-09
Just do a re-install of VirtualBox. It will make the needed corrections and then on restart, you won't be greeted by this error.

---

### Post by forza.stiinta on 2010-06-10
I installed and reinstalled several times. The same. I use synaptic for uninstalling...

---

### Post by forza.stiinta on 2010-06-10
I tried unistalling all packets related to virtualbox. No luck. The same. I also put version 3.1 then 3.2, all bring up the same error... I appeared when I upgraded from 3.1 to to 3.2.

---

### Post by TransitMan on 2010-06-10
Did you download the i386 version or the amd64 version?
And what version of Ubuntu are you using?

---

### Post by forza.stiinta on 2010-06-10
i386 and I am using 10.4 (32 bits version)

---

### Post by TransitMan on 2010-06-10
Are you using the package from Synaptic or the one from Oracle?

This is the latest one from Oracle - [http://download.virtualbox.org/virtualbox/3.2.4/virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb](http://download.virtualbox.org/virtualbox/3.2.4/virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb)

Uninstall VirtualBox via Synaptic, close it out, double click on the latest download and then test to see if this cures your problem.

---

### Post by BobLand on 2010-06-10
I've been running VB for a few weeks.  When I did an Ubuntu upgrade this morning, my Virtual Box locked up the system.  This is the first time in 3 years that I've experienced a lockup.  I've downloaded the latest version of VB from the Oracle site but still get the lock up.

At this point, the programs I'm running on VB are more important then Ubuntu.  Last week, my wife's machine refused to run Lucid so she abandoned it because of work issues.  Looks like I'm next.

With the release of Lucid, I'm losing faith in Ubuntu as this is not the only problem I'm having.

---

### Post by BobLand on 2010-06-11
Turns out I had a badly installed DDR, which was my fault.  Once I resolved the installation everything is working fine.  

My bad.  Apologies for the noise.

bobland

---

