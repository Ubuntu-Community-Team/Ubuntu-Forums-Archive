---
title: "help installing vmware player"
date: 2008-05-14
forum: Virtualisation
---

### Post by El-ahrairah on 2008-05-14
Hi to all! :D

I hope this is the right place to post... I recently installed ubuntu 8.04 (which is very good, IMHO :D) but I have a problem while installing vmware player:

I have downloaded the tar file from vmware.com, extracted it and lauched the install.pl, and all went ok... then, when running the config.pl, I get an error that says that it cannot find prebuild module for my kernel, and asks if I want to compile them directly. If I say NO, the configuration ends... If I say YES, it gives me an error while compiling! :(

what can I do to have it installed and working?

I use ubuntu 8.04 with 2.6.24-17 kernel

thanks in advance.

---

### Post by Het Irv on 2008-05-14
I have had alot of trouble installing VMware on Ubuntu, in fact I have never gotten it to work.  If no one can help you, I would suggest VirtualBox, avalible in Add/Remove.  It does the samething as VMware, just as good.

---

### Post by quelx on 2008-05-14
You need a patch for vmware

[http://groups.google.com/group/vmkernelnewbies/files](http://groups.google.com/group/vmkernelnewbies/files)

use vmware-any-any-update-116.tgz, extract it and change into the vmware directory and ```
sudo ./runme.pl
```

try the installation again

```
sudo /usr/bin/vmware-config.pl
```

If this doesn't work paste the error message into this thread so we can have a looksee

---

### Post by El-ahrairah on 2008-05-14
thanks for the advice :D I'll give it a try, if it doesn't work, I'll switch to virtualbox

EDIT: here is what I get with the patch

```
Building the vmmon module.

Unknown VMware Workstation 6.0.3 build 80004 detected. Building for Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

:(

---

### Post by El-ahrairah on 2008-05-14
> **Het Irv said:**
> I have had alot of trouble installing VMware on Ubuntu, in fact I have never gotten it to work.  If no one can help you, I would suggest VirtualBox, avalible in Add/Remove.  It does the samething as VMware, just as good.

I searched in the add/remove menu, but I can't find it...

---

### Post by quelx on 2008-05-14
You need the gcc compiler, so do this then run the ./runme.pl file again

```
sudo apt-get install gcc build-essential
```

That should be the last of the dependencies

FWIW virtualbox is **virtualbox-ose** in apt/synaptic

---

### Post by bodhi.zazen on 2008-05-14
I suggest VMWare server.

There is a how-to at the top of this forum. Includes links and brief but specific instructions.

Link : **[B]Sticky:**[/B] 			                          			 			[How to VMWare in Ubuntu 8.04]("http://ubuntuforums.org/showthread.php?t=779934")

Works just fine in 8.04 for *most* people.

---

### Post by Oldsoldier2003 on 2008-05-14
> **quelx said:**
> You need the gcc compiler, so do this then run the ./runme.pl file again

```
sudo apt-get install gcc build-essential
```

That should be the last of the dependencies

FWIW virtualbox is **virtualbox-ose** in apt/synaptic

FWIW don't bother installing virtualbox from the repositories. The VirtualBox Puel Edition available at their [website]("http://www.virtualbox.org/") is much better.

---

### Post by tighem on 2008-05-14
VMWare player installs issue free in Hardy if you have the build tools install. VMWare server has lots of issues.

I would also recommend Virtualbox, but NOT 1.6 unless you're comfortable disabling kernel modules as KVM & VB 1.6 causes Hardy to lock up hard.

---

### Post by El-ahrairah on 2008-05-15
> **quelx said:**
> You need the gcc compiler, so do this then run the ./runme.pl file again

```
sudo apt-get install gcc build-essential
```


It worked :D I had the gcc installed, but I was missing the build-essential... now it seems to be working correctly, I'll discover it as I finish download the fedora image...

EDIT: but, in the end, what would be better, between virtual box and vmware? is there a WinXP Pro image for vmware?

---

### Post by El-ahrairah on 2008-05-16
I managed to install vmware player correctly... then, I downloaded a fedora 7 image for it, and the first times I used it, there were no problem at all... now, I have started working with it, and the boot time has increased greatly, like, ten times!!!

how is this possible?

thanks for help

EDIT: this is incredible!!! I have launched the virtual machine more than 20 minutes ago, and the boot is still going, the login screen hasn't appeared yet!

---

### Post by Shazaam on 2008-05-16
It could be a corrupted image. Or you have allocated too much memory to the vm. A good rule of thumb is to allocate no more than half of your actual memory. So if you had 1gig of physical memory you would allocate 512meg to the vm.
BTW, here is a good site for making vmx's for VMware Player....
[http://www.easyvmx.com/](http://www.easyvmx.com/)

---

### Post by El-ahrairah on 2008-05-17
the fact is that the image was working greatly until yesterday, with 2 minutes of boot time... now, it takes ages to boot, but in the beginning, it didn't!

Could I have somehow corrupted it by working with it? I just installed openldap on it...

and about memory, it has 256 MB of physical memory... as stated by the player itself, this is the recommended value, with a lower bound of 32 MB and an upper bound of 512 MB... could it help if I raise it up to the upper bound?

---

### Post by bodhi.zazen on 2008-05-17
There are a number of possibilities and I will  warn you guest OS can "implode" on VMWare / VirtualBox / or QEMU.

Best keep the backed up.

I advise you re-download the image to see if that may be the problem.

Otherwise I advise you go with VMWare server or VirtualBox, both allow you to create yow own guests.

---

### Post by El-ahrairah on 2008-05-17
ok, thanks you all for the advices :D now, I have tried upgrading the physical memory dedicated for the virtual machine to 512 MB and also I have restored the authentications settings which I previously modified to their original settings. Now the virtual machine restarted working correctly.

Now, last question (at least, I hope so :D): what is the difference between bridged networking and nat networking? which one is "best"? I tried setting it to bridged, but it seems to be not working, perhaps it is just me not knowing what I have to do to make it work properly. Nat networking is working fine.
Also, I have 2 net interfaces on my pc (a cable and a wireless one), but in the guest OS there is only one, which seems to be used to emulate both my physical devices. Is this correct?

---

### Post by Fintan on 2008-05-19
For those who are interested here is a link to my updated thread on the kubuntu forum:
[http://kubuntuforums.net/forums/index.php?topic=3090895.0]("http://kubuntuforums.net/forums/index.php?topic=3090895.0")

Pay attention to the "official" vmware soltution:)
Hope it helps:)

---

