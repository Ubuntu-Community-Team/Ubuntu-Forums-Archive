---
title: "mounting large ext3 drives in Vista (w/size 256 inodes)"
date: 2009-01-24
forum: Windows
---

### Post by zeus77 on 2009-01-24
I am trying to mount a 1.5TB ext3 drive in Windows Vista (I'd even be happy with read-only support), but I cannot succeed.  Note that the drive has inodes of size 256, which is the Ubuntu default as of intrepid 8.10.  Reformatting my drive is not an option I want to consider.

So far as I am aware, there are only 2 freely available ext2/3 filesystem drivers for Windows that are actively being developed, but neither seems to be able to mount a large ext3 volume with size 256 inodes:

[Ext2 IFS]("http://www.fs-driver.org/") was what I used for some time because its interface was slicker and it was easier to use.  It is closed source, however, and the current version only supports size 128 inodes.  Until the developer adds support for size 256 inodes, this is not a feasible solution.

[Ext2Fsd]("http://sourceforge.net/projects/ext2fsd") has come a long way since I first used it, and looks quite usable now.  It does not suffer from the inode limitation, and I am able to successfully mount 300GB and 500GB drives with Vista.  However, it refuses to mount my 1.5TB drive.  There are no error messages, it just simply won't mount.  I could not find documentation about the largest supported drive size.  

It's hard to believe that, in 2009, it is still not possible to mount a modern drive that has been formatted with the default parameters.  Has anyone successfully mounted a large ext3 drive (formatted with the Ubuntu defaults, i.e. size 256 inodes) in Vista?  

Thanks.
zeus77

---

### Post by UV-Ray on 2009-02-04
Ext2Fsd does not reboot system automatically and does not work without reboot.
Install it, then make sure service "Ext2 Volume Manager" will start on automatically. Reboot.
Ubuntu drive with inode=256 should be visible now.

---

### Post by zeus77 on 2009-02-09
I did reboot as requested during installation, and have no problem mounting 300 GB drives with inode=256.  The problem is mounting LARGE drives (in this case 1.5 TB).  Has anyone successfully mounted such a large drive?

Thanks.
zeus77

---

