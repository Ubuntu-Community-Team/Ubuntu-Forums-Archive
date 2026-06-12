---
title: "sendmail permissions problems"
date: 2006-07-07
forum: Server Platforms
---

### Post by maino82 on 2006-07-07
I am receiving the following error in /var/log/mail.log that seems to point to a permissions problem with the www-data user (apache) not being able to send mail or create the needed directories. The problem is that I have been unable to find any information about which files/directories need to have their permissions changed, or if it's a problem inherent in the www-data user that needs to be corrected. Any help you could offer would be greatly appreciated!

> Jul  7 12:34:07 localhost sendmail[16364]: k67GY74N016364: from=www-data, size=87, class=0, nrcpts=1, msgid=<200607071634.k67GY74N016364@localhost.localdomain>, relay=www-data@localhost
Jul  7 12:34:07 localhost sm-mta[16365]: k67GY7lH016365: SYSERR(root): collect: Cannot write ./dfk67GY7lH016365 (bfcommit, uid=0, gid=122): No such file or directory
Jul  7 12:34:07 localhost sm-mta[16365]: k67GY7lH016365: from=<www-data@localhost.localdomain>, size=324, class=0, nrcpts=1, proto=ESMTP, daemon=MSP-v4, relay=localhost.localdomain [127.0.0.1]
Jul  7 12:34:07 localhost sendmail[16364]: k67GY74N016364: to=ADDRESS@gmail.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30087, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfk67GY7lH016365 (bfcommit, uid=0, gid=122): No such file or directory


Thanks!
Dave

---

### Post by lamego on 2006-07-07
The "No such file or directory" looks more like a missing directory.
I believe that during local messages delivery the files are created on the mail spool at:
/var/spool/mail

---

### Post by maino82 on 2006-07-07
I checked and the /var/spool/mail directory does exist. I'm not sure if that's the directory it's looking for though since this is not doing local mail delivery (at least it shouldn't be... it should be going to a gmail account). I'm sure I could be wrong about this, however, since I'm not entirely sure what's going on and I'm by no means an expert. Are there any other log files that I missed that may shed some light on this? Or maybe any information that's staring me in the face from the previously posted log that I just completely missed?

---

