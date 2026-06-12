---
title: "SoftwareRAID during Install"
date: 2008-07-14
forum: Server Platforms
---

### Post by duiu on 2008-07-14
I am installing ubuntu Server 8.04. I have a 8.7GB install IDE drive. I have two 1TB SATA drives that I want to mirror using RAID1. The first time I did this, I screwed it up and set two active drives and stuff got screwed and it wasn't mirroring. So I went through the install again. I configure the two SATA drives to be "physical volume for RAID" and then go to "Configure software RAID" The old RAID shows up again, and I can't delete it. It says it's "might be in use." How the heck do I get it to go away so I can set 1 active and 1 inactive drive? And then how do I tell that my RAID is actually working?

Thanks

duiu

---

### Post by fjgaude on 2008-07-15
I'm not sure how to get out of your situation, but I do know that once you setup a drive as part of an array the only way to get it out is to have **mdadm** zero the drive's superblock.

Now where you are, you have to have mdadm installed on your machine. Then use this command to zero:

```
sudo mdadm --zero-superblock /dev/sd[n]
```

That might do it.

To learn about software raid on Linux here's some links:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz

[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)

Take your time for there is lots to learn when using software raid.

---

### Post by duiu on 2008-07-15
OK, thanx. I decided to go a long route and install windows and reformat my drives in NTFS to wipe everything clean. Then I'll restart. 

Formatting 1TB takes a long time...

---

