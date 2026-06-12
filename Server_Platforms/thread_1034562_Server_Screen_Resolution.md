---
title: "Server Screen Resolution?"
date: 2009-01-08
forum: Server Platforms
---

### Post by jairom70 on 2009-01-08
Hi im using Ubuntu Server Edition. 
Is it possible to change the screen resolution when using
CLI?   Ty.

---

### Post by Dr Small on 2009-01-08
Ubuntu doesn't include the framebuffer sizes in GRUB's menu.lst, but Arch does:
```
#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

```


At the end of your kernel line, add "vga=###", like this:
```
kernel /vmlinuz26 root=/dev/sda3 ro vga=771
```

---

### Post by jairom70 on 2009-01-08
I use 1680*1050 resolution.
Is that the highest it goes?

---

### Post by cdtech on 2009-01-08
The highest is 1600x1200, you could use "ask" in place of the numeric value and it will ask which value to use but you would need to have the list in front of you to select the proper value:
```

   Colors ( depth) 640x480 800x600 1024x768 1280x1024 **1600x1200**
   ---------------+-------+-------+--------+---------+---------
   256    ( 8 bit)| 769    771     773      775       796
   32,768 (15 bit)| 784    787     790      793       797
   65,536 (16 bit)| 785    788     791      794       798
   16.8M  (24 bit)| 786    789     792      795       799

```
**UPDATE::.**
Framebuffer HOWTO:
[http://www.tldp.org/HOWTO/Framebuffer-HOWTO.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTO.html)

---

### Post by jairom70 on 2009-01-08
It tells me bash kernel command not found

---

### Post by Dr Small on 2009-01-09
> **jairom70 said:**
> It tells me bash kernel command not found
You have to edit the bootup file, and the restart. The file is here:
```
/boot/grub/menu.lst
```

Find your kernel line, edit it with the vga=value, save it, and reboot to try it.

---

