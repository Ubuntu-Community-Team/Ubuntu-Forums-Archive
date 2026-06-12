---
title: "regular interval backup onto USB drive"
date: 2022-05-27
forum: Server Platforms
---

### Post by Heeter on 2022-05-27
Hi all

Would like to do regular, once a week backup of 2 files (1 is 46GB, other is 250GB) on my Ubuntu 20.04.4 LTS server to a mounted USB drive

Would like it overwrite or update the current backup at that time.

The internet searches show a few different commands to set this up.

Would like better input on how to do this properly.

regards

---

### Post by TheFu on 2022-05-27
Backing up huge files is problematic, since nearly all backup tools use librsync and files much over 4G become less efficient with rsync. We usually just copy the file completely rather than allowing rsync to look for similar blocks.

If these files are virtual machines, don't do this.  It is a waste.  

Use a normal backup method from inside each VM - probably file-based - as the backup method.  I speak from years of experience. Image-based backups are a terrible answer for many reasons.  Mainly downtime and storage in-efficiencies.

I used rsync for crappy backups for 4 yrs.  The backups took longer and longer and longer, until they were taking more time than our allowed backup window.  I spend a year testing about 10 different backup tools.  We really wanted the latest backups to be a mirror of the source files, so that recovery could be a simple cp of the files back and at the time, users could self-serve their own recovery needs.  

Thanks to malware, we decided to not allow clients any access to the backups. The backup server "pulls" the backups from each VM nightly and retains at least 90 days of versioned backups for normal systems and 2-3x that number of versions for higher risk systems.  I've posted and posted and posted about backups in these forums, so I won't repeat more. Feel free to review those 100+ posts.  I would recommend reading the few that explain how to restore a system, so you know the overall method.  In short, system restores take less than 45 minutes and aren't tied to any physical hardware or hypervisor. It is extremely flexible and can be used for many other needs, besides a simple system restore.

---

### Post by LHammonds on 2022-06-02
> **Heeter said:**
> Would like to do regular, once a week backup of 2 files (1 is 46GB, other is 250GB) on my Ubuntu 20.04.4 LTS server to a mounted USB drive
Would like it overwrite or update the current backup at that time.
You are not giving us much details as to what you are doing so I can only say how I'd handle "just" what you are saying (which is a very narrow request).  As TheFu pointed out, if those are virtual machines, there are better ways than trying to copy the VM directly.  If those are encrypted file volumes, there are better / faster ways of handling those as well.

With that said and nothing else to go on:
I would recommend against overwrite.  Why?  Because if the copy fails, you no longer have the old backup and if that is the ONLY backup, you have no backup at all.
I would copy it so its a new / unique file.
Once the verified copy is complete, then I'd remove the prior backup and rename the new backup to what the original was called (if desired)
After a successful, verified copy, I would also create an md5  for the file so I'd know if it were altered since the time it was  backed up to when it needs to be restored.

Having a single backup is risky.  The bare minimum is 3 copies.  2 copies being on different media and 1 of those copies being inaccessible to the main machine and offsite.  This 3-2-1 approach can cover many failure risk scenarios but the scenarios where data is corrupted / encrypted by malware is better guarded against if you have versioned backups over a long period of time since crypto-locking malware tend to stay hidden / active for long periods of time to try and get into your backup systems as well.  If the machine at risk has access to all your backups, you would have no good backups in that scenario.

LHammonds

---

