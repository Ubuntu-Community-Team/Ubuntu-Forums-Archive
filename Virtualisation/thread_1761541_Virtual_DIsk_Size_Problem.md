---
title: "Virtual DIsk Size Problem"
date: 2011-05-18
forum: Virtualisation
---

### Post by lynwode on 2011-05-18
Hi,
I have an issue with a VDI that I have expanded. I have followed the usual process of creating a new disk, cloning the original and resizing via gparted (done this dozens of times in the past with no issues).

The disk was expanded from 20GB to 200GB. VirtualBox shows the attached drive as 200GB in the manager. However when I do a df in the guest its still at 20GB. I have checked in Gparted and its showing 200GB, the strange thing is though is its showing it as 185GB Full?

The VDI on the filesystem is 16GB.

Any ideas as to a) why the guest is not seeing the increased size and b)why is gparted reporting it as 185GB full?

Hope this makes sense.

Tim.

---

### Post by lynwode on 2011-05-18
One last thing fdisk -l shows it as 200GB - now I'm really confused.

---

### Post by lmarmisa on 2011-05-18
This link could help you:

[http://ubuntuforums.org/showpost.php?p=9792918&postcount=16](http://ubuntuforums.org/showpost.php?p=9792918&postcount=16)

---

### Post by lynwode on 2011-05-18
Genius - that worked a treat.
Now the question is why did this not happen as part of the resizing process?

---

### Post by lmarmisa on 2011-05-18
> **lynwode said:**
> Genius - that worked a treat.
Now the question is why did this not happen as part of the resizing process?

Gparted works normally fine resizing partitions, but sometimes it fails. I do not know the reasons.

Best regards,

Luis

---

### Post by lynwode on 2011-05-19
Thanks Luis, now I know to keep a eye out in the future.

---

