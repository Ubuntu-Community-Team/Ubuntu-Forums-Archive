---
title: "Help sharing Logical Volume via Samba"
date: 2015-12-31
forum: Server Platforms
---

### Post by robo731 on 2015-12-31
I'm new to Ubuntu, just to warn you. I've successfully created a logical volume and set it to mount at startup. Now I'd like to make that logical volume a samba share. I don't know how to go about this though. Do I need to create a directory within the logical volume and then share that?

---

### Post by bab1 on 2015-12-31
> **robo731 said:**
> I'm new to Ubuntu, just to warn you. I've successfully created a logical volume and set it to mount at startup. Now I'd like to make that logical volume a samba share. I don't know how to go about this though. Do I need to create a directory within the logical volume and then share that?
The LV is just the container for the partition that has a file system formatted on it (i.e. ext4).  Samba always shares a directory in the file system hierarchy.  So create a directory (folder) and share that with Samba.

---

### Post by robo731 on 2015-12-31
Okay, that's what I figured. Here's an excerpt from ```
mount
``````
/dev/mapper/UbuntuServer--vg-Media on /mnt/media type ext4 (rw)
``` So I should make a directory within /mnt/media right?

---

### Post by bab1 on 2015-12-31
> **robo731 said:**
> Okay, that's what I figured. Here's an excerpt from ```
mount
``````
/dev/mapper/UbuntuServer--vg-Media on /mnt/media type ext4 (rw)
``` So I should make a directory within /mnt/media right?
Right.  You never deal with the LV directly.  The formatted (ext4) partition is mounted at /mnt/media and you can make a directory there to share.

---

### Post by robo731 on 2015-12-31
Got it. Thanks again bab1.

---

