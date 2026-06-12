---
title: "[SOLVED] Adding a Hard drive"
date: 2007-12-12
forum: The Cafe
---

### Post by Techwiz on 2007-12-12
I am considering adding a second hard drive to my desktop and I was wondering 2 things:
1. How does Ubuntu deal with another hard drive that has just been added?
2. Is there any way of "merging" the two drives space into 1 virtual drive?

---

### Post by LaRoza on 2007-12-12
> **Techwiz said:**
> I am considering adding a second hard drive to my desktop and I was wondering 2 things:
1. How does Ubuntu deal with another hard drive that has just been added?


It won't be in fstab, so you will have to manually mount it (and do it as root)

You can add it too fstab, if you want.

You should reformat it when you get it, if you don't have to share it with Windows, make it ext3.

---

### Post by koenn on 2007-12-12
1- Ubuntu might recognize the disk if it has a filesystem ( if it's "formatted"), and might mount it to /media. Not too sure here. You may have to make ubuntu "handle" it.

2- you can, in several ways. 

I did a few exercises about this once - here are my notes:
[http://users.telenet.be/mydotcom/howto/linux/disks1.htm](http://users.telenet.be/mydotcom/howto/linux/disks1.htm)

---

### Post by LaRoza on 2007-12-12
> **koenn said:**
> 1- Ubuntu might recognize the disk if it has a filesystem ( if it's "formatted"), and might mount it to /media. Not too sure here. You may have to make ubuntu "handle" it.


It will be mounted under /media, and will have a weird name or a generic one, unless it has a label.

---

### Post by Jimmey on 2007-12-12
When you do, make sure that you set up the jumper pins on the second drive properly. You probably want to set it to "slave", or "cable select". Info on that will be on the back of the drive.

You can use Gparted to put an EXT3 filesystem on the drive.

There's no real need to merge two drives together. All you need to do is to add a line in fstab that mounts the drive with the "user" option. If you really wanted to, you could have the drive mount in a folder in your /home folder, but I've got a three drives mounted in /media/hdX (1 to 3), and it's fine.

---

### Post by Techwiz on 2007-12-12
Thank you, I will try that.

---

### Post by LaRoza on 2007-12-12
> **Jimmey said:**
> When you do, make sure that you set up the jumper pins on the second drive properly. You probably want to set it to "slave", or "cable select". Info on that will be on the back of the drive.


Sata drives don't use that, in fact, they can't, one drive per cable/controller.

---

### Post by Texas_tea on 2007-12-12
not to go off topic to terribly but i linked a second hard drive up to my computer to delete files that was causing the dreaded blue screen.

I was desperate cause i did not want to reload windows and all the drivers again.

It worked!!!

---

### Post by Lostincyberspace on 2007-12-12
> **Techwiz said:**
> 
2. Is there any way of "merging" the two drives space into 1 virtual drive?

If you can reinstall you can make it a raid it takes quite a bit of work though. :)

---

### Post by mips on 2007-12-13
> **Techwiz said:**
> 
2. Is there any way of "merging" the two drives space into 1 virtual drive?

LVM works a charm.

---

### Post by Techwiz on 2007-12-13
> LVM works a charm.
Thank you so much!

---

