---
title: "Problem with samba"
date: 2010-11-15
forum: Server Platforms
---

### Post by mr_Loki on 2010-11-15
Bought a new 1TB hard for local file server. Formatted as ext4, permanently mounted as /mnt/hard/ in /etc/fstab. Created folder /mnt/hard/storage/ and added this in smb.conf:

[storage]
path = /mnt/nard/storage/
browseable = yes
writable = yes
public = yes
create mode = 0750
directory mode = 0775

Displays in ubuntu and windows xp, but doesn`t open.

---

