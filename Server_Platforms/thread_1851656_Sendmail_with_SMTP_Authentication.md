---
title: "Sendmail with SMTP Authentication"
date: 2011-09-28
forum: Server Platforms
---

### Post by malleyme1 on 2011-09-28
Hello all,

I'm new to Ubuntu.  I'm running an HP Proliant DL380 G3 server with Ubuntu Server 11.04.

Some Background: I'm trying to set up my server to send mail from a PHP  script (like mail(args)) through a separate SMTP server which requires  authentication.  Although I've found many threads on the topic, and  tried multiple tutorials (which makes me fear that my config files are  just disasters at this point) it has been in vain.

Sendmail 8.14 is installed.  I have sendmail's path in my php.ini file,  so I know the mail function is calling sendmail (so the problem is  strictly to do with sendmail- not php).  Beyond that, my sendmail.mc  file is likely a mess after editing multiple times and regenerating .cf  after .cf with it.  When I try to sendmail I get the attached photo  (command screen).  

I suppose I'd like to start from scratch since I obviously didn't get  the errors appearing in the attachment before I tried to configure SMTP  Auth.  

If I'm missing anything, please advise.  Thank you for the help.

---

### Post by malleyme1 on 2011-09-30
I'm going to try the above link and see what happens...I thought that I didn't need to use Pear for SMTP Auth if I was calling sendmail directly from the mail() function.

I'm hoping that I can do this without restructuring my code because that would require a LOT of coding (the site I'm working on is huge).

---

### Post by malleyme1 on 2011-09-30
I think I'm getting MUCH closer.  It seems that the mail is attempting to go through my smtp server and it's simply not found?  That's what I interpret the log to mean... If that's actually the case, could this be an issue with my network?  Or the smtp address?  Any suggestions are appreciated- I feel like I may be close.

```

root@ubuntunovel:/var/log# tail mail.log
Sep 30 15:55:49 ubuntunovel sendmail[3922]: p8UJtn4v003922: from=www-data, size=116, class=0, nrcpts=1, msgid=<201109301955.p8UJtn4v003922@ubuntunovel.preferredoffices.local>, relay=www-data@localhost
Sep 30 15:55:50 ubuntunovel sm-mta[3923]: p8UJto7v003923: from=<www-data@host.domain>, size=443, class=0, nrcpts=1, msgid=<201109301955.p8UJtn4v003922@ubuntunovel.preferredoffices.local>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Sep 30 15:55:50 ubuntunovel sendmail[3922]: p8UJtn4v003922: to=michael.malley@novelapplications.com, ctladdr=www-data (33/33), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30116, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p8UJto7v003923 Message accepted for delivery)
Sep 30 15:55:50 ubuntunovel sm-mta[3925]: p8UJto7v003923: to=<michael.malley@novelapplications.com>, ctladdr=<www-data@ubuntunovel.preferredoffices.local> (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=120443, relay='smtp.1and1.com', dsn=5.1.2, stat=Host unknown (Name server: 'smtp.1and1.com': host not found)
Sep 30 15:55:50 ubuntunovel sm-mta[3925]: p8UJto7v003923: p8UJto7v003925: DSN: Host unknown (Name server: 'smtp.1and1.com': host not found)
Sep 30 15:55:50 ubuntunovel sm-mta[3925]: p8UJto7v003925: to=<www-data@host.domain>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent
Sep 30 15:57:38 ubuntunovel sendmail[4537]: alias database /etc/mail/aliases rebuilt by noveladmin
Sep 30 15:57:38 ubuntunovel sendmail[4537]: /etc/mail/aliases: 3 aliases, longest 4 bytes, 35 bytes total
Sep 30 15:57:42 ubuntunovel sm-mta[3906]: restarting /usr/sbin/sendmail-mta due to signal
Sep 30 15:57:42 ubuntunovel sm-mta[4582]: starting daemon (8.14.4): SMTP+queueing@00:10:00
root@ubuntunovel:/var/log# tail mail.log
Sep 30 15:57:38 ubuntunovel sendmail[4537]: alias database /etc/mail/aliases rebuilt by noveladmin
Sep 30 15:57:38 ubuntunovel sendmail[4537]: /etc/mail/aliases: 3 aliases, longest 4 bytes, 35 bytes total
Sep 30 15:57:42 ubuntunovel sm-mta[3906]: restarting /usr/sbin/sendmail-mta due to signal
Sep 30 15:57:42 ubuntunovel sm-mta[4582]: starting daemon (8.14.4): SMTP+queueing@00:10:00
Sep 30 15:58:44 ubuntunovel sendmail[4602]: p8UJwinD004602: from=www-data, size=116, class=0, nrcpts=1, msgid=<201109301958.p8UJwinD004602@ubuntunovel.preferredoffices.local>, relay=www-data@localhost
Sep 30 15:58:44 ubuntunovel sm-mta[4603]: p8UJwiAv004603: from=<www-data@ubuntunovel.preferredoffices.local>, size=443, class=0, nrcpts=1, msgid=<201109301958.p8UJwinD004602@ubuntunovel.preferredoffices.local>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Sep 30 15:58:44 ubuntunovel sendmail[4602]: p8UJwinD004602: to=michael.malley@novelapplications.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30116, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p8UJwiAv004603 Message accepted for delivery)
Sep 30 15:58:44 ubuntunovel sm-mta[4605]: p8UJwiAv004603: to=<michael.malley@novelapplications.com>, ctladdr=<www-data@ubuntunovel.preferredoffices.local> (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=120443, relay='smtp.1and1.com', dsn=5.1.2, stat=Host unknown (Name server: 'smtp.1and1.com': host not found)
Sep 30 15:58:44 ubuntunovel sm-mta[4605]: p8UJwiAv004603: p8UJwiAv004605: DSN: Host unknown (Name server: 'smtp.1and1.com': host not found)
Sep 30 15:58:45 ubuntunovel sm-mta[4605]: p8UJwiAv004605: to=<www-data@ubuntunovel.preferredoffices.local>, delay=00:00:01, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

```

---

### Post by hawkmage on 2011-09-30
It looks like you are tryig to sen email via the smtp relay smtp.1and1.com.  The message you posted mentions that the server can't resolve the name smtp.1and1.com.  

What do you get if to run the command on your server:
```
host smtp.1and1.com
```

---

### Post by malleyme1 on 2011-10-03
Thank you for your response Hawkmage.

The output is below:

```
root@ubuntunovel:/home/noveladmin# host smtp.1and1.com
smtp.1and1.com has address 74.208.5.2
smtp.1and1.com has address 74.208.5.17

```

---

### Post by malleyme1 on 2011-10-14
Looks like I was able to find some options in the website I was working on that allowed me to turn on/off an SMTP mailer function that was hard-coded into the website itself.  So I guess we can consider this one "solved."

---

