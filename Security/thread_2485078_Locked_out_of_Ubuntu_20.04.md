---
title: "Locked out of Ubuntu 20.04"
date: 2023-03-19
forum: Security
---

### Post by bhubunt on 2023-03-19
Hi,
I am no longer able to access the Ubuntu 20.04 OS -- desktop -- on a Lenovo x230i, on which I am writing a book.

On Friday, something went wrong  while typing in the two passwords I need to transition to my Ubuntu 20.04 files. 

Instead of getting the Ubuntu log in screen, there now just is a black screen with a blinking cursor in the upper left corner.

Today, I tried another internal disk on this laptop, after installing another Ubuntu OS -- with some difficulty. Now I only have to type in the initial password -- not two passwords -- before the Ubuntu log in screen comes up. 

However, I would really like to continue working on the former internal disk and wonder how I can call up the Ubuntu 20.04 log in screen again.  

Suggestions welcome.

P S this is a different Lenovo from the Lenovo x230 discussed in another thread....

---

### Post by oldfred on 2023-03-19
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Of course run from live installer with drive you are having issues with.
Since mention of two passwords, is drive encrypted? If so you must have good backups as most issues with encryption are easiest resolved with reinstall & restore from backup.

---

### Post by bhubunt on 2023-03-19
Hi, 
Thanks very much for the suggestions.

The home folder is encrypted indeed. The first two passwords are bios related; then there are two more passwords for the Ubuntu files. 

Is there any way to get such files off of an encrypted internal disk on another computer? I have back ups, but it would be nice to know.

So I gather this is a booting problem then? 

Will boot repair restore access to the files, in case the disk is not damaged?

---

### Post by oldfred on 2023-03-19
Boot-Repair's most common fix is a grub update or reinstall of grub.
But report can tell us lots of info about configuration and if other repairs may be required.

I do not use encryption, but if you install the encryption software which may not be in live installer & correctly mount it, you may be able to see drive.
But those that use encryption, say if more than an hour to fix, just reinstall & restore from backups.

---

