---
title: "Mounted share access issue"
date: 2022-05-05
forum: Server Platforms
---

### Post by brent1975 on 2022-05-05
I am running 20.04 and have nextcloud installed and is running smoothly. 


[LIST]
[*]I am working on backups and would like to move the nextcloud data directory off the server.
[*]Currently I have the data directory sitting in /opt/nextcloud which is working fine.
[*]I would like to point the data directory to /mnt/linux-share/nextcloud/ which is an external attached windows share. (Yes I know it's not optimal but it's what I have available)
[*] I can access the share on the box flawless.
[/LIST]

when I point nextcloud data directory to /mnt/linux-share/nextcloud which is where I copied the data folder I am getting the following permission issue.

```
Your data directory is not writablePermissions can usually be fixed by giving the webserver write access to the root directory. See https://docs.nextcloud.com/server/23/go.php?to=admin-dir_permissions.
```

This appears to be apache write permission to the data directory but I don't know how to resolve this. I followed this site [https://stackoverflow.com/questions/22062266/how-to-give-apache-permission-to-write-to-home-directory](https://stackoverflow.com/questions/22062266/how-to-give-apache-permission-to-write-to-home-directory) to CHOWN the folder to www-data.

I checked /opt/nextcloud/data
```
brent@web1:/opt/nextcloud/data$ lltotal 5492
drwxr-x---  6 www-data www-data    4096 Nov 24 14:13 ./
drwxr-xr-x  3 root     root        4096 Oct  7  2021 ../
drwxr-xr-x 14 www-data www-data    4096 Feb 23 21:07 appdata_ocgxj5vyhjq1/
drwxr-xr-x  7 www-data www-data    4096 Mar 18 16:50 brent/
-rw-r--r--  1 www-data www-data     542 Apr 22 10:22 .htaccess
-rw-r--r--  1 www-data www-data       0 Apr 22 10:22 index.html
drwxr-xr-x  5 www-data www-data    4096 Oct  7  2021 linda/
-rw-r-----  1 www-data www-data 5488966 May  5 10:22 nextcloud.log
-rw-r--r--  1 www-data www-data       0 Apr 22 10:22 .ocdata
-rw-r--r--  1 www-data www-data   90849 Apr 22 10:22 updater.log
drwxr-xr-x  4 www-data www-data    4096 Apr 22 10:22 updater-ocgxj5vyhjq1/

```

I  am not sure if this is the best way of doing this and may cause some performance issues loading etc. Perhaps an actual backup job would be a better option. 

Any assistance or advice is greatly appreciated.

---

### Post by rsteinmetz70112 on 2022-05-05
What are the permissions of 
```
 /mnt/linux-share/nextcloud/

```
and
```
/opt/nextcloud/data
```
?
It looks like the last one is```
 drwxr-xr-x  root root
``` so www-data does not have write access

---

### Post by brent1975 on 2022-05-05
for /mnt/linux-share/nextcloud/
```
drwxr-xr-x 2 root root           0 May  5 13:55  nextcloud/
```

for /opt/nextcloud/data
 ```
drwxr-x--- 6 www-data www-data 4096 Nov 24 14:13 data/
```

I have tried running ```
sudo chown -R www-data:www-data /mnt/linux-share/nextcloud
```

The ownership wont change. Is this because it's a mounted windows share?

---

### Post by rsteinmetz70112 on 2022-05-05
Your chown command is incomplete you need the new owner.

---

### Post by brent1975 on 2022-05-06
I forgot to add www-data to the post. The ownership won't change. None the less I am just doing full VM backups. I think saving this to an external share will cause performance issues. 

I appreciate the assistance.

---

### Post by rsteinmetz70112 on 2022-05-06
As a test you could try```
sudo  chmod 757 /mnt/linux-share/nextcloud/
``` to see if that helps

---

### Post by TheFu on 2022-05-06
> **brent1975 said:**
> for /mnt/linux-share/nextcloud/
```
drwxr-xr-x 2 root root           0 May  5 13:55  nextcloud/
```

for /opt/nextcloud/data
 ```
drwxr-x--- 6 www-data www-data 4096 Nov 24 14:13 data/
```

I have tried running ```
sudo chown -R www-data:www-data /mnt/linux-share/nextcloud
```

The ownership wont change. Is this because it's a mounted windows share?

You can't use CIFS for nextcloud data to my knowledge.  You cannot use NTFS either.  File permissions are a core part of the data security model for nearly all Linux servers.

When you copied all the data, you lost the permissions, owner, group, ACLs and some xattrs.  Ouch.  I hope you have a backup which contains those things.  We cannot just blindly use a file manager to copy and paste server data around. That is extremely likely to break things, even if both the source and targets are native Linux file systems.

In my nextcloud data directory, some of the subdirs are
```
drwxr-xr-x  8 www-data www-data
drwxr-x---  4 www-data www-data
```
They all appear to be www-data:www-data, so that's probably safe.
Similarly, files under each user are 644 and directories are 755.

Because I don't trust nextcloud, most data is actually provided to nextcloud as read-only NFS mounts, which were setup using autofs for photos, ebooks, and music.  I find that nextcloud isn't very good at sharing any of those - not really, but I do use it from android to pull ebooks and audiobooks local to the android devices before leaving the house.

---

