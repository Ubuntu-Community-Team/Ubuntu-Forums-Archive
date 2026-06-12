---
title: "Can't log into user management"
date: 2014-02-22
forum: Security
---

### Post by oygle on 2014-02-22
I use **sudo** for a few commands, and the password is accepted okay for kate, mount,etc. But today I entered the pwd for user management and no dialogue box opened at all. No errors, nothing. Caps lock is not on, as I can use the same pwd in GParted. There was a software update today - 

> Start-Date: 2014-02-22  15:43:57
Upgrade: kde-config-touchpad:amd64 (0.8.1-1ubuntu1.1, 0.8.1-1ubuntu1.2)
End-Date: 2014-02-22  15:44:12

Strange ..

Also in the syslog I see this ..

> 
Feb 22 18:00:02 asus64 sendmail[10249]: My unqualified host name (asus64) unknown; sleeping for retry
Feb 22 18:01:02 asus64 sm-msp-queue[9990]: unable to qualify my own domain name (asus64) -- using short name
Feb 22 18:01:02 asus64 sendmail[10249]: unable to qualify my own domain name (asus64) -- using short name
Feb 22 18:01:02 asus64 sendmail[10249]: s1M7128U010249: from=root, size=743, class=0, nrcpts=1, msgid=<201402220701.s1M7128U010249@asus64>, relay=root@localhost
Feb 22 18:01:04 asus64 sm-mta[10253]: s1M712ek010253: from=<root@asus64>, size=964, class=0, nrcpts=1, msgid=<201402220701.s1M7128U010249@asus64>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Feb 22 18:01:04 asus64 sendmail[10249]: s1M7128U010249: to=root, ctladdr=root (0/0), delay=00:00:02, xdelay=00:00:02, mailer=relay, pri=30743, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (s1M712ek010253 Message accepted for delivery)
Feb 22 18:01:04 asus64 sm-mta[10254]: s1M712ek010253: to=<root@asus64>, ctladdr=<root@asus64> (0/0), delay=00:00:01, xdelay=00:00:00, mailer=local, pri=31162, dsn=2.0.0, stat=Sent
Feb 22 18:06:40 asus64 /usr/bin/crontab[11058]: (root) LIST (nobody)
Feb 22 18:07:02 asus64 sm-mta[2395]: rejecting new messages: min free: 100


but I'm not "sending" any mail. KMail is runing and doing occasional POP3's though (it has to do smtp auth first, maybe that is it ??)

---

### Post by oygle on 2014-02-22
GParted (login as **sudo**) works but KDE Partition Manager does not.

Seems kdesudo is not working ??

---

### Post by oygle on 2014-02-23
I can now login okay, it was a "root full" problem, see [http://ubuntuforums.org/showthread.php?t=2207307](http://ubuntuforums.org/showthread.php?t=2207307)

It would be great if the user management told me that "root" was full, or is it in the logs somewhere ? I looked in the "auth" logs.

---

