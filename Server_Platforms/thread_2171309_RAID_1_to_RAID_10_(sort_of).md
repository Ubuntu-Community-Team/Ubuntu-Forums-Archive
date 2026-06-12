---
title: "RAID 1 to RAID 10 (sort of)"
date: 2013-08-30
forum: Server Platforms
---

### Post by soapdude on 2013-08-30
This forum and one specific user were a HUGE help with a previous issue that I had with a failed RAID 1 array.. Thank you!

Here's my new question: 

I have four identical hard drives. I am running Ubuntu 12.04 server edition under a RAID 1 array which currently utilizes two of the hard drives.

For various reasons, I am considering reinstalling Ubuntu. I would like to use the two new hard drives to reinstall Ubuntu, copy relevant information from the two old hard drives, and then include the two original hard drives plus the two new hard drives into a RAID 10 array.. Is there any way to make this happen? Is there a better option?

---

### Post by houstonbofh on 2013-08-30
Not really...  Setting up the two mirrors is no problem, but adding a stripe to an existing data set is not going to happen.  How are you get every other block to the other mirror?

---

### Post by soapdude on 2013-09-06
Got it. Makes sense. Thank you!

---

### Post by SaturnusDJ on 2013-09-06
Actually...it is possible.

I never tried this myself but read about it several times.
Check the posts over here: [http://serverfault.com/questions/43677/best-way-to-grow-linux-software-raid-1-to-raid-10](http://serverfault.com/questions/43677/best-way-to-grow-linux-software-raid-1-to-raid-10)
In your case you don't have to do it exactly this way, it can be simpler.

---

### Post by soapdude on 2013-09-06
Interesting..! I may give it a try if I can get the RAID1 array working properly again. RAID10 would be a big improvement over having two RAID 1 setups

---

### Post by houstonbofh on 2013-09-06
There are lots of ways to do this under the table.  But they all start with make a good backup.  If you can make a good backup, you will get much better results if you just restore it to a new and clean filesystem than if you muck about with creating degraded arrays.

---

