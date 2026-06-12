---
title: "Is this Backup/Recovery scheme good enough?"
date: 2011-10-04
forum: Security
---

### Post by rs2k on 2011-10-04
This is the current backup/recovery scheme I'm intending to use on my server. It hosts several websites(eCommerce/forums) and a minecraft server.

1. I have a list of all installed programs and how I installed them. Software versions, etc. If the server was destroyed I can follow the list and setup the same OS and software on another system within a few hours.

2. I have a list of important data directories and backups of data and config files.

3. I have a backup directory of "snapshots" that I create with cp and rsync using this page as a reference: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/). My plan is to have hourly, daily, weekly, and monthly snapshots

4. Mysql database backed up daily with crucial data like emails sent to a second computer instantly.

5. The backup directory is rsync'd to a remote computer nightly and kept on two separate hard drives.

---

### Post by CharlesA on 2011-10-04
Sounds like a fine backup plan.

I have been syncing everything to my server and having it back up to external media daily - with full backups taken monthly.

---

### Post by rs2k on 2011-10-04
Thanks, there is something I worry about though.

Since I'm using an incremental backup a lot of the data is just stored in one place. If the hard drive with the backup directory on the remote (hosted server) computer is stored on goes bad and corrupts the data will the rsync on my local computer copy that corrupted data?

I guess that's what full monthly backups are there to protect from.

---

### Post by CharlesA on 2011-10-04
It would copy the corrupted data, since it syncs it up, but if it's incremental you should be able to recover from an older file.

---

### Post by collisionystm on 2011-10-04
> **rs2k said:**
> This is the current backup/recovery scheme I'm intending to use on my server. It hosts several websites(eCommerce/forums) and a minecraft server.

1. I have a list of all installed programs and how I installed them. Software versions, etc. If the server was destroyed I can follow the list and setup the same OS and software on another system within a few hours.

2. I have a list of important data directories and backups of data and config files.

3. I have a backup directory of "snapshots" that I create with cp and rsync using this page as a reference: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/). My plan is to have hourly, daily, weekly, and monthly snapshots

4. Mysql database backed up daily with crucial data like emails sent to a second computer instantly.

5. The backup directory is rsync'd to a remote computer nightly and kept on two separate hard drives.



Your method of rsync 'snapshots' is way to complicated! Do yourself a favor and install rsnapshot.

Make a Clonezilla image of each of your servers you want to backup. Store that away somewhere.

Nightly, have rsnapshot do backups of your systems. 

If system fails, restore using clonezilla, upload changed files since the clonezilla  from your rsnapshots.

I have an old dell desktop with a buffalo raid 5 storage attached. It gives me 2 weeks worth of rsnapshots. I could set it for longer but 2 weeks is more than enough for me.

---

### Post by CharlesA on 2011-10-04
> **collisionystm said:**
> Your method of rsync 'snapshots' is way to complicated! Do yourself a favor and install rsnapshot.

Make a Clonezilla image of each of your servers you want to backup. Store that away somewhere.

Nightly, have rsnapshot do backups of your systems. 

If system fails, restore using clonezilla, upload changed files since the clonezilla  from your rsnapshots.

I have an old dell desktop with a buffalo raid 5 storage attached. It gives me 2 weeks worth of rsnapshots. I could set it for longer but 2 weeks is more than enough for me.

I do snapshots the same way the OP does, but mostly cuz I already have the scripts set up and tested and it works fine for me. I've looked into rsnapshot but haven't played around with it much. Might have to check it out again.

---

### Post by rs2k on 2011-10-04
Thanks, I looked over rsnapshot and it looks like it'll do everything I need for me.

Clonezilla I'm not familiar with. Their main page said it was similar to norton ghosts.

How would I use clonezilla to backup and restore a hosted system I have no access to?

---

### Post by collisionystm on 2011-10-04
> **rs2k said:**
> Thanks, I looked over rsnapshot and it looks like it'll do everything I need for me.

Clonezilla I'm not familiar with. Their main page said it was similar to norton ghosts.

How would I use clonezilla to backup and restore a hosted system I have no access to?

Ohhh gotcha. Hosted system. Nevermind.

---

### Post by rs2k on 2011-10-04
rsnapshot is working great and doing exactly what I wanted it to do. I think the scripts I was planning to write would have done exactly the same thing, but rsnapshots simplified the process quite a bit.

Thanks for the recommendation.

---

### Post by CharlesA on 2011-10-04
> **rs2k said:**
> rsnapshot is working great and doing exactly what I wanted it to do. I think the scripts I was planning to write would have done exactly the same thing, but rsnapshots simplified the process quite a bit.

Thanks for the recommendation.
I think I am going to have to take a look at rsnapshop now too, maybe it'll simplify the scripts I am using.

*Quick to the test machine!*

---

### Post by rs2k on 2011-10-04
It's really simple

After you configure the conf file there is a list of backup locations and scripts you create in the conf file.

any script that runs on this list will have its output placed in a folder you specify. 

I have a script that forces a world save on the minecraft server then stops world saving run, then I have a script that backs up the mysql databases and gzips them.
I then have several folders backup.
I then have a script that restarts worlds saving on minecraft.

I have this in the cron to make the backups:
0 */1 * * *       /usr/local/bin/rsnapshot hourly
20 23 * * *       /usr/local/bin/rsnapshot daily
40 23 * * 0       /usr/local/bin/rsnapshot weekly


The full monthly backup I'll just handle with rsync.

---

### Post by CharlesA on 2011-10-05
That's actually pretty nice. Thanks.

---

