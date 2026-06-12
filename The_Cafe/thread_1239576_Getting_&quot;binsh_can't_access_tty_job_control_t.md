---
title: "Getting &quot;/bin/sh can't access tty job control turned off&quot; after adding a new HDD"
date: 2009-08-13
forum: The Cafe
---

### Post by gardara on 2009-08-13
I have no idea if I'm allowed to post this here... wasn't there a subforum for other distros? I can't seem to find it.


Anyhow, I'm having problems with my debian fileserver.

I just installed a new HDD and I'm getting this error

```
Decompressing Linux... Parsing ELF... done.
Booting the kernel
Loading, please wait...
mount: mounting /dev on /root/dev failed: No Such file or directory
mount: mounting /sys on /root/sys failed: No Such file or directory
mount: mounting /proc on /root/proc failed: No Such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg

Busybox v1.10.2 (Debian 1:1.10.2-2) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```


Any ideas how I could fix this?

---

### Post by calrogman on 2009-08-13
> **gardara said:**
> I have no idea if I'm allowed to post this here... wasn't there a subforum for other distros? I can't seem to find it.


Anyhow, I'm having problems with my debian fileserver.

I just installed a new HDD and I'm getting this error

```
Decompressing Linux... Parsing ELF... done.
Booting the kernel
Loading, please wait...
mount: mounting /dev on /root/dev failed: No Such file or directory
mount: mounting /sys on /root/sys failed: No Such file or directory
mount: mounting /proc on /root/proc failed: No Such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg

Busybox v1.10.2 (Debian 1:1.10.2-2) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```


Any ideas how I could fix this?

Take out the new hard drive and learn how to edit /etc/fstab and /boot/grub/menu.lst to use UUID's instead of /dev/sdx block devices.

---

### Post by gardara on 2009-08-13
> **calrogman said:**
> Take out the new hard drive and learn how to edit /etc/fstab and /boot/grub/menu.lst to use UUID's instead of /dev/sdx block devices.


allright, any links or something to get me started? :)

---

### Post by tom66 on 2009-08-13
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

(First Google result for me.)

---

### Post by gardara on 2009-08-13
> **tom66 said:**
> [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

(First Google result for me.)

Am I blind or don't they mention anything about UUID's?

---

### Post by Yes on 2009-08-13
This might help - [http://wiki.archlinux.org/index.php/Fstab#Using_UUID_Identifiers](http://wiki.archlinux.org/index.php/Fstab#Using_UUID_Identifiers)

---

### Post by .Maleficus. on 2009-08-13
To actually find the UUID of your devices, you can use either:
```
blkid
ls -l /dev/disk/by-uuid
```
I'm not sure if Ubuntu has 'blkid' but 'ls' should work fine.

---

### Post by gardara on 2009-08-14
Cheers guys!

Setting uuid's in my fstab and menu.lst worked!

Such a simple fix for a problem I just couldn't find the solution for!

---

