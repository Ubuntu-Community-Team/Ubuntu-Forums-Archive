---
title: "[SOLVED] nfs share second hdd"
date: 2008-09-14
forum: Server Platforms
---

### Post by trash on 2008-09-14
I had nfs working till I reinstalled mt server and changed what drive was being shared. Originally the share was on the same drive as the server but now it is a second drive that i istalled. It mounts fine on the client but ro only. I read that shares on different drives require different mounts but can't figure it out!

hda1 is my server
hdb1 is mounted on hda1 as media/storage and pretty much the standard setup of nfs. Can anybody tell me why on both machines i have read only access?
On server the fstab is vfat rw,users,_netdev,exec,utf8
and on client nfs  timeo=14,intr,soft (which worked best my first time around).

---

### Post by trash on 2008-09-15
the drive was vfat so i needed umask=000 to mount it user friendly:)

---

