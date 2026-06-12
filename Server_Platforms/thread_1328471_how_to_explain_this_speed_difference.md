---
title: "how to explain this speed difference"
date: 2009-11-16
forum: Server Platforms
---

### Post by shreko on 2009-11-16
Server is 9.10 64 bit ubuntu server. I just got a new SLC SSD and wanted to test it with 1M records mysql dump file. So I logged via putty from a windows machine and query took around 8 minutes. I was about to claim a victory for SLC SSD, but later tried to do it once again logged localy on the server machine. This time took 32 minutes which is 4x
Is there any explanation for this?

---

### Post by dca on 2009-11-16
Got me on that one, I could understand similar tests running and comparing differences between say ext3 & ext4 filesystems or different kernels (possible regressions) but from moving from remote accessing system & directly accessing system & having that?  Was there anything else added (daemon/service) added in the middle?

---

### Post by shreko on 2009-11-16
Everything is the same, same way to login to mysql, same db.sql file from the same location /home/me/db.sql

---

### Post by dca on 2009-11-16
Nah, got nothing...  Both commands used were identical?  No other options, tables, etc, etc added to either?  Strange...

---

### Post by dca on 2009-11-16
Someone else experiencing speed issues w/ MySQL:
 
[http://ubuntuforums.org/showthread.php?t=1313834](http://ubuntuforums.org/showthread.php?t=1313834)
 
...trouble with ext4....

---

### Post by shreko on 2009-11-16
I just did a quick test on a little acer one netbook running 9.10 netbook remix. The netbook is acting as a mysql server in this test. I used same sql file just stopped the execution after 3 minutes. So if i log remotely I was able to insert first 200k records and if I log locally only 120k records. Still slower but not as bad as in the server. The netbook is also ext4
???

---

### Post by dca on 2009-11-16
Does the Acer have SSD card?

---

### Post by shreko on 2009-11-16
Yes, acer is 8Gb SSD, MLC I guess

---

### Post by dca on 2009-11-16
Perhaps that explains the 'not as bad' as the server speeds...

---

### Post by dca on 2009-11-16
I know you're not made of time, perhaps installing Ubuntu 8.04LTS 64bit using ext3 and see what times that comes up with.
 
It'll eliminate the ext4 (which I thought was supposed to be optimized for SSD) as a culprit and also remove the possibilities of 2.6.31 regressions...

---

### Post by shreko on 2009-11-16
I'll find some time to that. It may take me a day or two to report back
Thanks for your help

---

### Post by HermanAB on 2009-11-16
Note that the SSD controller will from time to time move blocks around, during which time the device may become unresponsive or slow.  this may be what you are running into.

---

### Post by shreko on 2009-11-16
It was very quick to install 8.04LTS 64 bit server from scratch.
Here are my results. Same 1M mysql dump file.

logged remotely via putty: 8 minutes and 38 seconds

then i did full machine shutdown and after I logged back in
run the same command locally: 10 minutes and 25 seconds

So, there is a still difference of 20% in speed between the two

---

### Post by shreko on 2009-11-16
Maybe this is the reason. I was suspecting the way mysql interacts with console running in default mode sending back to screen result, so I run mysql with --silent option and run locally it now took exactly 8 minutes to finish

---

### Post by insane_alien on 2009-11-16
perhaps the data was cached the first time round?

---

