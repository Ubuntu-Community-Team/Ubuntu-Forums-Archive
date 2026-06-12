---
title: "Ubuntu Server Backup Strategy"
date: 2013-03-05
forum: Server Platforms
---

### Post by carloss1 on 2013-03-05
Hello everyone!

I was wondering if i could get some advice on implementing a good backup strategy for the files in my Ubuntu Server box.  Currently, I have 8TB worth of data spread out over 2 x 1TB Drives and 3 x 2TB drives.  One of the 2TB drives failed on me last week (after coming home from a trip no less!) and I now realized I should've been backing everything up.

With that said, I'm not entirely sure how to go about this, but I do have a couple of questions that I'm hoping someone here can help me out with:

1. Is it possible to back up all the drives into 2 x 4TB drives, with each of these partitioned into 2TB and 1TB partitions so I can mirror my current drives exactly?
2. With that set up, is it possible to configure it so that if the drive fails, it switches to the backup automatically? and then i can replace the failed drive with a new one and copy everything over?
3. I'm guessing it would be possible to do a nightly incremental backup?

And of course, finally, what program can I use that would meet all these requirements?

Any help would be greatly appreciated!  Thank you!

---

### Post by tgalati4 on 2013-03-05
RAID is not a backup strategy.  3-2-1 is generally a good rule.  3 copies of important stuff.  2 different devices.  One remote/off-site backup.  How you do that is up to you.

---

### Post by carloss1 on 2013-03-05
> **tgalati4 said:**
> RAID is not a backup strategy.  3-2-1 is generally a good rule.  3 copies of important stuff.  2 different devices.  One remote/off-site backup.  How you do that is up to you.

Thank you for the reply! I've taken your advice into consideration and I've found rsync.  It looks like it'll be able to do the backing up I need to get done, but maybe not what I want to happen with #2 from my original post.  It does look like I won't have to worry so much about partitioning the backup drives to match the original drives I have.

Any experience using rsync?

---

### Post by papibe on 2013-03-06
Hi carloss1.

rsync is great, however...

rsync is not a comprehensive backup solution. Granted, it is a powerful tool, and it is used by a lot of backup software in the background.

For copy/mirror it is fantastic, and very easy to implement.

When you start thinking on as schedule the includes full, incremental and differential backups, an rsync command won't be enough. Don't get me wrong. You could, indeed, write some scripts that take care of all that (take a look at [this]("http://rsync.samba.org/examples.html") examples). But scripts need to be tested, debugged, etc. Considering going this route would depend  on the urgency, importance of your data, and your scripting abilities.

I would start by taking a look at [this]("https://help.ubuntu.com/community/BackupYourSystem"), and [this]("http://askubuntu.com/questions/2596/comparison-of-backup-tools") reviews of several backup tools.

Hope it helps. Let us know hot it goes.
Regards.

---

### Post by tgalati4 on 2013-03-08
You need to ask yourself, do I need to copy the entire operating system and personal data, so I can restore the machine at some point in the future?  Or, do I back up my personal data, and if the operating system gets trashed (quite rare under linux), I can simply do a fresh install (perhaps even a newer version!) and simply reinstall my personal data.  Rsync is not the right tool for a complete snapshot/mirror, but it is an appropriate tool for personal data that doesn't change that much over time.  It's mostly static except for the files that you added or edited during the recent past.

---

### Post by carloss1 on 2013-03-11
> **tgalati4 said:**
> You need to ask yourself, do I need to copy the entire operating system and personal data, so I can restore the machine at some point in the future?  Or, do I back up my personal data, and if the operating system gets trashed (quite rare under linux), I can simply do a fresh install (perhaps even a newer version!) and simply reinstall my personal data.  Rsync is not the right tool for a complete snapshot/mirror, but it is an appropriate tool for personal data that doesn't change that much over time.  It's mostly static except for the files that you added or edited during the recent past.


Hi tgalati4, 

I'm just looking to copy over personal data in a few hard drives, that, in the event of a hard drive failing, i can replace that hard drive and copy over my existing data to it.  Would rsync be suitable for that?

---

### Post by tgalati4 on 2013-03-11
Yes, rsync is well suited for that.  Search for several rsync tutorials on these forums.  Lots of switches and ways to use rsync.

---

### Post by carloss1 on 2013-03-11
> **tgalati4 said:**
> Yes, rsync is well suited for that.  Search for several rsync tutorials on these forums.  Lots of switches and ways to use rsync.

Thank you for your help!

---

### Post by tgalati4 on 2013-03-11
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

[http://askubuntu.com/questions/105314/how-to-backup-user-files-automatically-via-rsync](http://askubuntu.com/questions/105314/how-to-backup-user-files-automatically-via-rsync)

---

