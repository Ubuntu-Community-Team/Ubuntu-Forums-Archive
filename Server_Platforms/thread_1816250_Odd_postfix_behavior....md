---
title: "Odd postfix behavior..."
date: 2011-08-01
forum: Server Platforms
---

### Post by usszulu on 2011-08-01
Hello all,

I am having some odd log entries in my mail.log file. For some reason the www-data user is sending mail to itself (or at least trying to). I have no idea why this is happening and more over no idea how to stop it...here is the part of the log showing whats going on...

 [FONT=&quot]Aug  1 14:50:03 xxxxx postfix/pickup[3255]: 567211C80472: uid=33 from=<www-data>
Aug  1 14:50:03 xxxxx postfix/cleanup[3471]: 567211C80472: message-id=<20110801185003.567211C80472@xxxxx.net>
Aug  1 14:50:03 xxxxx postfix/qmgr[1380]: 567211C80472: from=<www-data@xxxxx.net>, size=1563, nrcpt=1 (queue active)
Aug  1 14:50:03 xxxxx postfix/local[3473]: warning: maildir access problem for UID/GID=33/33: create maildir file /var/www/Maildir/tmp/1312224603.P3473.xxxxx: Permission denied
Aug  1 14:50:03 xxxxx postfix/local[3473]: warning: perhaps you need to create the maildirs in advance
Aug  1 14:50:03 xxxxx postfix/local[3473]: 567211C80472: to=<www-data@xxxxx.net>, orig_to=<www-data>, relay=local, delay=0.67, delays=0.43/0/0/0.23, dsn=5.2.0, status=bounced (maildir delivery failed: create maildir file /var/www/Maildir/tmp/1312224603.P3473.xxxxx: Permission denied)
Aug  1 14:50:03 xxxxx postfix/cleanup[3471]: DF1BF1C80473: message-id=<20110801185003.DF1BF1C80473@xxxxx.net>
Aug  1 14:50:03 xxxxx postfix/qmgr[1380]: DF1BF1C80473: from=<>, size=3529, nrcpt=1 (queue active)
Aug  1 14:50:03 xxxxx postfix/bounce[3474]: 567211C80472: sender non-delivery notification: DF1BF1C80473
Aug  1 14:50:03 xxxxx postfix/qmgr[1380]: 567211C80472: removed
Aug  1 14:50:03 xxxxx postfix/local[3473]: warning: maildir access problem for UID/GID=33/33: create maildir file /var/www/Maildir/tmp/1312224603.P3473.xxxxx : Permission denied
Aug  1 14:50:03 xxxxx postfix/local[3473]: warning: perhaps you need to create the maildirs in advance
Aug  1 14:50:04 xxxxx postfix/local[3473]: DF1BF1C80473: to=<www-data@xxxxx.net>, relay=local, delay=0.12, delays=0.05/0/0/0.07, dsn=5.2.0, status=bounced (maildir delivery failed: create maildir file /var/www/Maildir/tmp/1312224603.P3473.xxxxx: Permission denied)
Aug  1 14:50:04 xxxxx postfix/qmgr[1380]: DF1BF1C80473: removed[/FONT]


[FONT=&quot]I am sure this is some daemon sending mail, but I really don't need it to. Any assistance you can provide is greatly appreciated. Thank you! =)
[/FONT]

---

### Post by usszulu on 2011-08-03
Bump...please help. I have no idea how to correct this. =(

---

### Post by rudelgurke on 2011-08-03
First - the "www-data" user isn't sending mail to itself. It tries to send mail to someone external, this message bounces and Postfix tries to deliver the bounce to "www-data".
Maybe some PHP script trying to send mails someone abuses ?

And - check your Postfix aliases and add, if not already present, a line like:

www-data root

Then "root" gets the bounce messages which should be a valid mailbox.

---

### Post by WhiteHorse on 2011-08-04
perhaps you need to create the maildirs in advance

---

