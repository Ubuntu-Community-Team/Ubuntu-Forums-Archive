---
title: "How to encrpt ubuntu so it is not accesible from windows?"
date: 2009-02-19
forum: Security
---

### Post by athealwashington on 2009-02-19
Hi, I use Ubuntu for personal use and I have a lot of private stuff on it. But I let my family use Windows so I want to know how to encrypt ubuntu so it is not accessible from windows (it currently is I configured it) But besides my family poking around I don't want a windows Trojan to format all the hard drives, so correct me if I am wrong but if I encrypt the ubuntu hdd a virus can't access it right?




My hard drive configuration is like this:


40GB Maxtor with Windows XP on it. NTFS.


320GB with Ubuntu on it. Ext2.

---

### Post by bodhi.zazen on 2009-02-19
Well, there are 2 issues ...

Your best bet is to use the alternate CD and install into encrypted partitions.

In terms of windows malware, best way to stop them is not to use Windows. I am not aware of any windows malware that can read an ext2/3/4 partition and any malware that reformated you HD will ignore the underlying file system, so if you windows system is compromised not much you can do about it ...

---

### Post by lensman3 on 2009-02-19
Take a look at "truecrypt". "truecrypt.org".  It is Open Source.  You can encrypt partitions or you can encrypt subdirectories.  

You will have to install all of the kernel headers because you will have to compile truecrypt's source.  There is a nice GUI interface.  After the encrypted partition/file is mounted, navigation is done through the usual interfaces/GUI/etc.   There is good on line help as well as a help forum.

I have a Terabyte drive that I have encrypted for backups.  I first encrypted it all, then I laid down the new ext4 file system.  The drive is removable and if anybody installs it into another computer, it looks like it has never been formatted.  The information looks like noise.

You also could encrypt this under windows using truecrypt, then mount it under Ubuntu and decrypt it there too. The disk could be available under both OS's. The encryption will work both under M$ and Linux.

---

### Post by Tubes6al4v on 2009-02-20
I'd suggest using the alternate CD. You can get things set up much easier. Truecrypt is a great program, but I only use it for Volume encryption (i.e. storage). Your dm-crypt/LUKS volume can be accessed from Windows using  FreeOTFE, with your password of course.

---

### Post by cariboo on 2009-02-20
Why not just remove the software you installed to access ext3 partitions?

Jim

---

