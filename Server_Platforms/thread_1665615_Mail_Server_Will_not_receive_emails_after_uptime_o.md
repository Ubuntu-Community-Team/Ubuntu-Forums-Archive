---
title: "Mail Server Will not receive emails after uptime over one hour"
date: 2011-01-12
forum: Server Platforms
---

### Post by ITDude on 2011-01-12
It is the strangest thing. I can not receive emails on this server after it has been up for an hour. I noticed that everytime and email is received that a sshd opens but never closes. Causeing a memory issue that I dont know how to fix. Also the mailq grows and grows. Mostly with email stating the recipient and send are both [email]root@mail.jmchd.com[/email]
also [email]postmaster@mail.jmchd.com[/email] shows mail system configuration error. I have to restart the server every 30 minutes so users can get and send emails. 
This is horrible because for every 5 minutes out of the hour emails are bouncing. 
I need help... I can copy any log needed. I have looked through them but I know not what I am looking at. 

PS. I was thrown into the position and have limited knowledge. I am used to a GUI. 

All Help is appreciated!!!

---

### Post by elico on 2011-01-12
what mail MTA are you using? 
whai is the /var/log/mail.log is saying on the error? and what in the /var/log/message ..
on the time ?
how many users do you have there?

---

### Post by HermanAB on 2011-01-13
Howdy,

What kind of GUI?  Do you have local access to the machine?

Open a console and run ps to see what is running:
$ sudo ps -e

Look for something resembling a MTA such as postfix or qmail or whatever, then visit the MTA project web site and read a bit to figure out how to debug it - where are the mail queues - how can you flush them etc.

---

### Post by ITDude on 2011-01-13
> **elico said:**
> what mail MTA are you using? 
whai is the /var/log/mail.log is saying on the error? and what in the /var/log/message ..
on the time ?
how many users do you have there?

I am using PostFix here is the end of the mail log


> Jan 13 10:44:32 mail postfix/smtpd[8295]: connect from unknown[187.23.251.163]
Jan 13 10:44:32 mail postfix/smtpd[8653]: connect from localhost.jmchd.com[127.0.0.1]
Jan 13 10:44:32 mail postfix/smtpd[8653]: AD87E122C077: client=localhost.jmchd.com[127.0.0.1]
Jan 13 10:44:32 mail postfix/cleanup[8319]: AD87E122C077: message-id=<4D2ED0050200006200072871@ag03ng02.nash.tenn>
Jan 13 10:44:32 mail postfix/smtpd[8653]: disconnect from localhost.jmchd.com[127.0.0.1]
Jan 13 10:44:32 mail postfix/qmgr[8157]: AD87E122C077: from=<prvs=1987d421e7=will.oden@tn.gov>, size=15085, nrcpt=1 (queue active)
Jan 13 10:44:32 mail amavis[7883]: (07883-09) FWD via SMTP: <prvs=1987d421e7=will.oden@tn.gov> -> <lmooney@jmchd.com>,BODY=7BIT 250 2.6.0 Ok, id=07883-09, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as AD87E122C077
Jan 13 10:44:32 mail amavis[7883]: (07883-09) Passed CLEAN, [170.143.36.97] [170.143.36.97] <prvs=1987d421e7=will.oden@tn.gov> -> <lmooney@jmchd.com>, Message-ID: <4D2ED0050200006200072871@ag03ng02.nash.tenn>, mail_id: o6T-kGH63+qY, Hits: 0.001, size: 14639, queued_as: AD87E122C077, 1413 ms
Jan 13 10:44:32 mail postfix/smtp[8650]: 2C7AB122C074: to=<lmooney@jmchd.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=2.9, delays=1.5/0.01/0/1.4, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as AD87E122C077)
Jan 13 10:44:32 mail postfix/qmgr[8157]: 2C7AB122C074: removed
Jan 13 10:44:32 mail amavis[7883]: (07883-09) TIMING [total 1417 ms] - SMTP greeting: 2 (0%)0, SMTP EHLO: 0 (0%)0, SMTP pre-MAIL: 1 (0%)0, SMTP pre-DATA-flush: 2 (0%)0, SMTP DATA: 38 (3%)3, check_init: 1 (0%)3, digest_hdr: 0 (0%)3, digest_body: 0 (0%)3, gen_mail_id: 1 (0%)3, mime_decode: 44 (3%)6, get-file-type2: 24 (2%)8, decompose_part: 2 (0%)8, parts_decode: 0 (0%)8, check_header: 2 (0%)8, AV-scan-1: 10 (1%)9, spam-wb-list: 2 (0%)9, SA parse: 4 (0%)9, SA check: 1218 (86%)95, update_cache: 7 (1%)96, decide_mail_destiny: 1 (0%)96, fwd-connect: 15 (1%)97, fwd-mail-pip: 2 (0%)97, fwd-rcpt-pip: 0 (0%)97, fwd-data-chkpnt: 0 (0%)97, write-header: 1 (0%)97, fwd-data-contents: 0 (0%)97, fwd-end-chkpnt: 30 (2%)99, prepare-dsn: 1 (0%)99, main_log_entry: 8 (1%)100, update_snmp: 1 (0%)100, SMTP pre-response: 0 (0%)100, SMTP response: 0 (0%)100, unlink-2-files: 0 (0%)100, rundown: 0 (0%)100
Jan 13 10:44:32 mail postfix/smtp[8654]: AD87E122C077: to=<lmooney@jmchd.com>, relay=phobos.jmchd.com[192.168.1.85]:25, delay=0.14, delays=0.03/0.01/0.04/0.07, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 1C7A2230041)
Jan 13 10:44:32 mail postfix/qmgr[8157]: AD87E122C077: removed
Jan 13 10:44:35 mail postgrey[7628]: action=greylist, reason=new, client_name=unknown, client_address=187.23.251.163, sender=jicuqecaq8968@virtua.com.br, recipient=bolgcsullivan@jmchd.com
Jan 13 10:44:35 mail postfix/smtpd[8295]: NOQUEUE: reject: RCPT from unknown[187.23.251.163]: 450 4.2.0 <bolgcsullivan@jmchd.com>: Recipient address rejected: Greylisted, see [http://postgrey.schweikert.ch/help/jmchd.com.html;](http://postgrey.schweikert.ch/help/jmchd.com.html;) from=<jicuqecaq8968@virtua.com.br> to=<bolgcsullivan@jmchd.com> proto=ESMTP helo=<virtua.com.br>
Jan 13 10:44:35 mail postfix/smtpd[8295]: disconnect from unknown[187.23.251.163]
Jan 13 10:44:35 mail postgrey[7628]: action=pass, reason=recipient whitelist, client_name=tx2ehsobe004.messaging.microsoft.com, client_address=65.55.88.14, sender=Broadcast_giuhlf4o@bounce.sas.com, recipient=jboyd@jmchd.com
Jan 13 10:44:35 mail postfix/smtpd[8461]: DC20C122C074: client=tx2ehsobe004.messaging.microsoft.com[65.55.88.14]
Jan 13 10:44:36 mail postfix/smtpd[8334]: connect from ppp92-100-92-2.pppoe.avangarddsl.ru[92.100.92.2]
Jan 13 10:44:37 mail postfix/smtpd[8295]: connect from unknown[151.55.16.66]
Jan 13 10:44:37 mail postfix/cleanup[8649]: DC20C122C074: message-id=<27001779.1294935679830.JavaMail.webowner@sems.unx.sas.com>
Jan 13 10:44:37 mail postfix/qmgr[8157]: DC20C122C074: from=<Broadcast_giuhlf4o@bounce.sas.com>, size=11946, nrcpt=1 (queue active)
Jan 13 10:44:37 mail amavis[7876]: (07876-10) ESMTP::10024 /var/lib/amavis/tmp/amavis-20110113T103359-07876: <Broadcast_giuhlf4o@bounce.sas.com> -> <jboyd@jmchd.com> SIZE=11946 Received: from mail.jmchd.com ([127.0.0.1]) by localhost (mail.jmchd.com [127.0.0.1]) (amavisd-new, port 10024) with ESMTP for <jboyd@jmchd.com>; Thu, 13 Jan 2011 10:44:37 -0600 (CST)
Jan 13 10:44:37 mail amavis[7876]: (07876-10) Checking: nOTlKN2kkk46 [65.55.88.14] <Broadcast_giuhlf4o@bounce.sas.com> -> <jboyd@jmchd.com>
Jan 13 10:44:37 mail amavis[7876]: (07876-10) p003 1 Content-Type: multipart/alternative
Jan 13 10:44:37 mail amavis[7876]: (07876-10) p001 1/1 Content-Type: text/plain, size: 1890 B, name:
Jan 13 10:44:37 mail amavis[7876]: (07876-10) p002 1/2 Content-Type: text/html, size: 7063 B, name:
Jan 13 10:44:37 mail postfix/smtpd[8461]: disconnect from tx2ehsobe004.messaging.microsoft.com[65.55.88.14]
Jan 13 10:44:39 mail postgrey[7628]: action=greylist, reason=new, client_name=unknown, client_address=151.55.16.66, sender=ediukian7968@6600690.ru, recipient=bolgjboyd@jmchd.com
Jan 13 10:44:39 mail postfix/smtpd[8295]: NOQUEUE: reject: RCPT from unknown[151.55.16.66]: 450 4.2.0 <bolgjboyd@jmchd.com>: Recipient address rejected: Greylisted, see [http://postgrey.schweikert.ch/help/jmchd.com.html;](http://postgrey.schweikert.ch/help/jmchd.com.html;) from=<ediukian7968@6600690.ru> to=<bolgjboyd@jmchd.com> proto=ESMTP helo=<[151.55.16.66]>
Jan 13 10:44:39 mail postfix/smtpd[8295]: disconnect from unknown[151.55.16.66]
Jan 13 10:44:40 mail postgrey[7628]: action=greylist, reason=new, client_name=ppp92-100-92-2.pppoe.avangarddsl.ru, client_address=92.100.92.2, sender=OscarGlasier@fredsegalfeet.com, recipient=csullivan@jmchd.com
Jan 13 10:44:40 mail postfix/smtpd[8334]: NOQUEUE: reject: RCPT from ppp92-100-92-2.pppoe.avangarddsl.ru[92.100.92.2]: 450 4.2.0 <csullivan@jmchd.com>: Recipient address rejected: Greylisted, see [http://postgrey.schweikert.ch/help/jmchd.com.html;](http://postgrey.schweikert.ch/help/jmchd.com.html;) from=<OscarGlasier@fredsegalfeet.com> to=<csullivan@jmchd.com> proto=ESMTP helo=<emachine-52189d>
Jan 13 10:44:40 mail postfix/smtpd[8334]: lost connection after DATA (0 bytes) from ppp92-100-92-2.pppoe.avangarddsl.ru[92.100.92.2]
Jan 13 10:44:40 mail postfix/smtpd[8334]: disconnect from ppp92-100-92-2.pppoe.avangarddsl.ru[92.100.92.2]
Jan 13 10:44:41 mail postfix/smtpd[8461]: connect from dslb-088-068-118-007.pools.arcor-ip.net[88.68.118.7]
Jan 13 10:44:43 mail postgrey[7628]: action=greylist, reason=new, client_name=dslb-088-068-118-007.pools.arcor-ip.net, client_address=88.68.118.7, sender=vuvitasyp1354@arcor-ip.net, recipient=bolgamycox@jmchd.com
Jan 13 10:44:43 mail postfix/smtpd[8461]: NOQUEUE: reject: RCPT from dslb-088-068-118-007.pools.arcor-ip.net[88.68.118.7]: 450 4.2.0 <bolgamycox@jmchd.com>: Recipient address rejected: Greylisted, see [http://postgrey.schweikert.ch/help/jmchd.com.html;](http://postgrey.schweikert.ch/help/jmchd.com.html;) from=<vuvitasyp1354@arcor-ip.net> to=<bolgamycox@jmchd.com> proto=ESMTP helo=<arcor-ip.net>
Jan 13 10:44:43 mail postfix/smtpd[8461]: disconnect from dslb-088-068-118-007.pools.arcor-ip.net[88.68.118.7]
Jan 13 10:44:45 mail postfix/smtpd[8653]: connect from localhost.jmchd.com[127.0.0.1]
Jan 13 10:44:45 mail postfix/smtpd[8653]: 107B9122C077: client=localhost.jmchd.com[127.0.0.1]
Jan 13 10:44:45 mail postfix/cleanup[8328]: 107B9122C077: message-id=<27001779.1294935679830.JavaMail.webowner@sems.unx.sas.com>
Jan 13 10:44:45 mail postfix/smtpd[8653]: disconnect from localhost.jmchd.com[127.0.0.1]
Jan 13 10:44:45 mail postfix/qmgr[8157]: 107B9122C077: from=<Broadcast_giuhlf4o@bounce.sas.com>, size=12388, nrcpt=1 (queue active)
Jan 13 10:44:45 mail amavis[7876]: (07876-10) FWD via SMTP: <Broadcast_giuhlf4o@bounce.sas.com> -> <jboyd@jmchd.com>,BODY=7BIT 250 2.6.0 Ok, id=07876-10, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 107B9122C077
Jan 13 10:44:45 mail amavis[7876]: (07876-10) Passed CLEAN, [65.55.88.14] [149.173.6.148] <Broadcast_giuhlf4o@bounce.sas.com> -> <jboyd@jmchd.com>, Message-ID: <27001779.1294935679830.JavaMail.webowner@sems.unx.sas.com>, mail_id: nOTlKN2kkk46, Hits: -2.586, size: 11946, queued_as: 107B9122C077, 7667 ms
Jan 13 10:44:45 mail postfix/smtp[8650]: DC20C122C074: to=<jboyd@jmchd.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=11, delays=3.1/0/0/7.7, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 107B9122C077)
Jan 13 10:44:45 mail postfix/qmgr[8157]: DC20C122C074: removed
Jan 13 10:44:45 mail amavis[7876]: (07876-10) TIMING [total 7670 ms] - SMTP greeting: 2 (0%)0, SMTP EHLO: 0 (0%)0, SMTP pre-MAIL: 1 (0%)0, SMTP pre-DATA-flush: 2 (0%)0, SMTP DATA: 44 (1%)1, check_init: 1 (0%)1, digest_hdr: 1 (0%)1, digest_body: 0 (0%)1, gen_mail_id: 1 (0%)1, mime_decode: 28 (0%)1, get-file-type2: 32 (0%)1, decompose_part: 1 (0%)1, decompose_part: 2 (0%)1, parts_decode: 0 (0%)1, check_header: 2 (0%)2, AV-scan-1: 8 (0%)2, spam-wb-list: 2 (0%)2, SA parse: 5 (0%)2, SA check: 7492 (98%)99, update_cache: 6 (0%)99, decide_mail_destiny: 1 (0%)99, fwd-connect: 4 (0%)100, fwd-mail-pip: 2 (0%)100, fwd-rcpt-pip: 0 (0%)100, fwd-data-chkpnt: 0 (0%)100, write-header: 1 (0%)100, fwd-data-contents: 0 (0%)100, fwd-end-chkpnt: 22 (0%)100, prepare-dsn: 1 (0%)100, main_log_entry: 7 (0%)100, update_snmp: 1 (0%)100, SMTP pre-response: 0 (0%)100, SMTP response: 0 (0%)100, unlink-2-files: 0 (0%)100, rundown: 0 (0%)100
Jan 13 10:44:45 mail postfix/smtp[8654]: 107B9122C077: to=<jboyd@jmchd.com>, relay=phobos.jmchd.com[192.168.1.85]:25, delay=0.11, delays=0.02/0/0/0.08, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 68B7D230041)
Jan 13 10:44:45 mail postfix/qmgr[8157]: 107B9122C077: removed
Jan 13 10:44:51 mail postfix/smtpd[8334]: connect from LCaen-156-54-11-250.w217-128.abo.wanadoo.fr[217.128.206.250]
Jan 13 10:44:53 mail postgrey[7628]: action=greylist, reason=new, client_name=LCaen-156-54-11-250.w217-128.abo.wanadoo.fr, client_address=217.128.206.250, sender=udotereq6828@wanadoo.fr, recipient=moldiestjko1@jmchd.com
Jan 13 10:44:53 mail postfix/smtpd[8334]: NOQUEUE: reject: RCPT from LCaen-156-54-11-250.w217-128.abo.wanadoo.fr[217.128.206.250]: 450 4.2.0 <moldiestjko1@jmchd.com>: Recipient address rejected: Greylisted, see [http://postgrey.schweikert.ch/help/jmchd.com.html;](http://postgrey.schweikert.ch/help/jmchd.com.html;) from=<udotereq6828@wanadoo.fr> to=<moldiestjko1@jmchd.com> proto=ESMTP helo=<wanadoo.fr>
Jan 13 10:44:53 mail postfix/smtpd[8334]: disconnect from LCaen-156-54-11-250.w217-128.abo.wanadoo.fr[217.128.206.250]
Jan 13 10:45:01 mail postfix/pickup[8156]: 50527122C078: uid=0 from=<root>
Jan 13 10:45:01 mail postfix/cleanup[8319]: 50527122C078: message-id=<20110113164501.50527122C078@mail.jmchd.com>
Jan 13 10:45:01 mail postfix/qmgr[8157]: 50527122C078: from=<root@mail.jmchd.com>, size=529, nrcpt=1 (queue active)
Jan 13 10:45:01 mail postfix/pickup[8156]: 53648122C074: uid=0 from=<root>
Jan 13 10:45:01 mail postfix/cleanup[8328]: 53648122C074: message-id=<20110113164501.53648122C074@mail.jmchd.com>
Jan 13 10:45:01 mail postfix/virtual[8323]: 50527122C078: to=<root@mail.jmchd.com>, orig_to=<root>, relay=virtual, delay=0.06, delays=0.04/0/0/0.02, dsn=5.1.1, status=bounced (unknown user: "root@mail.jmchd.com")
Jan 13 10:45:01 mail postfix/cleanup[8319]: 585F8122C07F: message-id=<20110113164501.585F8122C07F@mail.jmchd.com>
Jan 13 10:45:01 mail postfix/qmgr[8157]: 585F8122C07F: from=<>, size=2296, nrcpt=1 (queue active)
Jan 13 10:45:01 mail postfix/bounce[8360]: 50527122C078: sender non-delivery notification: 585F8122C07F
Jan 13 10:45:01 mail postfix/qmgr[8157]: 50527122C078: removed
Jan 13 10:45:01 mail postfix/qmgr[8157]: 53648122C074: from=<root@mail.jmchd.com>, size=529, nrcpt=1 (queue active)
Jan 13 10:45:01 mail postfix/virtual[8322]: 585F8122C07F: to=<root@mail.jmchd.com>, relay=virtual, delay=0.08, delays=0.02/0.04/0/0.02, dsn=5.1.1, status=bounced (unknown user: "root@mail.jmchd.com")
Jan 13 10:45:01 mail postfix/virtual[8323]: 53648122C074: to=<root@mail.jmchd.com>, orig_to=<root>, relay=virtual, delay=0.14, delays=0.12/0/0/0.02, dsn=5.1.1, status=bounced (unknown user: "root@mail.jmchd.com")
Jan 13 10:45:01 mail postfix/qmgr[8157]: 585F8122C07F: removed
Jan 13 10:45:01 mail postfix/cleanup[8328]: 6C197122C078: message-id=<20110113164501.6C197122C078@mail.jmchd.com>
Jan 13 10:45:01 mail postfix/bounce[8325]: 53648122C074: sender non-delivery notification: 6C197122C078
Jan 13 10:45:01 mail postfix/qmgr[8157]: 6C197122C078: from=<>, size=2296, nrcpt=1 (queue active)
Jan 13 10:45:01 mail postfix/qmgr[8157]: 53648122C074: removed
Jan 13 10:45:01 mail postfix/virtual[8322]: 6C197122C078: to=<root@mail.jmchd.com>, relay=virtual, delay=0.04, delays=0.03/0/0/0.01, dsn=5.1.1, status=bounced (unknown user: "root@mail.jmchd.com")
Jan 13 10:45:01 mail postfix/qmgr[8157]: 6C197122C078: removed
Jan 13 10:45:06 mail pop3d: Connection, ip=[::ffff:192.168.1.192]
Jan 13 10:45:06 mail pop3d: LOGIN, user=shayes@jmchd.com, ip=[::ffff:192.168.1.192], port=[1979]
Jan 13 10:45:06 mail pop3d: LOGOUT, user=shayes@jmchd.com, ip=[::ffff:192.168.1.192], port=[1979], top=0, retr=20624, rcvd=56, sent=21340, time=0
Jan 13 10:45:40 mail postfix/smtpd[8295]: warning: 118.71.41.211: hostname ip-address-pool-xxx.fpt.vn verification failed: Name or service not known
Jan 13 10:45:40 mail postfix/smtpd[8295]: connect from unknown[118.71.41.211]
Jan 13 10:45:42 mail postgrey[7628]: action=greylist, reason=new, client_name=unknown, client_address=118.71.41.211, sender=kexekyaky9492@fpt.vn, recipient=anatomies41@jmchd.com
Jan 13 10:45:42 mail postfix/smtpd[8295]: NOQUEUE: reject: RCPT from unknown[118.71.41.211]: 450 4.2.0 <anatomies41@jmchd.com>: Recipient address rejected: Greylisted, see [http://postgrey.schweikert.ch/help/jmchd.com.html;](http://postgrey.schweikert.ch/help/jmchd.com.html;) from=<kexekyaky9492@fpt.vn> to=<anatomies41@jmchd.com> proto=ESMTP helo=<fpt.vn>
Jan 13 10:45:43 mail postfix/smtpd[8295]: disconnect from unknown[118.71.41.211]
Jan 13 10:45:57 mail postfix/smtpd[8461]: connect from unknown[68.233.242.36]
Jan 13 10:45:57 mail postgrey[7628]: action=greylist, reason=new, client_name=unknown, client_address=68.233.242.36, sender=patty@sangofikes.com, recipient=blewis@jmchd.com
Jan 13 10:45:57 mail postfix/smtpd[8461]: NOQUEUE: reject: RCPT from unknown[68.233.242.36]: 450 4.2.0 <blewis@jmchd.com>: Recipient address rejected: Greylisted, see [http://postgrey.schweikert.ch/help/jmchd.com.html;](http://postgrey.schweikert.ch/help/jmchd.com.html;) from=<patty@sangofikes.com> to=<blewis@jmchd.com> proto=ESMTP helo=<oqru55.sangofikes.com>
Jan 13 10:45:58 mail postfix/smtpd[8461]: disconnect from unknown[68.233.242.36]
Jan 13 10:46:01 mail postfix/pickup[8156]: 58B4A122C078: uid=0 from=<root>
Jan 13 10:46:01 mail postfix/cleanup[8319]: 58B4A122C078: message-id=<20110113164601.58B4A122C078@mail.jmchd.com>
Jan 13 10:46:01 mail postfix/qmgr[8157]: 58B4A122C078: from=<root@mail.jmchd.com>, size=529, nrcpt=1 (queue active)
Jan 13 10:46:01 mail postfix/pickup[8156]: 5D7D9122C077: uid=0 from=<root>
Jan 13 10:46:01 mail postfix/virtual[8323]: 58B4A122C078: to=<root@mail.jmchd.com>, orig_to=<root>, relay=virtual, delay=0.06, delays=0.04/0/0/0.02, dsn=5.1.1, status=bounced (unknown user: "root@mail.jmchd.com")
Jan 13 10:46:01 mail postfix/cleanup[8328]: 5D7D9122C077: message-id=<20110113164601.5D7D9122C077@mail.jmchd.com>
Jan 13 10:46:01 mail postfix/cleanup[8319]: 62885122C07F: message-id=<20110113164601.62885122C07F@mail.jmchd.com>
Jan 13 10:46:01 mail postfix/qmgr[8157]: 5D7D9122C077: from=<root@mail.jmchd.com>, size=529, nrcpt=1 (queue active)
Jan 13 10:46:01 mail postfix/virtual[8322]: 5D7D9122C077: to=<root@mail.jmchd.com>, orig_to=<root>, relay=virtual, delay=0.1, delays=0.08/0/0/0.02, dsn=5.1.1, status=bounced (unknown user: "root@mail.jmchd.com")
Jan 13 10:46:01 mail postfix/qmgr[8157]: 62885122C07F: from=<>, size=2296, nrcpt=1 (queue active)
Jan 13 10:46:01 mail postfix/bounce[8360]: 58B4A122C078: sender non-delivery notification: 62885122C07F
Jan 13 10:46:01 mail postfix/qmgr[8157]: 58B4A122C078: removed
Jan 13 10:46:01 mail postfix/cleanup[8328]: 6EA23122C078: message-id=<20110113164601.6EA23122C078@mail.jmchd.com>
Jan 13 10:46:01 mail postfix/virtual[8323]: 62885122C07F: to=<root@mail.jmchd.com>, relay=virtual, delay=0.07, delays=0.04/0.01/0/0.02, dsn=5.1.1, status=bounced (unknown user: "root@mail.jmchd.com")
Jan 13 10:46:01 mail postfix/qmgr[8157]: 62885122C07F: removed
Jan 13 10:46:01 mail postfix/bounce[8325]: 5D7D9122C077: sender non-delivery notification: 6EA23122C078
Jan 13 10:46:01 mail postfix/qmgr[8157]: 6EA23122C078: from=<>, size=2296, nrcpt=1 (queue active)
Jan 13 10:46:01 mail postfix/qmgr[8157]: 5D7D9122C077: removed
Jan 13 10:46:01 mail postfix/virtual[8322]: 6EA23122C078: to=<root@mail.jmchd.com>, relay=virtual, delay=0.03, delays=0.02/0/0/0.01, dsn=5.1.1, status=bounced (unknown user: "root@mail.jmchd.com")
Jan 13 10:46:01 mail postfix/qmgr[8157]: 6EA23122C078: removed
Jan 13 10:46:08 mail postfix/smtpd[8334]: connect from osbk-4d08be6b.pool.mediaWays.net[77.8.190.107]
Jan 13 10:46:09 mail postgrey[7628]: action=greylist, reason=new, client_name=osbk-4d08be6b.pool.mediaWays.net, client_address=77.8.190.107, sender=uukoikoaud5475@mediaWays.net, recipient=bloodiests523@jmchd.com
Jan 13 10:46:09 mail postfix/smtpd[8334]: NOQUEUE: reject: RCPT from osbk-4d08be6b.pool.mediaWays.net[77.8.190.107]: 450 4.2.0 <bloodiests523@jmchd.com>: Recipient address rejected: Greylisted, see [http://postgrey.schweikert.ch/help/jmchd.com.html;](http://postgrey.schweikert.ch/help/jmchd.com.html;) from=<uukoikoaud5475@mediaWays.net> to=<bloodiests523@jmchd.com> proto=ESMTP helo=<mediaWays.net>
Jan 13 10:46:09 mail postfix/smtpd[8334]: disconnect from osbk-4d08be6b.pool.mediaWays.net[77.8.190.107]
Jan 13 10:46:10 mail postfix/smtpd[8295]: connect from 88-212-142-58.rdns.as8401.net[88.212.142.58]
Jan 13 10:46:11 mail postgrey[7628]: action=greylist, reason=new, client_name=88-212-142-58.rdns.as8401.net, client_address=88.212.142.58, sender=bolgcrobinson@jmchd.com, recipient=bolgcrobinson@jmchd.com
Jan 13 10:46:11 mail postfix/smtpd[8295]: NOQUEUE: reject: RCPT from 88-212-142-58.rdns.as8401.net[88.212.142.58]: 450 4.2.0 <bolgcrobinson@jmchd.com>: Recipient address rejected: Greylisted, see [http://postgrey.schweikert.ch/help/jmchd.com.html;](http://postgrey.schweikert.ch/help/jmchd.com.html;) from=<bolgcrobinson@jmchd.com> to=<bolgcrobinson@jmchd.com> proto=ESMTP helo=<[80.4.123.96]>
Jan 13 10:46:11 mail postfix/smtpd[8295]: disconnect from 88-212-142-58.rdns.as8401.net[88.212.142.58]
Jan 13 10:46:13 mail postfix/smtpd[8461]: connect from mxsb6.state.tn.us[170.143.36.97]
Jan 13 10:46:14 mail postgrey[7628]: action=pass, reason=client AWL, client_name=mxsb6.state.tn.us, client_address=170.143.36.97, sender=prvs=1987ce4124=susan.barber@tn.gov, recipient=kimtedford@jmchd.com
Jan 13 10:46:14 mail postfix/smtpd[8461]: 0F255122C074: client=mxsb6.state.tn.us[170.143.36.97]
Jan 13 10:46:14 mail postfix/cleanup[8649]: 0F255122C074: message-id=<4D2ED0DF.DCAE.0019.0@tn.gov>
Jan 13 10:46:14 mail postfix/qmgr[8157]: 0F255122C074: from=<prvs=1987ce4124=susan.barber@tn.gov>, size=2454, nrcpt=1 (queue active)
Jan 13 10:46:14 mail amavis[7883]: (07883-10) ESMTP::10024 /var/lib/amavis/tmp/amavis-20110113T103529-07883: <prvs=1987ce4124=susan.barber@tn.gov> -> <kimtedford@jmchd.com> SIZE=2454 Received: from mail.jmchd.com ([127.0.0.1]) by localhost (mail.jmchd.com [127.0.0.1]) (amavisd-new, port 10024) with ESMTP for <kimtedford@jmchd.com>; Thu, 13 Jan 2011 10:46:14 -0600 (CST)
Jan 13 10:46:14 mail amavis[7883]: (07883-10) Checking: I+2y17+w2cgS [170.143.36.97] <prvs=1987ce4124=susan.barber@tn.gov> -> <kimtedford@jmchd.com>
Jan 13 10:46:14 mail amavis[7883]: (07883-10) p003 1 Content-Type: multipart/alternative
Jan 13 10:46:14 mail amavis[7883]: (07883-10) p001 1/1 Content-Type: text/plain, size: 302 B, name:
Jan 13 10:46:14 mail amavis[7883]: (07883-10) p002 1/2 Content-Type: text/html, size: 705 B, name:
Jan 13 10:46:14 mail postfix/smtpd[8461]: disconnect from mxsb6.state.tn.us[170.143.36.97]
Jan 13 10:46:15 mail postfix/smtpd[8653]: connect from localhost.jmchd.com[127.0.0.1]
Jan 13 10:46:15 mail postfix/smtpd[8653]: 33F8A122C077: client=localhost.jmchd.com[127.0.0.1]
Jan 13 10:46:15 mail postfix/cleanup[8319]: 33F8A122C077: message-id=<4D2ED0DF.DCAE.0019.0@tn.gov>
Jan 13 10:46:15 mail postfix/smtpd[8653]: disconnect from localhost.jmchd.com[127.0.0.1]
Jan 13 10:46:15 mail postfix/qmgr[8157]: 33F8A122C077: from=<prvs=1987ce4124=susan.barber@tn.gov>, size=2906, nrcpt=1 (queue active)
Jan 13 10:46:15 mail amavis[7883]: (07883-10) FWD via SMTP: <prvs=1987ce4124=susan.barber@tn.gov> -> <kimtedford@jmchd.com>,BODY=7BIT 250 2.6.0 Ok, id=07883-10, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 33F8A122C077
Jan 13 10:46:15 mail amavis[7883]: (07883-10) Passed CLEAN, [170.143.36.97] [170.143.36.97] <prvs=1987ce4124=susan.barber@tn.gov> -> <kimtedford@jmchd.com>, Message-ID: <4D2ED0DF.DCAE.0019.0@tn.gov>, mail_id: I+2y17+w2cgS, Hits: 0.001, size: 2454, queued_as: 33F8A122C077, 1108 ms
Jan 13 10:46:15 mail postfix/smtp[8650]: 0F255122C074: to=<kimtedford@jmchd.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.5, delays=0.38/0/0/1.1, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 33F8A122C077)
Jan 13 10:46:15 mail postfix/qmgr[8157]: 0F255122C074: removed
Jan 13 10:46:15 mail amavis[7883]: (07883-10) TIMING [total 1112 ms] - SMTP greeting: 2 (0%)0, SMTP EHLO: 0 (0%)0, SMTP pre-MAIL: 1 (0%)0, SMTP pre-DATA-flush: 2 (0%)0, SMTP DATA: 36 (3%)4, check_init: 1 (0%)4, digest_hdr: 0 (0%)4, digest_body: 0 (0%)4, gen_mail_id: 1 (0%)4, mime_decode: 20 (2%)6, get-file-type2: 21 (2%)7, decompose_part: 1 (0%)8, parts_decode: 0 (0%)8, check_header: 2 (0%)8, AV-scan-1: 5 (0%)8, spam-wb-list: 2 (0%)8, SA parse: 3 (0%)9, SA check: 956 (86%)94, update_cache: 6 (1%)95, decide_mail_destiny: 1 (0%)95, fwd-connect: 4 (0%)95, fwd-mail-pip: 2 (0%)96, fwd-rcpt-pip: 0 (0%)96, fwd-data-chkpnt: 0 (0%)96, write-header: 1 (0%)96, fwd-data-contents: 0 (0%)96, fwd-end-chkpnt: 37 (3%)99, prepare-dsn: 1 (0%)99, main_log_entry: 8 (1%)100, update_snmp: 1 (0%)100, SMTP pre-response: 0 (0%)100, SMTP response: 0 (0%)100, unlink-2-files: 0 (0%)100, rundown: 0 (0%)100
Jan 13 10:46:15 mail postfix/smtp[8654]: 33F8A122C077: to=<kimtedford@jmchd.com>, relay=phobos.jmchd.com[192.168.1.85]:25, delay=0.11, delays=0.04/0/0/0.07, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 9062D230041)
Jan 13 10:46:15 mail postfix/qmgr[8157]: 33F8A122C077: removed
Jan 13 10:46:18 mail pop3d: Connection, ip=[::ffff:192.168.1.45]
Jan 13 10:46:18 mail pop3d: LOGIN, user=jkirk@jmchd.com, ip=[::ffff:192.168.1.45], port=[1245]
Jan 13 10:46:18 mail pop3d: LOGOUT, user=jkirk@jmchd.com, ip=[::ffff:192.168.1.45], port=[1245], top=0, retr=0, rcvd=12, sent=39, time=0
Jan 13 10:46:18 mail postfix/smtpd[8334]: warning: 96.9.137.173: hostname 969137173.hostnoc.net verification failed: Name or service not known
Jan 13 10:46:18 mail postfix/smtpd[8334]: connect from unknown[96.9.137.173]
Jan 13 10:46:19 mail postgrey[7628]: action=pass, reason=triplet found, client_name=unknown, client_address=96.9.137.173, sender=info@coyolpato.com, recipient=blewis@jmchd.com
Jan 13 10:46:19 mail postfix/smtpd[8334]: 853B6122C074: client=unknown[96.9.137.173]
Jan 13 10:46:19 mail postfix/cleanup[8649]: 853B6122C074: message-id=<5982345564620866215.1631475785.JavaMail.java@mail.coyolpato.com>
Jan 13 10:46:19 mail postfix/qmgr[8157]: 853B6122C074: from=<info@coyolpato.com>, size=4896, nrcpt=1 (queue active)
Jan 13 10:46:19 mail amavis[7876]: (07876-11) ESMTP::10024 /var/lib/amavis/tmp/amavis-20110113T103359-07876: <info@coyolpato.com> -> <blewis@jmchd.com> SIZE=4896 BODY=8BITMIME ENVID=360538 Received: from mail.jmchd.com ([127.0.0.1]) by localhost (mail.jmchd.com [127.0.0.1]) (amavisd-new, port 10024) with ESMTP for <blewis@jmchd.com>; Thu, 13 Jan 2011 10:46:19 -0600 (CST)
Jan 13 10:46:19 mail amavis[7876]: (07876-11) Checking: cZWpnqJr2b+m [96.9.137.173] <info@coyolpato.com> -> <blewis@jmchd.com>
Jan 13 10:46:19 mail postfix/smtpd[8334]: disconnect from unknown[96.9.137.173]
Jan 13 10:46:19 mail amavis[7876]: (07876-11) WARN: MIME::Parser error: part did not end with expected boundary
Jan 13 10:46:19 mail amavis[7876]: (07876-11) p003 1 Content-Type: multipart/alternative
Jan 13 10:46:19 mail amavis[7876]: (07876-11) p001 1/1 Content-Type: text/plain, size: 662 B, name:
Jan 13 10:46:19 mail amavis[7876]: (07876-11) p002 1/2 Content-Type: text/html, size: 2539 B, name:
Jan 13 10:46:20 mail amavis[7876]: (07876-11) local delivery: <info@coyolpato.com> -> <bad-header-quarantine>, mbx=/var/lib/amavis/virusmails/badh-cZWpnqJr2b+m
Jan 13 10:46:20 mail postfix/smtpd[8653]: connect from localhost.jmchd.com[127.0.0.1]
Jan 13 10:46:20 mail postfix/smtpd[8653]: AB2FA122C077: client=localhost.jmchd.com[127.0.0.1]
Jan 13 10:46:20 mail postfix/cleanup[8328]: AB2FA122C077: message-id=<5982345564620866215.1631475785.JavaMail.java@mail.coyolpato.com>
Jan 13 10:46:20 mail postfix/smtpd[8653]: disconnect from localhost.jmchd.com[127.0.0.1]
Jan 13 10:46:20 mail postfix/qmgr[8157]: AB2FA122C077: from=<info@coyolpato.com>, size=5463, nrcpt=1 (queue active)
Jan 13 10:46:20 mail amavis[7876]: (07876-11) FWD via SMTP: <info@coyolpato.com> -> <blewis@jmchd.com>,ENVID=360538 BODY=8BITMIME 250 2.6.0 Ok, id=07876-11, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as AB2FA122C077
Jan 13 10:46:20 mail amavis[7876]: (07876-11) Passed BAD-HEADER, [96.9.137.173] [96.9.137.173] <info@coyolpato.com> -> <blewis@jmchd.com>, quarantine: badh-cZWpnqJr2b+m, Message-ID: <5982345564620866215.1631475785.JavaMail.java@mail.coyolpato.com>, mail_id: cZWpnqJr2b+m, Hits: 1.619, size: 4893, queued_as: AB2FA122C077, 1100 ms
Jan 13 10:46:20 mail postfix/smtp[8650]: 853B6122C074: to=<blewis@jmchd.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.8, delays=0.68/0/0/1.1, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as AB2FA122C077)
Jan 13 10:46:20 mail postfix/qmgr[8157]: 853B6122C074: removed
Jan 13 10:46:20 mail amavis[7876]: (07876-11) TIMING [total 1104 ms] - SMTP greeting: 2 (0%)0, SMTP EHLO: 0 (0%)0, SMTP pre-MAIL: 1 (0%)0, SMTP pre-DATA-flush: 2 (0%)0, SMTP DATA: 37 (3%)4, check_init: 1 (0%)4, digest_hdr: 0 (0%)4, digest_body: 0 (0%)4, gen_mail_id: 1 (0%)4, mime_decode: 17 (2%)6, get-file-type2: 32 (3%)8, decompose_part: 1 (0%)9, decompose_part: 1 (0%)9, parts_decode: 0 (0%)9, check_header: 2 (0%)9, AV-scan-1: 11 (1%)10, spam-wb-list: 2 (0%)10, SA parse: 4 (0%)10, SA check: 924 (84%)94, update_cache: 6 (1%)95, decide_mail_destiny: 1 (0%)95, open-mbx: 19 (2%)96, write-header: 1 (0%)96, save-to-local-mailbox: 0 (0%)96, fwd-connect: 4 (0%)97, fwd-mail-pip: 2 (0%)97, fwd-rcpt-pip: 0 (0%)97, fwd-data-chkpnt: 0 (0%)97, write-header: 1 (0%)97, fwd-data-contents: 0 (0%)97, fwd-end-chkpnt: 21 (2%)99, prepare-dsn: 1 (0%)99, main_log_entry: 7 (1%)100, update_snmp: 2 (0%)100, SMTP pre-response: 0 (0%)100, SMTP response: 0 (0%)100, unlink-3-files: 0 (0%)100, rundown: 0 (0%)100
Jan 13 10:46:20 mail postfix/virtual[8323]: AB2FA122C077: to=<blewis@jmchd.com>, relay=virtual, delay=0.06, delays=0.02/0/0/0.03, dsn=2.0.0, status=sent (delivered to maildir)
Jan 13 10:46:20 mail postfix/qmgr[8157]: AB2FA122C077: removed

---

### Post by ITDude on 2011-01-13
> **HermanAB said:**
> Howdy,

What kind of GUI?  Do you have local access to the machine?

Open a console and run ps to see what is running:
$ sudo ps -e

Look for something resembling a MTA such as postfix or qmail or whatever, then visit the MTA project web site and read a bit to figure out how to debug it - where are the mail queues - how can you flush them etc.


There is no GUI on the server. I was referring to my limited knowldge of command lines because I am spoiled because of GUI's. lol... :) 

I have been flushing the mail queues when they grow so big but the server will still stop functioning after an hour or so of uptime. :(

---

