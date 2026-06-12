---
title: "Ubuntu 7.10 Samba - Sharing /var/backups?"
date: 2008-02-17
forum: Server Platforms
---

### Post by duren on 2008-02-17
Hey guys I just noticed something weird. Samba is sharing out /var/backups as "Backup" and I don't have that anywhere in my config file! I accidentally noticed this because when I redid my server I called it the same thing and my windows drive mappings had a link to a backup share that existed on the old server. Whats more is that the comment on this share is the same one as the home directory share comment.

Is this a bug in samba? I'm running version 3.026.

---

### Post by duren on 2008-02-17
It appears to occur when you manually create a "Home Directories Share". The "Backup" share is hidden but revealed when you go to it manually ie \\server\backup.

Can anyone verify this?

---

### Post by rfreeman on 2008-05-27
Hi all,

I also have the /var/backups folder being shared as \\server\backup (not listed in my samba conf file!). I too have home directories enabled. The comment next to the backup share is "Home Directory", as it is for my home shares!

Anyone got any ideas?

thanks...

---

### Post by rfreeman on 2008-05-27
Of course, if you change permissions for /var/backups you can control access!

---

