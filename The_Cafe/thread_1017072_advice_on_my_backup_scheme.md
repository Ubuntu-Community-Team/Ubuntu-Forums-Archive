---
title: "advice on my backup scheme"
date: 2008-12-20
forum: The Cafe
---

### Post by il-luzhin on 2008-12-20
It's that time of year for me, PC cleanup.  I know, I know, 8.10 came up months ago but I've skipped the upgrade this time around but I'll ge tto it soon enough so I'm a little more cluttered than my usual six month cycle allows for.  So here's my philosophy.  I was wondering if anyone had suggestions on how to better use my resources.  

Laptop: 
20 GB Vista - 15 GB Ubuntu 7.10 - 80 GB Data
I manually back up the Data partition to my Desktop's home partition about once a week.  Full copies of any changed data.

Desktop:
20 GB mythbuntu 8.04 / - 140 GB mythbuntu 8.04 /var - 500GB mythbuntu 8.04 /home - 250 GB external USB-HDD
I backup all keeper Data to the USB-HDD, full backup is its only job.  I figure if I'm copying more than half my home partition I've got issues so I don't worry about size.  Any important stuff gets burned to disc or to a 4 GB flash drive.  I use rsync to keep rolling backups and send those to my slave.  

Slave: 5 GB Ubuntu 8.04 server / - 35 GB Ubuntu 8.04 server /home
This headless pc does all sorts of stuff but most importantly it stores the rsync files off my Desktop via a cron job.

That's basically it.  Any suggestions?

---

