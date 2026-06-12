---
title: "Problem with reconfigure vmware workstation with v9.04"
date: 2009-05-12
forum: Virtualisation
---

### Post by cocolocko on 2009-05-12
Hi @ all,

for the problem of the Intel-Driver i installed a new Kernel for Jaunty.
Normaly if you change the Kernel you have to build new the VMWARE-Workstation, but this is not working.
I become the following answer :)

> sudo vmware
Logging to /tmp/vmware-root/setup-26435.log
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
Stopping VMware services:
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.30-020630rc2-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630rc2-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
In file included from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:31:
/tmp/vmware-root/modules/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:67: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-root/modules/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-root/modules/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630rc2-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'

and the SETUP-LOG

> May 12 19:20:55.486: app| Log for VMware Workstation pid=24193 version=6.5.2 build=build-156735 option=Release
May 12 19:20:55.486: app| Host codepage=UTF-8 encoding=UTF-8
May 12 19:20:55.486: app| Logging to /tmp/vmware-root/setup-24193.log
May 12 19:20:56.550: app| Extracting the sources of the vmmon module.
May 12 19:20:56.600: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.30-020630rc2-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.3.3

and a Box with this

> Error
Unable to build kernel module.
See log file

Does someone know a Solution?
Thanks

Greetings

---

### Post by TJet1.8 on 2009-05-24
Have you installed the linux headers and build essentials prior to re-compiling your VMware Workstation modules?

Install your Linux Headers and Build Essential files:
sudo apt-get install build-essential linux-headers-$(uname -r)

Re-compile your VMware modules:
sudo /usr/bin/vmware-modconfig --console --install-all

Try it and let us know.

:)

---

### Post by cocolocko on 2009-05-25
Hi TJet1.8,

i try to install the Linux-Headers:
```
Install your Linux Headers and Build Essential files:
sudo apt-get install build-essential linux-headers-$ 2.6.30-020630rc7-generic
```

**But they are installed:**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
E: Couldn't find package linux-headers-$

Then i try the re-compiling:
```
Re-compile your VMware modules:
sudo /usr/bin/vmware-modconfig --console --install-all

```

**And the answer was:**
sudo /usr/bin/vmware-modconfig --console --install-all
Stopping VMware services:
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.30-020630rc7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630rc7-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
In file included from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:31:
/tmp/vmware-root/modules/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:67: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-root/modules/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-root/modules/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630rc7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
Unable to install vmmon


It looks linke that the kernel is to new for the VMware, or?
But in OpenSUSE with the newest Kernel, i could perfectly build it new.

PS: Imade the "Bleeding-Edge* Configuration" of this thread - [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
because of my GM965 Graphic Card

---

### Post by veloce on 2009-05-25
If you compiled a new kernel, you must have to get the headers from the same source - it seems unlikely that they will be sitting in the jaunty repository (even if you type the command correctly).

Until you have the appropriate headers, attempting to compile the vmware modules is a waste of time.

Until you do that you can't determine whether the new kernel will work with vmware.  (Sometimes newer kernels require patching the vmware-config.pl file to get it to compile things properly but you won't know that until you have the right headers.)

---

### Post by Triptol on 2009-06-03
This worked for me (although I am on the 2.6.29 kernel and not the 2.6.30): [http://communities.vmware.com/thread/192355](http://communities.vmware.com/thread/192355)

---

### Post by Triptol on 2009-06-03
Ok, that was a bit too quick. The modules build (except for the monitoring one), but after that my vmware-workstation segfaults.

---

### Post by cocolocko on 2009-06-05
> This worked for me (although I am on the 2.6.29 kernel and not the 2.6.30): [http://communities.vmware.com/thread/192355](http://communities.vmware.com/thread/192355)


Thank you very much for the information TRIPTOL.
Works perfect for me with the Kernel 2.6.29-02062904-generic x86_64! :D

Greetings

---

### Post by Triptol on 2009-06-09
This did it for me: [http://communities.vmware.com//message/1213099](http://communities.vmware.com//message/1213099) (I took the second patch, the one with the updates)

---

### Post by Triptol on 2009-06-16
And for VMWare 6.5.2 you need to go here: [http://communities.vmware.com/thread/203231](http://communities.vmware.com/thread/203231)

---

### Post by v1nsai on 2009-08-31
I was having the problem with the missing modules, and I read somewhere to try vmware-modconfig and that failed with the 'Icon name must be set' error, and just when I was going to feed my computer a molotove cocktail, I stumbled across this [https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation) .  I never even thought to check the community docs lol.  Ubuntu ftw.

---

### Post by floflo530 on 2010-10-25
[https://bbs.archlinux.org/viewtopic.php?pid=815476](https://bbs.archlinux.org/viewtopic.php?pid=815476)

---

