---
title: "I accidentally changed / to 770"
date: 2010-05-20
forum: Security
---

### Post by sam1948 on 2010-05-20
Hi.
while trying to change some other directory I accidentally pressed the enter 
do not try this at home:
```
chmob 770 /
``` 
any idea how to recover this clumsy mistake??
(i was in a "sudo -i" shell)
thanks

---

### Post by anomie on 2010-05-20
I'm presuming what you typed was 'chmod' (not 'chmob'), and that your post above contains a typo. 

AFAIK, there is no "recovering" from this, per se. The best approach is to restore from your backups.

---

### Post by snova on 2010-05-20
> **sam1948 said:**
> Hi.
while trying to change some other directory I accidentally pressed the enter 
do not try this at home:
```
chmob 770 /
``` 
any idea how to recover this clumsy mistake??
(i was in a "sudo -i" shell)
thanks

If the system still boots, and you can get to a root shell (recovery mode may or may not work), then simply revert the permissions:

```
chmod 755 /
```

Otherwise boot a live CD and repair it from there.

---

### Post by sam1948 on 2010-05-21
thanks for the replay.
(I used chmod of course.)
the system won't start even in recovery mode and root shell.
I do have live cd and also another installation on other partition.
i tried to chmod back from the uther installation but it did not work.
I really prefer to restore permissions rather than restore my backups.
any idea will be helpful.

thank again.

---

### Post by anomie on 2010-05-21
I'd add that I assumed you changed perms recursively, from / on down. If you didn't do so recursively, it really would be as simple as changing the perms on /. 

Unless you have an accurate point of reference - e.g. a HIDS db already built for that system, or a similar Ubuntu system that you can refer to - it's going to be difficult to restore *only* permissions. Even with a reference point, it's going to be tedious. 

This is a hard mistake to abide, but I'm fairly certain you won't be making it again.

---

### Post by sam1948 on 2010-05-21
thanks again
so I guess i'll restore from backup.
(it was not recursively but still, the problem is how to refer "/" of one system from another and as "/" and not as a regular mount point)

---

### Post by cdenley on 2010-05-21
From the livecd, you would mount the filesystem which is on your hard drive, then chmod the mount point, which would be the root directory of that filesystem.
```

sudo chmod 755 /media/[UUID?]

```
You don't want to chmod the livecd's root filesystem, as that wouldn't fix anything.

---

### Post by anomie on 2010-05-21
[QUOTE=sam1948]thanks again
so I guess i'll restore from backup.
(it was not recursively but still, the problem is how to refer "/" of one system from another and as "/" and not as a regular mount point)[/QUOTE]

Oof. I totally misunderstood your post (and assumed the wrong thing). No need to dig out your backups yet, although I'm proud that you actually *have* backups. 

If you can't even get to single-user mode, a live CD is definitely the way to go to solve your problem. And you've already gotten replies with tips on this thread.

---

### Post by sam1948 on 2010-05-22
> **anomie said:**
> Oof. I totally misunderstood your post (and assumed the wrong thing). No need to dig out your backups yet, although I'm proud that you actually *have* backups. 

If you can't even get to single-user mode, a live CD is definitely the way to go to solve your problem. And you've already gotten replies with tips on this thread.

never mind a fresh 10.04 was installed.
my 2Gb file ubuntu_backup.tar.gz was corrupted ):
I tried to "chmod 755 /dev/disk/by-uuid/?#R#fdsds_whatever"
but it didn't help. I believe / of one installation can't be referred as a mounted partition on other installation.

bests & stability (:
thanks

---

### Post by snova on 2010-05-22
> **sam1948 said:**
> 
I tried to "chmod 755 /dev/disk/by-uuid/?#R#fdsds_whatever"
but it didn't help.


Uh, those are device files.

> I believe / of one installation can't be referred as a mounted partition on other installation.

Yes you can; / is *the mount point itself*. Boot a live CD, mount the drive, and chmod whatever directory appears in /media.

---

### Post by jerome1232 on 2010-05-23
Seeing as the live cd won't auto mount it you just have to mount it (I know this is late but just in case someone else stumbles on it)

So assuming your / is /dev/sda1 you would have

```
sudo mount /dev/sda1 /mnt
sudo chmod 755 /mnt
```

---

### Post by sam1948 on 2010-05-25
DO NOT TRY THIS AT HOME

I know it sounds reasonable and simple but those solutions didn't work.
the drive was mounted and the mod was change but the system still fail to start after boot.

bests

---

