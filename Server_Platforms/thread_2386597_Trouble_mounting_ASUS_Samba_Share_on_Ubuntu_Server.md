---
title: "Trouble mounting ASUS Samba Share on Ubuntu Server"
date: 2018-03-07
forum: Server Platforms
---

### Post by vsiege2 on 2018-03-07
I'm trying to mount a USB drive (attached to ASUS RT-AC87U router) on my Ubuntu box. I have created credentials which I have verified are working from my OS X computer.

Here's how I try to mount it and the message:

```
[B]sudo mount -v -t cifs -o username=tt,password=123456 //HOUSE/hallway /mnt/hallway
[/B]mount.cifs kernel mount options: ip=192.168.1.1,unc=\\HOUSE\hallway,user=tt,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I can see the samba share on Ubuntu using [B]smbtree:
[/B]```
[INDENT][COLOR=#4C2F2D][FONT=Courier]smbtree
[/FONT][/COLOR]on DataTraveler G3
        \\HOUSE\hallway           USB_STICK16's stairway in Kingston DataTraveler G3[/INDENT]

```
Server Info:
```
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"
NAME="Ubuntu"
VERSION="16.04.4 LTS (Xenial Xerus)"

```

ASUS Router:[INDENT]RT-AC87U
[/INDENT]

I installed the following packages on the server and created the mount point:
```

[FONT=courier new][COLOR=#000000]apt-get install cifs-utils [/COLOR][COLOR=#4C2F2D]smbclient -y
[/COLOR]sudo mkdir -p /mnt/hallway
sudo chown :myteam /mnt/hallway
sudo chmod g+w /mnt/hallway[/FONT]

```

---

### Post by wildmanne39 on 2018-03-07
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by vsiege2 on 2018-03-07
Here's the latest. I tried making the share name lowercase and got the following:
```
sudo mount -v -o username=tt,password=12345 //hallway /mnt/hallway
[sudo] password for usernameHere: 
mount.cifs kernel mount options: ip=192.168.2.1,unc=\\hallway\,user=tt,prefixpath=mnt/hallway,pass=********
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

---

### Post by vsiege2 on 2018-03-07
Solved. I made the name lowercase and added the IP address.:D
```
sudo mount -v -o username=tt,password=12345 //192.168.1.1/hallway /mnt/hallway

```

---

