---
title: "Installed Ubuntu Studio, other OS won't boot"
date: 2014-02-24
forum: Ubuntu Studio
---

### Post by Tristan_Williams on 2014-02-24
I have two HDDs. 

YESTERDAY:
I had Ubuntu Minimal 13.10 on /dev/sda, and another Ubuntu Minimal 13.10 on /dev/sdb (One system for stable usage, other for playing around)
Both of them booted perfectly fine.

LAST NIGHT:
Installed Ubuntu Studio on /dev/sda

Ubuntu studio on /dev/sda boots fine.
Ubuntu Minimal on /dev/sdb does not boot. When I select Ubuntu Minimal in Grub, it just boots to a black screen, with a blinking cursor in the top left corner.

Here is my output from 'sudo update-grub'
```

tristan@tristan-vostro-220:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-17-lowlatency
Found initrd image: /boot/initrd.img-3.11.0-17-lowlatency
Found linux image: /boot/vmlinuz-3.11.0-17-lowlatency
Found initrd image: /boot/initrd.img-3.11.0-17-lowlatency
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-11-lowlatency
Found initrd image: /boot/initrd.img-3.11.0-11-lowlatency
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 13.10 (13.10) on /dev/sdb1
done

```

---

### Post by Tristan_Williams on 2014-02-24
It boots now but looks like Windows ME... New thread time i guess...

---

