---
title: "KVM broken by last kernel update"
date: 2009-07-03
forum: Virtualisation
---

### Post by Emanuele_Z on 2009-07-03
Hi all.

As per subject I've noticed that KVM is broken with new following kernel:
**2.6.28-13-generic**

Instead, when I use
ema@blademaster:~$ uname -a
Linux blademaster **2.6.28-11-generic** #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

It works a treat.
Specifically with -13 I can't boot XP (I'm successful only in safe mode), instead with -11 it works great.

Am I the only one reporting this?

Regards,

---

### Post by bodhi.zazen on 2009-07-03
Not being able to boot a windows guest is not the same thing as saying KVM is broken, windows has any number of problems :lolflag: .

You need to provide a bunch more detail.

How are you using KVM ? virt-manager or command line ?
what is the problem with your windows guest ?

---

### Post by Emanuele_Z on 2009-07-04
Following is the shell script I use to launch Windows XP:
```

#!/bin/bash
kvm -localtime -m 1024 windows.img

```
My windows image always worked through 1.5 years, but just now with the latest release it stalls (1 cpu 100%) when it changes the screen from VESA resolution (640x480) to 1280x1024.
Naturally running it on previous kernel works.

Regards,

---

### Post by Tomy on 2009-07-04
> **Emanuele_Z said:**
> Following is the shell script I use to launch Windows XP:
```

#!/bin/bash
kvm -localtime -m 1024 windows.img

```My windows image always worked through 1.5 years, but just now with the latest release it stalls (1 cpu 100%) when it changes the screen from VESA resolution (640x480) to 1280x1024.
Naturally running it on previous kernel works.

Regards,

I just upgraded to **2.6.28-13-generic** and have no problem running my kvm winXP quests. The cpu usage seems the same.

This script worked:

```
#!/bin/sh
kvm -no-acpi -usb -usbdevice tablet \
-hda winXP.img  \
-boot c \
-m 512
```and so did this one:
```
sudo kvm-bridge  -soundhw all -vga std \
-hda winXP3.img \
-boot c \
-m 512
```You might try adding "-vga std" to your options. This gives you a different video driver that has higher resolutions than the default driver.

---

### Post by Emanuele_Z on 2009-07-05
If I use this command line:
```

#!/bin/bash
kvm -vga std -localtime -m 1024 windows.img

```
Same issue.
If I add *-no-acpi* kvm restarts itself when windows tries to switch from VESA to 1280x1024.

I can only execute WinXP in safe mode in 640x480. When I try to change the resolution from safe mode (to 1280x1024) it does not.

Any Idea?

---

### Post by Emanuele_Z on 2009-07-05
An update.
I tried to redo this from scratch reinstalling WinXP on another img file.
```

qemu-img create -f qcow2 winxp.img 10G
kvm -localtime -vga std -cdrom /dev/cdrom -m 1024 -boot d winxp.img
kvm -localtime -vga std -m 1024 winxp.img

```

After updating to XP SP2 I have the same issue once again...

How can I fix this? shall I use the older kernel version?

Thanks again,

---

### Post by scaphandre on 2009-07-06
Just wanted to sencond this report. My command line is :
```

#!/bin/bash
kvm -vga std -cdrom /dev/cdrom -no-quit -m 800 -usb -usbdevice tablet -name WinXP ~/vmware/winXP.img

```I am running the latest package
```
$ kvm -h | grep version
QEMU PC emulator version 0.9.1 (kvm-84), Copyright (c) 2003-2008 Fabrice Bellard

```Booting WinXP in safe mode is the only way to get access to login. In normal boot, everything gets stuck after text curses-based progress bar has fullfilled.
Note that I have this problem since last upgrade, which upgraded both kvm and linux kernel.
```
$ uname -a
Linux kilo 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux
```This seriously brokes my everyday workflow, should I downgrade to the older kernel or should a fix be available shortly ?
Can I help to get that solved quickly ?
Cheers,
scaph'.

---

### Post by Emanuele_Z on 2009-07-06
Luckyly I'm not the only one...
If I run Ubuntu with **2.6.28-11-generic** chosen from grub screen everything works...I'd recommend to use that kernel version...
With that version kvm works.

Cheers,

---

### Post by veloce on 2009-07-07
Personally, I always rdp to my virtual machines and have had no difficulty with the latest kernel -13. 

This may be a work around for some of you.

gnome-rdp has the nice feature of allowing you to specify any random resolution.  I use this to set a resolution such that the window (with it's borders) exactly fits on what ever screen I'm using.

---

### Post by Emanuele_Z on 2009-07-07
Has anyone any update on this?

How to reproduce:
Install WinXP, upgrade to SP2.
After that you won't be able to start the virtualized WinXP unless in safe mode.
If you run it against previous kernel it works.

Regards,

---

### Post by veloce on 2009-07-07
I can't reproduce this issue.  All my windows vms continue to run fine.

What systems is it failing on?

My details:

```
km@NPLT24:~$ uname -a
Linux NPLT24 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux
```

Virt Manager 0.6.1

VMs:
Windows XP Professional 64 bit

---

### Post by gervin23 on 2009-07-08
Same thing here. -11 works perfectly while -13 doesn't. XP freezes regardless of which -vga option I use (std or cirrus).

---

### Post by scaphandre on 2009-07-08
I second that, tested -11 kernel, work falwlessly.
-13 still crashes. Please, tell me how can help to solve this, it's really a pain in teh sas.
Cheers,
scaph'.

---

### Post by munzli on 2009-07-09
starting like this ```
kvm -cpu qemu64,-nx images/winxp-ie7.img
``` seems to work.

---

### Post by Jimbob0i0 on 2009-07-10
> **munzli said:**
> starting like this ```
kvm -cpu qemu64,-nx images/winxp-ie7.img
``` seems to work.

I have the same issue - 32 bit windows on kvm/qemu 0.9.1 with 2.6.28-13-generic kernel on jaunty. 

Confirmed this does appear to work to start the virt guest in normal that would only start in safe mode post kernel update.

Specifically it is the ,-nx that seems to get this working again qemu32 and qemu64 both work....

Does anyone know where to patch virsh to make the -cpu argument to kvm/qemu to include ,nx after the processor to be emulated?

I'm guessing that the -13 kernel update enabled or disabled somethign to do with NX in the host CPU or hypervisor capabilities and now KVM is trying to make use of it but windows is getting confused by it and encountering a deadlock or something (although the guest appears to be frozen cpu analysis indicates that it is very active probably in a loop of some nature).

---

### Post by Jimbob0i0 on 2009-07-10
Okay I have a workaround for now.....

Edit the XML for your domain to include the line:

<emulator>/etc/libvirt/qemu/kvm-32</emulator>

within the <devices/> element.

In this script (note this is tailored to 32 bit... amend for 64 bit if needed) have the following:

#!/bin/bash
exec kvm -cpu qemu32,-nx `echo $*`

Make sure it is executable by all (or your user) and start the guest domain using teh new xml definition. This will tell virsh to use that specific emulator and will add the relevant cpu option at the start....

This has once again got my guest domain running under virsh/kvm until such time as the bug can be investigated and resolved.....

Has anyone raised a bug on launchpad yet?

---

### Post by Jimbob0i0 on 2009-07-10
I have filed a bug upstream with redhat:

[https://bugzilla.redhat.com/show_bug.cgi?id=510695](https://bugzilla.redhat.com/show_bug.cgi?id=510695)

---

### Post by scaphandre on 2009-07-11
I hereby confirm that a modification of the command to

```
#!/bin/bash
kvm -cpu qemu32,-nx -cdrom /dev/cdrom -no-quit -m 800 -usb -usbdevice tablet -name WinXP ~/vmware/winXP.img

```Actually fixes the problem, I can continue to work, thank you.
Cheers, 
--
Scaph'

---

### Post by mevdschee on 2009-07-28
I can confirm this.. Windows XP SP3 is not booting (blank screen with white cursor) on Ubuntu Jaunty 9.04 32 bit using KVM. It does boot in safe mode or when I use kernel 2.6.28-11 (generic) instead of 2.6.28-13 (generic).

 I suspect it has something to do with the virtual display adapter.

---

### Post by Explodinglemur on 2009-07-28
I have a similar issue.  Under 2.6.28-11, my WinXP guest works fine when launched from virt-manager.  Under 2.6.28-13, it starts okay (boot menu comes up and allows me to select the WinXP hardware profile), but then the console display goes blank.  CPU, disk, and memory usage seem to indicate the VM is launching normally, but the VNC console displays nothing.  Video card is an nVidia 7300GS, using nVidia driver 180.44.

---

### Post by mevdschee on 2009-07-29
desktop:~$ uname -a
Linux desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

After a kernel update to 2.6.28-14-generic it is still not working..

---

### Post by emiplegie on 2009-07-29
I've similar problems with kvm, 
Il update kernel this morning to 2.6.28-14-generic it is still not working.

My problem is that kvm not working (the vm not start) and triggered a kde freeze (kde4)... 

After any investigations, i didn't succed to find a solution, I have non log except this : kvm: 8866: cpu0 unhandled wrmsr: 0xc0010117 data 0 or kvm: 4377: cpu0 unhandled wrmsr: 0xc0010117.....

:(:(

---

### Post by mevdschee on 2009-08-19
updated to 2.6.28-15-generic, problem still exists..

desktop:~$ uname -a
Linux desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

seems to get fixed in 9.10..

see: [https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/395356](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/395356)

---

