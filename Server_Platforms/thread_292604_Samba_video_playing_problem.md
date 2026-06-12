---
title: "Samba video playing problem"
date: 2006-11-04
forum: Server Platforms
---

### Post by ariek on 2006-11-04
Hi,

On my Edgy server I'm running samba to share my music and videos.
On my laptop I'm running XP as well as Edgy. With XP I can play videos from my server - ofcourse without downloading them first. With Edgy, however, I cannot. The only way to play my videos is to download them first.

Has anyone an idea?

---

### Post by fernando_lopes_jr on 2006-11-04
I had the exact same problem you have to mount your share in FSTAB, if you are using Places >> Connect to Server you cannot view your movies or hear your mp3 it doesn't make a lot of sense since they are both mounts of shares.

---

### Post by ariek on 2006-11-04
Hi Fernando,

Thanx for your quick  reply. Your remark send me into the right direction.  When I use mount smbfs etc. it works as well.
Now I would like to know the diffences between Nautilus' way to connect to a server, and Samba mount.

Arie

---

