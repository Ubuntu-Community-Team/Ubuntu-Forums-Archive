---
title: "update-grub /menu problem"
date: 2014-05-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-05-23
update-grub will not load 3.15.0-2 kernel pointer to grub menu.

```


ventrical@ventrical-desktop:~$ sudo update-grub
[sudo] password for ventrical: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.15.0-2-generic
Found initrd image: /boot/initrd.img-3.15.0-2-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.13.0-23-generic
Found initrd image: /boot/initrd.img-3.13.0-23-generic
Found linux image: /boot/vmlinuz-3.13.0-19-generic
Found initrd image: /boot/initrd.img-3.13.0-19-generic
Found linux image: /boot/vmlinuz-3.13.0-14-generic
Found initrd image: /boot/initrd.img-3.13.0-14-generic
Found linux image: /boot/vmlinuz-3.13.0-11-generic
Found initrd image: /boot/initrd.img-3.13.0-11-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda6
done
ventrical@ventrical-desktop:~$ 


```


It is there .. but will just not echo in the menu.

---

### Post by Elfy on 2014-05-23
For some reason - when I installed upgrades and the kernel - I didn't get linux-image-3.15.0-2-generic (3.15.0-2.6) and linux-image-extra-3.15.0-2-generic (3.15.0-2.6) installed - grub updated, didn't notice rebooted to the old kernel, then looked :) installed those 2 - updated grub and rebooted to new kernel

---

### Post by Cavsfan on 2014-05-23
> **ventrical said:**
> update-grub will not load 3.15.0-2 kernel pointer to grub menu.

```


ventrical@ventrical-desktop:~$ sudo update-grub
[sudo] password for ventrical: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.15.0-2-generic
Found initrd image: /boot/initrd.img-3.15.0-2-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.13.0-23-generic
Found initrd image: /boot/initrd.img-3.13.0-23-generic
Found linux image: /boot/vmlinuz-3.13.0-19-generic
Found initrd image: /boot/initrd.img-3.13.0-19-generic
Found linux image: /boot/vmlinuz-3.13.0-14-generic
Found initrd image: /boot/initrd.img-3.13.0-14-generic
Found linux image: /boot/vmlinuz-3.13.0-11-generic
Found initrd image: /boot/initrd.img-3.13.0-11-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda6
done
ventrical@ventrical-desktop:~$ 


```


It is there .. but will just not echo in the menu.

I wouldn't know I always have a custom grub menu. It always boots into the last installed kernel. 
I'd have to jack with it to get into an older kernel and I've *very* rarely had the need to do that. 

[[IMG]http://www.zimagez.com/miniature/20140522151808.jpg[/IMG]]("http://www.zimagez.com/zimage/20140522151808.php")

---

