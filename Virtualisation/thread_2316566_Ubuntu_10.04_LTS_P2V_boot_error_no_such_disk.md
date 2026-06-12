---
title: "Ubuntu 10.04 LTS P2V boot error no such disk"
date: 2016-03-09
forum: Virtualisation
---

### Post by david499 on 2016-03-09
[LEFT]Hello, I've done a P2V conversion of my Ubuntu Server 10.04 LTS with VMware vCenter Converter 6, to my ESXi 5.5. 
The job works perfectly in the software, completed without any error message... 
The problem is now when I boot the freshly created VM, I have the following error message on the prompt :

 [[IMG]https://communities.vmware.com/servlet/JiveServlet/downloadImage/2-2580824-57214/boot.PNG[/IMG]]("https://communities.vmware.com/servlet/JiveServlet/showImage/2-2580824-57214/boot.PNG")

Have you any idea about how to resolve this ?
 
Thanks for you help.
[/LEFT]

---

### Post by v3.xx on 2016-03-09
I use vBox so no help here with VMware, but did you know that 10.04 is no longer supported?

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by MAFoElffen on 2016-03-09
You said it continued and booted right?

If so, check your disk stats while the vm is running... For instance, some shows /dev/sda as /dev/vda. Then check your fstab for mouns that did not get converted from the old physical assignments to what the VM is using.

---

### Post by david499 on 2016-03-10
> **v3.xx said:**
> I use vBox so no help here with VMware, but did you know that 10.04 is no longer supported?

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Yep I know but we don't need to upgrade the OS, this server is only  use for read access for the old emails, we have two exchange servers  now.


> **MAFoElffen said:**
> You said it continued and booted right?

If so, check your disk stats while the vm is running... For instance, some shows /dev/sda as /dev/vda. Then check your fstab for mouns that did not get converted from the old physical assignments to what the VM is using.

No it doesn't boot, if I press any key, it reload the same message :(

---

### Post by MAFoElffen on 2016-03-10
So then, dl an Ubutnu LiveCD ISO image. Mount it to the virtual CD drive of that VM. Boot it into the LiveCD image.

Start Nautilus and inspect the virtual **** image, to ensure it is readable and it looks okay. After looking at it, umount from nautilus.

Go to my sticky in my signature line, post #3, for basic instructions to mount/chroot into your installed system from a LiveCD. chroot into that system... Then reinstall grub. Your physically installed Ubuntu 10.04's version of grub pointed to a drive assignment that does not exixt in your VM. Reinstalling grub should update the new assignments.

---

### Post by david499 on 2016-03-14
Hello,

Thanks for your help.

When I boot on ubuntu 10.04 liveCD, I can't see my disks...but if I use the ubuntu 14 liveCD, then I can access to everything :confused:

Is it possible to use the ubuntu 14 liveCD to reinstall Grub on an Ubuntu 10.04 ?

---

### Post by MAFoElffen on 2016-03-15
Yes ... (not the best recommendation, but do-able) because you will be chrooted into your installed system.

---

### Post by david499 on 2016-03-15
Ok, I'll try it today, thanks again :)

---

