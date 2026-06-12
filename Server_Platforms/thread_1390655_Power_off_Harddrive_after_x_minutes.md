---
title: "Power off Harddrive after x minutes"
date: 2010-01-25
forum: Server Platforms
---

### Post by kanolsen on 2010-01-25
I have a small shuttle computer with ubuntu 9.10 on it. 
It has 2 harddrives on it, and most of the time it's idle, but the harddrives get quite hot. 

Is there a way of shutting the harddrives off in ubuntu after a set amount of minutes, so it wakes up again when I try to access them?

Thanks in advance.
Kanolsen

---

### Post by ian dobson on 2010-01-26
Hi,

Have a look at hdparm the -S option lets you set the powerdown time. Something like:-
hdparm -S30 /dev/sdd

Regards
Ian Dobson

---

### Post by kanolsen on 2010-01-27
Thank you, I did look in the BIOS, and found a harddrive shutdown feature there, does Ubuntu follow the BIOS instruction, or do I still have to make the command mentioned in the thread?

Thanks in advance

Kanolsen

---

