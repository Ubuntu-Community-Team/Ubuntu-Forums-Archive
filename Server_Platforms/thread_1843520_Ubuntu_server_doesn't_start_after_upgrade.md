---
title: "Ubuntu server doesn't start after upgrade"
date: 2011-09-13
forum: Server Platforms
---

### Post by mtw666 on 2011-09-13
Hi,
I have a problem. After upgrading my ubuntu server, after restart I get this error message:

[IMG]http://www.image-share.com/upload/922/213.jpg[/IMG]

I've tried to change /dev/disk/by-uuid/xxxxxxxxxx to /dev/cciss/c0d0, then to /dev/cciss/c0d1, but it doesn't worked. 

Maybe you could help me :)

---

### Post by arrrghhh on 2011-09-13
> **mtw666 said:**
> Hi,
I have a problem. After upgrading my ubuntu server, after restart I get this error message:

I've tried to change /dev/disk/by-uuid/xxxxxxxxxx to /dev/cciss/c0d0, then to /dev/cciss/c0d1, but it doesn't worked. 

Maybe you could help me :)

Did you change hard disks at all or anything related to it...?  I've never seen that before.  Why would you change it to /dev/cciss/c0d0?  Usually disks are /dev/sda1 or /dev/sdb2 etc...

Either way, it seems the UUID of your disk changed.  I would verify the UUID is correct, and fix the entry.

---

### Post by mtw666 on 2011-09-13
I haven't changed disks. I use HP Proliant server, which has HP Smart Array CCISS driver. So in /dev I can't see sda1, nor hda1 etc. But I see /dev/cciss/c0d0, /dev/cciss/c0d1 :)

---

### Post by arrrghhh on 2011-09-13
> **mtw666 said:**
> I haven't changed disks. I use HP Proliant server, which has HP Smart Array CCISS driver. So in /dev I can't see sda1, nor hda1 etc. But I see /dev/cciss/c0d0, /dev/cciss/c0d1 :)

Can you still mount the disks from a LiveCD or something similar?

---

### Post by mtw666 on 2011-09-13
I could try only tomorrow. What shoud I mount and how? :) I not very experienced user. For example mount /dev/cciss/c0d0 /mnt?

---

### Post by arrrghhh on 2011-09-13
> **mtw666 said:**
> I could try only tomorrow. What shoud I mount and how? :) I not very experienced user. For example mount /dev/cciss/c0d0 /mnt?

Wherever you can mount 'em.  I usually mount them in /media, but it doesn't matter.  So long as it's a valid place to mount.

I'd also be curious to see what fdisk -l puts out.

---

### Post by Entilza on 2011-09-13
Hold shift when booting and try to boot with the older kernel if you did a kernel update.

---

### Post by mtw666 on 2011-09-14
Shift doesnt help.
Here are some additional info:
/dev/disk/by-id
[IMG]http://www.image-share.com/upload/923/291.jpg[/IMG]
/dev/disk/by-label
[IMG]http://www.image-share.com/upload/923/292.jpg[/IMG]
/dev/disk/by-path
[IMG]http://www.image-share.com/upload/923/293.jpg[/IMG]
/dev/disk/by-uuid
[IMG]http://www.image-share.com/upload/923/294.jpg[/IMG]
/dev
[IMG]http://www.image-share.com/upload/923/295.jpg[/IMG]
fdisk -l
[IMG]http://www.image-share.com/upload/923/296.jpg[/IMG]
Part of /boot/grub/menu.lst
[IMG]http://www.image-share.com/upload/923/297.jpg[/IMG]

So what should I put in /boot/grub/menu.lst in the kernel line? 
I've tried /dev/sda1, /dev/cciss/c0d0, /dev/cciss/c0d1, /dev/cciss/c0d0p1, etc...

---

### Post by arrrghhh on 2011-09-14
Hrm, that UUID appears to match what you have.  Also, I would think /dev/cciss/c0d1 would work...  I'm honestly at a loss here.

Have you tried recovery mode?  Does memtest even work?!?

---

### Post by mtw666 on 2011-09-15
After changing grub legacy to grub 2, i've hot grub error 15. After that somehow, now I get "Attempting boot from hard drive (C:)". And now I totally stuck. I've tried to reinstall grub2, but it didn't help.

---

### Post by arrrghhh on 2011-09-15
> **mtw666 said:**
> After changing grub legacy to grub 2, i've hot grub error 15. After that somehow, now I get "Attempting boot from hard drive (C:)". And now I totally stuck. I've tried to reinstall grub2, but it didn't help.

Are you able to boot from a LiveCD?  You might need to backup your data and start over.

---

### Post by mtw666 on 2011-09-15
Yes, I can boot to Rescue mode. But I would like to fix the current installation.

---

