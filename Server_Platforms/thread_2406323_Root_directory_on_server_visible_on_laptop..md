---
title: "Root directory on server visible on laptop."
date: 2018-11-19
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2018-11-19
When I open the file manager I can click my server. When clicking it, it loads the servers / directory. I have double and triple checked my shares. Nothing is exporting /. They are all to specific directories in my snapraid pool. Why can I browse my servers /?

---

### Post by TheFu on 2018-11-19
Which protocols have you configured on the server?
Have you checked all the running listeners?

---

### Post by Tadaen_Sylvermane on 2018-11-20
Samba config. Just part I've changed. Rest is default file on installation.

```
[backups]path = /snapraid/pool/backups/yansell
valid users = yansell
read only = no
directory mask = 0755
create mask = 0644


[music]
path = /snapraid/pool/music
valid users = @ourmedia
read only = no
directory mask = 0755
create mask = 0644


[videos]
path = /snapraid/pool/videos
valid users = @ourmedia
read only = no
directory mask = 0755
create mask = 0644


[paperwork]
path = /snapraid/pool/backups/paperwork
valid users = @ourpaperwork
read only = no
directory mask = 0775
create mask = 0664
```

NFS exports. Full file.

```
##### pool for media sharing across the network #####
/snapraid/pool          192.168.1.0/24(rw,insecure,no_root_squash,no_subtree_check,fsid=2)
##### paperwork backup #####
/snapraid/data/data1/backups/paperwork  192.168.1.0/24(rw,no_root_squash,no_subtree_check)
```

Could it be the ftp server I recently setup to make it easier for the wife to add media to the server? Was using Samba shares at the time but I figured the FTP server would be easier for her to work with.

How to check running listeners?

---

