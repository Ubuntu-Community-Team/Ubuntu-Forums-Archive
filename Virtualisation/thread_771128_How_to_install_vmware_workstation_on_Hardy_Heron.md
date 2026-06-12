---
title: "How to install vmware workstation on Hardy Heron?"
date: 2008-04-27
forum: Virtualisation
---

### Post by pengko.eo on 2008-04-27
hello there. i am a newbie of hardy heron. i tried following the tutorial from:
[http://blog.zmang.com/installing-vmware-workstation-65-beta-on-ubuntu-hardy-heron-804-faqs/#comment-4878](http://blog.zmang.com/installing-vmware-workstation-65-beta-on-ubuntu-hardy-heron-804-faqs/#comment-4878)

The thing is when i try to untar the file, the terminal gave me a feedback of this?
tar: VMware-workstation-e.x.p-84113.i386.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

could you please help me? thanks a lot

---

### Post by olskar on 2008-04-27
Try putting the file in your homefolder and try again.
Or you could rightclick the file and unpack it from there (which is what the command does)

Or you could try the excellent free VirtualBox on [www.virtualbox.org](www.virtualbox.org) :)

---

### Post by Julius on 2008-04-27
I installed it with

tar xvzf filename.tar.gz
cd vmware-distrib
and then
sudo ./vmware-install.pl

(maybe I messed up the file names but it was like that!)

---

### Post by ghost_ryder35 on 2008-04-27
> **Julius said:**
> I installed it with
 
tar xvzf filename.tar.gz
cd vmware-distrib
and then
sudo ./vmware-install.pl
 
(maybe I messed up the file names but it was like that!)
Its a little more complicated now because it does not compile correctly with the current kernel so there is some patches for "vmmon" amound other things that are necessary to get it to work.

---

### Post by coloured on 2008-04-27
Can anyone post a link to the fixes to get it to compile with the Hardy kernel?
also - I have never used virtualbox, I read through the documentation, but its not like taking it for a test drive. I use Vmware for work - and am constantly changing the networking options on a guest from NAT to Bridged to Host only etc.... can virtualbox change these options just as easily?

cheers

---

### Post by ghost_ryder35 on 2008-04-27
> **coloured said:**
> Can anyone post a link to the fixes to get it to compile with the Hardy kernel?
also - I have never used virtualbox, I read through the documentation, but its not like taking it for a test drive. I use Vmware for work - and am constantly changing the networking options on a guest from NAT to Bridged to Host only etc.... can virtualbox change these options just as easily?
 
cheers
[http://communities.vmware.com/thread/137477](http://communities.vmware.com/thread/137477)
 
[http://groups.google.com/group/vmkernelnewbies/files](http://groups.google.com/group/vmkernelnewbies/files)
 
[http://communities.vmware.com/community/beta/workstation6.5](http://communities.vmware.com/community/beta/workstation6.5)
 
[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

---

### Post by pengko.eo on 2008-04-29
Does anyone know how to solve this?

when running sudo ./runme.pl, i got this message from the terminal:

Unable to open the installer database /etc/vmware/locations in read-mode.

Execution aborted.

how should i fix this? thanks a lot

---

### Post by bmwman on 2008-04-30
Which version of Vmware Workstation you're trying to install?? I used VMware.Workstation.v6.0.3.80004 and did the following changes. Worked like a charm. I've tried installing Vmware server and workstation 6.5beta but have had so many issues with all of them. Here is how i did mine, very simple:

..........................................................................
Good news Linux kernel 2.6.24.x users! VMware Workstation v6.0.3 build 80004
can be made to build on the current stable kernel (at the time of this writing,
the current stable version is 2.6.24.3). However, it needs a little hacking to
make work so please observe the following instructions;


1) untar the VMware Workstation distribution provided by this torrent

EXAMPLE:
tar xvf /path/to/the/file/VMware-workstation-6.0.3-80004.i386.tar.gz


2) move to the directory containing vmmon module source

EXAMPLE:
cd ./vmware-distrib/lib/modules/source


3) untar vmmon.tar

EXAMPLE:
tar xvf ./vmmon.tar


4) apply the following sed

DO THIS:
sed -i 's/asm\/bitops.h/linux\/bitops.h/' ./vmmon-only/include/vcpuset.h


5) Repackage the vmmon tarball

EXAMPLE:
rm ./vmmon.tar && tar cf ./vmmon.tar vmmon-only/


6) return to top level directory

EXAMPLE:
cd /path/to/vmware-distrib


7) build the package

sudo ./vmware-install.pl *OR*

su (requires root password)
./vmware-install.pl

THE PROBLEM:
^^^^^^^^^^^^
The exact problem is in the file vcpuset.h, located inside the vmmon.tar file
under the directory "vmmon-only/lib/modules/source/include". On line 74 of
vcpuset.h you will find:

#include "asm/bitops.h"

This *must* be changed to:

#include "linux/bitops.h"

Before the vmmon kernel module will compile. This was tested and works on Ubuntu 8.04
...........................................................................
Good luck!

---

### Post by highpitch on 2008-05-03
> **bmwman said:**
> Which version of Vmware Workstation you're trying to install?? I used VMware.Workstation.v6.0.3.80004 and did the following changes. Worked like a charm. I've tried installing Vmware server and workstation 6.5beta but have had so many issues with all of them. Here is how i did mine, very simple:

..........................................................................
Good news Linux kernel 2.6.24.x users! VMware Workstation v6.0.3 build 80004
can be made to build on the current stable kernel (at the time of this writing,
the current stable version is 2.6.24.3). However, it needs a little hacking to
make work so please observe the following instructions;


1) untar the VMware Workstation distribution provided by this torrent

EXAMPLE:
tar xvf /path/to/the/file/VMware-workstation-6.0.3-80004.i386.tar.gz


2) move to the directory containing vmmon module source

EXAMPLE:
cd ./vmware-distrib/lib/modules/source


3) untar vmmon.tar

EXAMPLE:
tar xvf ./vmmon.tar


4) apply the following sed

DO THIS:
sed -i 's/asm\/bitops.h/linux\/bitops.h/' ./vmmon-only/include/vcpuset.h


5) Repackage the vmmon tarball

EXAMPLE:
rm ./vmmon.tar && tar cf ./vmmon.tar vmmon-only/


6) return to top level directory

EXAMPLE:
cd /path/to/vmware-distrib


7) build the package

sudo ./vmware-install.pl *OR*

su (requires root password)
./vmware-install.pl

THE PROBLEM:
^^^^^^^^^^^^
The exact problem is in the file vcpuset.h, located inside the vmmon.tar file
under the directory "vmmon-only/lib/modules/source/include". On line 74 of
vcpuset.h you will find:

#include "asm/bitops.h"

This *must* be changed to:

#include "linux/bitops.h"

Before the vmmon kernel module will compile. This was tested and works on Ubuntu 8.04
...........................................................................
Good luck!


Will this work with 6.0.2? :popcorn: I am using VM Workstation 6.0.2. It was working in Ubuntu 7.10. Stop working after the kernel upgrade (to Hardy Heron). Sorry, I'm a Windows->Ubuntu newbie.

Here's the error message that I got. Regardless what I do, at the end, it always says "Unable to build the vmmon module". 

> Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config7/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config7/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:83:
/tmp/vmware-config7/vmmon-only/./include/vm_basic_types.h:170: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
In file included from /tmp/vmware-config7/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:84:
/tmp/vmware-config7/vmmon-only/./include/x86cpuid.h:383:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config7/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config7/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:84:
/tmp/vmware-config7/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config7/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config7/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config7/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:84:
/tmp/vmware-config7/vmmon-only/./include/compat_wait.h:60: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:65: error: previous declaration of &#8216;poll_initwait&#8217; was here
/tmp/vmware-config7/vmmon-only/linux/driver.c:198: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config7/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config7/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Any help is appreciated.

---

### Post by highpitch on 2008-05-03
Never mind. I installed VMWare workstation 6.0.3 by following bmwman's guide. It works. Thank you! :guitar:

---

### Post by mrtrevin on 2008-05-07
Thanks BMWMan, I was struggling with VMWare 6.0.3 with Hardy for a while before I found your post!  Works great.

---

### Post by bmwman on 2008-06-25
You're very welcome :)

BTW the newer VMware workstaiton 6.0.4 works without any patches with the latest kernels.

---

### Post by andreiashu on 2008-07-23
Thanks BMWman !!! Worked for me too :)

---

### Post by Aaditya_DMW on 2008-07-23
I already Have An Installed XP and Ubuntu 8.04 on My Hard Disk. Currently I Installed VMware On Ubuntu 8.04 ,
I want to Boot My Already Installed XP Using VMware(I Didn’t Installed Xp Using VMware and i Don't want To Install Again) And Work on it. Will dre Be Ny After-Effects On My Windows XP If i Boot It traditionally without Using VMware
Plz Help By Giving Ur Suggestion, i m Desperately Waiting For FollowUp Comments

---

### Post by bmwman on 2008-07-23
I'm not exactly sure what are you trying to do but I think this is what you want:

[http://ubuntuforums.org/showthread.php?t=631671](http://ubuntuforums.org/showthread.php?t=631671)

---

### Post by Aaditya_DMW on 2008-07-24
Thnx For ur Reply >>bmwman
I want to make d situation more clear by stating that >>
Actually i Didn't Installed My XP using VMware , i Installed it in traditional Way,and then i installed Ubuntu 8.04 and then VMware in Ubuntu. Now i want to Work on both d OS Simultaneously i.e on Ubuntu 8.04 and XP,>> But My VMware Unable to Detect My Installed XP , So is dre Ny way To Work on that Xp from Ubuntu using VMware..Without Re-installing It(XP) using VMware .
I Hope I Xplained Well Enough..So plz Help..>>

---

### Post by bmwman on 2008-07-24
You can boot your existing XP inside VMware. Read the above thread and follow the instructions.

---

### Post by oktapod on 2008-07-27
Thank you. It works form me.

HP Pavilion DV6780el 2.4 Centrino Duo, 4GB Ram, 256 VGA.
On Ubuntu Hardy

---

### Post by bigjig on 2008-09-23
Thanks a lot 'bmwman' for those detailed steps mate. Works like a charm!

I've installed VM Workstation 6.0.5 build 109488, no issues at all, clean install.


Cheers

---

### Post by bmwman on 2008-09-23
I'm using the beta VMware workstatio 6.5. I love it!!! Especially the "Unity" feature.

---

### Post by bigjig on 2008-09-23
Pardon my ignorance but what's the unity feature?

---

### Post by bmwman on 2008-09-24
When you run XP or Vista or whatever your guest OS is in Unity mode, it just runs in the background and you can see only the Start menu button. Then you can start individual programs and have 'em run inside Linux and not have the whole Windows desktop there too.

It's a great feature, kinda like the Seamless mode in Virtual Box except that VMware Workstation is far more advanced and easy to use. Not to mention the better performance and 3D support that 6.5 has.

---

