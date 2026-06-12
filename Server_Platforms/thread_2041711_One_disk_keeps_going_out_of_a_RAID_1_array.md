---
title: "One disk keeps going out of a RAID 1 array"
date: 2012-08-13
forum: Server Platforms
---

### Post by mansonthomas on 2012-08-13
Hi guys,

 it's been quite a nightmare this weekend...

  I perform an upgrade from 11.04 to 12.04... the first reboot for 11.04 to 11.10 was OK, but the second, the serve won't start...

  because /dev/sdb partitions was removed from the raid...

  It's the second time it happen.. my host company say it's nothing, and I rebuilt the array...

  this time I spend a few hours between 3 & 7 am to restart my server correctly. there's still a f*cking bug that prevent you to type 'Y' to the question : would you like to boot a degraded array, I finally change the kernel option to allow booting  degraded array, and got the service back.

 Now, when I look to smartctl, I see bad sectors on /dev/sda, and /dev/sdb seems fine.
  it's soft raid, so I can't explain why /dev/sdb goes out the array from time to time.

 any idea of how to debug this ?

Regards,
Thomas.

---

