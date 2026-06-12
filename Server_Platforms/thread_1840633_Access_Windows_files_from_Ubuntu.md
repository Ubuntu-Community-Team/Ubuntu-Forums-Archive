---
title: "Access Windows files from Ubuntu"
date: 2011-09-07
forum: Server Platforms
---

### Post by Zisis19992 on 2011-09-07
Hello,
I want to access the files that i have stored in Windows (XP) from Ubuntu... I read that i need first the GNOME partition manager (to find out whitch disk i'll enter in Terminal) but both of the disks (/dev/hda1 & /dev/hda2) are locked... What to do?:([URL="http://gparted.sourceforge.net/"]
[/URL]

---

### Post by papibe on 2011-09-07
Is it a Wubi or a regular install?

Regards.

---

### Post by Zisis19992 on 2011-09-08
> **papibe said:**
> Is it a Wubi or a regular install?

Regards.
Wubi :)

---

### Post by Rubi1200 on 2011-09-08
> **How do I access the Windows drives?**

 The  Windows partition where you installed Wubi is available as /host within  Ubuntu (Places > Computer > File System > Host) All the other partitions will be available under Places > Removable Media
[https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F)

Hope this helps.

---

### Post by Zisis19992 on 2011-09-08
> **Rubi1200 said:**
> [https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F)

Hope this helps.
Thank you so much... :) I've read an other way (via terminal) and i had some troubles... This is much simplier... Thanks again!;):D

---

### Post by Rubi1200 on 2011-09-08
Sure, no problem.

Enjoy :)

---

