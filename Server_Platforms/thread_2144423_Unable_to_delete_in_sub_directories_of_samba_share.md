---
title: "Unable to delete in sub directories of samba share"
date: 2013-05-12
forum: Server Platforms
---

### Post by RandomP on 2013-05-12
Hello all, 

I have an issue with my server. I have it set up as a Transmission torrent server that downloads directly into a local simple samba share. 

The issue that I am having is that group writing access is applied to the folder:
```
chmod -R 775 /home/debian-transmission/Downloads
```
But sub directories within that directory do not have the same permissions. I would like to be able to delete contents I download while I am away from the server and not have to SSH into it to do it.

So basically, I want to have read/write access to everything within my samba share. What would be the best method to do this?

---

### Post by darkod on 2013-05-12
I had a similar problem. I think transmission by default writes the files with its own user as owner. There was a setting you can put in settings.json something like:
umask = 0 (if I remember correctly)

In that case the transmission daemon will not be the owner of the downloaded files and you should be able to delete without problems.

---

### Post by volkswagner on 2013-05-12
Is Transmission writing directly to the folder, or is it connecting via SAMBA.

My first thought is to add yourself to the Transmission group.

If you can get Transmission to write to the directory via SAMBA, you'll be able to add settings to smb.conf.

```
[downloads]
  comment = Transmission folder
  path = /home/debian-transmission/Downloads
  valid users = random joe
  force group = users 
  create mask = 0775
  directory mask = 0775

```

---

### Post by RandomP on 2013-05-12
> **darkod said:**
> I had a similar problem. I think transmission by default writes the files with its own user as owner. There was a setting you can put in settings.json something like:
umask = 0 (if I remember correctly)

In that case the transmission daemon will not be the owner of the downloaded files and you should be able to delete without problems.

Ahh, this solved it. Thanks a bunch. Had to ssh in to delete the old stuff, but now everything is good.

> **volkswagner said:**
> Is Transmission writing directly to the folder, or is it connecting via SAMBA.

My first thought is to add yourself to the Transmission group.

If you can get Transmission to write to the directory via SAMBA, you'll be able to add settings to smb.conf.
I have it set up as Transmissions' download folder is being shared via SAMBA. The poster above solved my problem.

---

