---
title: "UbuntuStudio how to install Grub not Lilo?"
date: 2009-04-30
forum: Ubuntu Studio
---

### Post by kevin2i on 2009-04-30
Curious if anyone else ran into this, o r if I
Downloaded UbuntoStudio from the link - (not sure why everything is listed "alternative)

[http://cdimage.ubuntu.com/ubuntustudio/releases/9.04/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/9.04/release/)

-Download, burn install to a newly formatted (ext4 + swap) partition
-Installation only gives boot option of Lilo - I choose to install on the same partition (so I don't change/destroy my grub installation)

Lilo will not install, installation asks if I want to continue with installation or exit - I continue and installation completes (with warning OS may not boot).

After installation:
-UbuntuStudio will not boot if set to active partion
-UbuntuStudio WILL boot using my existing GRUB listing for hd(0,1) (beta-11 fedora) but no network connections (and other load issues).
-I change /boot/grub/menu.lst and copy the UbuntuStudio /boot files to my active /boot - but I only get errors (I assume now that Lilo and Grub files are not compatible)

My Grub that (partially) works:
title  UbuntuStudio (Fedora-11 boot settings)
       root (hd0,0)
       kernel /vmlinuz-2.6.29.1-70.fc11.x86.64 ro root=dev/mapper/vg_mediahost-lv_root rghb quiet
       initrd /initrd-2.6.29.1-70.fc11.x86_64.img

If if use the vmlinuz/initrd 2.6.28-3-rt this will not boot

My other partition is running Jaunty - and I don't want to alter anything  since it is working well as my htpc (nvidia 185.51, xbmc, etc).

Is there a Studio install using Grub available?
Any comments are appreciated.

---

### Post by logos34 on 2009-04-30
what?  when did studio switch to lilo as default?  You can't choose grub?  Doesn't sound right 

(I'm running x64 ubuntustudio 8.04 LTS w/ linux-rt kernel, grub bootloader)

maybe try reinstalling but with ext3 partition instead (but that shouldn't be an issue with grub)

note:

"alternate" = text-based installer (vs. desktop live cd)

---

### Post by kevin2i on 2009-04-30
Thanks for the note - made me think to try it again.

> **kevin2i said:**
> 
-Installation only gives boot option of Lilo - 

? I tried the SAME disk in another computer, and got a GRUB install :confused:

yes, same disk.

I'm just going to copy the /boot files into the other computer, and add this to the menu.lst  (Seems ok to mix/match (hdx,y) and uuid entries.

title		Ubuntu 9.04, kernel 2.6.28-3-rt
uuid		78b3017e-c986-45fb-b58c-d57cd48f4f9a
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=78b3017e-c986-45fb-b58c-d57cd48f4f9a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-3-rt
quiet

title		Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid		78b3017e-c986-45fb-b58c-d57cd48f4f9a
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=78b3017e-c986-45fb-b58c-d57cd48f4f9a ro  single
initrd		/boot/initrd.img-2.6.28-3-rt

---

### Post by logos34 on 2009-05-01
> **kevin2i said:**
> 
I'm just going to copy the /boot files into the other computer, and add this to the menu.lst  (Seems ok to mix/match (hdx,y) and uuid entries.


You might want to use the [symlink]("http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink") or configfile grub menu boot entry.  Set it  'n forget it (otherwise you'll continue booting the old kernel even after the next kernel update)

hope that helps

---

