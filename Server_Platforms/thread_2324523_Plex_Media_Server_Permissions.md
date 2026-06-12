---
title: "Plex Media Server Permissions"
date: 2016-05-14
forum: Server Platforms
---

### Post by jimbostrong on 2016-05-14
Hi all,
I know this has been covered a few times, but i just want some clarification.

I have just installed Plex Media Server on my Ubuntu 16.04 server.

I have 2 additional Hard Drives i have formatted to NTFS as 'Media Storage' and 'Media Storage 2'.  I want to put the Plex Library on 'Media Storage'.

I have changed it so that 'PLEX' is added to the group 'James' which is the normal user.

However, when i go into Plex, it cannot see either of the drives, if i navigate to media/james (in fact it cannot see any folders from here).

I have tried changing permissions in the GUI by going to the folder and the drives and allowing all users to edit/change the files but to no avail.

Is there something i am missing?

Any help greatly appreciated.

---

### Post by QDR06VV9 on 2016-05-14
See if this helps: [https://forums.plex.tv/discussion/112804/plex-wont-read-folders-files-on-mounted-drive-in-linux-mint](https://forums.plex.tv/discussion/112804/plex-wont-read-folders-files-on-mounted-drive-in-linux-mint)

---

### Post by jimbostrong on 2016-05-14
Hi,
Thanks for your message.

So i went into the config and tried to change the run as user to my user 'james', restarted Plex and still no joy....

---

### Post by QDR06VV9 on 2016-05-14
Read that page very carefully it holds all the answers.

---

### Post by bab1 on 2016-05-14
> **jimbostrong said:**
> ...
I have just installed Plex Media Server on my Ubuntu 16.04 server.

I have 2 additional Hard Drives i have formatted to NTFS as 'Media Storage' and 'Media Storage 2'.  I want to put the Plex Library on 'Media Storage'.

If there is no overriding reason to use NTFS, you should not do that.  You can't change the permissions or ownership after the partition is mounted when the partition is formatted using NTFS.  This may be part of your problem.  Why are you using NTFS formatting for these 2 HDD's?
> 
...I have tried changing permissions in the GUI by going to the folder and the drives and allowing all users to edit/change the files but to no avail.
As I said, this won't work with NTFS formatted partitions.  The permissions would need to be set when the partition (actually the file system) is mounted.
> 
I have changed it so that 'PLEX' is added to the group 'James' which is the normal user.
However, when i go into Plex, it cannot see either of the drives, if i navigate to media/james (in fact it cannot see any folders from here).

...So i went into the config and tried to change the run as user to my user 'james', restarted Plex and still no joy

At this point I would seriously consider formatting the 2 partitions ('Media Storage' and 'Media Storage 2') as ext4 and mounting them somewhere else in the file system if there are no overriding concerns. There is no technical reason to use one mount point or another outside of your home directory.  It's just less confusing and more intuitive if you use a location such as /plex or /data.  The traditional use of /media is for temporarily  mounting USB connected devices such as flash drives or CD or DVD's.   The Plex app doesn't care either way.

How many mortal users (humans) are going to access these directories?  Just you or are there others?  The system user plex is no different any other user as far as directory or file ownership or permissions are concerned.  The big difference is a system such as plex can't log in log in to the running  OS and certainly has no method of becoming the root user.  I'd prefer to run Plex using the system user "*plex*" rather than a user that has interactive login abilities.

Frankly I found the the plex forums link ([https://forums.plex.tv/discussion/112804/plex-wont-read-folders-files-on-mounted-drive-in-linux-mint]("https://forums.plex.tv/discussion/112804/plex-wont-read-folders-files-on-mounted-drive-in-linux-mint")) pretty vague myself.

---

