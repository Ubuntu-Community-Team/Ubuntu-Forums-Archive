---
title: "World Of Warcraft Install Problems."
date: 2009-04-21
forum: Wine
---

### Post by benster0080 on 2009-04-21
I will try to make this as thorough as possible. I attempted to install WoW using this guide here. [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft). I am on Ubuntu 8.10. The dvd mounted as the mac osx install so I unmounted it with ```
sudo umount /media/cdrom
``` and tried to remount it with the command ```
sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
```

This produced the following ```
mount: special device /dev/hdc does not exist
``` How do I remount it as Windows? Please Help.:(

---

