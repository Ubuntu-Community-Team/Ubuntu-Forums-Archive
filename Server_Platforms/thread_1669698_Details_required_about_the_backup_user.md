---
title: "Details required about the backup user"
date: 2011-01-18
forum: Server Platforms
---

### Post by brynellis on 2011-01-18
I just went to create a user called 'backup' to use as my nightly backup user and noticed that it already existed.  I haven't create it so it must be a default user.

I also notice that it's home directory is /var/backups and that there are some files in there that must be getting backed up automatically.

I still want to use this user so I've changed it in the following ways:
[LIST=1]
[*]Set the password
[*]Changed it's default shell from /bin/sh to /bin/bash
[*]Changed it's home directory to /home/backup
[/LIST]

Now I'm kinda thinking "whoops!  are these changes going to prevent the automatic backing up of those files in /var/backups and whatever else it does"?

I'm struggling to find any articles on the web detailing what this user is for and what it does in the background.

Could someone help please?

---

