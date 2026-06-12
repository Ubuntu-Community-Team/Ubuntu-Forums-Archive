---
title: "How do I performed a full validation of a soft raid 5 array?"
date: 2012-05-09
forum: Server Platforms
---

### Post by MikeNash1977 on 2012-05-09
Hi There
 
I am fairly new to using Ubuntu and linux in general, so please forgive me if I do a poor job of phrasing this question.
 
I am running Ubuntu Server 10.04 and I have a Raid 5 array setup which seems to running fine.
 
However, after seeing a few odd problems copying files to the server (they would copy successfully, but then a diff showed that the files weren't the same) yesterday I performed a MemTest on the machine and discovered that one of my DIMMs has been "dropping" bits (i.e. a bit contains a zero when it should contain a 1). 
 
I have replaced the memory, but I am concerned that this may have affected the integrity of the array.
 
"mdadm --detail" and "cat /proc/mdstat" both show the array as being clean, but they don't actually go through the array and validate that all of the parity data is consistent right?
 
Is there a way for me to check the integrity of the entire array (i.e. ensure that the parity value is correct for every single stripe) or is there something about the way that raid works which means that I don't have to do that?
 
Thanks
 
 
Mike
 
P.S. My array made up of 8x1.5TB disks - I am okay with the fact that it may takes days for the check to run! ;-)

---

### Post by rubylaser on 2012-05-09
mdadm has a cron task in /etc/cron.d/mdadm that runs on the first Sunday of every month and runs a check action that does exactly what you're talking about. My (10) disk RAID6 array only takes overnight to run it's check, so it shouldn't take days to run.

---

