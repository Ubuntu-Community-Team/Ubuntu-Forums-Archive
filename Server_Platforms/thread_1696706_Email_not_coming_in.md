---
title: "Email not coming in"
date: 2011-02-27
forum: Server Platforms
---

### Post by xalu on 2011-02-27
Hi,

I set up a new server based on this guide [http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3-p4](http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3-p4). I believe I did everything correct but at one point I may have done a few things wrong since I somehow had two of those guides open and one was different.

The issue is that emails aren't coming in. I had one email come in then I must have changed something because they aren't now. I also have multiple domains I am trying to get work on the server. It is a home server.

My log is fillllled with this...
```

Feb 27 18:58:44 cloud9 sm-mta[6400]: p1RC74q5015493: to=<www-data@cloud9.exampleNetwork.com>, delay=11:51:38, xdelay=00:00:00, mailer=local, pri=6510000, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:44 cloud9 sm-mta[6400]: p1RCA2ZU015613: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=11:48:42, xdelay=00:00:00, mailer=local, pri=6511167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:44 cloud9 sm-mta[6400]: p1RBv43v015259: to=<www-data@cloud9.exampleNetwork.com>, delay=12:01:38, xdelay=00:00:00, mailer=local, pri=6600000, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:44 cloud9 sm-mta[6400]: p1RC02Ej015371: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=11:58:42, xdelay=00:00:00, mailer=local, pri=6601167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RBl422025176: to=<www-data@cloud9.exampleNetwork.com>, delay=12:11:39, xdelay=00:00:00, mailer=local, pri=6690000, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RBo2DT015165: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=12:08:43, xdelay=00:00:00, mailer=local, pri=6691167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RBe27D030935: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=12:18:43, xdelay=00:00:00, mailer=local, pri=6781167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RBU2nV030708: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=12:28:43, xdelay=00:00:00, mailer=local, pri=6871167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RBK3Z1030473: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=12:38:42, xdelay=00:00:00, mailer=local, pri=6961167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RBA2kH030251: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=12:48:43, xdelay=00:00:00, mailer=local, pri=7051167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RB032Q030017: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=12:58:42, xdelay=00:00:00, mailer=local, pri=7141167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RAo3ZX029818: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=13:08:42, xdelay=00:00:00, mailer=local, pri=7231167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RAe2S5029625: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=13:18:43, xdelay=00:00:00, mailer=local, pri=7321167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RAR4m9029295: to=<www-data@cloud9.exampleNetwork.com>, delay=13:31:35, xdelay=00:00:00, mailer=local, pri=7410000, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RAU2Kj029393: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=13:28:43, xdelay=00:00:00, mailer=local, pri=7411167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 18:58:45 cloud9 sm-mta[6400]: p1RAK3FN029201: to=<www-data@cloud9.exampleNetwork.com>, ctladdr=<www-data@cloud9.exampleNetwork.com> (33/33), delay=13:38:42, xdelay=00:00:00, mailer=local, pri=7501167, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL

```

Also, I have an script for a form that uses php mail but that isn't sending any emails either.

---

### Post by xalu on 2011-02-27
Just saw this....

```
Feb 27 19:40:01 cloud9 pop3d: Connection, ip=[::1]
Feb 27 19:40:01 cloud9 pop3d: Disconnected, ip=[::1]
Feb 27 19:40:02 cloud9 sendmail[8179]: p1S0e2XV008179: from=www-data, size=602, class=0, nrcpts=1, msgid=<201102280040.p1S0e2XV008179@cloud9.exampleNetwork.com>, relay=www-data@localhost
Feb 27 19:40:02 cloud9 sm-mta[8180]: p1S0e2Wo008180: from=, size=902, class=0, nrcpts=1, msgid=<201102280040.p1S0e2XV008179@cloud9.exampleNetwork.com>, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Feb 27 19:40:02 cloud9 sendmail[8179]: p1S0e2XV008179: to=www-data, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30602, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p1S0e2Wo008180 Message accepted for delivery)
Feb 27 19:40:03 cloud9 sm-mta[8181]: p1S0e2Wo008180: to=, ctladdr= (33/33), delay=00:00:01, xdelay=00:00:00, mailer=local, pri=31163, dsn=4.0.0, stat=Deferred: local mailer (/usr/sbin/sensible-mda) exited with EX_TEMPFAIL
Feb 27 19:40:24 cloud9 imapd: Connection, ip=[::1]
Feb 27 19:40:24 cloud9 imapd: LOGIN, user=james@exampleNetwork.com, ip=[::1], port=[43767], protocol=IMAP
Feb 27 19:40:24 cloud9 imapd: LOGOUT, user=james@exampleNetwork.com, ip=[::1], headers=0, body=0, rcvd=87, sent=391, time=0
Feb 27 19:45:01 cloud9 imapd: Connection, ip=[::1]
Feb 27 19:45:01 cloud9 pop3d: Connection, ip=[::1]
Feb 27 19:45:01 cloud9 pop3d: Disconnected, ip=[::1]
Feb 27 19:45:01 cloud9 sm-mta[8234]: p1S0j1Ll008234: localhost.localdomain [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
```


and in mail.err
```
Feb 27 16:58:50 cloud9 sm-mta[1974]: p1R8o2Kp027080: SYSERR(root): putbody: write error: Broken pipe
Feb 27 16:58:50 cloud9 sm-mta[1974]: p1R8e2ct026840: SYSERR(root): putbody: write error: Broken pipe
Feb 27 16:58:50 cloud9 sm-mta[1974]: p1R8U2ip026621: SYSERR(root): putbody: write error: Broken pipe
Feb 27 16:58:50 cloud9 sm-mta[1974]: p1R8K33C026439: SYSERR(root): putbody: write error: Broken pipe
Feb 27 16:58:50 cloud9 sm-mta[1974]: p1R8A2ds026149: SYSERR(root): putbody: write error: Broken pipe
Feb 27 16:58:50 cloud9 sm-mta[1974]: p1R8034q025866: SYSERR(root): putbody: write error: Broken pipe
Feb 27 16:58:50 cloud9 sm-mta[1974]: p1R7o3V7025593: SYSERR(root): putbody: write error: Broken pipe
Feb 27 16:58:51 cloud9 sm-mta[1974]: p1R7e3Mk025363: SYSERR(root): putbody: write error: Broken pipe
Feb 27 17:58:33 cloud9 sm-mta[4173]: p1RMmXVk003836: SYSERR(root): putbody: write error: Broken pipe
```

---

### Post by xalu on 2011-03-01
Anyone have any tips? I haven't been able to figure it out.

---

### Post by artheus on 2011-03-01
Hey there.

Maybe this will help you

[http://www.issociate.de/board/goto/1622382/mail.local_exited_with_EX_TEMPFAIL.html](http://www.issociate.de/board/goto/1622382/mail.local_exited_with_EX_TEMPFAIL.html)

Cheers,
Artheus

---

### Post by yashar on 2011-03-01
i dont know about postfix, but :

- check your smtp from outside and check it works, when i works you have two smtp types:

mails come from users that need authentication or mails which comes from out side, by smtp command check each of two conditions via command line and find the problem.

---

### Post by xalu on 2011-03-01
I did a reinstall to see if that would work.

I believe something is misconfigured.
The server and address are incorrect, but I am unsure where that is configured. It should have been set up during install.

xx@cloud9:/sbin$ nslookup
> 192.168.0.19
Server:         209.18.47.61
Address:        209.18.47.61#53

** server can't find 19.0.168.192.in-addr.arpa.: NXDOMAIN

---

### Post by xalu on 2011-03-01
It seems that this is the IP of time warner (my ISP). Is it possible I need to add something in my router?

---

### Post by xalu on 2011-03-02
It seems that the installer dropped a few packages. Also imap was corrupt and not starting. I needed to install maildrop and a couple others as well. So I uninstalled and reinstalled courier-imap and imap-ssl. Afterwards, I was able to get my joomla working with emails and incoming emails are coming in.

---

### Post by yashar on 2011-03-05
so you almost did it, i hope that i can do it later too :)

---

### Post by xalu on 2011-04-28
I got it working yes. I can receive and send emails. The only problem is my ip is blacklisted for emails by google and I am sure everyone else. So the issue about sending emails, in a way, still is a problem. Since, what good is an email if it just gets labeled spam. Te only solution it seems ( with time warner) is to use a mail service to forward the outgoing and incoming emails. 

I have not set it up yet but I'll post about it once I do.

---

