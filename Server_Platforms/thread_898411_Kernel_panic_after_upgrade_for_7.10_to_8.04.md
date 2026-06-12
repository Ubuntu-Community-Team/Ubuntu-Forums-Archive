---
title: "Kernel panic after upgrade for 7.10 to 8.04"
date: 2008-08-23
forum: Server Platforms
---

### Post by mansonthomas on 2008-08-23
Hi,

  I've recently tryied to upgrade my ubuntu server 7.10 to 8.04, all the process complete without error until the final reboot happen.

  The box won't boot. The difficult part is that the linux box is a dedicated server, without physical acces, and a very poor KVM over IP solution, plus a lobotomized support service that takes 2 days to answer a mail while it's just a production server that is down.

 Anyway, when I finally got acces to the kvm solution I could see this : 

```
Starting up ...
Uncompressing Linux ... OK, booting the kernel.
Kernel panic - not syncing :VFS :Unable to mount root fs on unknow-block(0,0)

```

The good news, is that i've also access to a rescue mode, which is a livecd booting the machine. 

So maybe I can fix the problem.

The question : How do I fix this issue ? 

Thanks for help,
Thomas.

---

### Post by windependence on 2008-08-23
It's probably this bug:

[https://bugs.launchpad.net/ubuntu/+source/gforge/+bug/222799](https://bugs.launchpad.net/ubuntu/+source/gforge/+bug/222799)

Solutions are on the bug page.

-Tim

---

### Post by mansonthomas on 2008-08-23
Thanks Tim.

To try fix this from the rescue cd, here is what I did : 

Mount the hard disk / partition in /mnt

```
mount /dev/sda2 /mnt
```

chroot to /mnt

```
chroot /mnt
```

mount the /boot partition

```
mount /dev/sda1 /boot
```

run update grub

```
root@dedibox1:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.21.1dedibox-r7
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@dedibox1:/#

```

rebooting : 

```
reboot
```

wait and pray ;)

And it did not work...
As I've not the KVM over IP (it's 20&#8364; half a day, and the hell to get it)

I'll backup from my rescue cd, and reinstall..;

Thomas.

---

### Post by windependence on 2008-08-23
Hey we tried right? :)

-Tim

---

### Post by mansonthomas on 2008-08-23
In fact, the new kernel is not in /boot, and the existing kernel are modified-one by the host company.

Anyway, they offer an automated install process, in 20 minutes I'll have the Hardy Heron running on the server ;)

---

