---
title: "How do you back up ubuntu server system?"
date: 2020-04-27
forum: Server Platforms
---

### Post by 2niekai on 2020-04-27
I have a problem with this.
 The common rsync method does not work, because it has no permission to copy files from lxcfs folder. 
How should I do full system backups? 
How do you do it?

---

### Post by LHammonds on 2020-04-27
I use LVM to create partition backups.  I only use rsync for specific data backups such as web sites, config files and shares.

**EDIT**: I have included direct links to the pertinent sections of my server guide.

[Partition design]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p614") (how I did it for 18.04...I am using fewer partitions in 20.04)
[Backup LVM partitions using FSArchiver]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p632")
[Partition-level restores]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244&start=20#p633")

**EDIT:** 20.04 version of the 18.04 article above:
[Partition design]("https://hammondslegacy.com/forum/viewtopic.php?p=811#p811")
[Backup LVM partitions using FSArchiver]("https://hammondslegacy.com/forum/viewtopic.php?p=833#p833")
[Partition-level restores]("https://hammondslegacy.com/forum/viewtopic.php?p=834#p834")

LHammonds

---

### Post by 2niekai on 2020-05-14
Thank you  LHammonds, will check that out.

---

### Post by SeijiSensei on 2020-05-14
If you run rsync as root with sudo, you shouldn't have any permission problems.

---

### Post by Nr1Dane on 2020-05-19
Really cool stuff here, thank you for this!

---

