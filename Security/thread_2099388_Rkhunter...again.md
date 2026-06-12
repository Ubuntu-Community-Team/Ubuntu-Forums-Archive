---
title: "Rkhunter...again"
date: 2012-12-29
forum: Security
---

### Post by DanR01 on 2012-12-29
I know there are a ton of threads on rkhunter and the large number of false positives it generates so I'm slightly hesitant to post this. 

I've got lots of warnings about changed file properties for most of the coreutils (uname, echo, md5sum, chown, pwd....) dating from the 19 November. I've checked the md5sums for the packages against those stored in /usr/share and none of them match.

In addition I've got a warning about Group '_cvsadmin' has been added to the group file.

I'm hoping that this is due to an update (I don't run rkhunter --propud after every update as I know I should) but the mismatched md5sums have me slightly worried. My log files don't stretch back that far. I'm running 12.04.

Is this anything to worry about or should I just uninstall rkhunter and save myself the bother?

---

### Post by cariboo on 2012-12-29
You should have a /var/log/dpkg.log.*.gz, unless you have removed logrotate. You can read these logs without decompressing them using mc.

---

