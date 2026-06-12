---
title: "Need help with a backup solution"
date: 2010-03-01
forum: Server Platforms
---

### Post by vtec on 2010-03-01
I have a personal ubuntu server that provides apache, glassfish, firewall, routing, email, CVS,  MySQL, etc.... This server has been running for a while with two hard drives configured into a RAID 1 array. The array has two partitions, one for swap and one for the data. I currently back up the data with a removable hard drive. I use dd and create an image of one drive and the MBRs (partition tables) of each drive. In a disaster situation I can use this data to recreate one drive and then re mirror it to the second, or just boot the back up. I like this solution because I can easily recover from bare metal, and the backup is transparent. I can browser it if needed since its an uncompressed image of the drive. The one drawback is that I need to reboot the system with a linux CD to do the backup.

My hard drive space is almost at capacity. So what I want to do is add a third drive to the array and migrate it to RAID 5. However this will cause my current backup method to no longer work. How can I back up this RAID 5 array. I need to back up the entire system, and not just the data. I have made many tweaks to the system over the years that it has been running that I can't lose if a restore is needed. I have seen a large thread here that people have been using tar. My concern with tar is how do you use a tar archive to restore a system to a new array. Im assuming that you would need to setup the array and then just restore the archive? Also, i don't have much faith in using tar on a running system. Doesn't this open yourself up to corrupted backups? My second idea is using rsync. While I consider myself experienced in linux from 10 years of personal and professions use, I have not had much experience with this utility. Would rsync provide a more reliable way to backup a running system that would enable a bare metal restore later? I once read something about people using rsync with hard links to create a backup that could store many incremental backups. Does anyone do this? My main concern with both rsync and tar is not being able to restore the OS to the state that it was in at the time of the backup.

Sorry for the long post. Backups always worry me. You don't need to restore often, but when you do, the restore has to work.

---

### Post by Barriehie on 2010-03-01
While not running a RAID array I can say I've been using tar for my backups and have not had ANY issues with anything ever being corrupted.  On the rare occasion I've had to use them it worked flawlessly.  The backups are made on the fly in the wee hours of the AM and I'm emailed the results.  I'm not concerned with incremental backups since all of this is happening while I sleep and I've plenty of space.  I keep a 'rolling' 2 weeks worth.

HTH,
Barrie

---

### Post by R.Bucky on 2010-03-01
I use rsync with my home server and also at my employer. I set a couple of cron jobs for my databases, apache directory, and samba shares. Aside from that, I backup my bind, vsftpd, dhcp, and samba file once every month as they do not change at all or often. I backup the RAID1 server to external 1TB SATA drives. My personal server took me 2 hours to restore from a complete wipe (yes, I had time to kill!) including all data. 

I actually started with .tar, however I found that if a user at my employer had erased something, it was time consuming to untar a 20GB file for a hundred MB. If you have space issues, a .tar is alright, but not ideal.

---

### Post by vtec on 2010-03-01
Thanks for the replies. I guess my question now is, if you have a tar archive, or rsync backup of the root of a filesystem can you just dump that on a formatted drive or array and be up and running again?

---

### Post by Barriehie on 2010-03-01
> **vtec said:**
> Thanks for the replies. I guess my question now is, if you have a tar archive, or rsync backup of the root of a filesystem can you just dump that on a formatted drive or array and be up and running again?

Pretty much, there are some directories that should be excluded from the backup that you'll have to recreate.  Here's a good thread. [http://ubuntuforums.org/showthread.php?t=35087&highlight=howto%3A+backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=howto%3A+backup)

---

