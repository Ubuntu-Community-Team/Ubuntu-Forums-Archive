---
title: "EncryptedFilesystemOnIntrepid"
date: 2009-05-02
forum: Security
---

### Post by ubuntu01 on 2009-05-02
I have followed the instructions on [https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid) and still cannot get the device to boot.  Tried more than once.

Whenever I get to the point where I am to run Cryptotest from the boot menu I get the following error:

Begin: Mounting root file system... ...
/init: line 217: syntax error: 0x7fb1082-e1cd-4929-97e8-e5be589a2ca8
[   5.233223] Kernel panic - not syncing: Attempted to kill init!

Any help would be much appreciated.
I am running under 9.04, Jaunty Jackalope

Thanks in advance,
J.

---

### Post by lelmo85 on 2009-06-26
Did you get a reply? I have same problem.Boot code (multiboot-Fedora 9;XP (both work ok)code for Ubuntu (attempted) boot: (/ is on Fedora)
map   (hd0)(hd1)
map   (hd1)(hd0)
root  (hd1,0)/media/disk
kernel /boot/vmlinuz-2.6.28-11-generic ro root=UUID=0807897e-c416-4414-ae9e-e38509c3b6e2 all_generic_ide
initrd /boot/initrd.img-2.6.28.11-generic

At boot the code runs and then "blows up" exactly like shown in your post. I am a poor coder-dont know how to correct "/init:line 217 syntax error.

---

