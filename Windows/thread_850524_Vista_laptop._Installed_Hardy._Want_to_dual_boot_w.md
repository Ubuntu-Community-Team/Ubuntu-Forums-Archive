---
title: "Vista laptop. Installed Hardy. Want to dual boot with XP, now"
date: 2008-07-05
forum: Windows
---

### Post by -ronin- on 2008-07-05
My HP Compaq 6820s came preinstalled with Vista. I installed Hardy on the entire disk. Now I want to install XP on it and then Hardy, again. This way, I can dualboot Hardy and XP. But when I try to install XP, I get this error:

```
Setup did not find any hard disk drives installed in your computer.
Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufacturer-supplied diagnostic or setup program.
Setup cannot continue. To quit Setup, press F3.
```

What do I have to do to get a a Hardy+XP dualboot going on this laptop?

---

### Post by Nessa on 2008-07-05
Format the drive to NTFS. I think you can use the Live CD for that. Then your XP should be able to read the drive and just repartition it for Hardy.

---

### Post by -ronin- on 2008-07-05
> **Nessa said:**
> **Format the drive to NTFS. I think you can use the Live CD for that. **Then your XP should be able to read the drive and just repartition it for Hardy.

how?

---

### Post by ad_267 on 2008-07-05
Use gparted on the ubuntu live cd. Boot into the live cd and it's under System - Administration - Partition Editor or something like that. Then just format the whole thing as ntfs and install xp on it. Afterwards you can shrink the xp partition and install Ubuntu.

---

### Post by -ronin- on 2008-07-05
that worked. thank u. :-)

---

