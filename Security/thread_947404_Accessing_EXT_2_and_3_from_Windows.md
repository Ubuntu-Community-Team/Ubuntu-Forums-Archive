---
title: "Accessing EXT 2 and 3 from Windows"
date: 2008-10-14
forum: Security
---

### Post by lukjad on 2008-10-14
This [program]("http://www.fs-driver.org/") allows for accessing the EXT2/EXT3 file systems directly from Windows. I was wondering if this would be a security hazard if a malware program were to infect the Windows partition, would it be able to damage the Linux partition? Could it delete or damage files?

Sorry if I sound a bit paranoid, but I was just wondering if there would be any reason for not installing this program.

---

### Post by caljohnsmith on 2008-10-14
I think it definitely would be possible for malware in Windows to damage your linux partition if you have your linux partition mounted with that program, because that program allows both read and write access. But since your linux partition doesn't have any Windows system files that Windows malware would be interested in, then realistically, probably the worst that would happen would be the malware putting some files in your Linux partition; but those files would be harmless since they wouldn't run in LinuxLand.

---

### Post by cdenley on 2008-10-14
Windows malware would probably be able to damage the drive whether it is mounted or not by writing directly to the disk. It just isn't likely. I would be more worried about the driver corrupting your filesystem. I'm not sure if it's considered stable.

---

### Post by Archmage on 2008-10-14
Since a virus could wipe out your whole harddrive, there is much additional risk that you are putting you under.

---

### Post by hyper_ch on 2008-10-14
I agree cdenley but think ext2/3 drivers will not corrupt the linux file system ;)

---

### Post by lukjad on 2008-10-14
Okay. I was trying to weigh the convenience factor against the threat and I guess I got my answer. Thanks for the help.

---

### Post by SSVegito888 on 2008-10-14
Also, If you use EXT2IFS from the site and you use an ext3 partition in windows, it will mount the volume as an ext2 partition.


Ext3 and EXT2 partitions are backward compatible.

As far as I know Ext3 filesystems are basically Ext2 but with support for journaling 

So you will be able to read\write to the partition but Ext3's journaling will be disabled.



Also, if you use this software I reccomend downloading the mountdiag command line tool from the same site.

[[COLOR="Blue"]http://www.fs-driver.org/download/mountdiag.exe[/COLOR]]("http://www.fs-driver.org/download/mountdiag.exe")


If you have trouble mounting the partition or some other problem you can run the mountdiag utility and it will tell you what you need to do to fix the problem.




When I install the EXT2IFS software I usually put the mountdiag utility in C:\windows\system32


I realize, this may not be the best practice in the world, but I hate messing with paths in Windows.


Someone else may be able to tell you if it is okay to put the mountdiag utility in the system32 folder, because I am not sure.

---

