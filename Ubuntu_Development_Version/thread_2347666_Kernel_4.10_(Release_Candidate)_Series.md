---
title: "Kernel 4.10 (Release Candidate) Series"
date: 2016-12-27
forum: Ubuntu Development Version
---

### Post by Doug S on 2016-12-27
[Kernel 4.10-RC1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc1/") (Release Candidate 1) has been available for a couple of days. So far, I have only been running it for a few minutes:```
Linux s15 4.10.0-rc1-stock #166 SMP Tue Dec 27 08:39:08 PST 2016 x86_64 x86_64 x86_64 GNU/Linux
```

O.K. so finally the regression fixes for the high number of kworker threads have made their way to the mainline kernel. Tested, and fixed. By the way, the fix was fast track backported to Ubuntu and is already in zesty, and in proposed for yakety.

References:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626564]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626564")
[https://bugs.launchpad.net/ubuntu/yakkety/+source/linux/+bug/1649905]("https://bugs.launchpad.net/ubuntu/yakkety/+source/linux/+bug/1649905")
[https://bugzilla.kernel.org/show_bug.cgi?id=172991]("https://bugzilla.kernel.org/show_bug.cgi?id=172991")
[https://bugzilla.kernel.org/show_bug.cgi?id=172981]("https://bugzilla.kernel.org/show_bug.cgi?id=172981")

---

### Post by Doug S on 2016-12-27
Kernel 4.10-RC1 seems to have a problem with reading MSRs (Machine Specific Registers). Kernel 4.9 works fine. The following examples are all from a fresh boot, and we expect my first attempt to fail because I did not yet load the msr module:
```
doug@s15:~$ sudo su
[sudo] password for doug:
root@s15:/home/doug# rdmsr 0x19d -a
root@s15:/home/doug# modprobe msr
root@s15:/home/doug# rdmsr 0x19d -a
0
0
0
0
0
0
0
0
root@s15:/home/doug# rdmsr --bitfield 15:8 -d -a 0x198
16
16
16
16
16
16
16
16
root@s15:/home/doug# uname -a
Linux s15 [COLOR="#FF0000"]4.9.0-stock[/COLOR] #165 SMP Sun Dec 11 15:36:11 PST 2016 x86_64 x86_64 x86_64 GNU/Linux

``````
doug@s15:~$ sudo su
[sudo] password for doug:
root@s15:/home/doug# rdmsr --bitfield 15:8 -d -a 0x198
root@s15:/home/doug# modprobe msr
root@s15:/home/doug# rdmsr --bitfield 15:8 -d -a 0x198
root@s15:/home/doug# lsmod | grep msr
msr                    16384  0
root@s15:/home/doug# uname -a
Linux s15 [COLOR="#FF0000"]4.10.0-041000rc1-generic[/COLOR] #201612252031 SMP Mon Dec 26 01:33:43 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```Anybody else seeing this or know of any references to bug reports or e-mail lists? (I have not looked yet, but will before I start a kernel bisection.)

EDIT: bisection started. It will take a couple of days.

---

### Post by Doug S on 2016-12-28
The problem commit appears to be:```
dc280d93623927570da279e99393879dbbab39e7 is the first bad commit
commit dc280d93623927570da279e99393879dbbab39e7
Author: Thomas Gleixner <tglx@linutronix.de>
Date:   Wed Dec 21 20:19:49 2016 +0100

    cpu/hotplug: Prevent overwriting of callbacks
```and looking at the e-mail threads and such, there seems to have been 3 commits done almost immediately after 4.10-rc1 that should fix the issue.```
0dad3a3 x86/mce/AMD: Make the init code more robust
b9d9d69 smp/hotplug: Undo tglxs brainfart
b4b8664 arm64: don't pull uaccess.h into *.S
7ce7d89 Linux 4.10-rc1

```I am compiling a kernel, including those commits now, and will edit this post later as to results.

EDIT 1: My kernel 4.10-rc1+ is working fine for rdmsr and tubsostat and sensors and ... So, users that do not want to compile their own kernel should wait for 4.10-rc2.
EDIT 2: There seems to be several other side effects from the bad commit mentioned above.

---

### Post by #&amp;thj^% on 2016-12-30
Thanks Doug for your very intensive coverage of this release.
I'm unsuccessful at building it at all.. so I will wait for RC2 to try again...with your useful information provided.

---

### Post by Doug S on 2016-12-30
> **1fallen said:**
> I'm unsuccessful at building it at all.. so I will wait for RC2 to try again...with your useful information provided.Hmmm... While -rc1 has issues, you should still be able to compile it.

Meanwhile, and because of another issue I was looking into, I have been beating up kernel 4.10-rc1+ pretty hard on my test server and VM host, running 3 heavily loaded VM's on it pretty hard. It has been fine.

---

### Post by #&amp;thj^% on 2016-12-30
It's no big deal at this early stage but i get along the lines of:
```
kernel panic - not syncing: Attempted to kill inint !
PId: 1, comm: init not tainted
```
Going off memory though and probably a bit different syntax.
When I boot to Ubuntu tomorrow I will read my logs if you want.
Tried a few work arounds to solve..but no joy.
I'm just fine waiting for RC2 to hit though...unless you want me to do anything else here on Rc1.

---

### Post by zika on 2016-12-31
> **1fallen said:**
> It's no big deal at this early stage but i get along the lines of:
```
kernel panic - not syncing: Attempted to kill inint !
PId: 1, comm: init not tainted
```
Going of memory though and probably a bit different syntax.
When I boot to Ubuntu tomorrow I will read my logs if you want.
Tried a few work arounds to solve..but no joy.
I'm just fine waiting for RC2 to hit though...unless you want me to do anything else here on Rc1.That was (re)solved in 99{4,9} already, several days ago.

---

### Post by Doug S on 2016-12-31
@1fallen: I guess I misunderstood. I thought you were having troubles compiling kernel 4.1-rc1. However, and as expected, you seem to be having troubles running it.

@zika: I didn't think of trying the 999 kernel, which must also now include the fix commit(s).

---

### Post by #&amp;thj^% on 2016-12-31
> **zika said:**
> That was (re)solved in 99{4,9} already, several days ago.
Thanks zika will give it a go.

> **Doug S said:**
> @1fallen: _**I guess I misunderstood. I thought you were having troubles compiling kernel 4.1-rc1.**_ However, and as expected, you seem to be having troubles running it.

@zika: I didn't think of trying the 999 kernel, which must also now include the fix commit(s).

Yes and sorry...I see now I was fairly vague in my description.

---

### Post by Doug S on 2017-01-01
Kernel 4.10-rc2 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc2/"). Very very few changes, which is unusual for so early in the RC cycle.

EDIT: Been running for a few hours now. No problems, but also haven't really pounded on it yet.```
$ uname -a
Linux s15 4.10.0-rc2-stock #184 SMP Sun Jan 1 19:53:24 PST 2017 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by MikeMecanic on 2017-01-02
Hmmmmmm...   This one passes the Kernel Panic Test.  
 
 
 ```
Linux zz 4.10.0-041000rc2-generic #201701011831 SMP Sun Jan 1 23:33:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


```

---

### Post by zika on 2017-01-02
> **Doug S said:**
> Kernel 4.10-rc2 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc2/"). Very very few changes, which is **unusual** for so early in the RC cycle.[http://lkml.iu.edu/hypermail/linux/kernel/1701.0/00069.html](http://lkml.iu.edu/hypermail/linux/kernel/1701.0/00069.html)
> [COLOR=#000000][FONT=&amp]Hey, it's been a really slow week between Christmas Day and New Years [/FONT][/COLOR][COLOR=#000000][FONT=&amp]Day, and I am not complaining at all.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]It does mean that rc2 is ridiculously and unrealistically small. I [/FONT][/COLOR][COLOR=#000000][FONT=&amp]almost decided to skip rc2 entirely, but a small little meaningless [/FONT][/COLOR][COLOR=#000000][FONT=&amp]release every once in a while never hurt anybody. So here it is.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]The only even remotely noticeable work here is the DAX fixups that [/FONT][/COLOR][COLOR=#000000][FONT=&amp]really arguably should have been merge window material but depended on [/FONT][/COLOR][COLOR=#000000][FONT=&amp]stuff during this merge window and were delayed until rc2 due to that.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Even that wasn't big, and the rest is trivial small fixes.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I'm expecting things to start picking up next week as people recover [/FONT][/COLOR][COLOR=#000000][FONT=&amp]from the holidays.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Linus[/FONT][/COLOR]

---

### Post by fthx on 2017-01-04
Does anybody know if 4.10 will include some power management for NVMe SSDs ?

---

### Post by Doug S on 2017-01-05
> **fthx said:**
> Does anybody know if 4.10 will include some power management for NVMe SSDs ?My interpretation, right or wrong, of this [e-mail]("http://marc.info/?l=linux-pm&m=148060259532154&w=2") is that some ground work is being laid in kernel 4.10, but that the real power management improvements are yet to come.

---

### Post by fthx on 2017-01-05
Ok you're right, so it should be logical that the "upcoming nvme power management code" will land soon in 4.10 RCs.
I already know that it exists some related stuff : [https://wiki.archlinux.org/index.php/Solid_State_Drives/NVMe#NVME_Power_Saving_Patch](https://wiki.archlinux.org/index.php/Solid_State_Drives/NVMe#NVME_Power_Saving_Patch) .

---

### Post by Doug S on 2017-01-05
> **fthx said:**
> Ok you're right, so it should be logical that the "upcoming nvme power management code" will land soon in 4.10 RCs.No. At the earliest it would be kernel 4.11-rc1. New stuff is not added to rc kernels after -rc1, only fixes and such.

---

### Post by zika on 2017-01-07
[4.10 is coming...]("https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable")

---

### Post by MikeMecanic on 2017-01-08
I have the exact same problem with 4.10-rc2 on **first restart only.**  After a cold shutdown, rc2 runs normally.  Here for 2 days(CKT), the machine restarts all the time in a dead screen with no tty.  Also, for an unknown reason it boots into the grub menu (not dual boot/UEFI).  The CKT ppa (hard to reach, only the key works) is disable because update manager always returns the same message: Failed to download the repo…   
 
 
 This modification to Grub has no effect:  
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=warm,cold,bios,smp,triple,kbd,acpi,efi,pci,force"
 
 
 Succeed once only with *bios parameter* in the admin account but it was rapidly freezing into the boot image in the non-sudoer account:
 
 
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=bios"  
 
 
 ```
dpkg --list | grep linux-image

 ii  [COLOR=#ff3333]linux-image[/COLOR]-4.10.0-0-generic                    4.10.0-0.1                                 amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]linux-image[/COLOR]-extra-4.10.0-0-generic              4.10.0-0.1                                 amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
 ii [COLOR=#ff3333] linux-image[/COLOR]-generic                             4.10.0.0.1                                 amd64        Generic Linux kernel image

``` 
 
 [CKT ppa]("https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable")

---

### Post by zika on 2017-01-08
I'm not sure if I've got to the core of Your question but I did have reboot and poweroff hesitations with 4.{9,10} in the transition period and I did solve them using simple REISU{O,B} method to prevent lockups after closing all the tty (not necessary but I do love to do that, for ease of mind sake)...
Do try &#8222;pci&#8220; for reboot switch...

---

### Post by MikeMecanic on 2017-01-08
> **zika said:**
> Do try „pci“ for reboot switch...

  	 	 	 	   [LEFT]It is the first thing I made (+acpi), only bios was working on the admin account.[/LEFT] [LEFT]
 [/LEFT] [LEFT]Yes, ALT+SysRq+B works.  I have no shutdown hesitation or problem under .10.  Did not try O.   Will be moving forward with rc3...  [/LEFT] [LEFT]
 [/LEFT] [LEFT]Thanks for the suggestions,[/LEFT]

---

### Post by MikeMecanic on 2017-01-08
I would like to say *fixed upstream* but it is not the case.  The only good news is that I’m not seeing power play in splash screen anymore.
 
 
 ```
dpkg --list | grep linux-image

 ii  [COLOR=#ff3333]linux-image[/COLOR]-4.10.0-0-generic                    4.10.0-0.2                                 amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]linux-image[/COLOR]-extra-4.10.0-0-generic              4.10.0-0.2                                 amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]linux-image[/COLOR]-generic  

``` 
    	 	 	 	   Edit:  powerplay error is still there and ALT+SysReq+b is intermittent.  Reboot switch set to pci does not give the expected result.
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"
  
 All the best,

---

### Post by Doug S on 2017-01-08
> **MikeMecanic said:**
> I would like to say *fixed upstream* but it is not the case.  The only good news is that I&#8217;m not seeing power play in splash screen anymore.
 
 
 ```
dpkg --list | grep linux-image

 ii  [COLOR=#ff3333]linux-image[/COLOR]-4.10.0-0-generic                    4.10.0-0.2                                 amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]linux-image[/COLOR]-extra-4.10.0-0-generic              4.10.0-0.2                                 amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]linux-image[/COLOR]-generic  

``` 
    	 	 	 	   Edit:  powerplay error is still there and ALT+SysReq+b is intermittent.  Reboot switch set to pci does not give the expected result.
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"
  
 All the best,Mike, That is not upstream. The mainline kernel is upstream. The Ubuntu variants of the kernel are downstream. Try 4.10-rc3 when it is available in the Ubuntu mainline PPA, which should be shortly. It is already available at [kernel.org]("https://www.kernel.org/").

EDIT: There are a fair number, not an excessive number, of kernel configuration changes between the Ubuntu 4.10-rc2 and 4.10-rc3 kernels.

---

### Post by MikeMecanic on 2017-01-08
Thanks for the precision Doug.
 
 
 Same as in rc2, loosing the monitor on first restart.  Runs normally after, but I have a new bug.  Suspend mode is not working (won’t wake-up in both accounts).   

 
 
 ```
dpkg --list | grep linux-image

 ii  [COLOR=#ff3333]linux-image[/COLOR]-4.10.0-041000rc3-generic            4.10.0-041000rc3.201701081831              amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP

```  

Regards,

---

### Post by aljosa2 on 2017-01-09
Hi guys, I have been advised to test the latest upstream kernel 4.10-rc3 *(Bug: ASUS G752VS - Touchpad and Fn keys not working)*
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456)

Can you please tell me if kernel 4.10-rc3 breaks NVIDIA driver?

---

### Post by Doug S on 2017-01-09
> **aljosa2 said:**
> Hi guys, I have been advised to test the latest upstream kernel 4.10-rc3 *(Bug: ASUS G752VS - Touchpad and Fn keys not working)*
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456)

Can you please tell me if kernel 4.10-rc3 breaks NVIDIA driver?You will have to install the kernel and do the test yourself. You can get the kernel from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc3/").

---

### Post by aljosa2 on 2017-01-10
Kernel 4.10-rc3 installed and uninstalled before restarting because unfortunaetly it breaks NVIDIA driver:

```
~/Downloads$ sudo dpkg -i *.deb[sudo] password:
Selecting previously unselected package linux-headers-4.10.0-041000rc3.
(Reading database ... 183917 files and directories currently installed.)
Preparing to unpack linux-headers-4.10.0-041000rc3_4.10.0-041000rc3.201701081831_all.deb ...
Unpacking linux-headers-4.10.0-041000rc3 (4.10.0-041000rc3.201701081831) ...
Selecting previously unselected package linux-headers-4.10.0-041000rc3-generic.
Preparing to unpack linux-headers-4.10.0-041000rc3-generic_4.10.0-041000rc3.201701081831_amd64.deb ...
Unpacking linux-headers-4.10.0-041000rc3-generic (4.10.0-041000rc3.201701081831) ...
Selecting previously unselected package linux-image-4.10.0-041000rc3-generic.
Preparing to unpack linux-image-4.10.0-041000rc3-generic_4.10.0-041000rc3.201701081831_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
Done.
Unpacking linux-image-4.10.0-041000rc3-generic (4.10.0-041000rc3.201701081831) ...
Setting up linux-headers-4.10.0-041000rc3 (4.10.0-041000rc3.201701081831) ...
Setting up linux-headers-4.10.0-041000rc3-generic (4.10.0-041000rc3.201701081831) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
ERROR (dkms apport): kernel package linux-headers-4.10.0-041000rc3-generic is not supported
Error! Bad return status for module build on kernel: 4.10.0-041000rc3-generic (x86_64)
Consult /var/lib/dkms/nvidia-375/375.26/build/make.log for more information.
Setting up linux-image-4.10.0-041000rc3-generic (4.10.0-041000rc3.201701081831) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
ERROR (dkms apport): kernel package linux-headers-4.10.0-041000rc3-generic is not supported
Error! Bad return status for module build on kernel: 4.10.0-041000rc3-generic (x86_64)
Consult /var/lib/dkms/nvidia-375/375.26/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-041000rc3-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-041000rc3-generic
Found initrd image: /boot/initrd.img-4.10.0-041000rc3-generic
Found linux image: /boot/vmlinuz-...
```

---

### Post by zika on 2017-01-10
> **aljosa2 said:**
> Kernel 4.10-rc3 installed and uninstalled before restarting because unfortunaetly it breaks NVIDIA driver:

```
~/Downloads$ sudo dpkg -i *.deb[sudo] password:
Selecting previously unselected package linux-headers-4.10.0-041000rc3.
(Reading database ... 183917 files and directories currently installed.)
Preparing to unpack linux-headers-4.10.0-041000rc3_4.10.0-041000rc3.201701081831_all.deb ...
Unpacking linux-headers-4.10.0-041000rc3 (4.10.0-041000rc3.201701081831) ...
Selecting previously unselected package linux-headers-4.10.0-041000rc3-generic.
Preparing to unpack linux-headers-4.10.0-041000rc3-generic_4.10.0-041000rc3.201701081831_amd64.deb ...
Unpacking linux-headers-4.10.0-041000rc3-generic (4.10.0-041000rc3.201701081831) ...
Selecting previously unselected package linux-image-4.10.0-041000rc3-generic.
Preparing to unpack linux-image-4.10.0-041000rc3-generic_4.10.0-041000rc3.201701081831_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
Done.
Unpacking linux-image-4.10.0-041000rc3-generic (4.10.0-041000rc3.201701081831) ...
Setting up linux-headers-4.10.0-041000rc3 (4.10.0-041000rc3.201701081831) ...
Setting up linux-headers-4.10.0-041000rc3-generic (4.10.0-041000rc3.201701081831) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
ERROR (dkms apport): kernel package linux-headers-4.10.0-041000rc3-generic is not supported
Error! Bad return status for module build on kernel: 4.10.0-041000rc3-generic (x86_64)
Consult /var/lib/dkms/nvidia-375/375.26/build/make.log for more information.
Setting up linux-image-4.10.0-041000rc3-generic (4.10.0-041000rc3.201701081831) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
ERROR (dkms apport): kernel package linux-headers-4.10.0-041000rc3-generic is not supported
Error! Bad return status for module build on kernel: 4.10.0-041000rc3-generic (x86_64)
Consult /var/lib/dkms/nvidia-375/375.26/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-041000rc3-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.10.0-041000rc3-generic /boot/vmlinuz-4.10.0-041000rc3-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-041000rc3-generic
Found initrd image: /boot/initrd.img-4.10.0-041000rc3-generic
Found linux image: /boot/vmlinuz-...
```Is it a bona fide issue or just a rejection from compiled driver due to forced restrictions imposed on it by its config...?
[http://rglinuxtech.com/?tag=kernel-4-10-rc3](http://rglinuxtech.com/?tag=kernel-4-10-rc3)
```
ERROR (dkms apport): kernel package linux-headers-4.10.0-041000rc3-generic is not supported
```gives a clue... ;)

---

### Post by aljosa2 on 2017-01-10
Hi zika, thanks for your reply.
Honestly I don't have a clue what are you asking me...
Yes I saw on the Internet that the patch is required for NVIDIA driver 375.26 with 4.10-rc kernels, and thats exactly the reason why, when I noticed reported errors, I uninstalled 4.10-rc3 before restarting my laptop (I'm not capable to apply the mentioned patch).
It seems to me that I will have to wait few weeks untill 4.10-rc kernels becomes compatible with NVIDIA driver 375.26.

---

### Post by dino99 on 2017-01-10
works with nvidia 375.26 patched :[https://devtalk.nvidia.com/default/topic/981993/linux/-patch-included-4-10-rc2/](https://devtalk.nvidia.com/default/topic/981993/linux/-patch-included-4-10-rc2/)

but the kernel compilation needs a parameter:
set CONFIG_STACK_VALIDATION=n when building the kernel, otherwise the compilation of almost any project from source will result in error because of a bug where linking is done before the compilation itself.

---

### Post by Doug S on 2017-01-16
Kernel 4.10-rc4 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc4/"). I've only been running it (my own compile) for a few minutes, so far.```
$ uname -a
Linux s15 4.10.0-rc4-stock #186 SMP Mon Jan 16 07:42:53 PST 2017 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by fyfe54 on 2017-01-22
4.10-rc5 is out there now.  

So far, so good.

---

### Post by Doug S on 2017-01-22
> **fyfe54 said:**
> 4.10-rc5 is out there now.Yes. 
Recall that during the [Kernel 4.7 rc series]("https://ubuntuforums.org/showthread.php?t=2326220&page=5&highlight=scheduler"), the default scheduler changed from CFQ to DEADLINE.
Well, it just changed back:
```
$ scripts/diffconfig .config-4.10.0-041000rc4-generic .config-4.10.0-041000rc5-generic
 BLK_WBT_SQ y -> n
 [COLOR="#FF0000"]DEFAULT_CFQ n -> y
 DEFAULT_DEADLINE y -> n
 DEFAULT_IOSCHED "deadline" -> "cfq"[/COLOR]

```

---

### Post by aljosa2 on 2017-02-06
just tried 4.10-rc7  - it still breaks NVIDIA driver, so uninstalled before rebooting :(

---

### Post by Doug S on 2017-02-12
Hmmm... a week ago the thinking was that were would not be an -rc8 this cycle, but now I see that there is.

EDIT: [http://www.spinics.net/lists/kernel/msg2442989.html](http://www.spinics.net/lists/kernel/msg2442989.html)

---

### Post by aljosa2 on 2017-02-15
Kernel 4.10-rc8 is still incompatible with NVIDIA drivers (378.13 included).
I just saw that kernel 4.10.0-8.10 was uploaded into Zesty proposed 2 days ago: 
*[https://launchpad.net/ubuntu/zesty/+source/linux](https://launchpad.net/ubuntu/zesty/+source/linux)*
Does anyone know if this "Ubuntu version" of kernel 4.10 is ok with NVIDIA or not?

By the way, with the original 4.9 kernel I'm currently getting red error message:
> [14.025824] fwupd[2406]: segfault at 556600000008 ip 00007fce24962e78 sp 00007fffd0aeeb60 error 4 in libc-2.24.so[7fce248e2000+1bd000]
Does anyone know what it is and how to fix it?

---

### Post by fthx on 2017-02-15
In proposed you can now get nvidia-375 v. 39 with 4.10 support.

---

### Post by aljosa2 on 2017-02-15
> **fthx said:**
> In proposed you can now get nvidia-375 v. 39 with 4.10 support.
Thanks man :)
I need proposed only for NVIDIA and kernel 4.10, after that i will disable again the proposed updates.
I know how to install NVIDIA, but with proposed enabled what command should I use to update only kernel?

---

### Post by fthx on 2017-02-16
Simply use Synaptic, that's a very handy way to proceed.

---

### Post by zika on 2017-02-16
> **aljosa2 said:**
> Thanks man :)
I need proposed only for NVIDIA and kernel 4.10, after that i will disable again the proposed updates. 
I know how to install NVIDIA, but with proposed enabled what command should I use to update only kernel?Just install newest kernel```
sudo apt install linux-image-4.10.0-8-generic linux-headers-4.10.0-8 linux-headers-4.10.0-8-generic linux-image-extra-4.10.0-8-generic
```(I do have Kernel PPA enabled ([https://launchpad.net/~ubuntu-kernel-test/+archive/ubuntu/devel](https://launchpad.net/~ubuntu-kernel-test/+archive/ubuntu/devel)) but I've checked and the latest is in proposed PPA) and follow comments You get while doing that.

---

