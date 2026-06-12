---
title: "Backup server 20.04"
date: 2021-09-02
forum: Server Platforms
---

### Post by peter-1984 on 2021-09-02
Hi,
What is the better way to do the server backup? I mean the complete way to be able to restore everything to the point on which backup has been done.

---

### Post by scorp123 on 2021-09-02
You may want to check the on-going discussion here?

[https://ubuntuforums.org/showthread.php?t=2466648&p=14057078#post14057078]("https://ubuntuforums.org/showthread.php?t=2466648&p=14057078#post14057078")

---

### Post by peter-1984 on 2021-09-12
Hi,
Thanks a lot.

---

### Post by peter-1984 on 2021-09-30
Hi,
Is it possible for me to back up the whole server OS and later on restore it into another OS (to overwrite the whole OS with the previous server backup)?

---

### Post by MAFoElffen on 2021-10-01
You can do what you want... 

As a Sys Admin, my plans usually followed a staggered strategy, where I did both full imaging for monthly's and incrementals between those. My disaster recovery had steps, depended on how bad the disaster was, from pre-created boot recovery disks, where (in a total system loss, where a whole cluster failure with no failover) I could restore the images and get then incrementals to get back to a point in time... or less.= (if only needing to get back to a point in time with certain files).

My strategies had alternates to alternates. If the network backup server, which did imaging and deployments, was down, iDRAC or BMC to remote deploy, or then a removable boot recovery media at the machine... Many ways to do the same. From different perspectives.

As people will tell you, one of your steps should be "to test" that you can successfully restore what you need to, to make sure your plan works.

---

### Post by LHammonds on 2021-10-01
> **peter-1984 said:**
> Hi,
Is it possible for me to back up the whole server OS and later on restore it into another OS (to overwrite the whole OS with the previous server backup)?

Most-definitely yes.  My backup approach is very similar to MAFoElffen.  I create monthly snapshots of my partitions as well as more frequent full/differential backups of the data.

I use [LVM snapshots + fsarchiver]("https://hammondslegacy.com/forum/viewtopic.php?p=833#p833") to create my partition-level backups.  To restore them, I use [SystemRescueCD + fsarchiver]("https://hammondslegacy.com/forum/viewtopic.php?p=834#p834").  When I created my volumes, I made sure to label them which makes identifying them during restoration VERY easy when using the fsarchiver command with the "probe" option.

Data backups vary from machine to machine though so I tend to have specialized backup scripts...such as for web servers, database servers, etc.

LHammonds

---

