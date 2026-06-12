---
title: "Running out of space on /var partition. Please advise"
date: 2011-01-31
forum: Server Platforms
---

### Post by trileru808 on 2011-01-31
Hello. I have a Ubuntu 8.10 perfect server and I made a stupid decision at install. I selected only 160 gb for /var partition and now it's 99% full. I added another mail domain and they came with alot of emails from the old server. How can I manage this? I got /home partition that's double in size and it's almos empty. Can I create a shortcut for the whole domain and move it to /home? Right now it resides in /var/www/www.xxx.com. I would like to make this move without affecting the files properties nor users passwords. Most perfect would be to remake the whole system on a single / partition. I have configured a soft raid thou using 2 hard-disks in mirror. So I prefer to get a new hard-disk, format it for a single / partition and swap and move the whole system on that. Would it be too complicated? Or make a new Perfect Ubuntu 10.04 LTS server with ispconfig 2 and move the whole domains with the users passwords and emails and websites? Any help will be greatly appreciated because I'm on a tight squeeze and have to make a decision pretty fast. Thank you all.

---

### Post by SeijiSensei on 2011-01-31
I'd start by looking in /var/log and seeing what you can trim there.  Do you have log rotations set up in /etc/logrotate.d/?

You can get a quick overview of the storage demands of each subdirectory of /var by running "cd /var; du -s *" at the prompt.

160 GB is a *lot* of space for /var.  I suspect there's a lot of cruft in there that you can clean out before resorting to other tricks.

If you're supporting users' websites, I'd keep them in each person's home directory, not under /var/www.  You just have to be careful with permissions so the www-data user can read the files in /home/me/mywebsite.

---

### Post by drs305 on 2011-01-31
/var/log is a good place to look, as stated by *SeijiSensei*. Recently I experienced a huge /var/lib/mlocate/mlocate.db file caused by it looking at every partition I had mounted at the time updatedb ran.

I bring up my experience only to illustrate the point that you could have one or more huge files that shouldn't be there. I created a thread on finding large files and other reasons disk space was 'lost' and provided some methods to troubleshoot the problem:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Backups to the wrong partition are also a common problem, although I don't think they would end up in the /var folder.

---

### Post by trileru808 on 2011-01-31
well I have multiple domains of wich only 2 have active mail users. The one that I had before the last addition has something like 50 mailusers totaling a 127gb mailspace occupied. The last domain that I migrated to my server brought about 10 very active users that tried to upload their old emails and that's when I ran out of space. So the logs and everything are not that big, it is the actual size of each users Inbox that's taking alot of space. I have more than 10 that are past 10gb in size. And that's only in the last 2 years. Is there a "common sense" mailbox size limit that I should apply? I do have another 300gb free in /home so I could use those. The users don't have webpages, but the domains those users are in have, not large, but they reside in /var/www/www.example.com and the users are in /var/www/www.example.com/users 
So my best ideea was to move [www.example.com](www.example.com) on /home with a simplink in /var/www pointing to /home partition but I don't know if this is a good practice among linux servers from a security point of view, as well of functionality.

---

### Post by trileru808 on 2011-01-31
I will as well cut the logs a bit, but there are less than 2gb in /var/log . And 2gb won't help since I ran out of space and the new domain users didn't even add their full list of emails in the inbox. They prefer this way since they can look up via IMAP an email from everywhere.

---

### Post by trileru808 on 2011-01-31
I think I'll go with the resize partition option. any help on what tool to use? If I remember correctly I installed this system with software raid. So I plan on cutting about 200gb from /home and adding them to /var.

---

### Post by SeijiSensei on 2011-01-31
You might want to consider using quotas.  Those mailboxes are ridiculously large.  At some client sites, we use scripts I wrote to automatically rotate messages out of the inbox after a period of time. 

What are you doing to filter spam?  How many of those gigabytes of mail are real messages and how much is junk?  Do you send the junk to a separate mailbox under /home/user?

I hope you're charging a lot for this service.  Given that 1-2 GB is the common maximum size for free email at places like Google, anything much larger than this should cost money.  Anyone with inboxes in the 10+ GB range should be paying serious money.

---

### Post by trileru808 on 2011-02-01
I am hired at this company so they do pay me, but as I said, they want all their email available at all times from imap. I tried to reason with them but no luck :) Romania is the worst kind to negotiate anything...
Most of the email from the larger mailboxes are good emails, with attachments, maybe that's the reason. We are in media bussiness so we need alot of small clips transfered via email. So I decided to extend that partition, I would like some help in that direction. Shall I remove on hard disk from raid, resize the partition on the remaining one than rebuild the raid? And if this is the case, what tool is best advised for that? Shall I boot a live CD and use a graphical tool?

p.s. the raid is software and I'm using spamassasin. I do not use any rotation rules nor any redirect of spam, just discard or rename depending on the importance of the mailbox, the most important ones cannot afford to miss any email so I just rename the spam. But that's not the determining factor in mailbox size...it's the actual emails.

---

### Post by SeijiSensei on 2011-02-01
Under the circumstances, I'd buy another drive, say 1-2 TB, and mount that as /var.  Sounds to me like you're just going to run up against this problem again in the future if you just repartition the drive you have now.

---

### Post by trileru808 on 2011-02-01
For that I have to break the raid. Currently I have only 2 HDD bays. It's 1U rack mountable Dell R300 server. No external sata connections or anything. Maybe USB :))

---

### Post by psusi on 2011-02-01
You need to rebuild the server.  Not just because of the /var issue, but also because you are running 8.10, which has been discontinued for almost a year.  Even 9.04 has been discontinued for a few months so you can't even upgrade.  Without updates your system almost certainly now has a number of security vulnerabilities.

You should install 10.04, which is an LTS release and so will be supported on server for 5 years.

---

### Post by trileru808 on 2011-02-01
If I can migrate the users with their emails and passwords, webpages and settings for ispconfig2 that would be perfect. I would very much appreciate any info on this matter

---

### Post by psusi on 2011-02-01
User web pages should be in their home directories which you can just restore from backup.  You can also restore /etc/passwd and /etc/shadow and get all of the accounts back.

Depending on how your mail server is configured, their mail will either be in their home directories or in /var/spool/mail.  Since you said var is full, that is probably where they are and why it is full.  You might want to migrate that to their home directories instead.

---

