---
title: "Server - Screen Resolution"
date: 2007-02-03
forum: Server Platforms
---

### Post by JimTDI on 2007-02-03
Is there a way to set the terminal screen resolution on Ubuntu Server 6.06LTS, or do I just need to get used to the H-U-G-E text size.

I saw a post where someone said to change the kernel boot options to VGA=ask, but I don't know how to do that.

Thanks!

---

### Post by MachaB on 2007-08-05
Hi there,

well, I have the same problem -too large characters-, anybody know how to change this? Thanks in advance

---

### Post by laytek on 2007-09-14
I too had the same problem, but the solution is very easy. You need to tell the kernel the vga mode to use when it starts. For 256 colors, use vga=771 for 800x600 resoluiton, vga=773 for 1024x768 resolution, or vga=775 for 1280x1024 resolution.
First,  change to the grub directory.
```
cd /boot/grub
```
Then, as root, use your favorite editor to add a vga=??? boot parameter to the kernel.
```
sudo nano menu.lst
```
Now find the menu item, near the bottom, that is called to start the kernel. Mine looks like this:
```
title           Ubuntu, kernel 2.6.20-16-server
root            (hd0,4)
kernel          /vmlinuz-2.6.20-16-server root=/dev/mapper/Ubuntu-root vga=773 ro quiet splash
initrd          /initrd.img-2.6.20-16-server
savedefault


```
Notice that I have added vga=773 to the kernel line. I get a nice 1024x768 display that is perfect for a server.

Hope this helps,
LayTek

---

### Post by laytek on 2007-09-25
The solution that I posted last week has worked well for me, but it didn't survive the kernel update today. Studying only the /boot/grub/menu.lst comments, I believe it is necessary to put the "vga=???" kernel option on a second line in menu.lst so that the next time grub creates a new menu.lst, your kernel option will be inserted after a kernel update. So, fire up your trusty editor and open /boot/grub/menu.lst and look for this:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=773 quiet splash


```

The "vga=791" is an example option that should be in your menu.lst. The "vga=773" is the kernel option that I have added. Notice that I have placed this in the section for default boot options, but not with the alternatives. I did this so that if things really go wrong, I can boot a recovery kernel with minimum options.

When the next kernel upgrade comes along, hopefully AUTOMAGIC KERNELS LIST will write my "vga=???'" option into the newest kernel startup line. Can anybody confirm this?

Always more to learn,
LayTek

---

