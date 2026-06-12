---
title: "NFS file permission problem, able to mount with read but no write."
date: 2010-02-14
forum: Server Platforms
---

### Post by crackerizer on 2010-02-14
Hello, O:)

I'm setting up a home server. Things are going quite well. But i have some problems with NFS server. Below is the background situation:

- I've setup NFSv4 and it's actually working. I can mount everything attacthed to NFS server (/etc/exports).
- idmapd is working fine. it can map local & remote user/group correctly. Also, permission of files are mounted correctly.
- if both local & remote have the same owner (same username), i can access the mounted drive with read and write (or correct) permission.

Now, here is my problem:

- I can not write to any file when i dont have the same usename. Simple speak, group permission does not work.

I spent many hours looking for solution. But no luck.

Please give me some advise.

Tony

---

### Post by Jose Catre-Vandis on 2010-02-14
As a starting point have you put the "other" user in the same group as the one that works on both machines, and checked that the permissions for the files/directories are set for group level rw access?

---

### Post by crackerizer on 2010-02-14
Jose,

Thank you for your answer. And, yes, I checked it over and over again. All user/group/permission are set correctly. Only owner permission is working here.

---

### Post by Jose Catre-Vandis on 2010-02-15
Try here:

[http://ubuntuforums.org/showthread.php?t=295765](http://ubuntuforums.org/showthread.php?t=295765)

and here:

[http://ubuntuforums.org/showthread.php?t=1372642](http://ubuntuforums.org/showthread.php?t=1372642)

also, is your nfs share from the home directory of the "main" user? If so, try a share from a common area?

and

Depending on the level of security you need, what happens if you set all files with full read / write permissions (on the server)

```
sudo chmod -R 777 /files 
```

---

