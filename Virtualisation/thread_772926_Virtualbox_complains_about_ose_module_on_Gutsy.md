---
title: "Virtualbox complains about ose module on Gutsy"
date: 2008-04-28
forum: Virtualisation
---

### Post by tomcat2007 on 2008-04-28
I have tried creating an XP virtual box under Hardy Beta, Hardy, and now Gutsy and each time when I start it, I get the following error.  I have added myself to the vboxusers group, the ose for kernel 2.6.22-14 (version 6) is installed.  Can someone give me some idea what is wrong and how to fix it?  Thanks!


******
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface:

---

### Post by tomcat2007 on 2008-04-30
I just tried to set up an XP partition with QEMU and am running into errors there too.  I create a virtual machine, give it 500 megs of RAM, 6 gigs of harddisk space, then boot the XP CD.  After it bombed a couple times, it got to the point of creating a partition, formatting to NTFS, and now an error is generating stating that Setup was unable to format the partition.

Now I don't consider myself the smartest person in the world, but I'm certainly not the dumbest.  Is there an issue with Virtual machines on HP dv9000 laptops?  I haven't been able to get a single virtual solution to work except for the preloaded, unconfigurable VMWARE machines.

---

### Post by GavinZac on 2008-04-30
from this similar thread:
[http://ubuntuforums.org/showthread.php?p=4821997#post4821997](http://ubuntuforums.org/showthread.php?p=4821997#post4821997)

> open a terminal and run this:

sudo apt-get install virtualbox-ose-modules-generic

or just do a search for "virtualbox-ose-modules-generic" in Synaptic Package Manager (System->Admin->Synaptic) and install that. It will automatically add the proper driver you need then.

---

### Post by tomcat2007 on 2008-05-01
Yup, I tried that one.  Still getting the same error ...

---

### Post by tomcat2007 on 2008-05-01
Well, just for laughs I reinstalled the module again, now it works.  To be perfectly honest, I'm extremely puzzled as to why it works because I already tried that... several times.  Wish I'd kept notes of everything I had done while tinkering around because it's likely that this whose scenario will repeat on the next clean install :lol:

Ah well, on to the next challenge!

---

### Post by Arthur Archnix on 2008-05-02
Is it me, or is it ridiculous that installing virtualbox through synaptic means not everything is installed that you need in order to run virtual machines. There are like twenty different module packages available in synaptic. Which one do I want on a Hardy system 386? I'm not exactly new to this, but this seems a bit silly to me that it doesn't pull in the correct module as a dependency.

---

### Post by Arthur Archnix on 2008-05-02
Ok, dystopianray on IRC helped me out.

I had the same error message as the original poster. After boot if you notice an error message in your dmesg than you might have the same problem as me. It's fixed by installing the right module. 

If you use 386 and Hardy then do this:
```
sudo apt-get install virtualbox-ose-modules-2.6.24-16-generic
sudo modprobe vboxdrv
```
[COLOR=#af7f00][SIZE=3][/SIZE][/COLOR]

---

