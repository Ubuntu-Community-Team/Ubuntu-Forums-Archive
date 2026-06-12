---
title: "Windows XP regocnizes itself as F:"
date: 2006-10-17
forum: Windows
---

### Post by aswells on 2006-10-17
I recently finished installing a small "wintendo" patrition in my linux-only machine. After the install was was complete, I was unable to install any drivers or the like because my windows partition recognizes itself as F: instead of C:. How would I chance the windows partition to C?

Thanks in advance

---

### Post by Lord Illidan on 2006-10-17
This happened to me too. What I do is change the paths in the installation program. So if it asks to install in C:/Program Files, I change it to F:/Program Files.

---

### Post by aswells on 2006-10-17
Thanks Illidan, If I cant find a way to change the drives name I am planning on that.

---

### Post by Lord Illidan on 2006-10-17
You can also try this, but there is a risk...
[http://www.petri.co.il/change_system_drive_letter_in_windows_xp.htm](http://www.petri.co.il/change_system_drive_letter_in_windows_xp.htm)

---

### Post by aswells on 2006-10-17
Changing the installation path wont be bad. I just checked, and GRUB doesnt regocnize windows. I used this method to restore grub after the windows install on the ubuntu live cd

```

sudo -i
grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
```

Any ideas?

---

### Post by RJARRRPCGP on 2006-11-26
The only ways to prevent this issue:

Format the partition with FAT32.

-or-

Disconnect other HDDs before installing Windows. 
Leave only one HDD connected!

---

### Post by aswells on 2006-11-26
I only have one hard drive, I installed windows on its own partition on the same hard drive.

---

### Post by RJARRRPCGP on 2006-11-26
> **aswells said:**
> I only have one hard drive, I installed windows on its own partition on the same hard drive.

Then you must install from a CD, delete all other partitions and try again.

---

### Post by Chinkostu on 2006-11-27
You'll have to remove all partitions, install windows, and then setup your partitions. even if XP does not support EXT out of the box, it would still physically recognise them (C being partition1, D being 2 etc) so it stuck inself into 4 and named itself F.

---

### Post by ShadowVlican on 2006-11-28
this only happens because you didn't install windows on the "first" drive

the bios detects the drives and usually IDE hard drives have priority, so if you install windows on sata with IDE present, it usually doesn't come out as C:

---

