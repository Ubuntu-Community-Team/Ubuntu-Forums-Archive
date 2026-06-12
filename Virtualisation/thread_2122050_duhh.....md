---
title: "duhh...."
date: 2013-03-03
forum: Virtualisation
---

### Post by mayagrafix on 2013-03-03
Im running VM for the first time. I get the following message:
> 
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I checked for DKMS and it is already installed. I tried to execute '/etc/init.d/vboxdrv setup' and bash responded: no such file or directory. I looked in $/etc and found no directory named init.d
Also the "First Start Wizzard" which would ask me for installation media did not appear.
Thanks for any and all help you may kindly provide-:KS-

---

### Post by ibjsb4 on 2013-03-04
First, just to be clear.  Thats the "dkms" package you have installed and not the "virtualbox-dkms" package.

You did not say, but sounds like you installed from the software center.  If so, I would suggest installing from the vBox site.  For me, it just seems to work better.  Just follow the instructions and add it to your "sources.list".

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

This works well for me on 12o4.  If your using 12.10 there could be other issues, 12.10 does not seem to play nice with vBox.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=virtualbox+ubuntu+12.10&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=virtualbox+ubuntu+12.10&sa=Search&cof=FORID:9)

---

### Post by mayagrafix on 2013-03-04
Thanks for the info, this thread seemed to have the answer:

[http://ubuntuforums.org/showthread.php?t=2082194](http://ubuntuforums.org/showthread.php?t=2082194)
in particular these two command lines:

[COLOR="#008000"]sudo apt-get install dkms build-essential linux-headers-generic
sudo /etc/init.d/vboxdrv setup[/COLOR]

after running these VM started up and runs good.

---

### Post by ibjsb4 on 2013-03-04
Good deal :)

[sudo /etc/init.d/vboxdrv setup] is a good general fix-all command for vBox.

Don't forget to mark your thread solved

---

