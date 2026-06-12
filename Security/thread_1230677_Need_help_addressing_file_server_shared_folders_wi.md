---
title: "Need help addressing file server shared folders with WinXP"
date: 2009-08-03
forum: Security
---

### Post by flatland2d on 2009-08-03
I'm currently in the planning stages for building a home file/backup/media server and I have a question about shared folders.

The server will use two 1TB drives for pictures and video.  I will use rsync to backup one drive (primary) to the other (backup).  I know this isn't the best backup policy, since both drives are in the same box, but I'm willing to settle here.

So WinXP will be able to connect with the primary 1TB drive, but not the backup 1TB drive.  I would like my "My Pictures" and "My Videos" folders to link directly to the shared drive.  The dilemma is, how can I prevent a virus on the WinXP machine from screwing around with the shared folders on the file server, and then those files eventually overwrite the backup copies if not caught in time?

Is that just something you just have to accept by doing it with this method?  I'm open to suggestions on this, but I want the integration of the file server to WinXP to be as seamless as possible (like pointing "My Pictures" directly to the file server).  My wife won't like it if it's something too different than what she's used to.

Any ideas would be appreciated.  I've been having a lot of fun learning about servers and setting up rsync with crontab.

---

### Post by Revolutionary101 on 2009-08-03
This is how you prevent a virus from messing around with the folders. Only access the hard drive with Ubuntu. If you use Ubuntu why can't you access the files with Ubuntu.

---

### Post by flatland2d on 2009-08-03
The file server (Ubuntu) needs to be able to allow the WinXP machine to access it.  I've tried converting it to Ubuntu but the wife won't make the switch.  Not sharing the files/folders kind of defeats the purpose of having a file server.

---

### Post by Revolutionary101 on 2009-08-03
I see. Is windows currently able to access the files?

---

### Post by bodhi.zazen on 2009-08-03
If you stop and think about it , it is not really a Linux problem and frankly the problem is best solved on the windows side.

Your best defense is not to run windows =)

Second best is to secure windows.

A distant third is to run antiviurs on the Ubuntu server. Viruses do not run on the linux server, so no problems there.

The problem with this third strategy is that if your windows box is insecure, viruses will come in via windows and trash the place no matter what you do on the Linux server =)

---

### Post by flatland2d on 2009-08-04
I agree that Windows is the problem and that is what really needs to be addressed.  I'm going to look into some solutions for that, but honestly I've never had a major virus issue when using Windows.  I just know that's it's bound to happen eventually.

I just started thinking of another backup strategy.  I know this is redundant and a little paranoid, but it solves this issue of Windows trashing the shared Ubuntu folders.  I'm thinking about creating another backup that is run manually, and not very frequently.  This backup would be on a separate partition not shared with Windows.  The risk of using rsync is the unsupervised overwriting of backup files so manually calling the command at least gives you a chance to look things over before making the copy. 

I'm approaching 150GB of pictures with my dSLR which creates two files for every picture - a large RAW file (average about 12MB) and a small JPG file (average about 1MB).  I like having the RAWs for having maximum control of picture editing, but I could make a concession that for the sake of something being better than nothing, I could make a second backup of just the JPGs done manually as described.  It would be easy to do with a second cronjob that runs "rsync -av Pictures/*.jpg /Backup-folder".  Since the JPG backups are much smaller, the 1TB drive could be divided 900GB primary backup, 100GB secondary backup, without sacrificing too much in overall storage.  The end goal is to have pictures and videos on separate redundant drives, making four 1TB drives total.  I can't afford to do that yet, though.

Even better than that is good old fashion drag and drop, since I'd only be copying over the new files.  This would prevent rsync copying over a corrupted file I accidentally missed since it just isn't feasible to look over 40,000 pictures before doing the rsync.  This is at a trade off of convenience though.  Anyone know if rsync supports only syncing "new" files (created within a certain date range), and not an entire directory?  That would solve this issue and still be automated.

Just throwing out more ideas.  What do you all think?  I know it's getting a bit extreme, but I don't want to lose a lifetime of pictures, and I'm not yet willing to store multiple backups on different media in different places around the world.  Thanks for any input.

---

