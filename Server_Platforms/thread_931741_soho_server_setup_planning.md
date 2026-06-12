---
title: "soho server setup planning"
date: 2008-09-27
forum: Server Platforms
---

### Post by vtcat on 2008-09-27
I have a small office, in which I use an old Duron box as a file server (currently running gutsy on a single ext3 hd) for two XP boxes.  I recently had to replace the power supply, which made me realize that my backup plan is not sufficient.

I'd like to set it up with some sort of software raid, so that the data is mirrored to a separate ntfs hd (both drives are ide).  I'm kind of a noob, and need some general idea how to go about this.

Also, the data is currently on a separate partition, and not in the home folder.  I've had occasional permission issues when one of the XP users writes to the shared data partition, so I almost certainly have that set up incorrectly.

In the process, I'll probably start from scratch with a new hardy installation and /home on a separate partition of the primary drive.  Any general guidance or links would be greatly appreciated.

---

### Post by freebeer on 2008-09-27
Is this office physically located in your home?  If not, you might want to consider off-site storage of backups.  Should anything happen - such as a fire, hurricane, flood, etc. if your backups are physically located in the same place you run the risk of losing everything.  Hardware can be replaced, but data is really hard (and time consuming!) to recreate.

If that sounds appealing and would like some ideas on how to implement it, let me know.

---

### Post by vtcat on 2008-09-27
> **freebeer said:**
> Is this office physically located in your home?  

If that sounds appealing and would like some ideas on how to implement it, let me know.

Thanks for your reply.

No, it's in my office across town.  I backup to dvds weekly, which I take home.  I do occasionally mount the shared office drive from home using sshfs, but I think that 768k upload on the dsl here probably isn't sufficient to do remote backups.  It's a few gigs of data.  If there's some way to do that, I would definitely like ideas.

The problem that made me rethink the setup is that last Friday (my usual backup day) I arrived at the office to find that the psu on the ubuntu box had kicked it.  The windows boxes couldn't see the ext3 drive with the data, so I had to take it home to retrieve the data, and return to the office with it on dvd, copy it to a win box, and reconfigure so it could be accessed.  Mirroring the data to an ntfs drive, and installing that to one of the win boxes would have saved time.

---

### Post by lykwydchykyn on 2008-09-27
> **vtcat said:**
> Also, the data is currently on a separate partition, and not in the home folder.  I've had occasional permission issues when one of the XP users writes to the shared data partition, so I almost certainly have that set up incorrectly.

I'm assuming you are using Samba?

If so, you can do several things:
- Configure Samba to use a single group and user for that share
- Add all the users to a common group and force the permissions of new files to be group-writeable.
- Install support for POSIX ACL permissions -- this way you can maintain per-user permissions on files even when the owner of the file changes.

If you need help doing any of these, just ask.

---

### Post by vtcat on 2008-09-27
I am using Samba, and setup a group with r/w permissions for that folder.  The owner does seem to change, though.  Mostly happens to existing files with the XP Home box (the other is XP Media Edition), but that may only be because the XPH accesses the shares more often.  If the shared folder were within /home, wouldn't that solve the ownership?

---

### Post by lykwydchykyn on 2008-09-27
XP home is a bit of a pain because Microsoft disabled its ability to edit NTFS file permissions, so what it might attempt to do to file permissions on the server is a mystery in some sense.

But that aside, I don't think the location of the files really matters, unless by moving things to /home you intend to keep everyone's files in their respective home directories and not share files at all.  

The basic problem is usually when a user saves a file and the permissions end up being 755 (rwxr-xr-x).  In this case, only the owner of the file can now write to the file.  Sometimes I've seen files created over SAMBA end up with 700 or 600 permissions (no read/write/execute for anyone but the owner).

I think your best bet is to set up samba to force group read/write and force the group to the common group.  For example:

```

[myshare]
path = /path/to/share
writeable = yes
create mask = 664
directory mask = 775
force group = users

```

---

### Post by lykwydchykyn on 2008-09-27
> **vtcat said:**
>   Mirroring the data to an ntfs drive, and installing that to one of the win boxes would have saved time.

What you want then is not really RAID, you just want to keep a copy of your data on a second drive for quick recovery.

Why not get an external USB hard drive, put an NTFS partition on it, and then set up a cron job to copy the data onto the NTFS drive periodically (maybe once an hour during the work day).  I would recommend using rsync, since it only copies changed files.  Your cron job would be:

```

#Assuming your data is in /data and your external drive is /dev/sdb
mount /dev/sdb /media/ntfs-drive
rsync -avz /data /media/ntfs-drive/
sleep 30
umount /dev/sdb

```

This would also give you a safeguard against accidentally deleted files.
There are more elaborate things that could be done, but I suspect this would give you what you need.

---

### Post by vtcat on 2008-09-27
Thanks lykwydchykyn

You're right, raid is probably overkill for what I need.  I do use grsync as part of the backups, but thanks for the cron script.  It'll save me some time friday afternoons :)

You're also right about the 755 permissions I see.  I wasn't aware of the force group option, so that should fix that issue.

---

### Post by freebeer on 2008-09-28
> **vtcat said:**
> but I think that 768k upload on the dsl here probably isn't sufficient to do remote backups.  

The thing to note about rsync (depending on the options you give it) is that it'll only send the portion of the file that has changed.  So if you have an updated file, only the changes are transmitted.  Saves a lot on the bandwidth issue. :D

The viability of that option really depends on the nature of your files. If you create a lot of large files frequently (say video), then remote backup may not be a good choice.  If you create small files, or edit existing one, then it might very well be a good option.

What I like about rsync over internet is that I can completely automate it.  I have all our Winboxes run rsync to the local server on a daily basis, then have the local server rsync to the remote (again, daily).  This gives me a local copy (for easy, quick retrieval) and a off-site copy for safety.  I can also retrieve a file from the remote if I need to over the 'net without having to make a trip home (where the remote backups are stored).

By automating the process, I never have to set aside time during my day to do the backups manually (and you know how that goes - if you have to set aside time to do a boring task, you're likely to let it slide from week to week :()

The next thing I'll implement is an automated system returning the results (particulary errors) via email.  That way, when I check my email, I'll get a notification if there's any issues with the system.

---

### Post by gjosef on 2008-11-11
> **freebeer said:**
> The next thing I'll implement is an automated system returning the results (particulary errors) via email.  That way, when I check my email, I'll get a notification if there's any issues with the system.

That sounds ideal. How did you do that?

---

### Post by freebeer on 2008-11-11
I don't know yet.  :) I'm currently chasing other projects, so I haven't implemented the email side of things yet.

oooh! shiny!  *runs off*

---

