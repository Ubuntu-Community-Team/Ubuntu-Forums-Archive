---
title: "Apache permissions"
date: 2011-03-03
forum: Server Platforms
---

### Post by ash369 on 2011-03-03
When i upload files to my www directory using a user i created myself the files do not show up (the apache logs show permission denied). I managed to fix it by using chmod -R 775 but i'm having to type that each time i add new files.

How can i allow people to access the files without having to type this chmod command each time?

---

### Post by James78 on 2011-03-03
775 is good, but all the files are supposed to be owned by the Apache user, www-data. This is why you have to add additional permissions.

For example, your username is myuser, now, myuser makes some files in /var/www, and these files have user and group read/write for example, but no world read/write. Apache can't access it because the files are owned by myuser, so you fixed the problem by making it word readable. Created files will always be apache readable/writable if they're owned by www-data. This was a really quick explanation just slopped together, I may not be exact exact on some super super fine details, but the whole idea still gets through excellently.

---

### Post by ash369 on 2011-03-04
I understand, i think. So could i possibly add myuser to www-data group? Would that be possible, would that fix it?

---

### Post by hawkmage on 2011-03-04
Not really.  When a user creates a file it is owned by their UID and primary GID, just putting your account if the www-data group will not cause your account to create files as the www-data group unless you make it your primary group.  

To fix it you could create a script or alias that runs the command:
```
sudo find /var/www/ -user `whoami` -exec chown www-data:www-data "{}" \;
```

---

### Post by ash369 on 2011-03-04
Could i login to www-data and upload the files that way? I'm just looking for a quick and simple fix. I just want to be able to upload the files over ftp and that would be all.

---

### Post by James78 on 2011-03-04
If you're using ProFTPD, you could use mod_exec to execute a command after files are uploaded, to change them to www-data.

If you want to know what I do. Is this.

I have a user, which my files in /home/user/public_html. When I create files and whatnot there, they're owned by user:user of course, with read/write user, and read group (default permissions basically). Now, Apache can access my files perfectly fine. You may be wondering how in the world did I do that since they're not world readable!

The solution is fairly simple. You see, since I have group readable, Apache could access my files if it has access to my group.. Or...
```
sudo adduser www-data myusergroupname
```More information about my FTP solution here.
[http://stackoverflow.com/questions/930421/run-php-script-when-a-new-file-is-added-via-ftp](http://stackoverflow.com/questions/930421/run-php-script-when-a-new-file-is-added-via-ftp)

> **ash369 said:**
> Could i login to www-data and upload the files  that way? I'm just looking for a quick and simple fix. I just want to be  able to upload the files over ftp and that would be all.
Not really no.

---

