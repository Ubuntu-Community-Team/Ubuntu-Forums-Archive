---
title: "Install Ubuntu server on Raid5"
date: 2008-01-08
forum: Server Platforms
---

### Post by geforce123 on 2008-01-08
So that's it. I'm currently installing ubuntu server 6.06 LTS.

When it comes up to GRUB install, it always freezes at 50 % (Installing grub on Hd0)...

Anyone had this issue ? What can I do ?

Thanks

Phil

---

### Post by fozy on 2008-01-08
Do you have the boot partition on a RAID 5 or RAID 1?  For Grub to work you need to have the boot partition on a RAID 1, while the rest of the system can be a RAID 5.

---

### Post by geforce123 on 2008-02-03
Yeah,

That was exactly my problem: I was trying to install grub on RAID-5.

Now it works #1 on Raid-1.

Thanks,

Phil

---

