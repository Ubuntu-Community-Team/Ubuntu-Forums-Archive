---
title: "RAID1 Ubuntu doesn't boot with only one hard disk"
date: 2008-09-25
forum: Server Platforms
---

### Post by andy80 on 2008-09-25
Hello,

I've my Ubuntu 8.04.1 configured in this way:

SATA1: HD 160Gb with WinXp
SATA2: HD 320Gb raid software for linux
SATA3: HD 320Gb raid software for linux

SATA2 and SATA3 are joined to create a RAID1 that is divided in:

- 50 Gb /
- 270 Gb /home

Everithing works fine. I just did this test: "what happens if I disconnect SATA3 before powering on the PC?".

I expect Ubuntu boot normally, but it doesn't. It shows me the GRUB menu, I choose Ubuntu Linux, the progress bar appears, going from left to right and viceversa. It stays in that state forever and I have to power off my machine, connect SATA3 to make it boot normally.

The problem is that nothing is logged on disks! So I cannot know what it happens! I've tried to boot also in recovery mode, so I can read something on the console... all that I remember was something like "md0 stop, md1 stop." that's all.

What can be the problem? I was expecting Linux boot normally without a disk, if configured in RAID1! What if one day a disk will have an hardware failure? The RAID will be completely unusefull!

---

### Post by Krupski on 2008-09-26
> **andy80 said:**
> Hello,

I've my Ubuntu 8.04.1 configured in this way:

SATA1: HD 160Gb with WinXp
SATA2: HD 320Gb raid software for linux
SATA3: HD 320Gb raid software for linux

SATA2 and SATA3 are joined to create a RAID1 that is divided in:

- 50 Gb /
- 270 Gb /home

Everithing works fine. I just did this test: "what happens if I disconnect SATA3 before powering on the PC?".

I expect Ubuntu boot normally, but it doesn't. It shows me the GRUB menu, I choose Ubuntu Linux, the progress bar appears, going from left to right and viceversa. It stays in that state forever and I have to power off my machine, connect SATA3 to make it boot normally.

The problem is that nothing is logged on disks! So I cannot know what it happens! I've tried to boot also in recovery mode, so I can read something on the console... all that I remember was something like "md0 stop, md1 stop." that's all.

What can be the problem? I was expecting Linux boot normally without a disk, if configured in RAID1! What if one day a disk will have an hardware failure? The RAID will be completely unusefull!

OK, let's see if I can help you.

First of all, since you are using RAID-1 for Linux, both drives (SATA2 and SATA3) have identical data on them (the GRUB boot files, the kernel image, etc...)

However, each drive has a different number!

Now, let's look at a piece of a typical Grub "menu.lst" file:

```

title           Ubuntu 8.04.1, kernel 2.6.24-19-server
root            [COLOR="Red"]**(hd0,0)**[/COLOR]
kernel          /boot/vmlinuz-2.6.24-19-server [COLOR="Red"]**root=/dev/sda1**[/COLOR] ro
initrd          /boot/initrd.img-2.6.24-19-server

```

See the red highlighted parts? Those tell Grub where to boot from.

If THAT drive from the RAID array is present, no problem. If the OTHER drive is present only, the boot fails because Grub can't find the drive specified (in red). See?

So, the solution is to use Grub's "fallback" feature. Basically, it sets up the "menu.lst" file to say "Boot from here first, if it fails try the next, if that fails try the next..." for as many options as you've setup.

So, now look at how the NEW "menu.lst" would be:

```

[COLOR="Red"]**fallback 1**[/COLOR]

title           Ubuntu 8.04.1, kernel 2.6.24-19-server (0)
root            [COLOR="Red"]**(hd0,0)**[/COLOR]
kernel          /boot/vmlinuz-2.6.24-19-server [COLOR="Red"]**root=/dev/sda1**[/COLOR] ro
initrd          /boot/initrd.img-2.6.24-19-server

title           Ubuntu 8.04.1, kernel 2.6.24-19-server (1)
root            [COLOR="Red"]**(hd1,0)**[/COLOR]
kernel          /boot/vmlinuz-2.6.24-19-server [COLOR="Red"]**root=/dev/sdb1**[/COLOR] ro
initrd          /boot/initrd.img-2.6.24-19-server

```

"Fallback 1" means "Try zero first, if it fails try one".

Note that the two entries are identical, EXCEPT that the specification for the "root" is different.

All you have to do, of course, is put in the proper root specs for YOUR system. In fact, if your root is specified with UUID, then ALL you need to change is the "root (hd0,0)" part (since both members of your RAID array will have identical UUID numbers).

Hope this makes sense...

-- Roger

---

### Post by andy80 on 2008-09-26
Hi!

Thanks for the reply, but I've discovered that my problem is another and it's related to this bug: [https://bugs.launchpad.net/initramfs-tools/+bug/120375]("https://bugs.launchpad.net/initramfs-tools/+bug/120375")

As you can see, it's a Ubuntu 8.04 bug and it will be fixed for 8.10 release.

Thanks anyway :)

---

### Post by Robstarusa on 2008-09-26
> **Krupski said:**
> OK, let's see if I can help you.

First of all, since you are using RAID-1 for Linux, both drives (SATA2 and SATA3) have identical data on them (the GRUB boot files, the kernel image, etc...)

However, each drive has a different number!

Now, let's look at a piece of a typical Grub "menu.lst" file:

```

title           Ubuntu 8.04.1, kernel 2.6.24-19-server
root            [COLOR="Red"]**(hd0,0)**[/COLOR]
kernel          /boot/vmlinuz-2.6.24-19-server [COLOR="Red"]**root=/dev/sda1**[/COLOR] ro
initrd          /boot/initrd.img-2.6.24-19-server

```

See the red highlighted parts? Those tell Grub where to boot from.

If THAT drive from the RAID array is present, no problem. If the OTHER drive is present only, the boot fails because Grub can't find the drive specified (in red). See?

So, the solution is to use Grub's "fallback" feature. Basically, it sets up the "menu.lst" file to say "Boot from here first, if it fails try the next, if that fails try the next..." for as many options as you've setup.

So, now look at how the NEW "menu.lst" would be:

```

[COLOR="Red"]**fallback 1**[/COLOR]

title           Ubuntu 8.04.1, kernel 2.6.24-19-server (0)
root            [COLOR="Red"]**(hd0,0)**[/COLOR]
kernel          /boot/vmlinuz-2.6.24-19-server [COLOR="Red"]**root=/dev/sda1**[/COLOR] ro
initrd          /boot/initrd.img-2.6.24-19-server

title           Ubuntu 8.04.1, kernel 2.6.24-19-server (1)
root            [COLOR="Red"]**(hd1,0)**[/COLOR]
kernel          /boot/vmlinuz-2.6.24-19-server [COLOR="Red"]**root=/dev/sdb1**[/COLOR] ro
initrd          /boot/initrd.img-2.6.24-19-server

```

"Fallback 1" means "Try zero first, if it fails try one".

Note that the two entries are identical, EXCEPT that the specification for the "root" is different.

All you have to do, of course, is put in the proper root specs for YOUR system. In fact, if your root is specified with UUID, then ALL you need to change is the "root (hd0,0)" part (since both members of your RAID array will have identical UUID numbers).

Hope this makes sense...

-- Roger

I can't wait until I get home to try this!

---

