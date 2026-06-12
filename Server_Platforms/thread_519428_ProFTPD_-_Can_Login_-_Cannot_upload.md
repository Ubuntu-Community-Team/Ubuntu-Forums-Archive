---
title: "ProFTPD - Can Login - Cannot upload"
date: 2007-08-07
forum: Server Platforms
---

### Post by iezugod on 2007-08-07
Hello,

It's me again.

I've been having tremendous issues setting up ProFTPD and no websites have been of much help.

The current issue is that when I log into my ftp with a new user I created specifically for FTP, I am able to log into my /www/var directory and see files. However, when I try to upload I get a 550 error saying permission is denied. Earlier today I was able to upload just fine but I made one change (can't remember what it was) and now it doesn't work. I tried deleting the usernames and starting over from scratch but the same thing happens... I can login but can't upload.

If I login with my admin account I can upload files fine. However, I want an account that is locked into the /var/www account and can't go any further backwards into the file system.

Does anyone have any ideas why I would be able to login but not upload?

Also, I am open to suggestion for a different FTP server setup as I have had nothing but problems with proftpd since I installed it. I would prefer someting compatible with webmin but at this point I'll give anything a shot.

Thanks,

Mark

---

### Post by bmathis on 2007-08-07
Does that user have rights to that directory? Try ```
sudo chown -R username:group /var/www
``` to give ownership to that user and you should be able to upload. That user will only have access to its home folder and /var/www.

---

### Post by iezugod on 2007-08-07
Will the user have access to sub-directories under /www/ as well?

Thanks,

Mark

---

### Post by iezugod on 2007-08-07
> **bmathis said:**
> Does that user have rights to that directory? Try ```
sudo chown -R username:group /var/www
``` to give ownership to that user and you should be able to upload. That user will only have access to its home folder and /var/www.

You are a saint!

Worked :D

---

### Post by bmathis on 2007-08-08
no problem!

---

