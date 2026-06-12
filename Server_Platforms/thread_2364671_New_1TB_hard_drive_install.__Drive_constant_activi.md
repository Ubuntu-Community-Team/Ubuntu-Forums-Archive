---
title: "New 1TB hard drive install.  Drive constant activity."
date: 2017-06-26
forum: Server Platforms
---

### Post by Michael_McKenney on 2017-06-26
I put in a brand new 1TB SATA drive.  I reinstalled 16.04 LTS clean.   Copied the web sites back in.  The drive is constantly active.  How can I find why and how to stop it.   It is noisy.   I want the hard drive activity for the web site.  I can't believe much activity is from the web site.  I read articles on various sites about constant disk activity.   Many different things to try.   I will backup everything first.

---

### Post by TheFu on 2017-06-27
I would use **lsof** to see which process(es) are using any files under that specific mount point.
But there are all sorts of reasons that a disk might be in use - updatedb, AV scanning (if you have that), search indexing (if you have that), or SMART testing (if you have that).  The type of "web site" is pretty vague.  Any chance that you've asked the web server to micro-cache stuff or compress it to be more efficient?  You should, BTW.

---

### Post by Michael_McKenney on 2017-06-28
Installed clean copy of Ubuntu 16.04 with /, /var, and /swap.   Installed Apache2 web server.  Copied my 4 web sites back into virtual servers.   Did not enable anything else.   I did upgrade the RAM to 6GB from 2GB.  I can run lsof tonight.   Anything else to look for.   The disk noise is loud and constant.

---

### Post by TheFu on 2017-06-28
I would assume a noisy disk was about to fail.  Check the SMART data. Check for firmware updates from the disk vendor, and if it is still withing 30 days of purchase - RETURN IT, ASAP!

There is small group of HDDs that are bad initially. If it doesn't feel right, take it back ASAP. It won't get any better over time.  Noisy HDDs aren't normal.   And if you can, get a refund and get a different vendor's HDD to avoid the issue of a bad batch of HDDs.

---

### Post by Michael_McKenney on 2017-06-28
Brand new hard drive.  Weeks old.   The old ATA drive did the same thing.   Constant spinning.   It was slower and quieter but still chirped.   The new SATA drive is much faster.   It has a 5 year warranty.   Someone posted a possible kernel bug causing it.   I was thinking of upgrading the kernel.   I think it is 4.4.0.79.

---

### Post by Michael_McKenney on 2017-06-28
fstab commit to 60 was one fix.   Another one said to upgrade the kernel and see if that fixes it.   I have another box running my Cisco VIRL on lbuntu 14.04.   It has the same issue the drives just constantly spin.   I was wondering if it is SMART checking, web indexing, journaling, or kernel issue.

---

### Post by TheFu on 2017-06-28
Could be anything. If it was data only that wasn't used by any services, then it would spin down and only come up when you specifically asked for it or when the daily updatedb job runs.  With websites on it, there are constant webcrawlers hitting them.  As much as google hits my sites, the other foreign-langauges crawlers hit them 10x more. I ended up blocking the Russian and Chinese crawler subnets worldwide since they never, ever, sent any traffic to me. They were just sucking GBs of bandwidth a month for zero return.

I assume you have analytics about who is hitting your websites and when that happens. It is all in the log files.

Some lsof examples: [https://www.tecmint.com/10-lsof-command-examples-in-linux/](https://www.tecmint.com/10-lsof-command-examples-in-linux/)
Lots more are possible. I usually use grep/egrep to find what I want. Check the manpage for more details.

---

### Post by Michael_McKenney on 2017-06-28
You have a point there.   My brother's company web site is on it.  I have Google crawling it.   How can I block foreign crawlers?   I really just want Google, Yahoo, Bing hitting it.  My three web sites have robot.txt files.

---

### Post by Michael_McKenney on 2017-06-28
[http://www.scsiraidguru.com/lsof.txt](http://www.scsiraidguru.com/lsof.txt)

---

### Post by Michael_McKenney on 2017-06-30
I posted the lsof.   I set the robots.txt file up.   Still getting constant disk activity.  How can I check if Apache 2 is journaling or indexing?

---

### Post by TheFu on 2017-06-30
> **Michael_McKenney said:**
> I posted the lsof.   I set the robots.txt file up.   Still getting constant disk activity.  How can I check if Apache 2 is journaling or indexing?

And what did you find after looking at the lsof output **when** the drive is being accessed?

BTW, I wouldn't look at my own lsof dump without being paid.  Did you read the prior posts and follow the links?

---

### Post by Michael_McKenney on 2017-06-30
When I looked at the lsof, it had more stuff listed than my Windows 7 workstation processes running and it has 100s of apps installed.     I read your posts and started with capturing the lsof.  Considering its an $80 hard drive and I backup my web site several times a week.    Hard drive dies, it is about 2 hours to install Ubuntu and 4 hours to copy the web sites back.   I was going to spend some more time on it this long weekend but it is not worth messing with it. 

I installed VMware 6.0 stand alone on my HP DL380e Gen8 for new Cisco Virtual Lab OVA file.   I used the HP VMware 6.0 ISO image.  It is optimized for my hardware.  It installed on a 8GB SDHC card on the motherboard.  It see all my hardware with no limitations except for a minimum of 8 vCPUs per VM.   I have 12 cores.  8 for Cisco Virtual Lab and 4 for other VMs.   Cisco VIRL uses Lubuntu 16.04.   I found an article on installing Ubuntu 16.04 with VMTools in VMware 6.0.   I will try it this weekend.   This server is quiet compared to my web server.  I will see if it does the same thing with drive activity.   The HP DL380e Gen8 has P222 cached SAS controller with 7200 RPM 1TB SAS drives.  I can add two SAS drives to it.   64GB of RAM that can expand to 384GB.  I have 6 NICs in it.  Cisco VIRL needs 4 dedicated NICs for processes.

---

