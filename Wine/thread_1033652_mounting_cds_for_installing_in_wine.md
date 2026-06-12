---
title: "mounting cds for installing in wine"
date: 2009-01-07
forum: Wine
---

### Post by twitch2197 on 2009-01-07
i need to mount an iso to use to install a game (using wine). it has a gold rating in the wine appdb so it should work but i need to know where to mount the disk image. i tried in the default disk location (cdrom0) but when i tried installing, wine told me "no disk inserted. please insert the cd and press retry".
is there a different location (maybe the "cdimages" folder) i need to mount the cd for it to work in wine?

I'm running hardy heron.

---

### Post by dadozgb on 2009-01-07
> **twitch2197 said:**
> i need to mount an iso to use to install a game (using wine). it has a gold rating in the wine appdb so it should work but i need to know where to mount the disk image. i tried in the default disk location (cdrom0) but when i tried installing, wine told me "no disk inserted. please insert the cd and press retry".
is there a different location (maybe the "cdimages" folder) i need to mount the cd for it to work in wine?

I'm running hardy heron.

There is no such thing as a folder on linux. It's directory. Where is your mount point for cdrom? You can see it if you writte in a terminal cat /etc/fstab and look for the line like this 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8
This is my mount point for cdrom device. Mount it like mount /media/cdrom0.

---

