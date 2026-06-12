---
title: "Raid 1"
date: 2009-07-05
forum: Server Platforms
---

### Post by ken22 on 2009-07-05
Is grub setup on both drives of a RAID 1 config by default?

I see it isn't on older versions but is it taken care of in 9.04?

Output of find /boot/grub/stage1 in grub is

```

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
 (hd1,0)
```

Does this mean I'm all set up?

---

### Post by Boondoklife on 2009-07-05
Well do you have more than one HD in the pc? if not then your good =). If you do then as long as the two raid drives are the ones specified then yes.

---

### Post by ken22 on 2009-07-06
I have 2 physical drives.

I made 2 partitions on each. 1 for / and 1 for swap.

Thank you for your response.

---

### Post by Boondoklife on 2009-07-06
Sounds like you are good to go, you could test it by unhooking a drive and trying to boot each drive.

---

### Post by ken22 on 2009-07-06
Ah yes, of course.

That'd do it.

Thanks.

---

### Post by fjgaude on 2009-07-06
It sure didn't be by default a year ago... it may not still be.

```
sudo grub
 grub>device (hd0) /dev/hdb
 grub>root (hd0,0)
 grub>setup (hd0)
```

Something like this will put the boot code on the other drive than where it is now at install.

Let us know how the testing goes, for our infomation. Thanks!

---

### Post by ken22 on 2009-07-07
I unhooked each drive and was able to boot off the other drive.

I didn't touch grub during my setup but I can successfully boot off both drives. Both MDRs are as they should be.

Cheers guys.

---

