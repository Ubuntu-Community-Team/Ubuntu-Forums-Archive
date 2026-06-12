---
title: "Question regarding sharing of folders and files"
date: 2013-03-19
forum: Server Platforms
---

### Post by Dudenell on 2013-03-19
I'm a little lost and new with Ubuntu server, but I'm looking to learn.

I have a directory under a user

/home/procon/logs/
and I want to share that directory on the actual website (using apache)
such as

rufclan.com/logs/ 

how would I do that without copying the files over ever few seconds?

Thank you in advance!

---

### Post by Mr. Shannon on 2013-03-19
Not sure about the security implications but you could use a symlink.  This is done with:
```
ln -s /home/procon/logs /var/www/mysite/shared_folder
```
This will essentially make it look as if all the files in /home/procon/logs are in /var/www/mysite/shared_folder.  Just make sure that the user apache is running as (www-data by default in Ubuntu) has read permissions for the files in that folder.

---

