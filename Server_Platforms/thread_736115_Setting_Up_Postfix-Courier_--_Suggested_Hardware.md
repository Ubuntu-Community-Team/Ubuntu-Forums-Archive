---
title: "Setting Up Postfix-Courier -- Suggested Hardware"
date: 2008-03-26
forum: Server Platforms
---

### Post by ryth on 2008-03-26
Hi folks,

I'm interested in setting up a **cost-affordable** and reliable mail server for a small-sized charity I work for.  Ideally it would run RAID5.

I'm curious as to whether anyone would have hardware suggestions? I'd like to run something that is as well supported and stable as possible without breaking the bank.  

Also with ~20 seats, what would the minimum RAM + processor ideally be?

Any comments or suggestions appreciated.

Cheers.

R

---

### Post by craigp84 on 2008-03-26
Hi Ryth,

I'm not sure why you would specify RAID5 as a requirement? Would it not make sense to drop the RAID requirement to better align with your goal of cost effectiveness?

RAID5 is a tool to help improve service availability - that is to say you should have less down time due to broken disks. It doesn't do anything else (especially it is not a form of backup). It also has trade offs in that it will increase the cost of the server, and reduce its performance (ever so slightly).

I would seriously consider ditching the RAID5 requirement, especially given it's only for 20 seats.

As for support, i think any of the big names have reasonable support services these days. Pay the extra for the sameday hardware replacement if you think it's necessary. Mail will typically queue up and retry for up to 72 hours on the senders side, so you can potentially afford a couple of hours downtime without losing mail.

For < 300 seats, absolutely any brand new server you can buy today will have enough CPU and at least 512Mb of ram which is absolutely tons for < 300 seats.

As a real life example, i run the following at one site -

 * Inbound / Outbound Mail for ~600 users
 * Intensive spam filtering on all inbound mail
 * Mandatory virus scanning via 2 x separate v/scan engines (CPU intensive, especially when it has to unzip attachements to scan them)

And all this runs very comfortably on a single 1.5GHz Xeon with 1Gb ram and old slower scsi disks. This server also runs a ton of reports on the mail / spam / virus volumes flowing through it, including rendering graphs (CPU intensive operation).

The bottom line: Buy onsite, sameday parts replacement (it's a production server!); don't worry about CPU speed, it really doesn't matter for this number of users; Buy as much ram as you can justify the cash for -- linux will use it wisely.

Hope this helps,

-c

---

### Post by StarMonkee on 2008-03-26
I'd suggest going for RAID - it might up the cost a little bit, but rather than worrying about downtime if a disk dies, I tend to worry more about backups. If a drive dies, you can just replace it and carry on from where you left off. Without RAID you'll be stuck at wherever your last backup was. Plus you could save money this way by not having an external backup solution.

Plus the headache of reinstalling the OS and all the mail services, then re-importing all the users mail is something you don't need to worry about.

Hardware wise, as craigp84 said, you don't need a high powered machine for that many users. I've ran a mail server for around 70 users in the past on an old p2 450 with 512mb ram without any problems.

If you're looking for the cheapest solution, then any old desktop machine should serve the purpose fine. Obviously with faster hardware you'll get better performance, but for a small number of users you probably wouldn't notice much difference. If you want to upgrade, then I'd agree that RAM is the wisest choice.

My current mail server is a fairly old dual core 1.4ghz with 2gb RAM (with RAID5). I've had a drive go in it, but with the hot swappable raid card, the uptime is over 810 days now :D

---

