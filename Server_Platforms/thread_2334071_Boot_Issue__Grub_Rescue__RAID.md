---
title: "Boot Issue / Grub Rescue / RAID"
date: 2016-08-16
forum: Server Platforms
---

### Post by marcusd2 on 2016-08-16
Hi all,

One of my Raid 1 HDD is crashed and i can´t boot from the single HDD. I get the GRUB rescue prombt. I try to use Boot repair but it doesn´t work.

[http://paste.ubuntu.com/23060764/](http://paste.ubuntu.com/23060764/)

Can anyone have a look - hopefully it´s possbile to boot with this disk.

Thanks
Marcus

---

### Post by oldfred on 2016-08-16
Moved to server sub forum where those who know RAID may respond.

---

### Post by darkod on 2016-08-16
The bootinfo seem to show dmraid, or equivalent to bios raid. Is that what you had configured? If yes, you need to do all management using the bios raid menu, where you configured it.
If you had mdadm software raid it's a different story. But it doesn't seem like it.

---

### Post by marcusd2 on 2016-08-16
i´m using the RAID from the motherboard. What is your recommendation ?

Thanks
Marcus

---

### Post by darkod on 2016-08-16
Go into the raid bios and check the array status there. It might give you some ideas.
Depending how it works, you might need to replace the failed disk in order to make the system boot.
This is why most people don't use mb raid. Especially if you have only linux on the machine, there are no benefits of mb raid. Only downsides. The mdadm sw raid is much better to use.

---

