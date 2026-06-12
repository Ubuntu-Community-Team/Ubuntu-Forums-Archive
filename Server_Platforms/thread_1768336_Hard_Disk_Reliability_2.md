---
title: "Hard Disk Reliability 2"
date: 2011-05-26
forum: Server Platforms
---

### Post by Vegan on 2011-05-26
This week my Windows box died when the 500 GB disk in it decided that was it.

I have triple redundant copies of important data so its not a problem.

[http://www.windows-it.tk/wp/disk-reliability.html]("http://www.windows-it.tk/wp/disk-reliability.html")

Seem that both of mt 500 GB disks have now failed. Other older disks are still working fine with seemingly invincible stamina.

Makes me wonder if hard disks makers are cutting reliability in order to cut costs?

These days I virtualize everthing. I was able to get Ubuntu to install in Hyper-V finally with a working system.

This year I am now looking to have to replace 2 disks

---

### Post by arrrghhh on 2011-05-26
You seem to be buying from cheapo lines tho...

Caviar Blue from WD for example - those are only warrantied for 3 years, which seems like you got the exact life out of them.

Caviar Black's AFAIK all have a 5-year warranty.  Any new disk I buy, I make sure has this warranty.  Not sure if they build them better and hence the longer warranty, or if it's just to make me feel better... but it does make me feel better :p.

Also, since I've migrated away from Windows entirely I haven't had any disks fail.  Not that Windows is the cause of all disk failures, but I know for a fact it has been the culprit in some premature disk failures.  NTFS is an atrocity.

---

### Post by dtfinch on 2011-05-26
I think 5 years ago we had 14 drives in 7 servers, just over half ide the rest scsi. Now we're up to about 25 in 9 servers, about 2/3 sata and the rest sas. In the 9 years I've been at my current job we've had 2 server hard drives (250gb maxtor ide) fail, both in the same month, in the same server, replaced by Dell under warranty.

The drives that failed had 4 platters, so I've been avoiding drives with more than 2. I also suspected heat issues, so I lean towards lower power drives. And I look at newegg reviews to get a sense of unreliability, adding up the % of 1 and 2 star reviews, and ignoring any drives that are too new or underreviewed.

Our newest servers have better airflow than our others which has me worrying that some of our drives might be running too cold, often reporting 17-20° C, which in Google's [drive reliability survey](http://labs.google.com/papers/disk_failures.pdf) is where you see a sharp increase in failures on the cold end.

I haven't noticed any consistently better manufacturer. It seems to vary between generations. 4 years ago I liked Seagate Barracuda drives. Now I lean toward Samsung Spinpoint drives, though I don't trust any drives over 1TB yet.

---

### Post by tgalati4 on 2011-05-26
Consumer drives are generally crap.  I put enterprise/server class drives in my home machines.

---

### Post by Vegan on 2011-06-21
I am using 2 plate drives simply as I have found more plates tend to be increasingly dodgy.

I was able to get RMA on one DOA disk and Seagate gave me a bigger disk from the next gen as the 7200.11 series had some issues. The new disk is the 7200.12 series, now in the middle between the XP and LP series.


This disk is brand new so I am hoping it lasts more than 20,000 hours. Right now my oldest disk has racked up over 43,000 hours and it still works.

My chart on the page is updated regularly. I check the disks all the time now hoping to catch a problem before it blows up.

I have had some problems with Linux on older machines but that was software not hardware.

Today I only trust it in a VM.

[http://www.windows-it.tk/wp/disk-reliability.html](http://www.windows-it.tk/wp/disk-reliability.html)

Updated several times in the last 2 weeks

---

### Post by kevinthecomputerguy on 2011-06-22
The WD Black is an excellent suggestion above, designed to not fail. But I know Vegan, so I know he doesn&#8217;t need the &#8220;always expect it to fail&#8221; spiel.
 
I must say, I have had so many vendors pale in comparison to western digital, but had many wd blue and green drives fail. The answer does seem to be wd black. I came into an un-expected donation and could afford to swap out everything to black, and haven&#8217;t seen over 100 black drives have a single problem.
-kev

---

### Post by Vegan on 2011-08-11
The majority of my disks are Seagate simply due to the region where I am at in a smaller locale.

I added to more disks to the pile. With my new server I have space for 4 disks easy so why not stuff the machine with them.

Power management means they tend to snooze when not in use.

I am using my server to hold 1 copy of my backups, the portable has the other copy.

I had 1 Seagate and 1 WD disk die but with the limited number of disks I have in the shop the table will have to suffer.

---

### Post by Gyokuro on 2011-08-12
Hi,

you can check Seagate Constellation ES drives, Cheetah NS 10K and Cheetah 15K drives which are designed for enterprise environments ( [http://www.seagate.com/www/en-us/products/enterprise](http://www.seagate.com/www/en-us/products/enterprise)). We use Samsung Spinpoint F3's and currently testing the successor Spinpoint F4 and they are working fine.

---

### Post by Vegan on 2011-08-19
I generally buy cheaper disks due to limited funds. Instead I go for several cheap disks and use redundancy as a way to guard valued files.

---

