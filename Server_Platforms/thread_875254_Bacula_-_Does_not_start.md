---
title: "Bacula - Does not start"
date: 2008-07-30
forum: Server Platforms
---

### Post by vcbranco on 2008-07-30
Hy everyone

I installed Bacula in Ubuntu Server 8.04 i386 and when I boot the system I have the following error:

Config error: expected a name, got T_EOL
            : line 49, col 20 of file /etc/bacula/bacula-sd.conf
  Archive device=


I checked the file and I don't see anything I consider wrong and  don't know what i need to search

Many thanks in advance

---

### Post by StickyStyle on 2008-07-30
What's on line 49?  It's saying that it expected some value to be somewhere, but just got an end of line.

If it's that printed out "Archive device=" line, and there is nothing after the '=' then that's your problem.  You need to specify the device on that line.

you can see a sample here [https://help.ubuntu.com/8.04/serverguide/C/bacula.html](https://help.ubuntu.com/8.04/serverguide/C/bacula.html)

---

### Post by vcbranco on 2008-08-03
Sorry for the delay.

I will check the configuration sample and I will post the results.

Thanks

---

