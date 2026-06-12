---
title: "Backing up a mail server"
date: 2008-08-01
forum: Server Platforms
---

### Post by w1z4rd on 2008-08-01
If you have several hundred mail users on a dedicated mail server, whats the best way to back those users email up?

The server would be be an IMAP server which is why it would need daily backups. 

I am looking for something cost effective.. perhaps a tape drive or something like that? This is also a business corporate environment so I expect there to be a lot of mail with a lot of attachments.

Thanks in advance!

---

### Post by windependence on 2008-08-01
Well, if it's mission critical, then yes you have to take it off site and keep it safe from disasters. Otherwise, I usually just put another disk in my office servers and mount it as /backup. Then I run a cron job to backup the items I need each night using rsync. If you need mail archived, then you should use a script with some kind of archiving and rotation of the backups.

-Tim

---

### Post by dca on 2008-08-01
If it's something as critical as a mail server like that then there should be two servers working at the same time in case one fails.  Fail over in other words.  Even if the server is RAIDed properly it still takes time to replace a single HDD and rebuild the RAID again.
 
Once that is taken care of then comes disaster recovery, back-ups, etc.
 
If it's just an MTA for POP3 accounts then you can get by w/ simple rsynch and scripts...

---

### Post by windependence on 2008-08-01
I agree. In his situation I would have two servers, load balancers, UPSs and a good firewall(s) since he mentioned several hundred users. Nothing like several hundred pi$$ed off people mad at you. ;)

-Tim

---

### Post by StickyStyle on 2008-08-01
> **w1z4rd said:**
> If you have several hundred mail users on a dedicated mail server, whats the best way to back those users email up?

The server would be be an IMAP server which is why it would need daily backups. 

I am looking for something cost effective.. perhaps a tape drive or something like that? This is also a business corporate environment so I expect there to be a lot of mail with a lot of attachments.

Thanks in advance!

What IMAP server are you using, and what is the mailbox format (mbox, maildir, Cyrus, etc...)?

For me I use dovcot with Maildir and have the following backup scheme...
Every 2 hours I do a backup with rsnapshot, which then rolls over to 4 daily snapshots.  This is for all those "can you recover a single email I deleted a hour ago" situations where recovering from tape would be a pain in the a$$ (or the email is not yet on tape).  I just do mutt -f /var/snapshot/user1/hourly.2/maildir on the server and bounce the mail back to the user.

Then I backup the maildir's nightly onto tape (Exabyte Packetloader 320 1Ux10) with my other backup jobs.  These autoloaders are pretty nice since VXA tapes are cheap, you dont have to babysit them everyday, was only like $2K.

---

### Post by Chayak on 2008-08-02
Backups are a must but nothing beats a second server constntly synced set for failover or better yet load balanced.

For backups on big cost very critical items nothing beats having something like a netapp on hand though your looking at a huge investment there but for 5x9s a set of them are hard to beat.

One of the more cost effective backups I've seen lately is using a Drobo.  It's simple, effective, and we put a test unit through hell and it still kept chugging along.  You just slide some sata drives in it and use it like a normal usb2 or firewire 800 drive.  It has linux support and is fairly quiet while it protects against individual drive failures and data loss.

I recently used two of them loaded with four 1TB drives each connected to a droboshare unit (which if you load the developer firmware into you get unix shell access to it.) to use instead of shelling out $30k for a 6TB netapp that was only going to be used for NAS.  The cost to do it was around $3K, roughly 10% of the netapp cost.  Great little units. [http://www.drobo.com]("http://www.drobo.com")

---

