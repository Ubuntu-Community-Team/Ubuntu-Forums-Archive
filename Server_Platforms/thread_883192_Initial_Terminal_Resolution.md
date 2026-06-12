---
title: "Initial Terminal Resolution"
date: 2008-08-07
forum: Server Platforms
---

### Post by Seaker on 2008-08-07
A newbie question here: 

I just installed Ubuntu Server 8.04.1 AMD64.  How do you set the initial terminal size to be something more useful than 80x25 when at the console?  Or how can you make it bigger after you are up an running?

Thanks!

---

### Post by windependence on 2008-08-08
In your /boot/grub/menu.list there are the listed kernels like this (open with sudo):

title Debian GNU/Linux, kernel 2.6.20-15-lowlatency
root (hd0,5)
kernel /boot/linux-2.6-bla root=UUID=something ro vga=792
initrd /boot/initrd.img-2.6.20-15-lowlatency
boot

I assume your graphics adapter can handle 1024x768. Just add the bold vga=792 at the end of the line. After a reboot or ctrl+alt+backspace you should be able to see bootmessages (if no splashscreen is configured) AND your terminal(s) (ctrl+alt+f1) in 1024x768

-Tim

---

### Post by Seaker on 2008-08-08
Many thanks!  It is amazing how much more usable it makes the console feel!

But I'm curious vga=792??  What is the 792 for?  Vertical resolution plus vertical blanking interval?

---

### Post by cdtech on 2008-08-08
Here is a table of VESA video modes (VGA codes):
```

        640×480  800×600  1024×768  1280×1024 1600×1200  Ask user at boot.
8 bits  vga=769  vga=771  vga=773   vga=775   vga=796    vga=ask
16 bits vga=785  vga=788  vga=791   vga=794   vga=798    vga=ask
32 bits vga=786  vga=789  vga=792   vga=795   vga=799    vga=ask

```

**Update::.**
Key: 8 bits = 256 colors, 16 bits = 65,536 colors, 32 bits = 16.8 million colors
(i.e. for 1280x1024 @ 256, you just use "vga=775")

---

### Post by windependence on 2008-08-08
I knew there was a table somewhere in this. THANKS!

-Tim

---

### Post by Vivaldi Gloria on 2008-08-09
[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

---

