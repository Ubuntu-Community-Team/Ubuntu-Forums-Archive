---
title: "Running Apache2 on external hard drive"
date: 2017-05-20
forum: Server Platforms
---

### Post by init.nelson on 2017-05-20
I'm trying to run apache2 on an external hard drive (NTFS), so far I've tried editing 000-default.conf as well as apache2.conf but alas no luck. These are my configurations, can anyone tell me what I am doing wrong. I'm on Ubuntu Gnome 17.04.

Error

```
**Forbidden**

 You don't have permission to access / on this server.
```

000-default.conf

```
DocumentRoot /media/nelson/httpdocs
```

apache2.conf
```
<Directory /media/nelson/httpdocs/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>
```

---

### Post by TheFu on 2017-05-20
Format to a Linux file system and make the ownership of the files/directories such that the www-data userid can read the files.

[CENTER][/CENTER]OR

NTFS permissions are generally controlled at mount time.  You probably don't want to allow automatic mounting of the NTFS nor do you want to mount it under /media/.  Plus, I don't know if symlinks are supported on NTFS using the Linux ntfs-3g driver.  Manually mount the NTFS partition and  carefully control the file and directory permissions at mount time to allow read by the www-data userid.

While it is possible to setup a userid <---> NTFS-userid mapping, this is a huge hassle and I've only seen that done in govt locations with 6+ full-time admins just for the network. It was a daily, constant, effort, to keep those mappings.

The easy answer is to switch to native linux file systems and use normal file and directory permissions. This will solve the problem forever.

---

### Post by Habitual on 2017-05-20
> **TheFu said:**
> Format to a Linux file system and make the ownership of the files/directories such that the www-data userid can read the files.

[CENTER][/CENTER]OR

NTFS permissions are generally controlled at mount time.  You probably don't want to allow automatic mounting of the NTFS nor do you want to mount it under /media/.  Plus, I don't know if symlinks are supported on NTFS using the Linux ntfs-3g driver.  Manually mount the NTFS partition and  carefully control the file and directory permissions at mount time to allow read by the www-data userid.

While it is possible to setup a userid <---> NTFS-userid mapping, this is a huge hassle and I've only seen that done in govt locations with 6+ full-time admins just for the network. It was a daily, constant, effort, to keep those mappings.

The easy answer is to switch to native linux file systems and use normal file and directory permissions. This will solve the problem forever.
Are you saying "defaults"? :)

Not trying to start trouble, just this topic looks familiar.
It's Saturday, I should disconnect.

search userdir at [https://help.ubuntu.com](https://help.ubuntu.com) for a tease?

---

### Post by TheFu on 2017-05-20
I'll try to explain.  Had to wipe an NTFS format this morning over file permissions.

Automatic NTFS mounting expects 1 userid to use the files.

Since this is likely web files for static AND dynamic purposes, the actual file permissions ARE very important.  Hence, why I strongly encourage the user to switch to a Linux file system from NTFS.  If this is just for static files, then it doesn't matter THAT much. 

The other option I mention is to control the NTFS mounts so that both the userid AND www-data have the necessary permissions.  After all, chmod doesn't work on NTFS, unless the userid <----> NTFS-uuid mapping has been done.  Anyone who wants to do that can certainly look it up and perform the work.  It is a hassle.  

It is possible to control file permissions for NTFS at mount time - all files get 775 and all directories get 775.  This way, cgi scripts, php, perl, python, ruby scripts can all work, but many of these programs will insist on specific file and directory permissions that aren't *stupid* for web security. I don't think that can be accomplished in a general way without using a file system that Linux natively understands.  Anyway, [https://ubuntuforums.org/showthread.php?t=1604251](https://ubuntuforums.org/showthread.php?t=1604251) explains the simpler method to control permissions at mount.

BTW, if this is an external drive, be careful with the fstab options. Don't force the drive to be mounted, even if it isn't there. That isn't good for a booting OS.

Some other ideas: [https://askubuntu.com/questions/54321/how-do-i-give-multiple-users-access-to-a-windows-ntfs-partition](https://askubuntu.com/questions/54321/how-do-i-give-multiple-users-access-to-a-windows-ntfs-partition)

I was unable to quickly find the NTFS-uuid to Linux userid mapping technique. Sorry.

---

