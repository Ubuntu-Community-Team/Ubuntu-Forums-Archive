---
title: "Trouble booting 14.04.5 LTS, Trusty Tahr 64 bit, lvm root, separate boot partition"
date: 2017-02-27
forum: Server Platforms
---

### Post by campbeld2017 on 2017-02-27
Hi all

After fixing mbr, purging and reinstalling grub2, finally I get initrd image running

But the system gives me "/dev/mapper/drv--03-root does not exist" and drops me into initramfs shell.

Tried waiting until the device shows up in blkid listing and then exiting, the system appears to just be unresponsive.

Tried waiting until the device shows up in blkid listing, mounting the device "mount /dev/mapper/drv--03-root /root" and then exiting, the system gives dm-0 device or resource is busy error.

Also tried "rootdelay=300" at one point but it didn't appear to work.

Now I'm wondering if there is some way to see what the system is trying to do, how do I know whether it successfully mounted root and whether it maybe got stuck on the kernel?


Not sure what the [COLOR=#333333][FONT=&amp]etiquette is but the log from boot-repair is large so I thought it would be good to just include the ubuntu pastebin link.[/FONT][/COLOR]
[http://paste.ubuntu.com/24082116/](http://paste.ubuntu.com/24082116/)

---

