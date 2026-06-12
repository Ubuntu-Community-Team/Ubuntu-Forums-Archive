---
title: "making read only files writable"
date: 2009-12-22
forum: Security
---

### Post by gamer4lyf3 on 2009-12-22
I have a portible hard drive and I'm trying to copy a folder from the hard drive onto a computer. However, the file is "read only" and I can't change it to read and write. Is there any work around so I can copy the folder?

---

### Post by cucuru on 2009-12-22
Are you the owner? when it happen to me is because I'm not the owner, so I can change the options, try with chown.

I hope I'll help you.

Regards

---

### Post by BkkBonanza on 2009-12-22
Read only is not going to prevent you from copying a file. It will prevent you from changing the file or deleting it. You can use "chmod u+w filename" to make it writeable but you need to have ownership or root rights on the file to do that.

---

### Post by gamer4lyf3 on 2009-12-22
Thanks for the responses. It looks like I'm not able to even make a folder in my own portable hard drive, or for that matter copy a folder. What could be causing this and how would I change it?

---

### Post by doas777 on 2009-12-22
it's probably owned by root. if you open a window to the drive and rightclick -> Properties -> Permissions, who is shown as the owner?

---

### Post by rookcifer on 2009-12-22
Welcome to Linux.  File permissions might seem daunting, but once you learn how it works, it will make a lot of sense.  [This site]("http://www.tuxfiles.org/linuxhelp/filepermissions.html") does a good job of explaining it all.

Basically, your problem seems to be you don't own the directory.  That can be taken care of with the *chown* command.  After that you might have to make it writable with the *chmod* command.

---

### Post by FuturePilot on 2009-12-22
It depends on what the file system is. If it is FAT* or NTFS changing permissions won't do anything since those file systems do not understand Linux permissions. If it's a Linux file system, Ext*, XFS, etc etc, then you probably just need to change the permissions.

---

### Post by mikewhatever on 2009-12-22
The ownership and the read only attribute are irrelevant, since the original file is not modified by copying. I don't think the OP has explained the problem very well.

---

### Post by doas777 on 2009-12-23
> **mikewhatever said:**
> The ownership and the read only attribute are irrelevant, since the original file is not modified by copying. I don't think the OP has explained the problem very well.

umm, I don't think that the problem is reading from the source, but in writing to the destination.

---

### Post by koenn on 2009-12-23
It's still unclear what the OP is trying to do : copy from, or copy to the external drive:

> **gamer4lyf3 said:**
> I have a portible hard drive and I'm trying to copy a folder** from the hard drive** 

> **gamer4lyf3 said:**
> It looks like I'm** not able to even make a folder in my own portable hard drive**, or for that matter copy a folder. 

---

