---
title: "System time keeps going back 4 hours"
date: 2008-09-28
forum: Windows
---

### Post by cmat on 2008-09-28
After I reboot my laptop the time goes back 4 hours on the task bar. What can be causing this? Every time I reboot I need to set it ahead 4 hours. 

Compaq CQ50 with only Vista installed.

---

### Post by smoker on 2008-09-29
just a suggestion, check the time in the bios, and if that is out by four hours reset it to correct time in the bios setup screen. maybe when you adjust the time in vista it is not altering the bios time, so when you reboot the bios time, ie, wrong time, is passed to the operating system!

---

### Post by fballem on 2008-09-29
The following thread may help with your problem:

[http://ubuntuforums.org/showthread.php?t=896447&highlight=ubuntu+utc](http://ubuntuforums.org/showthread.php?t=896447&highlight=ubuntu+utc)

By default, ubuntu assumes that the actual clock is using UTC - which it might not be if you are using Windows. I'm assuming that you are currently in the Eastern Time Zone, which is GMT - 4 hours during Daylight Savings time.

Hope this helps,

---

### Post by cmat on 2008-09-29
For some reason my time zone settings are all wonky. I didn't ever even touch that panel since my clock was set correctly when I bought it. Now all of a sudden.

---

### Post by forger on 2008-09-29
So you don't have dual-boot with vista and ubuntu on the laptop?
You could use Atomic Clock Sync to check your time:
[http://www.worldtimeserver.com/atomic-clock/](http://www.worldtimeserver.com/atomic-clock/)

---

### Post by cmat on 2008-09-29
I'll try the internet time sync like I use on Ubuntu. 

No I don't dual boot since there are far too many serious bugs that have no solutions yet for this laptop. Quite frankly I don't have the time to file the bugs to the various projects. Someday I will.

---

