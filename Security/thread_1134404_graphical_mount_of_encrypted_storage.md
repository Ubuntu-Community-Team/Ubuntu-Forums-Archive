---
title: "graphical mount of encrypted storage"
date: 2009-04-23
forum: Security
---

### Post by StefanX on 2009-04-23
I am using a dm-crypt+LUKS encrypted USB harddisk for several years. When connecting the drive a window appears prompting for the password. After entering the password the storage is mounted automatically. This drive is formated with ext3.

Now I bought a new eSATA harddisk which is encrypted the same way. When connecting the harddisk I don't get any prompts. Also the drive is not listed in gnome menu. Instead I have to unlock and mount the storage manually in the console (with cryptsetup and mount). This drive is formated with ext4 and I am using an appropriate kernel.

I don't have any entries for these drives in /etc/fstab.

Any idea how to get a prompt and automount for the eSATA drive? Any help is really appreciated!

---

### Post by agent8131 on 2009-05-06
I ran into this issue as well.  I wasn't surprised that the systems act differently for sata vs usb or firewire.  However, this is something that the user should have control over.  For my esata device I want it to work just like it did when the same hard drive was connected via a usb enclosure.  So I thought I would check the forums first to see if anyone had resolved this issue.  I can imagine that this will come up again as more people switch to esata.  For me it was not the speed boost but rather that I could use the existing tools such as smartmon and sdparm that made esata an attractive option.

So the question remains: how can we get an external esata device to be recognized as a "removable drive"?

---

