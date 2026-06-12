---
title: "Cannot install postfix"
date: 2011-07-11
forum: Server Platforms
---

### Post by instantepiphany on 2011-07-11
Hi all, I have been following the guide at [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix),
and it has all worked perfectly and as expected, except for when it says to run "telnet localhost 25". Instead of getting an ip address displayed as I have seen it is supposed to, it just out puts this.
"Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
Connection closed by foreign host."
I have restarted postfix several times, it has not helped.
Please help me :)

---

### Post by rudelgurke on 2011-07-11
Do you checked with "netstat -tulpen" if there's something listening on port 25 ? And if - is it Postfix ?
And maybe check the logfiles in /var/log/ what Postfix outputs upon starting it.

---

### Post by instantepiphany on 2011-07-11
Sshd was listening on 25. Couldn't see Postfix in there.
Here are the postfix related items in syslog (should I be looking in other places as well?
```

Jul 11 16:08:52 mcserver postfix/master[7690]: daemon started -- version 2.7.1, configuration /etc/postfix
Jul 11 16:09:01 mcserver CRON[7698]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -del$
Jul 11 16:10:01 mcserver postfix/smtpd[7715]: connect from gnfs1.cmg.internode.on.net[203.26.94.245]
Jul 11 16:10:01 mcserver postfix/smtpd[7715]: NOQUEUE: reject: RCPT from gnfs1.cmg.internode.on.net[203.26.94.245]: 550 5.1.1 <admin@instantepiphany.com>: Recipient address rejected: User unknown in local recip$
Jul 11 16:10:28 mcserver postfix/master[7690]: terminating on signal 15

Jul 11 16:13:42 mcserver postfix/master[8058]: daemon started -- version 2.7.1, configuration /etc/postfix
Jul 11 16:13:52 mcserver postfix/smtpd[8064]: connect from 115-64-127-45.tpgi.com.au[115.64.127.45]
Jul 11 16:13:52 mcserver postfix/smtpd[8064]: improper command pipelining after EHLO from 115-64-127-45.tpgi.com.au[115.64.127.45]
Jul 11 16:13:53 mcserver postfix/smtpd[8064]: disconnect from 115-64-127-45.tpgi.com.au[115.64.127.45]
Jul 11 16:13:53 mcserver postfix/smtpd[8064]: connect from 115-64-127-45.tpgi.com.au[115.64.127.45]
Jul 11 16:13:53 mcserver postfix/smtpd[8064]: lost connection after CONNECT from 115-64-127-45.tpgi.com.au[115.64.127.45]
Jul 11 16:13:53 mcserver postfix/smtpd[8064]: disconnect from 115-64-127-45.tpgi.com.au[115.64.127.45]
Jul 11 16:17:13 mcserver postfix/anvil[8068]: statistics: max connection rate 2/60s for (smtp:115.64.127.45) at Jul 11 16:13:53
Jul 11 16:17:13 mcserver postfix/anvil[8068]: statistics: max connection count 1 for (smtp:115.64.127.45) at Jul 11 16:13:52
Jul 11 16:17:13 mcserver postfix/anvil[8068]: statistics: max cache size 1 at Jul 11 16:13:52
Jul 11 16:23:55 mcserver postfix/master[8058]: terminating on signal 15
Jul 11 16:24:11 mcserver postfix/master[9349]: daemon started -- version 2.7.1, configuration /etc/postfix
Jul 11 16:33:01 mcserver CRON[9422]: (root) CMD (cd / && run-parts --report /etc/cron.hourly)
Jul 11 16:39:01 mcserver CRON[9468]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -del$
Jul 11 16:40:18 mcserver postfix/smtpd[9512]: connect from localhost.localdomain[127.0.0.1]
Jul 11 16:40:18 mcserver postfix/smtpd[9512]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 16:40:18 mcserver postfix/smtpd[9512]: fatal: no SASL authentication mechanisms
Jul 11 16:40:19 mcserver postfix/master[9349]: warning: process /usr/lib/postfix/smtpd pid 9512 exit status 1
Jul 11 16:40:19 mcserver postfix/master[9349]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 16:41:19 mcserver postfix/smtpd[9523]: connect from localhost.localdomain[127.0.0.1]
Jul 11 16:41:19 mcserver postfix/smtpd[9523]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 16:41:19 mcserver postfix/smtpd[9523]: fatal: no SASL authentication mechanisms
Jul 11 16:41:20 mcserver postfix/master[9349]: warning: process /usr/lib/postfix/smtpd pid 9523 exit status 1
Jul 11 16:41:20 mcserver postfix/master[9349]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 16:42:20 mcserver postfix/smtpd[9532]: connect from localhost.localdomain[127.0.0.1]
Jul 11 16:42:20 mcserver postfix/smtpd[9532]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 16:42:20 mcserver postfix/smtpd[9532]: fatal: no SASL authentication mechanisms
Jul 11 16:42:20 mcserver postfix/smtpd[9533]: connect from 115-64-127-45.tpgi.com.au[115.64.127.45]
Jul 11 16:42:21 mcserver postfix/smtpd[9533]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 16:42:21 mcserver postfix/smtpd[9533]: fatal: no SASL authentication mechanisms
Jul 11 16:42:21 mcserver postfix/master[9349]: warning: process /usr/lib/postfix/smtpd pid 9532 exit status 1
Jul 11 16:42:21 mcserver postfix/master[9349]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 16:42:21 mcserver postfix/smtpd[9534]: connect from 115-64-127-45.tpgi.com.au[115.64.127.45]
Jul 11 16:42:21 mcserver postfix/smtpd[9534]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 16:42:21 mcserver postfix/smtpd[9534]: fatal: no SASL authentication mechanisms
Jul 11 16:42:22 mcserver postfix/master[9349]: warning: process /usr/lib/postfix/smtpd pid 9533 exit status 1
Jul 11 16:42:22 mcserver postfix/master[9349]: warning: process /usr/lib/postfix/smtpd pid 9534 exit status 1
Jul 11 16:44:02 mcserver postfix/anvil[9535]: statistics: max connection rate 2/60s for (smtp:115.64.127.45) at Jul 11 16:42:21
Jul 11 16:44:02 mcserver postfix/anvil[9535]: statistics: max connection count 2 for (smtp:115.64.127.45) at Jul 11 16:42:21
Jul 11 16:44:02 mcserver postfix/anvil[9535]: statistics: max cache size 1 at Jul 11 16:42:21
Jul 11 16:46:17 mcserver postfix/smtpd[9570]: connect from 115-64-127-45.tpgi.com.au[115.64.127.45]
Jul 11 16:46:17 mcserver postfix/smtpd[9570]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 16:46:17 mcserver postfix/smtpd[9570]: fatal: no SASL authentication mechanisms
Jul 11 16:46:18 mcserver postfix/master[9349]: warning: process /usr/lib/postfix/smtpd pid 9570 exit status 1
Jul 11 16:46:18 mcserver postfix/master[9349]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 16:47:18 mcserver postfix/smtpd[9579]: connect from localhost.localdomain[127.0.0.1]
Jul 11 16:47:18 mcserver postfix/smtpd[9579]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 16:47:18 mcserver postfix/smtpd[9579]: fatal: no SASL authentication mechanisms
Jul 11 16:47:19 mcserver postfix/master[9349]: warning: process /usr/lib/postfix/smtpd pid 9579 exit status 1
Jul 11 16:47:19 mcserver postfix/master[9349]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 16:47:58 mcserver postfix/anvil[9572]: statistics: max connection rate 1/60s for (smtp:115.64.127.45) at Jul 11 16:46:17
Jul 11 16:47:58 mcserver postfix/anvil[9572]: statistics: max connection count 1 for (smtp:115.64.127.45) at Jul 11 16:46:17
Jul 11 16:47:58 mcserver postfix/anvil[9572]: statistics: max cache size 1 at Jul 11 16:46:17
Jul 11 16:53:29 mcserver postfix/postfix-script[9715]: the Postfix mail system is running: PID: 9349
Jul 11 16:55:53 mcserver postfix/smtpd[9819]: connect from localhost.localdomain[127.0.0.1]
Jul 11 16:55:53 mcserver postfix/smtpd[9819]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 16:55:53 mcserver postfix/smtpd[9819]: fatal: no SASL authentication mechanisms
Jul 11 16:55:54 mcserver postfix/master[9349]: warning: process /usr/lib/postfix/smtpd pid 9819 exit status 1
Jul 11 16:55:54 mcserver postfix/master[9349]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 16:56:07 mcserver postfix/postfix-script[9884]: error: unknown command: ''
Jul 11 16:56:08 mcserver postfix/postfix-script[9885]: fatal: usage: postfix start (or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration)
Jul 11 16:56:22 mcserver postfix/postfix-script[9914]: the Postfix mail system is running: PID: 9349
Jul 11 16:56:51 mcserver postfix/postfix-script[10055]: refreshing the Postfix mail system
Jul 11 16:56:51 mcserver postfix/master[9349]: reload -- version 2.7.1, configuration /etc/postfix
Jul 11 16:56:57 mcserver postfix/postfix-script[10069]: stopping the Postfix mail system
Jul 11 16:56:57 mcserver postfix/master[9349]: terminating on signal 15
Jul 11 16:57:35 mcserver postfix/smtpd[10189]: connect from localhost.localdomain[127.0.0.1]
Jul 11 16:57:35 mcserver postfix/smtpd[10189]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 16:57:35 mcserver postfix/smtpd[10189]: fatal: no SASL authentication mechanisms
Jul 11 16:57:36 mcserver postfix/master[10183]: warning: process /usr/lib/postfix/smtpd pid 10189 exit status 1
Jul 11 16:57:36 mcserver postfix/master[10183]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 17:00:26 mcserver postfix/master[10183]: terminating on signal 15
Jul 11 17:00:30 mcserver postfix/master[11518]: daemon started -- version 2.7.1, configuration /etc/postfix
Jul 11 17:06:08 mcserver postfix/smtpd[11602]: connect from localhost.localdomain[127.0.0.1]
Jul 11 17:06:08 mcserver postfix/smtpd[11602]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 17:06:08 mcserver postfix/smtpd[11602]: fatal: no SASL authentication mechanisms
Jul 11 17:06:09 mcserver postfix/master[11518]: warning: process /usr/lib/postfix/smtpd pid 11602 exit status 1
Jul 11 17:06:09 mcserver postfix/master[11518]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 17:09:01 mcserver CRON[11618]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -de$
Jul 11 17:18:17 mcserver postfix/smtpd[11677]: connect from localhost.localdomain[127.0.0.1]
Jul 11 17:18:17 mcserver postfix/smtpd[11677]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 17:18:17 mcserver postfix/smtpd[11677]: fatal: no SASL authentication mechanisms
Jul 11 17:18:18 mcserver postfix/master[11518]: warning: process /usr/lib/postfix/smtpd pid 11677 exit status 1
Jul 11 17:18:18 mcserver postfix/master[11518]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 17:19:18 mcserver postfix/smtpd[11687]: connect from www.instantepiphany.com[175.107.149.73]
Jul 11 17:19:18 mcserver postfix/smtpd[11687]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Jul 11 17:19:18 mcserver postfix/smtpd[11687]: fatal: no SASL authentication mechanisms
Jul 11 17:19:19 mcserver postfix/master[11518]: warning: process /usr/lib/postfix/smtpd pid 11687 exit status 1
Jul 11 17:19:19 mcserver postfix/master[11518]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 11 17:20:59 mcserver postfix/anvil[11688]: statistics: max connection rate 1/60s for (smtp:175.107.149.73) at Jul 11 17:19:18
Jul 11 17:20:59 mcserver postfix/anvil[11688]: statistics: max connection count 1 for (smtp:175.107.149.73) at Jul 11 17:19:18
Jul 11 17:20:59 mcserver postfix/anvil[11688]: statistics: max cache size 1 at Jul 11 17:19:18
Jul 11 20:11:25 mcserver postfix/master[11518]: terminating on signal 15
Jul 11 20:14:30 mcserver postfix/master[1446]: daemon started -- version 2.7.1, configuration /etc/postfix
Jul 11 20:20:02 mcserver postfix/pickup[1448]: 8FCAEE3D0BAC: uid=107 from=<smmsp>
Jul 11 20:20:02 mcserver postfix/cleanup[1671]: 8FCAEE3D0BAC: message-id=<20110711102002.8FCAEE3D0BAC@instantepiphany.com>
Jul 11 20:20:02 mcserver postfix/qmgr[1447]: 8FCAEE3D0BAC: from=<smmsp@instantepiphany.com>, size=684, nrcpt=1 (queue active)
Jul 11 20:20:03 mcserver postfix/local[1673]: 8FCAEE3D0BAC: to=<root@instantepiphany.com>, orig_to=<root>, relay=local, delay=1, delays=0.93/0.01/0/0.09, dsn=2.0.0, status=sent (delivered to maildir)
Jul 11 20:20:03 mcserver postfix/qmgr[1447]: 8FCAEE3D0BAC: removed
Jul 11 20:33:01 mcserver CRON[1831]: (root) CMD (cd / && run-parts --report /etc/cron.hourly)
Jul 11 20:39:02 mcserver CRON[1891]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -del$
Jul 11 20:40:01 mcserver CRON[1908]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Jul 11 20:40:02 mcserver postfix/pickup[1448]: CFAB4E3D0BAE: uid=107 from=<smmsp>
Jul 11 20:40:02 mcserver postfix/cleanup[1928]: CFAB4E3D0BAE: message-id=<20110711104002.CFAB4E3D0BAE@instantepiphany.com>
Jul 11 20:40:02 mcserver postfix/qmgr[1447]: CFAB4E3D0BAE: from=<smmsp@instantepiphany.com>, size=684, nrcpt=1 (queue active)
Jul 11 20:40:02 mcserver postfix/local[1930]: CFAB4E3D0BAE: to=<root@instantepiphany.com>, orig_to=<root>, relay=local, delay=0.15, delays=0.09/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to maildir)
Jul 11 20:40:02 mcserver postfix/qmgr[1447]: CFAB4E3D0BAE: removed
Jul 11 20:54:22 mcserver -- MARK --
Jul 11 20:54:34 mcserver postfix/pickup[1448]: EDB43E3D0BB2: uid=33 from=<www-data>
Jul 11 20:54:34 mcserver postfix/cleanup[3103]: EDB43E3D0BB2: message-id=<20110711105433.EDB43E3D0BB2@instantepiphany.com>
Jul 11 20:54:34 mcserver postfix/qmgr[1447]: EDB43E3D0BB2: from=<www-data@instantepiphany.com>, size=1046, nrcpt=1 (queue active)
Jul 11 20:54:36 mcserver postfix/smtp[3105]: certificate verification failed for gmail-smtp-in.l.google.com[74.125.65.27]:25: untrusted issuer /C=US/O=Equifax/OU=Equifax Secure Certificate Authority
Jul 11 20:54:40 mcserver postfix/smtp[3105]: EDB43E3D0BB2: to=mypersonalemail@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.65.27]:25, delay=7, delays=1.4/0.43/2.6/2.6, dsn=2.0.0, status=sent (250 2.0.0 OK 13$
Jul 11 20:54:40 mcserver postfix/qmgr[1447]: EDB43E3D0BB2: removed
Jul 11 21:00:01 mcserver CRON[3172]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Jul 11 21:00:03 mcserver postfix/pickup[1448]: 9F203E3D0BB2: uid=107 from=<smmsp>
Jul 11 21:00:03 mcserver postfix/cleanup[3193]: 9F203E3D0BB2: message-id=<20110711110003.9F203E3D0BB2@instantepiphany.com>
Jul 11 21:00:03 mcserver postfix/qmgr[1447]: 9F203E3D0BB2: from=<smmsp@instantepiphany.com>, size=684, nrcpt=1 (queue active)
Jul 11 21:00:03 mcserver postfix/local[3195]: 9F203E3D0BB2: to=<root@instantepiphany.com>, orig_to=<root>, relay=local, delay=0.99, delays=0.77/0.05/0/0.16, dsn=2.0.0, status=sent (delivered to maildir)
Jul 11 21:00:03 mcserver postfix/qmgr[1447]: 9F203E3D0BB2: removed
Jul 11 21:09:02 mcserver CRON[3299]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -del$
Jul 11 21:14:22 mcserver named[1277]: listening on IPv4 interface tun0, 10.9.0.1#53
Jul 11 21:20:02 mcserver CRON[3405]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)

Jul 11 21:20:03 mcserver postfix/pickup[1448]: E2D83E3D0BCC: uid=107 from=<smmsp>
Jul 11 21:20:03 mcserver postfix/cleanup[3426]: E2D83E3D0BCC: message-id=<20110711112003.E2D83E3D0BCC@instantepiphany.com>
Jul 11 21:20:03 mcserver postfix/qmgr[1447]: E2D83E3D0BCC: from=<smmsp@instantepiphany.com>, size=684, nrcpt=1 (queue active)
Jul 11 21:20:04 mcserver postfix/local[3428]: E2D83E3D0BCC: to=<root@instantepiphany.com>, orig_to=<root>, relay=local, delay=0.62, delays=0.6/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
Jul 11 21:20:04 mcserver postfix/qmgr[1447]: E2D83E3D0BCC: removed
Jul 11 21:33:01 mcserver CRON[3553]: (root) CMD (cd / && run-parts --report /etc/cron.hourly)
Jul 11 21:39:01 mcserver CRON[3646]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -del$
Jul 11 21:40:01 mcserver CRON[3663]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Jul 11 21:40:02 mcserver postfix/pickup[1448]: 42344E3D0BCE: uid=107 from=<smmsp>
Jul 11 21:40:02 mcserver postfix/cleanup[3684]: 42344E3D0BCE: message-id=<20110711114002.42344E3D0BCE@instantepiphany.com>
Jul 11 21:40:02 mcserver postfix/qmgr[1447]: 42344E3D0BCE: from=<smmsp@instantepiphany.com>, size=684, nrcpt=1 (queue active)
Jul 11 21:40:02 mcserver postfix/local[3686]: 42344E3D0BCE: to=<root@instantepiphany.com>, orig_to=<root>, relay=local, delay=1.3, delays=1.2/0.03/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
Jul 11 21:40:02 mcserver postfix/qmgr[1447]: 42344E3D0BCE: removed
Jul 11 21:44:36 mcserver postfix/pickup[1448]: A06CEE3D0BCE: uid=33 from=<www-data>
Jul 11 21:44:36 mcserver postfix/cleanup[3735]: A06CEE3D0BCE: message-id=<20110711114436.A06CEE3D0BCE@instantepiphany.com>
Jul 11 21:44:36 mcserver postfix/qmgr[1447]: A06CEE3D0BCE: from=<www-data@instantepiphany.com>, size=1513, nrcpt=1 (queue active)
Jul 11 21:44:41 mcserver postfix/smtp[3737]: A06CEE3D0BCE: to=<mypersonalemail@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.65.27]:25, delay=5, delays=0.28/0.13/2.3/2.3, dsn=2.0.0, status=sent (250 2.0.0 OK 1$
Jul 11 21:44:41 mcserver postfix/qmgr[1447]: A06CEE3D0BCE: removed

```

What were those entries that had my personal email in them?

---

### Post by instantepiphany on 2011-07-11
An update....
I fixed that previous error by installing sasl2-modules.

I could use telnet localhost 25 and succesfully send mail to exampleuser@localhost. I then did su - exampleuser and typed mail, but it said
```

mail: /home/fmaster/Maildir: Is a directory

```
I can manually cd into Maildir, then new, and use nano to read any mail in there but this is annoying, and doesn't mark the mail as read and move it out of the new folder. What am I doing wrong?

---

