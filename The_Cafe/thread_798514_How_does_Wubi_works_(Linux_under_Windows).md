---
title: "How does Wubi works (Linux under Windows)?"
date: 2008-05-18
forum: The Cafe
---

### Post by frenchn00b on 2008-05-18
Wubi is easy way for getting linux running with dualbooting; but 
[http://www.howtoforge.com/wubi_ubuntu_on_windows_p2](http://www.howtoforge.com/wubi_ubuntu_on_windows_p2)
  
Where does the ext3 is installed ?? into the ntfs without partitions we all know that linux cannot write in ntfs (copyrights) ? captive? then it may be risky for the data?

---

### Post by meborc on 2008-05-18
as long as i remember, ubuntu system will be installed all into one file in ntfs... like virtualbox hard-drives... 

anyone care to comment/correct?

---

### Post by bobbocanfly on 2008-05-18
[http://wubi-installer.org/faq.php:](http://wubi-installer.org/faq.php:)

> How does Wubi work?

Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.

Basically the ext3 filesystem is put into a single file on a hard disk (like a virtualbox/vmware hard disk) but unlike vmware Wubi lets you boot directly into it.

---

### Post by frenchn00b on 2008-05-18
> **bobbocanfly said:**
> [http://wubi-installer.org/faq.php:](http://wubi-installer.org/faq.php:)



Basically the ext3 filesystem is put into a single file on a hard disk (like a virtualbox/vmware hard disk) but unlike vmware Wubi lets you boot directly into it.
  
but the linux cannot write into NTFS ... hence there is need to put the data on a usb stick ?

---

### Post by meborc on 2008-05-18
> **frenchn00b said:**
> but the linux cannot write into NTFS ... hence there is need to put the data on a usb stick ?

dude, where have you been living... linux CAN write into NTFS... :) has done that for some time now... [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by bobbocanfly on 2008-05-18
> **frenchn00b said:**
> but the linux cannot write into NTFS ... hence there is need to put the data on a usb stick ?

When booting i dont think Wubi actually does much with NTFS. It picks up the ext3 partition file and boots directly into the ext3, all of which is handled by the boot loader, which means Ubuntu doesnt really have to touch it.

Disclaimer: I havent used Wubi, doubt i ever will, so i dont *really* know what im talking about, this is just how i understand it works from reading some FAQs

If you use irc you might want to talk to 'xivulon' on freenode as he seems to be the main developer.

---

### Post by FuturePilot on 2008-05-18
> **bobbocanfly said:**
> When booting i dont think Wubi actually does much with NTFS. It picks up the ext3 partition file and boots directly into the ext3, all of which is handled by the boot loader, which means Ubuntu doesnt really have to touch it.

Disclaimer: I havent used Wubi, doubt i ever will, so i dont *really* know what im talking about, this is just how i understand it works from reading some FAQs

If you use irc you might want to talk to 'xivulon' on freenode as he seems to be the main developer.

That's how I would think it is. You're basically booting a file that has an EXT3 file system inside of it.

---

