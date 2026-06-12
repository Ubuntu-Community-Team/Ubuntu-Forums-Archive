---
title: "hourly postfix problem?"
date: 2008-10-06
forum: Server Platforms
---

### Post by nashibuntu on 2008-10-06
I am running postfix, set up with virtual mailbox mapping and dovecot on ubuntu server. I am seeing the following hourly messages in my mail.info log file

```
Oct  6 14:17:01 myserver postfix/local[22117]: 3BE8E15205D: to=<myuser@localhost>, orig_to=<root@localhost>, relay=local, delay=0.11, delays=0.04/0/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 14:17:01 myserver postfix/qmgr[9623]: 3BE8E15205D: removed
Oct  6 15:17:01 myserver postfix/pickup[22119]: 41D80152060: uid=0 from=<root>
Oct  6 15:17:01 myserver postfix/cleanup[22142]: 41D80152060: message-id=<20081006141701.41D80152060@localhost>
Oct  6 15:17:01 myserver postfix/qmgr[9623]: 41D80152060: from=<root@localhost>, size=716, nrcpt=1 (queue active)
Oct  6 15:17:01 myserver clamsmtpd: 10022C: accepted connection from: 127.0.0.1
Oct  6 15:17:01 myserver postfix/smtpd[22146]: connect from localhost[127.0.0.1]
Oct  6 15:17:01 myserver postfix/smtpd[22146]: 57D1115205D: client=localhost[127.0.0.1]
Oct  6 15:17:01 myserver postfix/cleanup[22142]: 57D1115205D: message-id=<20081006141701.41D80152060@localhost>
Oct  6 15:17:01 myserver postfix/qmgr[9623]: 57D1115205D: from=<root@localhost>, size=919, nrcpt=1 (queue active)
Oct  6 15:17:01 myserver clamsmtpd: 10022C: from=root@localhost, to=root@localhost, status=CLEAN
Oct  6 15:17:01 myserver postfix/smtp[22144]: 41D80152060: to=<root@localhost>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.17, delays=0.07/0.01/0.05/0.04, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 57D1115205D)
Oct  6 15:17:01 myserver postfix/qmgr[9623]: 41D80152060: removed
Oct  6 15:17:01 myserver postfix/smtpd[22146]: disconnect from localhost[127.0.0.1]
Oct  6 15:17:01 myserver postfix/local[22149]: 57D1115205D: to=<myuser@localhost>, orig_to=<root@localhost>, relay=local, delay=0.11, delays=0.04/0/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 15:17:01 myserver postfix/qmgr[9623]: 57D1115205D: removed
Oct  6 16:17:01 myserver postfix/pickup[22160]: 58DE3152060: uid=0 from=<root>
Oct  6 16:17:01 myserver postfix/cleanup[22175]: 58DE3152060: message-id=<20081006151701.58DE3152060@localhost>
Oct  6 16:17:01 myserver postfix/qmgr[9623]: 58DE3152060: from=<root@localhost>, size=716, nrcpt=1 (queue active)
Oct  6 16:17:01 myserver clamsmtpd: 10022D: accepted connection from: 127.0.0.1
Oct  6 16:17:01 myserver postfix/smtpd[22179]: connect from localhost[127.0.0.1]
Oct  6 16:17:01 myserver postfix/smtpd[22179]: 6C66415205D: client=localhost[127.0.0.1]
Oct  6 16:17:01 myserver postfix/cleanup[22175]: 6C66415205D: message-id=<20081006151701.58DE3152060@localhost>
Oct  6 16:17:01 myserver postfix/qmgr[9623]: 6C66415205D: from=<root@localhost>, size=919, nrcpt=1 (queue active)
Oct  6 16:17:01 myserver clamsmtpd: 10022D: from=root@localhost, to=root@localhost, status=CLEAN
Oct  6 16:17:01 myserver postfix/smtp[22177]: 58DE3152060: to=<root@localhost>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.16, delays=0.07/0/0.05/0.04, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 6C66415205D)
Oct  6 16:17:01 myserver postfix/qmgr[9623]: 58DE3152060: removed
Oct  6 16:17:01 myserver postfix/smtpd[22179]: disconnect from localhost[127.0.0.1]
Oct  6 16:17:01 myserver postfix/local[22182]: 6C66415205D: to=<myuser@localhost>, orig_to=<root@localhost>, relay=local, delay=0.11, delays=0.04/0/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 16:17:01 myserver postfix/qmgr[9623]: 6C66415205D: removed
Oct  6 17:17:01 myserver postfix/pickup[22160]: 6FE45152060: uid=0 from=<root>
Oct  6 17:17:01 myserver postfix/cleanup[22206]: 6FE45152060: message-id=<20081006161701.6FE45152060@localhost>
Oct  6 17:17:01 myserver postfix/qmgr[9623]: 6FE45152060: from=<root@localhost>, size=716, nrcpt=1 (queue active)
Oct  6 17:17:01 myserver clamsmtpd: 10022E: accepted connection from: 127.0.0.1
Oct  6 17:17:01 myserver postfix/smtpd[22210]: connect from localhost[127.0.0.1]
Oct  6 17:17:01 myserver postfix/smtpd[22210]: 85DD715205D: client=localhost[127.0.0.1]
Oct  6 17:17:01 myserver postfix/cleanup[22206]: 85DD715205D: message-id=<20081006161701.6FE45152060@localhost>
Oct  6 17:17:01 myserver postfix/qmgr[9623]: 85DD715205D: from=<root@localhost>, size=919, nrcpt=1 (queue active)
Oct  6 17:17:01 myserver clamsmtpd: 10022E: from=root@localhost, to=root@localhost, status=CLEAN
Oct  6 17:17:01 myserver postfix/smtp[22208]: 6FE45152060: to=<root@localhost>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.17, delays=0.08/0/0.05/0.04, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 85DD715205D)
Oct  6 17:17:01 myserver postfix/qmgr[9623]: 6FE45152060: removed
Oct  6 17:17:01 myserver postfix/smtpd[22210]: disconnect from localhost[127.0.0.1]
Oct  6 17:17:01 myserver postfix/local[22213]: 85DD715205D: to=<myuser@localhost>, orig_to=<root@localhost>, relay=local, delay=0.1, delays=0.04/0/0/0.06, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 17:17:01 myserver postfix/qmgr[9623]: 85DD715205D: removed
Oct  6 18:17:01 myserver postfix/pickup[22214]: 86EA8152060: uid=0 from=<root>
Oct  6 18:17:01 myserver postfix/cleanup[22238]: 86EA8152060: message-id=<20081006171701.86EA8152060@localhost>
Oct  6 18:17:01 myserver postfix/qmgr[9623]: 86EA8152060: from=<root@localhost>, size=716, nrcpt=1 (queue active)
Oct  6 18:17:01 myserver clamsmtpd: 10022F: accepted connection from: 127.0.0.1
Oct  6 18:17:01 myserver postfix/smtpd[22242]: connect from localhost[127.0.0.1]
Oct  6 18:17:01 myserver postfix/smtpd[22242]: 9CE3915205D: client=localhost[127.0.0.1]
Oct  6 18:17:01 myserver postfix/cleanup[22238]: 9CE3915205D: message-id=<20081006171701.86EA8152060@localhost>
Oct  6 18:17:01 myserver postfix/qmgr[9623]: 9CE3915205D: from=<root@localhost>, size=919, nrcpt=1 (queue active)
Oct  6 18:17:01 myserver clamsmtpd: 10022F: from=root@localhost, to=root@localhost, status=CLEAN
Oct  6 18:17:01 myserver postfix/smtp[22240]: 86EA8152060: to=<root@localhost>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.17, delays=0.07/0.01/0.05/0.04, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 9CE3915205D)
Oct  6 18:17:01 myserver postfix/smtpd[22242]: disconnect from localhost[127.0.0.1]
Oct  6 18:17:01 myserver postfix/qmgr[9623]: 86EA8152060: removed
Oct  6 18:17:01 myserver postfix/local[22245]: 9CE3915205D: to=<myuser@localhost>, orig_to=<root@localhost>, relay=local, delay=0.11, delays=0.04/0/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 18:17:01 myserver postfix/qmgr[9623]: 9CE3915205D: removed
Oct  6 19:17:01 myserver postfix/pickup[22262]: 9DF0A152060: uid=0 from=<root>
Oct  6 19:17:01 myserver postfix/cleanup[22269]: 9DF0A152060: message-id=<20081006181701.9DF0A152060@localhost>
Oct  6 19:17:01 myserver postfix/qmgr[9623]: 9DF0A152060: from=<root@localhost>, size=716, nrcpt=1 (queue active)
Oct  6 19:17:01 myserver clamsmtpd: 100230: accepted connection from: 127.0.0.1
Oct  6 19:17:01 myserver postfix/smtpd[22273]: connect from localhost[127.0.0.1]
Oct  6 19:17:01 myserver postfix/smtpd[22273]: B3E9C15205D: client=localhost[127.0.0.1]
Oct  6 19:17:01 myserver postfix/cleanup[22269]: B3E9C15205D: message-id=<20081006181701.9DF0A152060@localhost>
Oct  6 19:17:01 myserver postfix/qmgr[9623]: B3E9C15205D: from=<root@localhost>, size=919, nrcpt=1 (queue active)
Oct  6 19:17:01 myserver clamsmtpd: 100230: from=root@localhost, to=root@localhost, status=CLEAN
Oct  6 19:17:01 myserver postfix/smtp[22271]: 9DF0A152060: to=<root@localhost>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.17, delays=0.07/0.01/0.05/0.04, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as B3E9C15205D)
Oct  6 19:17:01 myserver postfix/smtpd[22273]: disconnect from localhost[127.0.0.1]
Oct  6 19:17:01 myserver postfix/qmgr[9623]: 9DF0A152060: removed
Oct  6 19:17:01 myserver postfix/local[22276]: B3E9C15205D: to=<myuser@localhost>, orig_to=<root@localhost>, relay=local, delay=0.12, delays=0.04/0/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 19:17:01 myserver postfix/qmgr[9623]: B3E9C15205D: removed
Oct  6 20:17:01 myserver postfix/pickup[22262]: B4F6D152060: uid=0 from=<root>
Oct  6 20:17:01 myserver postfix/cleanup[22301]: B4F6D152060: message-id=<20081006191701.B4F6D152060@localhost>
Oct  6 20:17:01 myserver postfix/qmgr[9623]: B4F6D152060: from=<root@localhost>, size=716, nrcpt=1 (queue active)
Oct  6 20:17:01 myserver clamsmtpd: 100231: accepted connection from: 127.0.0.1
Oct  6 20:17:01 myserver postfix/smtpd[22305]: connect from localhost[127.0.0.1]
Oct  6 20:17:01 myserver postfix/smtpd[22305]: C39CE15205D: client=localhost[127.0.0.1]
Oct  6 20:17:01 myserver postfix/cleanup[22301]: C39CE15205D: message-id=<20081006191701.B4F6D152060@localhost>
Oct  6 20:17:01 myserver postfix/qmgr[9623]: C39CE15205D: from=<root@localhost>, size=919, nrcpt=1 (queue active)
Oct  6 20:17:01 myserver clamsmtpd: 100231: from=root@localhost, to=root@localhost, status=CLEAN
Oct  6 20:17:01 myserver postfix/smtp[22303]: B4F6D152060: to=<root@localhost>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.14, delays=0.05/0/0.05/0.04, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as C39CE15205D)
Oct  6 20:17:01 myserver postfix/qmgr[9623]: B4F6D152060: removed
Oct  6 20:17:01 myserver postfix/smtpd[22305]: disconnect from localhost[127.0.0.1]
Oct  6 20:17:01 myserver postfix/local[22308]: C39CE15205D: to=<myuser@localhost>, orig_to=<root@localhost>, relay=local, delay=0.11, delays=0.04/0/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 20:17:01 myserver postfix/qmgr[9623]: C39CE15205D: removed
Oct  6 21:17:01 myserver postfix/pickup[22317]: CBFD0152060: uid=0 from=<root>
Oct  6 21:17:01 myserver postfix/cleanup[22342]: CBFD0152060: message-id=<20081006201701.CBFD0152060@localhost>
Oct  6 21:17:01 myserver postfix/qmgr[9623]: CBFD0152060: from=<root@localhost>, size=716, nrcpt=1 (queue active)
Oct  6 21:17:01 myserver clamsmtpd: 100232: accepted connection from: 127.0.0.1
Oct  6 21:17:01 myserver postfix/smtpd[22346]: connect from localhost[127.0.0.1]
Oct  6 21:17:01 myserver postfix/smtpd[22346]: E1F6115205D: client=localhost[127.0.0.1]
Oct  6 21:17:01 myserver postfix/cleanup[22342]: E1F6115205D: message-id=<20081006201701.CBFD0152060@localhost>
Oct  6 21:17:01 myserver postfix/qmgr[9623]: E1F6115205D: from=<root@localhost>, size=919, nrcpt=1 (queue active)
Oct  6 21:17:01 myserver clamsmtpd: 100232: from=root@localhost, to=root@localhost, status=CLEAN
Oct  6 21:17:01 myserver postfix/smtp[22344]: CBFD0152060: to=<root@localhost>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.19, delays=0.07/0/0.06/0.06, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as E1F6115205D)
Oct  6 21:17:01 myserver postfix/qmgr[9623]: CBFD0152060: removed
Oct  6 21:17:01 myserver postfix/smtpd[22346]: disconnect from localhost[127.0.0.1]
Oct  6 21:17:02 myserver postfix/local[22349]: E1F6115205D: to=<myuser@localhost>, orig_to=<root@localhost>, relay=local, delay=0.14, delays=0.06/0/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Oct  6 21:17:02 myserver postfix/qmgr[9623]: E1F6115205D: removed
```

Does anyone know what's going on here? I am not sure how to go about debugging this. Any help gratefully received.

Thank you.

---

### Post by nashibuntu on 2008-10-11
So, just to summarise. It looks like there is an email that keeps getting sent to root, then being removed by the queue manager, then to myuser@localhost, then being removed, regularly. I don't understand why that would be happening. What's sending these emails and why are they removed before I have a chance to read them?

Thank you.

---

### Post by gombadi on 2008-10-11
I would guess that it is some output from a cron job.

```

grep 17 /etc/crontab
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly

```

cron.hourly runs every hour at 17 minutes past the hour.

Have a look at the file and/or as root run /etc/cron.hourly file and see what output it produces. If it produces anything the system will email the output to root.


> 
What's sending these emails and why are they removed before I have a chance to read them?

Oct  6 21:17:02 myserver postfix/local[22349]: E1F6115205D: to=<myuser@localhost>, orig_to=<root@localhost>, relay=local, delay=0.14, delays=0.06/0/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)


At the end of the above line it says that postfix delivered the message to maildir so postfix removed it from the mailqueue. The message still exists on your system somewhere - you will just have to find it.

Have a look in /etc/postfix/main.cf for clues to fine the directory that postfix is storing the messages in. If you need to then you will have to search the file system for the file. You can start looking under the /var directory.

```

find /var -type f -exec grep -l E1F6115205D {} \;

```

It will give you the name of every file it finds with the postfix email reference number in it.

---

### Post by nashibuntu on 2008-10-12
Thank you very much gombadi. I was able to identify the source of the messages, find the emails and fix the problem based on your instructions. I should have thought to check in the hourly cron myself.

I wasn't picking up the emails previously because I set up my postfix to use Maildir format, but the mail command is apparently not looking in the right place any more and so wasn't showing anything. I am not sure how to reconfigure it.

I managed to reconfigure mutt to work however, by adding commands to my muttrc file as described here: [http://www.elho.net/mutt/maildir/](http://www.elho.net/mutt/maildir/) I didn't do any of the other stuff that it suggests about setting up mailboxes and specifying macros... but it appears to work anyway.

Cheers

---

