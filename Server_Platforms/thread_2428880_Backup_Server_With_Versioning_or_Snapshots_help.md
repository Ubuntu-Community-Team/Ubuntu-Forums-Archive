---
title: "Backup Server With Versioning or Snapshots help"
date: 2019-10-10
forum: Server Platforms
---

### Post by Whiteice on 2019-10-10
I currently host a Minecraft Server for myself and a few friends. A week ago I updated the server and lost our world data and I learned a valuable lesson. A good backup is one that has all ready been done. So with that notion I went to work trying to figure out how to backup my system. I came up with a simple solution. I have in additional synology disk station that im using as a backup location. I mounted a share via cifs to my server and made a cron job to backup my Minecraft folder with Rsync once a day. However This is not the best method as if someone logs in and breaks the server I have 24 hours to resolve it or my backups been updated to the new broken version. With that being said I'm looking for a new solution. I want to do either a snapshot or a version of the backup so I can cue up a few days worth of backups so as not to lose as much. I however haven't come across a good solution. I cannot use hyper backup with synology since this is a networked folder ( I suppose I could have the synology run a hyper backup of the nightly backup but that seems silly), I cannot use rsnapshot since it requires hard links either. So any ideas?

---

### Post by TheFu on 2019-10-10
rdiff-backup is what I use. It works over ssh and uses librsync and librdiff underneath.

The backup server should "pull" the backups, not use mounted storage. The clients should not have direct access to the backup storage.  This prevents the malware problem that is hitting lots of backup solutions.

60 days of versioned backups uses between 10 and 20% more storage than the data being backed up.  You can setup snapshots to be backed up, if that is you desire/capability.  I use LVM snapshots.

CIFS is a terrible solution for Unix backups. It drops 50% of the data we need at restore time.  The owner, group, ACLs and permissions are absolutely critical for a successful restore.  The file contents are NOT sufficient alone.

---

### Post by LHammonds on 2019-10-10
I'll tell you what I did for my Minecraft server when I was running one (was a hub of 12 servers acting as one actually)

My backup integrated with the game via console commands.  I would push "say" commands letting everyone playing on the server know that a backup was being made and then push the "save-off" and "save-all" commands.

I would then run an rsync command to synchronize the production folder with the backup folder which was very quick since it only had to push files that changed since the last time.

Once completed, I would then send a "save-on" command to the console.

This one thing was handled by an rsync script I scheduled to run on a regular basis.

Now that I had a local and offline copy of the game, I could then begin archiving it.  I wanted a full backup every time so I created a tar.gz file.  You can use whatever method you want at this point because you don't have to worry about open files or a running state since you are only touching the local backup folder.

I also created a semi-automated script for restoring.  The script would look at each of the archives and present the files from a list to choose from.  Once an archive was selected (which clearly showed the date/timestamp, it would then gracefully shutdown the Minecraft instance, make a backup, and then restore the selected file.

LHammonds

---

