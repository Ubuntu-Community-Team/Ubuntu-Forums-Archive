---
title: "How to install VMware Server on Ubuntu"
date: 2009-10-12
forum: Virtualisation
---

### Post by Dedoimedo on 2009-10-12
Hi all,

Sounds like a trivial task, but it is not ...

Plus I found a few threads on this topic, many with partial or missing info, so I though about compiling it all into one flowing guide, with screenshots and all ...

I've written a detailed, step-by-step tutorial explaining how to install VMware Server on Ubuntu and overcome a variety of problems, including missing compilation tools, missing Xinetd super service, missing IA32 libraries, missing SSL certificate files, and running an update that patches the VMware sources and makes the building of the vmmon module possible.

This tutorial is a must for any virtualization fun. Follow me.

[http://www.dedoimedo.com/computers/vmware-server-ubuntu.html](http://www.dedoimedo.com/computers/vmware-server-ubuntu.html)


Comments and suggestions are welcome.

Regards,
Dedoimedo

---

### Post by fjgaude on 2009-10-12
Thank you, Dedoimedo, for your extensive effort that works for those who wish, can re-compile their kernels... I guess at this point, for Ubuntu 9.10 Beta, I'm not willing to even try.

Maybe by the time 9.10 is released the kernel, 2.6.31, will be fixed to permit an easier install of VMware Server.

---

### Post by GuerillaKilla on 2010-02-08
I have been having issues trying to install vmware server on ubuntu 9.10 64 bit.  I thought for sure when I saw this post my problems were soon to be over.  However, I'm still having some issues and was wondering if you had any ideas?

Current Kernel:
2.6.31-19-generic

Current Error:
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to make a vmmon module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config3/vmmon.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

---

### Post by TJet1.8 on 2010-02-13
Ok...first, lets make sure you have "all" the Linux components required to compile your modules:
sudo apt-get install gcc linux-headers-$(uname -r)

Then...follow these instructions for installing VMware Server 2.0.2 on Ubuntu 9.10:
[http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html)

Try it and let us know.

Good luck.

:p

---

### Post by Holla86 on 2010-02-26
Hello

I test vmware with the 2.6.31-19 ubuntu kernel and the patch from the site

[http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html)

and it works

Thanks

---

### Post by Krijk on 2010-03-11
Ever since I run 2.6.31 I had major issues. A lot of recompiling, inability of vmware to load the old datastore.

I stopped using VMware server altogether on 9.10. I think I'll wait until 10.04 LTS and hope that a stable VMware server build will appear.

---

### Post by Cliff21 on 2010-03-11
I ran into a couple of other issues that weren't described in the howto installing VMWare server 2.0.2 on Ubuntu 9.10 x32

I followed this howto:
[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)


Once installed, the mouse pointer and keyboard did not work in most of the screen, only the upper and left sections, even with vmtools installed. This required the following fix (copied below with a couple of clarifications/modifications:
[http://ubuntuforums.org/showpost.php?p=8745191&postcount=17](http://ubuntuforums.org/showpost.php?p=8745191&postcount=17)

> go into:
/home/**YOURUSERNAME**/.mozilla/firefox/**RANDOMSTRING_W_MOST_RECENT_DATE**/extensions/VMwareVMRC@vmware.com/plugins/lib

Then edit the file:
# sudo gedit wrapper-gtk24.sh      ; I can't remember if permissions needed to be changed to read/write

Add the following lines near the top:
VMWARE_USE_SHIPPED_GTK='force'
export VMWARE_USE_SHIPPED_GTK="force"
This fixed the mouse issue.



Upon reboot I would get a message stating:
When launching the virtual machine vmware spits out the error @ 95% completion stating: *Error while powering on: A general system error occurred: Cannot connect to the virtual machine.*
or *Failed to power on: A general system error occurred*

launching vmware from the command line required that I run 
**sudo /vmware-config.pl** after every reboot - not a great option to say the least, I found the following thread that dealt with the issue a "not_configured" file that is created on boot, it's a bit hackish, and won't alert you if you are running a new kernel, but it works.


[http://www.novell.com/communities/node/6798/allow-vmware-server-correctly-load-after-reboot-without-having-run-vmware-configpl-every-t](http://www.novell.com/communities/node/6798/allow-vmware-server-correctly-load-after-reboot-without-having-run-vmware-configpl-every-t)


I hope this helps someone going forward

---

### Post by alphasoup on 2010-03-13
I followed the same how-to and installed vmware 2.0.2 server -- with the patch as above. This was tried on several Ubuntu 9.10 -- this is 32 bits, tested on a P4 2.4GB hyperthreaded and on a dual core duo pentium 2GB.

I have run this vm 2.0.2 experiment for about 2 months on-and-off and I have given-up completely for my main usage via a rawDisk -- as totally unusable :(. The correct version of VMware tools was used in all the tests.

I have also tested USB and/or SATA for the raw disk, either on the same disk (different partition) or different disks than Ubuntu, same issue for all tests.

For me Vmware 2.0.2 is completely unstable to run a rawDisk windows XP pro guest.
The exact same image boots and run stable with VirtualBox (using a different hardware profile). However VirtualBox while much easier to use for a rawDisk configuration than vm2.0.2 is too slow on the 2 hardwares tested.

Having retried the same experiment with all the recent kernels all had the same problem: 2.6.31.16 up to 2.6.31.20, rawDisk Windows XP guest is unstable:
Windows will crash shortly after login via vmware 2.0.2 guest on Karmic Koala.

The same image now runs fine after un-installing 2.0.2 and reinstalling 1.0.10 on
a custom kernel based on 2.6.31 latest :cool:.

So if you have similar issue with 2.0.2 on Ubuntu 9.10 (e.g. for rawDisk), have a look at:
[http://www.howtoforge.com/how-to-install-vmware-server-1.0.x-on-an-ubuntu-9.10-desktop-p2](http://www.howtoforge.com/how-to-install-vmware-server-1.0.x-on-an-ubuntu-9.10-desktop-p2)

(In this configuration it is even possible from Ubuntu to use a Windows XP rawdisk guest on a USB disk with acceptable performance.)

---

### Post by dcstar on 2010-03-13
> **Krijk said:**
> Ever since I run 2.6.31 I had major issues. A lot of recompiling, inability of vmware to load the old datastore.

I stopped using VMware server altogether on 9.10. I think I'll wait until 10.04 LTS and hope that a stable VMware server build will appear.

Don't hold your breath, I cannot get Server 1.0.10 to work with the 2.6.32 kernel that is currently on the 10.04 Alpha release because it requires a full kernel recompilation to turn on an option that VMware server requires.

Having to do a full kernel compilation when an update arrives just to keep VMware server going is asking a bit too much.

I'm not 100% sure if server 2.0.x works with the 2.6.32 kernel yet, there seem to be some HOWTOs with various patch files around.

---

