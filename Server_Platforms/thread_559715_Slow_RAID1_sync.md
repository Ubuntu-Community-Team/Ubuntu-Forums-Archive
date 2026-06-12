---
title: "Slow RAID1 sync"
date: 2007-09-25
forum: Server Platforms
---

### Post by matt_b on 2007-09-25
Hi all,

I've just installed two brand new Hitachi 320GB SATA-II drives in my PC.  Using mdadm I created a RAID1 array, but for some reason the resync operation is *rediculously* slow. If I cat /proc/mdstat I get:

[b]
Personalities : [raid1]
md0 : active raid1 sdc1[1] sdb1[0]
312568576 blocks [2/2] [UU]
[>.....................] resync =  0.3% (993792/312568576) finish=5020.3min speed=1032K/sec
[/b]

Not sure why this is going so slow - the PC is an Athlon X2 4600+ with 2GB RAM, running Dapper AMD 64.

Can someone please help?

Thanks
Matt

---

### Post by raijinsetsu on 2007-09-25
This is probably because it is trying to nicely sync the drives. If it were to run at full speed, your system would be almost useless.

---

### Post by matt_b on 2007-09-25
Ahh I see. Given that the box is doing nothing, and I don't want to wait 83 hours for it to rebuild I ran the following command:

[b]
echo 50000 > /proc/sys/dev/raid/speed_limit_min
[/b]

And things have sped up a touch, now running at 54826K/sec, with a rebuild time of 85 minutes :)

---

