---
title: "permission problems with www-data user"
date: 2015-09-08
forum: Server Platforms
---

### Post by Hansje on 2015-09-08
Hi there,

I'm using owncloud for a while and I'm very happy, it does what I expect it to do.
Now I'm presented with a problem, the storage is full. I bought a new HD, added it in the computer and did a search on how to move owncloud to the new disk. I followed this guide: [https://forum.owncloud.org/viewtopic.php?t=7118](https://forum.owncloud.org/viewtopic.php?t=7118)

After doing exactly that, owncloud can't connect to my data dir and owncloud is complaining:
> Cannot create "data" directory (/media/neoscores/files/owncloud/ocdata)
This can usually be fixed by giving the webserver write access to the root directory.

I'm on an Ubuntu 14.04, ownCloud 8.1.1, PHP version 5.5.9-1.

The owner of /media/neoscores/files/owncloud is 'www-data:www-data' (recursive) and is not the mount point ('files' is the mount point). Permissions of /media/neoscores/files/owncloud are 770 (recursive).

Output of 
```
echo
"User: " . exec('whoami');
echo "Group: " . exec('groups');
```
is 'www-data'.

I'm stuck, no clue on what's going on. It has something to do with my linux, because I can't:
```
sudo -u www-data mkdir /media/neoscores/files/owncloud/testDir
```

But I can cd my way to '/media/neoscores/files/' and 
```
sudo -u www-data mkdir owncloud/testDir
```
without problems...

Ow yes, SELinux is disabled.

Is there anybody who can point out what's going wrong?

Thanks!

---

### Post by patlkli on 2015-09-08
Please check, that the user www-data has at least execute permission on **all** directories traversed when changing into /media/neoscores/files.

I guess that /media/neoscores has no execute permission set for others, so that www-data can't change into the directory.
However if you already are in the directory on the shell and execute something as www-data, it can traverse it anyhow.

---

### Post by Hansje on 2015-09-08
Ok, this costed me 2 days.
It worked.

The neoscores folder had no execute rights.

Thinking about it it's just logic that it should have these rights.

THX!

---

### Post by patlkli on 2015-09-08
No problem.

If your problem is fixed now, please mark the thread as solved using the Thread Tools.

---

