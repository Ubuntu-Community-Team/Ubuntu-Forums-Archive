---
title: "trouble installing VMware 7 on Ubuntu 10.04.1"
date: 2010-09-23
forum: Virtualisation
---

### Post by tranquillo on 2010-09-23
Hi to all! 

i realy hope that i am posting this in the right section!!

like already mentioned in the title - i just can't get VMware 7 running on my pc!

my ubuntu version is Ubuntu 10.04.1 (kernel: 2.6.32-24-generic-pae)
my VMware version is VMware Workstation 7.0.0 build-203739

installing the *.bundle worked fine - i get no errors. i even find the VMware Workstation / Player / Virtual Network Editor under Menu --> System Tools.

launching the VM Workstation under the GUI the VMware Kernel Modules Updater starts - i all checks go well besides the "Virtual Network Device" and when it trys to start the services i get the error message "unable to start services"

running the vmware command via CLI i get the debug of the operation and this is what comes out:

Starting VMware services:
   VMware USB Arbitrator                                               done
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family                            done
   Blocking file system                                                done
   Virtual ethernet                                                   failed

what i tried:
- reinstalling vmware (dooh!)
- downloading a generic kernel image under synaptic (because i thought that the -pae was a problem)
- i recompiled my pae kernel adding all the VMware modules
- tried all kind of variations under the Virtual Network Editor

my ethernet is up and running and has no problem what so ever!

any ideas?

thanks!

PS if this problem was already solved - just please link me the forum entry :)

tranquillo

---

### Post by fjgaude on 2010-09-23
I can't say if it is the pae kernel or not, but when I run player from CLI I get:

```
frank@sunshine:~$ vmplayer
Logging to /tmp/vmware-frank/setup-4879.log
filename:       /lib/modules/2.6.32-24-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     ACC40DE2B6729C4323EBF14
depends:        
vermagic:       2.6.32-24-generic SMP mod_unload modversions 
filename:       /lib/modules/2.6.32-24-generic/misc/vmnet.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Networking Driver.
author:         VMware, Inc.
srcversion:     8635E7D0E853EB32F1B00DD
depends:        
vermagic:       2.6.32-24-generic SMP mod_unload modversions 
filename:       /lib/modules/2.6.32-24-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-24-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic/misc/vmci.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     A010E9D2C04943FA8178682
depends:        
vermagic:       2.6.32-24-generic SMP mod_unload modversions 
filename:       /lib/modules/2.6.32-24-generic/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     BC1943DCE52AE461DCC2D43
depends:        vmci
vermagic:       2.6.32-24-generic SMP mod_unload modversions 
filename:       /lib/modules/2.6.32-24-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     ACC40DE2B6729C4323EBF14
depends:        
vermagic:       2.6.32-24-generic SMP mod_unload modversions 
```

Maybe someone else has run across this issue, I have not.

---

### Post by Fableflame on 2010-09-23
Regrettably, I have no idea.
But I hear that VirtualBox works better than VMware

---

### Post by tranquillo on 2010-09-27
i just tried the VirtualBox 3.2.8 Edition - it looks nice! BUT!!! it does not import my *.vmx files - witch is a bad thing.

to clear my doubt about the installation and kernel i tried to install VMWare 7 on a older notebook - i get the same error.

realy nobody can help? nobody is using VM Ware 7 on Ubuntu?

tranquillo83

---

### Post by fjgaude on 2010-09-27
Well, from what I've seen the latest update to the Ubuntu kernel breaks all the latest versions of VMware, server and player.

We have to notify vmware.com of the issue.

---

### Post by tranquillo on 2010-09-28
hmm.. before going through the troubble.. do you think if i use a older kernel it would work?

thanks

tranquillo83

---

### Post by fjgaude on 2010-09-28
Likely... but you have to go back to the kernel used in Ubuntu 9.04, or even 8.10... that's when Server had to be patched differently, and when Player 3.0.0 came out that was used instead of Server.

Player 3.1.1 worked on all updates to the kernel until about two weeks ago, when 2.6.32-22 came out. I've lost track. Now with Ubuntu 10.10 we have even another story, kernel 2.6.35... I can't say if and when VMware will alter their code to handle the newer kernels.

---

### Post by cenwesi on 2010-09-28
I pretty much gave up on vmware for ubuntu/linux. It seems every kernel that comes out, vmware doesn't work and vmware.com is slow or even willing to fix the problem. VBox is pretty sweet and it just works. Give it a try and go headless :)

---

### Post by saket3143 on 2010-09-28
VMWare does not support pae 
if u remove the pae version and install the normal one vmware will install without any problems

---

### Post by tranquillo on 2010-09-30
that's what i thought too... but pae is not the problem! i did 2 tries to remove the doubt.. 

1. downloading and compiling a generic kernel 
2. installing ubuntu on a older hardwhare that installed the generic kernel as defaul 

= still does not work.

i do not want to use an older kernel for a few reasons. 

im willing to give vbox a try, already got it up and running! does anybody know if vbox has a converter? i have very important VM's in vmx that i need to run! i googled about it - but no one that i found converts vmware 7!! anything?

thanks

tranquillo83

---

### Post by netlynx on 2010-10-01
Hey all,

   I can't say that I VMware Workstation 7 will work, however I have used the following setup for VMware Server 2.0.2 on Ubuntu 10.04.1 with success (and I am running a PAE kernel on the server):

[http://www.howtoforge.com/vmware-server-2.0.2-x-on-ubuntu-server-10.04-with-vmware-remote-console-plug-in](http://www.howtoforge.com/vmware-server-2.0.2-x-on-ubuntu-server-10.04-with-vmware-remote-console-plug-in)

   And what looks to be a variation of those instructions can also be found at:

[http://communities.vmware.com/thread/267682](http://communities.vmware.com/thread/267682)

Unfortunately I do not use workstation myself, so I am unable to give any help with that, but this may be something you can work with.

Peace!
Aaron
------
HP Proliant DL580 G2
(32 GB Ram - 4.5 TB HDD - Ubuntu Server 10.04.1)

---

### Post by cppdeveloper on 2010-10-11
Just came across this discussion and thought to give some feedback.

I have been using the latest VMWare Workstation with Ubuntu since VMware 6.5.x at least, with no problems as far as I remember.

I am currently running VMware Workstation 7.1.2 on Ubuntu Linux Desktop Edition 10.04.1 x64, with no problems.

---

