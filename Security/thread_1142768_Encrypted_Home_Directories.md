---
title: "Encrypted Home Directories"
date: 2009-04-29
forum: Security
---

### Post by CarlosinFL on 2009-04-29
I just installed Ubuntu and saw the option to 'encrypt' my users' home directory. I selected 'yes' to enable encryption on my home directory but have a few questions. Lets say all the data in /home/carlwill/ is encrypted however I have a cron job that rsync's all my home directory data to a back up server on my LAN. Does the data that gets backed up on my backup server move as encrypted data? Is it readable or usable for recovery on the backup server?

Thanks for any info!

---

### Post by ahbart on 2009-04-29
I have the same question. I assume that it will not been seen, because the actual data (if you are not logged in) is in another directory and mounted to /home/username. In this way I have setup my encfs and libpam-mount system.
I have to log in to make a backup.

---

### Post by l3dx on 2009-04-29
I did not notice this option when I installed Ubuntu NBR 9.04. Is this this only for "desktop edition", or did I just miss it?

---

### Post by ddrichardson on 2009-04-29
Dustin Kirkland just gave a very good talk on home folder encryption on IRC for OpenWeek if you're interested:

[https://wiki.ubuntu.com/MeetingLogs/openweekJaunty/EncryptHome](https://wiki.ubuntu.com/MeetingLogs/openweekJaunty/EncryptHome)

---

### Post by l3dx on 2009-04-29
> **ddrichardson said:**
> Dustin Kirkland just gave a very good talk on home folder encryption on IRC for OpenWeek if you're interested:

[https://wiki.ubuntu.com/MeetingLogs/openweekJaunty/EncryptHome](https://wiki.ubuntu.com/MeetingLogs/openweekJaunty/EncryptHome)

This helped me. But I didn't find another way but to re-create my user with the --encypt-home parameter.

---

### Post by LexLux on 2009-05-03
Dustin Kirkland explains more here:
[http://blog.dustinkirkland.com/2009/02/jaunty-encrypted-home-directories.html](http://blog.dustinkirkland.com/2009/02/jaunty-encrypted-home-directories.html)

---

