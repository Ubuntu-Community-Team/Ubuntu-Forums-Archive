---
title: "Re: Server Advice Needed"
date: 2009-09-20
forum: Server Platforms
---

### Post by Rivernet1 on 2009-09-20
By no means do I want to hijack a thread, but since my questions relate to the topic at hand, might I ask the following questions:

I am moving away from Windows to 9.04 Server/CLI only, using Webmin. I want to "force" myself to use the CLI and Webmin, when I really have to. Back in the DOS days, I would use a command window and I agree, it's much more efficient.

Q1: I have my webserver running on Windows XP/SP3. I already FTP'd all the webpages to the Ubuntu box, and was wondering if I can just copy the MySQL/data folder to the mysql folder on the Ubuntu box w/o a serious problem. I tried to figure out a way to restore it via Webmin, but I don't see a 'restore' option.

Q2: How do you mirror a drive (I guess in a RAID 0 fashion), and would this be the best way, say hd0 went belly up, can I just swap the data cables and hd1 becomes hd0 in seconds?

[COLOR=Silver]Q3: I installed ircd_ratbox and its mysql services package. That's fine and dandy, but how do I start it up?[/COLOR] *[COLOR=Black]Found the answer.[/COLOR]*

Much thanks in advance. Am looking forward to break the chain MSFT has on me and enjoy Open Source-Land. :)

[-o<

---

### Post by Sef on 2009-09-22
Moved to its own post.

---

### Post by Rivernet1 on 2009-09-22
Thank you Sef.

Anyone with some help on my questions, please? Much thanks!
I used the man for Q3. I already have my answer. :)

---

### Post by i.r.id10t on 2009-09-22
For your SQL stuff, use phpmyadmin to export it and then import it.

You don't want RAID-0 - the 0 indicates how much data you'll have if a drive dies. You want raid-1 (mirror 1:1) or raid-5 (3+ drives, w/ parity check)

---

### Post by openfly on 2009-09-22
There's a command called mysqldump that's used to dump mysql databases into a .sql file that you can port around and load up just fine.  Also great for backing up your database.

Just be careful with it as it contains passwords in cleartext.

There's also a linux filesystem called i think drbd that's basically a file system designed for synching two high availability linux systems databases.  You can deactivate a file system on one machine then activate it on another without any real data loss with it.  But replication is probably better in most situations.

Will this just be a basic LAMP ( linux apache mysql php ) environment?  I think it's a right of passage for any aspiring unix/linux admin to go full unix/linux.  It's like learning a language... total immersion works.  Dunno if I'd bank my job on it though.

---

### Post by Rivernet1 on 2009-09-22
> **openfly said:**
> There's a command called mysqldump that's used to dump mysql databases into a .sql file that you can port around and load up just fine.  Also great for backing up your database.

Just be careful with it as it contains passwords in cleartext.

There's also a linux filesystem called i think drbd that's basically a file system designed for synching two high availability linux systems databases.  You can deactivate a file system on one machine then activate it on another without any real data loss with it.  But replication is probably better in most situations.

Will this just be a basic LAMP ( linux apache mysql php ) environment?  I think it's a right of passage for any aspiring unix/linux admin to go full unix/linux.  It's like learning a language... total immersion works.  Dunno if I'd bank my job on it though.

Wow, I totally forgot about mysqldump. I'll get right on that. Yes, this is a LAMP server, with a few other things installed, like an ircd as well. Yes, I just wanted to jump in and learn as I go. I agree immersion is the way to go, but only when you know you're good and ready.

Thanks for the assist.

---

### Post by Rivernet1 on 2009-09-22
> **i.r.id10t said:**
> For your SQL stuff, use phpmyadmin to export it and then import it.

You don't want RAID-0 - the 0 indicates how much data you'll have if a drive dies. You want raid-1 (mirror 1:1) or raid-5 (3+ drives, w/ parity check)

Raid 1 - check. Yes, I totally forgot about that command. :)
Thanks.

---

### Post by hessiess on 2009-09-22
For your drive mirroring you could set up a chron job to rsync the drives.

---

### Post by Rivernet1 on 2009-09-26
> **hessiess said:**
> For your drive mirroring you could set up a chron job to rsync the drives.

I will research that as well. Thanks to everyone for their help. :) 

:KS

---

