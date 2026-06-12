---
title: "questions about adding another hard drive"
date: 2009-07-28
forum: Server Platforms
---

### Post by hellarough on 2009-07-28
Okay so I have had a server for a few months now and the day has come where the massive 80gb internal HD has filled up with various junk. I recently obtained another 320gb HD to install but before I attempt I want to know if I am going to mess anything up. 

I have most of my media in the /var/www/ directory and if I add a new harddrive and fstab it to mount as /var/www I want to know what will happen to all the media files that exist on the 80gb under /var/www/

---

### Post by hamstersquasher on 2009-07-28
You would probably be better off mounting the addition HDD to a subfolder in /var/www/.  If you just tried to mount the new drive to /var/www/, I believe the existing files in /var/www/ would be hidden and no longer accessible in your filesystem until you corrected the mount.

---

### Post by hellarough on 2009-07-28
> **hamstersquasher said:**
> You would probably be better off mounting the addition HDD to a subfolder in /var/www/.  If you just tried to mount the new drive to /var/www/, I believe the existing files in /var/www/ would be hidden and no longer accessible in your filesystem until you corrected the mount.

What if I were to install the HD then copy everything over to it with:
sudo cp -Rv /var/www/ /dev/hdb0 

then edit the fstab so that it mounts as /var/www/


also if I were to do that, will the 80g still register as full?

---

### Post by cariboo on 2009-07-28
Why not just mount the new drive in /media/disk and create a symlink to it, then move are your media files to the new drive.

```
sudo ln -s /media/disk /var/www/media
```

---

### Post by R.Bucky on 2009-07-29
It sounds like you could add your new hdd, mount it (include it in the fstab) at something like "/new_drive", then simply point your Apache /etc/apache2/sites-available/default at your "/new_drive." That way, all your web server files would be contained on your new drive. It is easy enough to partition your new hdd and configure away. Many options here. It depends on how you want to be organized...

---

### Post by hellarough on 2009-07-29
> **R.Bucky said:**
> It sounds like you could add your new hdd, mount it (include it in the fstab) at something like "/new_drive", then simply point your Apache /etc/apache2/sites-available/default at your "/new_drive." That way, all your web server files would be contained on your new drive. It is easy enough to partition your new hdd and configure away. Many options here. It depends on how you want to be organized...

Yeah I will probably end up going that way I just didnt want to change all my config files for torrentflux, samba, ushare, and apache and also have to change the default home directories for my ftp users. 

Thanks for the answers/suggestions!

---

