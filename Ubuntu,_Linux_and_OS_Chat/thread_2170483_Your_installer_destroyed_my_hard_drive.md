---
title: "Your installer destroyed my hard drive"
date: 2013-08-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Josh_Chudnovsky on 2013-08-26
I'm not looking for any support but I thought I'd post to let you know about unexpected behavior from your 13.04 installer.

I recently installed 12.10 on my Asus Revo L.  I partitioned 30 gigs to dedicate to Ubuntu.  After mucking around I wanted to go ahead and install 13.04.

However the 13.04 installer wouldn't boot up, and after a while i found out i had to go into grub boot config file and set "nomodeset".  Finally I was able to get into the installer.

The installer gave me some options: "Upgrade from 12.10 to 13.04" or "Erase 12.10 and install 13.04".  I chose the latter.  The installer then went on to repartition the entire hard drive, format it to Ubuntu, and install 13.04 in it.  I lost my windows install, for which there is no backup (the system does not come with a restore disc or flash drive) and all my content.  Over what? That never should have happened guys :(

---

### Post by Quackers on 2013-08-26
I think "destroyed the hard drive" is not the best way to describe it. It would appear that the drive has been over-written, not destroyed.
The installer shouldn't have done that unless you gave it the go-ahead to do it. It's strange that it happened.
In all honesty, partitioning of any kind carries a risk and it's always best to have a way to get back to what you had before you began partitioning. In fact some would say that it is imperative.

It is possible that your partitions could be re-created and some or all of the data recovered by using Testdisk, though there are no guarantees.
If you want to go down that route you should stop using the new installation immediately as further use may further over-write data.

---

### Post by Josh_Chudnovsky on 2013-08-26
At the end of the day, this machine is inconsequential to me so it's no big deal - but the reason i made the thread was to inform you of what happens under that circumstance.  As I was installing i couldn't have even fathomed that would happen.

---

### Post by developerzero on 2013-08-26
You should report this as a bug:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by eternal243 on 2013-08-26
Well, your disk was certainly not destroyed, just overwritten, there is quite a big difference there. Having backups is essential when messing around with partitioning and installation of new operating systems. 

Still, you said you where using the 13.04 installer, which I used yesterday as well to install Ubuntu alongside Win7, with no problem at all. I wonder however if you used the automatic partitioning option during the install, or did you use manual partitioning? Using the automatic partitioning will definitely overwrite data, since that is what it is designed to do, but if you did a manual partitioning and took great care to only use the correct harddrive space, and it still didn't work, then it is definitely a serious bug which need to be reported to, and addressed by, the developers.

---

### Post by oldfred on 2013-08-26
I believe one other user posted where he went into one of the install options, but then backed out, without rebooting and it reverted to a default where it overwrote everything. 
Did you start install and then back out and start over? If so definitely file a bug report. 

Forum is just users helping users and developers only look at bug reports.

---

### Post by oldos2er on 2013-08-26
Moved to Ubuntu, Linux & OS Chat.

---

### Post by cortman on 2013-08-27
That's a real shame, and I hope you file a bug report if indeed it is an Ubuntu error, but-

> **Josh_Chudnovsky said:**
> for which there is no backup

That's asking for it. :( Always back up before doing any kind of partitioning.

---

### Post by stalkingwolf on 2013-08-27
the Hirens boot cd also has several recovery tools that i have found useful.

---

### Post by ikt on 2013-08-27
> **developerzero said:**
> [SIZE=4]You should report this as a bug:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)[/SIZE]



This is important, the forum is for discussing bugs, you want to report a bug to get it fixed so that other people don't have the problem you had.

---

