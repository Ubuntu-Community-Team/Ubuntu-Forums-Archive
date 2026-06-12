---
title: "Combine two hard drives"
date: 2009-05-12
forum: Virtualisation
---

### Post by yazidarezki on 2009-05-12
Hello, I have two hard drives and have installed Ubuntu on one drive. Which command can I use so that Ubuntu sees the two hard drives as one. I would like to make use of all the space.
 
TIA
Yaz

---

### Post by Lampi on 2009-05-12
I guess lvm2 should cover it (LVM = logical volume management) - but it if I recall correctly this would require your current ubuntu installation to be in Logical Volume Group already.

If you don't want to move your current Ubuntu into a LVG you could assign the rest of the free disk space + the new disc into one Logical Volume

---

### Post by yazidarezki on 2009-05-13
Can you explain more
 
Thanks

---

### Post by bodhi.zazen on 2009-05-13
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

For info on LVM see : [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

---

