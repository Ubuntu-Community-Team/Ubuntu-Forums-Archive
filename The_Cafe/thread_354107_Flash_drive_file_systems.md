---
title: "Flash drive file systems"
date: 2007-02-05
forum: The Cafe
---

### Post by BWF89 on 2007-02-05
I was formatting my flash drive with Mac Disc Utility and it gives you a slew of different file systems for format it with.

```
Mac OS Extended (Journaled)
Mac OS Extended
Mac OS Extended (Case-sensitive, Journaled)
Mac OS Extended (Case-sensitive)
MS-DOS File System
MS-DOS File System (FAT16)
UNIX File System
```

FAT-16 is supposedly the best file system for cross platform compatibility. I use computers with all three main OS's (Mac, Lin, and Win) on an almost daily basis.

If I formatted my drive to a non-Microsoft file system, like UNIX or one of the Mac OS Extended ones would I still be able to read my data on all 3 OS's?

If yes, which one should I use?

---

### Post by Brainfart on 2007-02-05
FAT16 is old.  Use FAT32 if you need to.  Not sure what format "UNIX File System" refers to, but I'd guess ext2 or ext3.  There's a [ext2 driver for Windows]("http://www.fs-driver.org/") (ext3 is backwards compatible, pretty sure ext4 will be as well) you can use, and OSX obviously should support it as well.  I don't recall that permissions are maintained in Windows with that driver, but they will be for the other systems.  If it wasn't for Windows, you could probably even get drivers for HFS (I think that's what Macs use) but I've never looked into a Windows solution for that.  Stick with ext2/3 or FAT32 to be sure.

---

### Post by FuturePilot on 2007-02-05
Edit:
Never mind):P 
How do you delete in this forum? I must be missing something.

---

### Post by BWF89 on 2007-02-05
> **Brainfart said:**
> FAT16 is old.  Use FAT32 if you need to.
According to Mac Disc Utility I can only format my flash drive as MS-DOS or MS-DOS (FAT-16). I don't know how to format my flash drive using Kubuntu. Or to add more file systems to list of file systems available to format with Mac Disc Utility.
> **Brainfart said:**
> Not sure what format "UNIX File System" refers to, but I'd guess ext2 or ext3.  There's a [ext2 driver for Windows]("http://www.fs-driver.org/") (ext3 is backwards compatible, pretty sure ext4 will be as well) you can use, and OSX obviously should support it as well.  I don't recall that permissions are maintained in Windows with that driver, but they will be for the other systems.  If it wasn't for Windows, you could probably even get drivers for HFS (I think that's what Macs use) but I've never looked into a Windows solution for that.  Stick with ext2/3 or FAT32 to be sure.
What's the difference between using ext2 or ext3 as my file system, besides one being supported by that program you gave me a link to and the other not.

I don't have a Windows machine at home (yet). If I was going to use my files on the ext2 file system at a school computer that doesn't give us students admin privileges would it allow me to install and use the program or would I have trouble.

---

### Post by Brainfart on 2007-02-05
Sounds like you'd better stick with FAT32.  I'd assume that's what MS-DOS (not 16) is.  You could also format it on one of your school computers (if you have that permission; I'd be slightly surprised if they blocked even that).  

If you want to format a disk using Kubuntu look at the mkfs command (there's also mkfs.ext2, mkfs.<other formats>; mkfs just calls the appropriate other one as you tell it to).

---

