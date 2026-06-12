---
title: "[SOLVED] mail delivery delayed"
date: 2008-03-16
forum: Server Platforms
---

### Post by yanny on 2008-03-16
Hello people,

First I could send email via mail() function of PHP and the mail was delivered immediately, but now it isn't I dunno what I have done.

When I send email via a php script the email is sent (from the log messages) but it is not delivered immediately I think it took 1 day before it is actually received in the mailbox... seems like it's in the queue..

When I send an email via the terminal as root I received the email immediately... 

What should I do? Shall I use imap_mail function instead of mail() function or ...?

---

### Post by MJN on 2008-03-16
Hi Yanny,

We'd need to see the logs and the full headers of the received e-mail to see where the delays occurred.

Mathew

---

### Post by yanny on 2008-03-16
After I send email via the script, I did tail /var/log/mail.log:

[B]Mar 16 15:02:04 localhost imapd: LOGOUT, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=256, sent=2622, time=0, starttls=1
Mar 16 15:02:59 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar 16 15:02:59 localhost imapd: LOGIN, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 16 15:02:59 localhost postfix/pickup[12153]: 6D43770DB0: uid=33 from=<www-data>
Mar 16 15:02:59 localhost imapd: LOGOUT, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=256, sent=2622, time=0, starttls=1
Mar 16 15:02:59 localhost postfix/cleanup[13172]: 6D43770DB0: message-id=<20080316140259.6D43770DB0@localhost>
Mar 16 15:02:59 localhost postfix/qmgr[7723]: 6D43770DB0: from=<www-data@localhost>, size=389, nrcpt=1 (queue active)
Mar 16 15:03:01 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar 16 15:03:01 localhost imapd: LOGIN, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 16 15:03:01 localhost imapd: LOGOUT, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=256, sent=2622, time=0, starttls=1
[/B]

---

### Post by MJN on 2008-03-16
That doesn't show the message being sent by the SMTP/local daemon so we need to see the rest.

Do you have the headers of the received message?

Incidentally, don't be confused by any IMAP stuff - that has nothing to do with the sending of mail, only accessing and managing received mail. Speaking of which, what is your PHP script doing? If it's just sending mail why do you have all the IMAP accesses at the same time?

Mathew

---

### Post by yanny on 2008-03-16
This is an example of the full header:


[B]Return-Path: <www-data@localhost>
X-Original-To: [email]postmaster@yanling.nl[/email]
Delivered-To: [email]postmaster@yanling.nl[/email]
Received: from localhost (localhost.localdomain [127.0.0.1])
     by localhost (Postfix) with ESMTP id 4320170DA5;
     Sat, 15 Mar 2008 22:17:15 +0100 (CET)
X-Quarantine-ID: <o04TefbhvPHJ>
X-Virus-Scanned: Debian amavisd-new at localhost
X-Amavis-Alert: BAD HEADER Improper use of control character (char 0D hex):
     From: [email]yanling@yanling.nl[/email]\r\n
Received: from localhost ([127.0.0.1])
     by localhost (localhost.localdomain [127.0.0.1]) (amavisd-new, port 10024)
     with ESMTP id o04TefbhvPHJ; Sat, 15 Mar 2008 22:17:12 +0100 (CET)
Received: by localhost (Postfix, from userid 33)
     id 307D670DA4; Sat, 15 Mar 2008 22:17:11 +0100 (CET)
To: "To:sandra"@yanling.nl
Subject: help 1!!
From: [email]yanling@yanling.nl[/email]
Reply-To: [email]yanling@yanling.nl[/email]
Content-Type: text/html; charset=ISO-8859-15
Cc: [email]postmaster@yanling.nl[/email]
Message-Id: <20080315211712.307D670DA4@localhost>
Date: Sat, 15 Mar 2008 22:17:12 +0100 (CET)[/B]

I sent this message on Saturday night the date stated above. But did not received it in my mailbox immediately, it was definitely queued, in this morning I saw the mail was arrived.

---

### Post by MJN on 2008-03-16
And what do the logs say for this message? There should be an entry confirming exactly when it was delivered.

Mathew

---

### Post by yanny on 2008-03-16
I'm not sure but I think it is the messages below, because I found it via the Message-Id: <20080315211712.307D670DA4@localhost>

[B]
Mar 15 22:17:12 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar 15 22:17:12 localhost imapd: LOGIN, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 15 22:17:12 localhost postfix/pickup[13136]: 307D670DA4: uid=33 from=<www-data>
Mar 15 22:17:12 localhost imapd: LOGOUT, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=254, sent=1579, time=0, starttls=1
Mar 15 22:17:12 localhost postfix/cleanup[13167]: 307D670DA4: message-id=<20080315211712.307D670DA4@localhost>
Mar 15 22:17:12 localhost postfix/qmgr[13137]: 307D670DA4: from=<www-data@localhost>, size=395, nrcpt=2 (queue active)
Mar 15 22:17:15 localhost postfix/smtpd[13175]: connect from localhost.localdomain[127.0.0.1]
Mar 15 22:17:15 localhost postfix/smtpd[13175]: 4320170DA5: client=localhost.localdomain[127.0.0.1]
Mar 15 22:17:15 localhost postfix/cleanup[13167]: 4320170DA5: message-id=<20080315211712.307D670DA4@localhost>
Mar 15 22:17:15 localhost postfix/qmgr[13137]: 4320170DA5: from=<www-data@localhost>, size=920, nrcpt=2 (queue active)
Mar 15 22:17:15 localhost postfix/smtpd[13175]: disconnect from localhost.localdomain[127.0.0.1]
Mar 15 22:17:15 localhost amavis[5500]: (05500-07) Passed BAD-HEADER, <www-data@localhost> -> <"To:sandra"@yanling.nl>,<postmaster@yanling.nl>, quarantine: badh-o04TefbhvPHJ, Message-ID: <20080315211712.307D670DA4@localhost>, mail_id: o04TefbhvPHJ, Hits: 3.393, queued_as: 4320170DA5, 3060 ms
Mar 15 22:17:15 localhost postfix/smtp[13170]: 307D670DA4: to=<To:sandra@yanling.nl>, relay=127.0.0.1[127.0.0.1]:10024, delay=3.2, delays=0.11/0/0.02/3, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=05500-07, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 4320170DA5)
Mar 15 22:17:15 localhost postfix/smtp[13170]: 307D670DA4: to=<postmaster@yanling.nl>, relay=127.0.0.1[127.0.0.1]:10024, delay=3.2, delays=0.11/0/0.02/3, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=05500-07, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 4320170DA5)
Mar 15 22:17:15 localhost postfix/qmgr[13137]: 307D670DA4: removed
Mar 15 22:17:15 localhost postfix/virtual[13177]: 4320170DA5: to=<To:sandra@yanling.nl>, relay=virtual, delay=0.13, delays=0.07/0.03/0/0.03, dsn=5.1.1, status=bounced (unknown user: "to:sandra@yanling.nl")
Mar 15 22:17:15 localhost postfix/virtual[13177]: 4320170DA5: to=<postmaster@yanling.nl>, relay=virtual, delay=0.18, delays=0.07/0.03/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Mar 15 22:17:15 localhost postfix/cleanup[13167]: 6F32570DA6: message-id=<20080315211715.6F32570DA6@localhost>
Mar 15 22:17:15 localhost postfix/qmgr[13137]: 6F32570DA6: from=<>, size=2621, nrcpt=1 (queue active)
Mar 15 22:17:15 localhost postfix/bounce[13285]: 4320170DA5: sender non-delivery notification: 6F32570DA6
Mar 15 22:17:15 localhost postfix/qmgr[13137]: 4320170DA5: removed
Mar 15 22:17:15 localhost postfix/local[13286]: warning: database /etc/aliases.db is older than source file /etc/aliases
Mar 15 22:17:15 localhost postfix/local[13286]: 6F32570DA6: to=<www-data@localhost>, relay=local, delay=0.05, delays=0.02/0.02/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 15 22:17:15 localhost postfix/qmgr[13137]: 6F32570DA6: removed
[/B]

---

### Post by MJN on 2008-03-16
There weren't any delays. Stepping through the log for notable entries...

> **yanny said:**
> Mar 15 22:17:12 localhost postfix/pickup[13136]: 307D670DA4: uid=33 from=<www-data>
Mar 15 22:17:12 localhost imapd: LOGOUT, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=254, sent=1579, time=0, starttls=1
Mar 15 22:17:12 localhost postfix/cleanup[13167]: 307D670DA4: message-id=<20080315211712.307D670DA4@localhost>
Mar 15 22:17:12 localhost postfix/qmgr[13137]: 307D670DA4: from=<www-data@localhost>, size=395, nrcpt=2 (queue active)

This is the message being accepted, destined for two recipients, at 22:17:12.

> Mar 15 22:17:15 localhost postfix/smtp[13170]: 307D670DA4: to=<To:sandra@yanling.nl>, relay=127.0.0.1[127.0.0.1]:10024, delay=3.2, delays=0.11/0/0.02/3, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=05500-07, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 4320170DA5)
Mar 15 22:17:15 localhost postfix/smtp[13170]: 307D670DA4: to=<postmaster@yanling.nl>, relay=127.0.0.1[127.0.0.1]:10024, delay=3.2, delays=0.11/0/0.02/3, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=05500-07, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 4320170DA5)Three seconds later this is the two messages going through Amavis, being scanned, and feeding back into Postfix.

> Mar 15 22:17:15 localhost postfix/virtual[13177]: 4320170DA5: to=<To:sandra@yanling.nl>, relay=virtual, delay=0.13, delays=0.07/0.03/0/0.03, dsn=5.1.1, status=bounced (unknown user: "to:sandra@yanling.nl")This is the first recipient being bounced as 'no such user' (your script needs fixing as presumably there is a 'sandra' user but your recipient address was 'to:sandra@yanling.nl' i.e. had an erroneous 'to:' in it).

> Mar 15 22:17:15 localhost postfix/virtual[13177]: 4320170DA5: to=<postmaster@yanling.nl>, relay=virtual, delay=0.18, delays=0.07/0.03/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)This is the message being successfully delivered to 'postmaster'.

Hence, all in all, the message was delivered to the postmaster in three seconds following sending, and a bounce sent for the erroneous 'to:sandra' address.

> Mar 15 22:17:15 localhost postfix/local[13286]: warning: database /etc/aliases.db is older than source file /etc/aliasesThis means you've updated the /etc/aliases text file but not updated the database that Postfix uses with **sudo postmap /etc/aliases**

Mathew

---

### Post by yanny on 2008-03-16
> This is the first recipient being bounced as 'no such user' (your script needs fixing as presumably there is a 'sandra' user but your recipient address was 'to:sandra@yanling.nl' i.e. had an erroneous 'to:' in it).


Yeah that's my script's error I shall fix that first


> This means you've updated the /etc/aliases text file but not updated the database that Postfix uses with sudo postmap /etc/aliases

I'm not sure if Postfix use /etc/aliases as aliases file... :|
When I execute the command "sudo postmap /etc/aliases" it says: 

[B]postmap: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
postmap: warning: /etc/aliases, line 3: record is in "key: value" format; is this an alias file?
postmap: warning: /etc/aliases, line 4: record is in "key: value" format; is this an alias file?
postmap: warning: /etc/aliases, line 8: record is in "key: value" format; is this an alias file?
[/B]

This is my /etc/aliases file looks like: 

```

# Added by installer for initial user
postmaster: root
root: postmaster@yanling.nl
clamav: root
amavis: root

```


Maybe Postfix uses his own aliases file?? I'm not sure though...

When I grep -r "aliases" I get these results (terminal action):

/etc/aliases
/etc/modprobe.d/aliases
/usr/src/postfix-2.4.5/proto/aliases
/usr/src/postfix-2.4.5/conf/aliases
/usr/share/mime/aliases
/usr/share/X11/xkb/keycodes/aliases
/sys/slab/:0001408/aliases
...
...
...

The others are all from /sys/slab/....


I have not tested yet, it's going to be late here.. so I first finished something else from my webmail.

Thanks for your help anyway! =;

---

### Post by yanny on 2008-03-16
By the way I forgot to mention that when I use a new test file and I send email using mail() function that it received immediately (fast enough).

But with my current send email script it is way too slow (I get my email the following day :S) 

Does it mean because of the bounced email which is wrong ('to:sandra@yanling.nl')? So that it delays the other emails as well (e.g. the one cc to [email]postmaster@yanling.nl[/email])? 

If that is true then I think it will works when I fixed the [email]'to:sandra@yanling.nl'[/email] error...

---

### Post by cherva on 2008-03-16
My mail is delayed too... with sendmail I got it instantly ,but with postfix there is 30min delay ... please help :confused:

---

### Post by MJN on 2008-03-16
> **yanny said:**
> Does it mean because of the bounced email which is wrong ('to:sandra@yanling.nl')? So that it delays the other emails as well (e.g. the one cc to [EMAIL="postmaster@yanling.nl"]postmaster@yanling.nl[/EMAIL])?

No - the mail to postmaster was delivered immediately.

Regarding the alias issue, I wrongly suggested postmap (that's the usual text-to-database converter for Postfix), however the alias file uses its own converter - **sudo postalias /etc/aliases**

Mathew

---

### Post by yanny on 2008-03-17
When I execute the command 

**sudo postalias /etc/aliases**

nothing happened, or is it supposed to be like that?

---

### Post by MJN on 2008-03-17
That's fine - you can either run it with the -v flag for some output, or just check the date/time of the resultant /etc/aliases.db file.

Mathew

---

### Post by yanny on 2008-03-17
In /etc/aliases.db is no useful information, what I see is:

[B]^@^@^@^@^A^@^@^@^@^@^@^@a^U^F^@^H^@^@^@^@^P^@^@^@^H^@^@^@^@^@^@^B^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@"Ç
^@^@þ^@^@â©^ÛÐ^H ^@^@^@^@^@^@^A^@^@[/B]

---

### Post by MJN on 2008-03-17
That's because it's in a binary format for Postfix to use. The human-readable version is /etc/aliases.

Mathew

---

### Post by yanny on 2008-03-17
ok :)

I still need to change the to: bug and then test it, yeah I'm slow but I'm actually doing the layout of the website.. but I will let you know when I have done and if the problem is fixed.

---

### Post by yanny on 2008-03-17
Good news, good news!!

It was really the bouncing mail which causes the other mail to be delayed. Because to was wrong, I correct it and it delivered immediately!! :) I should test more and more also with multiple emailaddresses in to, bcc, cc. 

Thanks anyway!!!!!!! :razz:

This topic is solved now.

---

