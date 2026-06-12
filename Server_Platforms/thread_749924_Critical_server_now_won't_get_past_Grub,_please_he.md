---
title: "Critical server now won't get past Grub, please help"
date: 2008-04-08
forum: Server Platforms
---

### Post by googlah on 2008-04-08
Okay, so after 69 days I decided to reboot my server which has 10 dynamic webpages, 10 databases consisting of hundred of MB's, mailboxes etc.

After Grub has been loaded, I choose the only kernel I have. This is what it gives me back:

/init: /init: 158: /bin/sleep: not found
/init: /init: 158: /bin/sleep: not found
/init: /init: 158: /bin/sleep: not found
/init: /init: 158: /bin/sleep: not found
/init: /init: 158: /bin/sleep: not found
Check root= bootarg cat /prov/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/edfc39ca-e61a-47c5-af5a-39d60686c695 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.13-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

HERE I CAN'T DO MUCH AT ALL. I can browse around in a few folders and "cat" stuff, but no bash commands are recognized. No /boot is found here, no /etc/fstab either. Are they supposed to be in (initramfs) line? What can I do? Any ideas? Note that no "regular" data seem to be found. Like directories or files. It's just some basic (initramfs) shell here.

Who ever who can help me out with this issue can be rewarded with some $$$, because it is such important data I need to get back. Can I edit the Grub commands in some way? Can I work it out with a LiveCD? I've tried to set it to root=/dev/hda1, but it just tells me ALERT! /dev/hda1 does not exist. Dropping to a shell! still.

Reward or just some really kind help would be great. Thanks all.

---

### Post by netlogic on 2008-04-09
it seems to me, it can't find your kernel path...

1. when the computer boots to grub, press esc
2. hit "c" for a commandline option
3.  type "find /etc/fstab"
4.  it might come back with 
(hd0,0)
this means hd0 --> 1st drive
0 --> first partition
5. hit "esc" to exit grub
6. pick your kernel
7. hit "e" to edit your grub
your menu might look like
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hdx ro single
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot

8. hit "e" and edit your kernel to proper location as the result you got from number four.
9. hit "esc" until you get the main menu
10. hit "enter" to boot
11. once you booted use vi or nano to edit /boot/grub/menu.lst and permanently fix it.

---

### Post by netlogic on 2008-04-09
also, while you are in the grub menu.
you can also find it by trying these commands

find /vmlinuz
if it comes back with
(hd0,1)
double check by
root (hd0,1)
it might come with something like 
Filesystem type is reiserfs, partition type 0x83

also, you can take a look at your fstab by
cat /etc/fstab

---

### Post by googlah on 2008-04-09
Okay, thanks for helping me out so far. It was really appreciated and you will be rewarded for the very important job you doing here. Been down now for 9 hours and people are missing their sites and data. Your post was extremely useful, I have learned myself some new things now. But to the thing, it seem still like it can't boot. Did I do anything wrong perhaps?

Okay, you told me step by step. I am going too. Grub starts.
I choose Ubuntu 7.10, kernel 2.6.22-14-server by pressing 'e'.
There are Recovery Mode too, but that does not work either.

after pressing 'e' the lines look exactly like this,

root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-server root=UUID=edfc39ca-e61a-47c5-af5a-39d60686c695 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-server
quiet

In here, I press 'c' to go to command line, and type "find /etc/fstab". That gives me.
(hd0,0)

By typing "cat /etc/fstab" in command line, gives.
proc              /proc                       proc                                             defaults                                     0    0
/dev/hda1    /                              ext3                                             defaults,errors=remount-ro    0      1
/dev/hda5    none                       swap                                            sw                                             0     0
/dev/hdb0    /media/cdrom0       udf,iso9660 user,noauto,exec                                                     0      0


Anyway, I guess that's all worth to know. Any idea on how my kernel and root line should look like to "force" it to boot? Straight answers are appreciated, so we both understands. The one who can help me out can of course get something through PayPal. Or should I edit my /etc/fstab with something?

---

### Post by googlah on 2008-04-09
> **netlogic said:**
> it seems to me, it can't find your kernel path...

4.  it might come back with (find /etc/fstab)
(hd0,0)
8. hit "e" and edit your kernel to proper location as the result you got from number four.
9. hit "esc" until you get the main menu
10. hit "enter" to boot

So you mean, in my case, it would be
kernel /boot/vmlinuz-2.6.22-14-server root=(hd0,0) ro quiet splash ?

That won't work in my case. :(

---

### Post by smileypaul on 2008-04-09
grab a live cd and see if you can mount your disk .. 

Its very obvious it just can't see the disk.

Once mounted, although i can't remember how, theres a way to get the UUID of the disk, make sure its the right one.

---

### Post by netlogic on 2008-04-09
> **googlah said:**
> 
kernel /boot/vmlinuz-2.6.22-14-server root=UUID=edfc39ca-e61a-47c5-af5a-39d60686c695 ro quiet splash


change this to

```
kernel /boot/vmlinuz-2.6.22-14-server root=/dev/hda1 ro quiet splash
```

---

### Post by netlogic on 2008-04-09
> **smileypaul said:**
> grab a live cd and see if you can mount your disk .. 

Its very obvious it just can't see the disk.

Once mounted, although i can't remember how, theres a way to get the UUID of the disk, make sure its the right one.

na, if the disk isn't there, it wouldn't even boot to grub.

---

### Post by koenn on 2008-04-09
seeing the diagnosis so far, i.e. that you can get grub to start, but that grub faills to find your kernel, would it be worth a try to
1- boot an install cd
2- choose "rescue"
3- proceed to the point where you can select the menu item "install grub" (or something similar)
4- run "install grub" - this should scan tour disks, detect kernels, and update the grub menu
5- exit
6- reboot

you should probably try this on a test system (VM ?) to see if you can actually do that without making things worse, and to note the exact steps (eg make sure you can actually skip steps such as 'partition hard disks' , cause you do not want that)

disclaimer. no guarantees, try at your own risk

---

