---
title: "Backup Server"
date: 2008-05-27
forum: Server Platforms
---

### Post by TheGameAh on 2008-05-27
Been presented with the following.

A windows share needs to be backed up.  Right now, they're just writing incremental (once a day) and full (once a week) backups to a removable hard drive (140 gigs of data, on a 200 gig extra drive).

They only have 2 devices.  They had to restore a file from a month ago, and unfortunately the backups didn't go back quite that far.  

I'm thinking about building a headless Samba box to act as a backup server.  Just thinking about how this would go.  Make a public share and just have the Windows server do an NTBACKUP write to the Samba share?  Any other suggestions?

---

### Post by windependence on 2008-05-27
You don't even need that. You should take a look at Amanda, or Bacula. Amanda can back up remote machines on the network, even Windows machines.


[http://www.amanda.org/](http://www.amanda.org/)


[http://www.bacula.org/en/](http://www.bacula.org/en/)


-Tim

---

### Post by molotov00 on 2008-05-27
I am running XP Home (not by choice) on a box that needs to be backed up. Because I can't set share permissions on Home (only Pro allows it), I do it this way, which you may want to consider:

Ubuntu Server w/ Samba has a user called upstairsbackup. That user has a home directory and is the only user who has access. It's shared to Windows machines through Samba.

WinXPHome mounts the Samba share as Z:, as user upstairsbackup. SyncToy (a syncing app from Microsoft) runs every night (scheduled task) and puts desired files from local machine onto the Samba share.

Result: the backed up files are only accessible to upstairsbackup or admin on my Ubuntu box. If I shared from WinXPHome, the shared folder would be accessible to anyone on the network, which I don't really want because I have wireless as well.

This is not the best solution but it is what I came up with given that XPHome doesn't network very well.

M

---

### Post by NateMan on 2008-05-27
While I don't really recommend doing this, as it can cause other issues of which I have no wish to trouble shoot, you can edit the registry to give xp home many of the same networking features as xp pro. I've done it for automounting a network drive in xp home, which normally can't happen. There were numerous other tweaks, but I haven't had a personal need for them.

---

### Post by Girya on 2008-05-27
I use Backuppc to backup my home network which includes a xp and ubuntu box. It works great. getting it up and running was a bit of a challenge for me but if I can do it anybody should be able to do it. 

It will do automated daily incrementals and and weekly fulls and I think you can set up an archiving function for back-ups going back months. some of the cool features: web interface for clients and admins, it pools files so it only backs up files that change and links to files that don't ( my back-ups show something like 100gb of back-ups but when I run df from the command line the back-up directory is less than 40gb.)

the one thing that might be worth investigating with whatever system you go with is checking how you migrate back-ups to new disks when the back-ups fill the current disks. LVM or Raid or both?

---

