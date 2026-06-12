---
title: "Problems with running programs in Ubuntu from USB drive"
date: 2014-10-18
forum: Ubuntu Application Development
---

### Post by flex567 on 2014-10-18
I use Eclipse and Ubuntu linux 14.04. When I create new projects(c++) in Eclipse  and when I save them on hard disk, compiled programs run as they should. 
If I try  to save my  programs(using Eclipse) on the USB drive and if try to compile them and run them from an USB drive I get this error message: 
```
Error starting process.
Exec_tty error:Cannot run program "/media/seba/KINGSTON/tester/tester/Debug/tester": Unknown reason
Exec_tty error:Cannot run program "/media/seba/KINGSTON/tester/tester/Debug/tester": Unknown reason
Exec_tty error:Cannot run program "/media/seba/KINGSTON/tester/tester/Debug/tester": Unknown reason
```

Is there a way to fix this problem so I could compile and run programs from my USB drive with Eclipse?

---

### Post by ajgreeny on 2014-10-18
Your usb drives are probably formatted to a Windows filesystem; ntfs or fat32.  That will not allow you to add execute permission to the files that you are trying to run.

You may be able to do what you want if you reformat the USB drive to ext2/3/4 which should allow execute permissions, though for normal use with read/write permissions you will need to change owner of the mountpoint folder, or even give it full 777 permissions if that is not too insecure for you.

---

### Post by flex567 on 2014-10-19
> 
You may be able to do what you want if you reformat the USB drive to  ext2/3/4 which should allow execute permissions, though for normal use  with read/write permissions you will need to change owner of the  mountpoint folder, or even give it full 777 permissions if that is not  too insecure for you.

After I do all this will I be able to use the USB key in Windows?

---

### Post by ajgreeny on 2014-10-19
> **flex567 said:**
> After I do all this will I be able to use the USB key in Windows?

No, sorry but windows can not read or use the Linux format types, and I don't think it can even see more than the first partition on a flash drive, if that is what we have here.

If it is an external hard drive, not flash memory, you could try having an ntfs partition on the first part of the flash, eg /dev/sdb1 in Linux terminology, and a second ext partition as /dev/sdb2, but that is something I have never done and do not even know if it's possible, though I can't see why it wouldn't be.

---

### Post by flex567 on 2014-10-27
how can i reformat the USB drive to ext2/3/4 ?

---

### Post by pauls2 on 2014-12-08
You might try using GParted. You should be able to set two partitions one in NTFS and the other in ext4. Your linux programs can use the ext4 partition and your windows stuff can use the NTFS partition.

Note: I have never tried this so it is all just conjecture. If you attempt it backup anything and everything on the thumb drive because creating partitions can, and likely will, delete any existing files unrecoverably.

---

