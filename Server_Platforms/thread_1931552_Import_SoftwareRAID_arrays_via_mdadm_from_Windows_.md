---
title: "Import SoftwareRAID arrays via mdadm from Windows arrays."
date: 2012-02-25
forum: Server Platforms
---

### Post by stolpee on 2012-02-25
Hi 

I followed this guide : [http://ubuntuforums.org/showthread.php?t=833653](http://ubuntuforums.org/showthread.php?t=833653)


"sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdd2 /dev/sdc2"
"sudo mkdir /media/Windows"
"sudo mount -t ntfs /dev/md0 /media/Windows"

Everything works fine, from building to mounting, until I view the content.. I'm missing a lot of files and some files are viewed as something they're not..

In the link above he mentioned that it could be a chunk size problem, but I've tried changing that, to no avail.

Note that I CAN build the arrays, and I CAN mount them... In Windows everything works fine.


Regards
Stolpee

---

### Post by SeijiSensei on 2012-02-26
After you build /dev/md0 you need to format it.  Just mounting it with "-t ntfs" isn't sufficient; you need to format it with NTFS.  (I'm not sure I understand why you're doing this, since Windows won't be able to see this mdadm device at all.)  

To do this, install [ntfsprogs]("http://manpages.ubuntu.com/manpages/lucid/man8/ntfsprogs.8.html") and use the mkntfs command to format the filesystem.

---

### Post by rubylaser on 2012-02-26
With the --build command, you can mount arrays built with Windows software RAID (I think it only supports RAID levels 0 and 1 though).  This should work, if you are trying to assemble from the correct partitions.  Unfortunately that post will have to be your guide. Although I'm very comfortable with mdadm, I don't ever use Windows softraid, or have I tried to port it to linux via mdadm.

---

