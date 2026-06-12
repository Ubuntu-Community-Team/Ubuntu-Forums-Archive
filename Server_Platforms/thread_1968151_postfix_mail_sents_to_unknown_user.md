---
title: "postfix mail sents to unknown user"
date: 2012-04-28
forum: Server Platforms
---

### Post by duceduc on 2012-04-28
I have recently checked my mail log and found a lot of these entries that sends to 'root@ducsu.com'. I checked my users table in my db and I do not see any users with 'root@ducsu.com'. I used flurdy's guide to setup my mail server.

> 
Apr 29 10:00:03 revomix postfix/pickup[7051]: 1871C840D05: uid=0 from=<root>
Apr 29 10:00:03 revomix postfix/cleanup[7346]: 1871C840D05: message-id=<20120429010003.1871C840D05@mail.ducsu.com>
Apr 29 10:00:03 revomix postfix/qmgr[2094]: 1871C840D05: from=<root@ducsu.com>, size=1296, nrcpt=1 (queue active)
Apr 29 10:00:03 revomix postfix/pickup[7051]: 6777A840B98: uid=0 from=<root>
Apr 29 10:00:03 revomix postfix/cleanup[7346]: 6777A840B98: message-id=<20120429010003.6777A840B98@mail.ducsu.com>
Apr 29 10:00:03 revomix postfix/qmgr[2094]: 6777A840B98: from=<root@ducsu.com>, size=1297, nrcpt=1 (queue active)
Apr 29 10:00:03 revomix postfix/pickup[7051]: 8833F840A65: uid=0 from=<root>
Apr 29 10:00:03 revomix postfix/cleanup[7346]: 8833F840A65: message-id=<20120429010003.8833F840A65@mail.ducsu.com>
Apr 29 10:00:03 revomix postfix/qmgr[2094]: 8833F840A65: from=<root@ducsu.com>, size=1313, nrcpt=1 (queue active)
Apr 29 10:00:03 revomix postfix/pickup[7051]: A0D9B840B77: uid=0 from=<root>
Apr 29 10:00:03 revomix postfix/cleanup[7346]: A0D9B840B77: message-id=<20120429010003.A0D9B840B77@mail.ducsu.com>
Apr 29 10:00:03 revomix postfix/qmgr[2094]: A0D9B840B77: from=<root@ducsu.com>, size=1261, nrcpt=1 (queue active)
Apr 29 10:00:03 revomix postfix/pickup[7051]: B75C1840B78: uid=0 from=<root>
Apr 29 10:00:03 revomix postfix/cleanup[7351]: B75C1840B78: message-id=<20120429010003.B75C1840B78@mail.ducsu.com>
Apr 29 10:00:03 revomix postfix/qmgr[2094]: B75C1840B78: from=<root@ducsu.com>, size=1277, nrcpt=1 (queue active)
Apr 29 10:00:03 revomix postfix/pickup[7051]: D815A840AF5: uid=0 from=<root>
Apr 29 10:00:03 revomix postfix/cleanup[7346]: D815A840AF5: message-id=<20120429010003.D815A840AF5@mail.ducsu.com>
Apr 29 10:00:03 revomix postfix/qmgr[2094]: D815A840AF5: from=<root@ducsu.com>, size=1281, nrcpt=1 (queue active)
Apr 29 10:00:03 revomix postfix/pickup[7051]: F09F6840BF4: uid=0 from=<root>
Apr 29 10:00:03 revomix postfix/cleanup[7351]: F09F6840BF4: message-id=<20120429010003.F09F6840BF4@mail.ducsu.com>
Apr 29 10:00:04 revomix postfix/qmgr[2094]: F09F6840BF4: from=<root@ducsu.com>, size=1313, nrcpt=1 (queue active)
Apr 29 10:00:08 revomix postfix/smtpd[7352]: connect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:08 revomix postfix/smtpd[7352]: 8D156840BF7: client=localhost.localdomain[127.0.0.1]
Apr 29 10:00:08 revomix postfix/cleanup[7346]: 8D156840BF7: message-id=<20120429010003.1871C840D05@mail.ducsu.com>
Apr 29 10:00:08 revomix postfix/qmgr[2094]: 8D156840BF7: from=<root@ducsu.com>, size=1893, nrcpt=1 (queue active)
Apr 29 10:00:08 revomix postfix/smtpd[7352]: disconnect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:08 revomix amavis[4541]: (04541-11) Passed CLEAN, <root@ducsu.com> -> <root@ducsu.com>, Message-ID: <20120429010003.1871C840D05@mail.ducsu.com>, mail_id: BbxgYlXTYB9r, Hits: -1.901, size: 1293, queued_as: 8D156840BF7, 5259 ms
Apr 29 10:00:08 revomix postfix/smtp[7348]: 1871C840D05: to=<root@ducsu.com>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10024, delay=5.6, delays=0.34/0.01/0/5.3, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 8D156840BF7)
Apr 29 10:00:08 revomix postfix/qmgr[2094]: 1871C840D05: removed
Apr 29 10:00:08 revomix postfix/virtual[7353]: 8D156840BF7: to=<root@ducsu.com>, relay=virtual, delay=0.22, delays=0.11/0/0/0.1, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:08 revomix postfix/cleanup[7351]: C1C71840D0F: message-id=<20120429010008.C1C71840D0F@mail.ducsu.com>
Apr 29 10:00:08 revomix postfix/bounce[7355]: 8D156840BF7: sender non-delivery notification: C1C71840D0F
Apr 29 10:00:08 revomix postfix/qmgr[2094]: C1C71840D0F: from=<>, size=3690, nrcpt=1 (queue active)
Apr 29 10:00:08 revomix postfix/qmgr[2094]: 8D156840BF7: removed
Apr 29 10:00:11 revomix postfix/virtual[7353]: C1C71840D0F: to=<root@ducsu.com>, relay=virtual, delay=3.1, delays=0.07/3/0/0.08, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:11 revomix postfix/qmgr[2094]: C1C71840D0F: removed
Apr 29 10:00:14 revomix postfix/smtpd[7352]: connect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:14 revomix postfix/smtpd[7352]: F3FCA840BF7: client=localhost.localdomain[127.0.0.1]
Apr 29 10:00:14 revomix postfix/cleanup[7346]: F3FCA840BF7: message-id=<20120429010003.6777A840B98@mail.ducsu.com>
Apr 29 10:00:15 revomix postfix/smtpd[7352]: disconnect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:15 revomix postfix/qmgr[2094]: F3FCA840BF7: from=<root@ducsu.com>, size=1894, nrcpt=1 (queue active)
Apr 29 10:00:15 revomix amavis[4543]: (04543-11) Passed CLEAN, <root@ducsu.com> -> <root@ducsu.com>, Message-ID: <20120429010003.6777A840B98@mail.ducsu.com>, mail_id: BGqF66ZDQxqd, Hits: -1.901, size: 1294, queued_as: F3FCA840BF7, 3208 ms
Apr 29 10:00:15 revomix postfix/smtp[7348]: 6777A840B98: to=<root@ducsu.com>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10024, delay=12, delays=0.74/8.3/0/3.2, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as F3FCA840BF7)
Apr 29 10:00:15 revomix postfix/qmgr[2094]: 6777A840B98: removed
Apr 29 10:00:15 revomix postfix/virtual[7353]: F3FCA840BF7: to=<root@ducsu.com>, relay=virtual, delay=0.14, delays=0.07/0/0/0.07, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:15 revomix postfix/cleanup[7351]: 21353840B98: message-id=<20120429010015.21353840B98@mail.ducsu.com>
Apr 29 10:00:15 revomix postfix/bounce[7355]: F3FCA840BF7: sender non-delivery notification: 21353840B98
Apr 29 10:00:15 revomix postfix/qmgr[2094]: 21353840B98: from=<>, size=3691, nrcpt=1 (queue active)
Apr 29 10:00:15 revomix postfix/qmgr[2094]: F3FCA840BF7: removed
Apr 29 10:00:18 revomix postfix/virtual[7353]: 21353840B98: to=<root@ducsu.com>, relay=virtual, delay=3.1, delays=0.07/3/0/0.08, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:18 revomix postfix/qmgr[2094]: 21353840B98: removed
Apr 29 10:00:21 revomix postfix/smtpd[7352]: connect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:21 revomix postfix/smtpd[7352]: 2FCA7840B98: client=localhost.localdomain[127.0.0.1]
Apr 29 10:00:21 revomix postfix/cleanup[7346]: 2FCA7840B98: message-id=<20120429010003.8833F840A65@mail.ducsu.com>
Apr 29 10:00:21 revomix postfix/smtpd[7352]: disconnect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:21 revomix postfix/qmgr[2094]: 2FCA7840B98: from=<root@ducsu.com>, size=1910, nrcpt=1 (queue active)
Apr 29 10:00:21 revomix amavis[4541]: (04541-12) Passed CLEAN, <root@ducsu.com> -> <root@ducsu.com>, Message-ID: <20120429010003.8833F840A65@mail.ducsu.com>, mail_id: Wki-5Yt+o5OK, Hits: -1.901, size: 1310, queued_as: 2FCA7840B98, 3074 ms
Apr 29 10:00:21 revomix postfix/smtp[7348]: 8833F840A65: to=<root@ducsu.com>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10024, delay=18, delays=0.8/15/0/3.1, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 2FCA7840B98)
Apr 29 10:00:21 revomix postfix/qmgr[2094]: 8833F840A65: removed
Apr 29 10:00:21 revomix postfix/virtual[7353]: 2FCA7840B98: to=<root@ducsu.com>, relay=virtual, delay=0.14, delays=0.08/0/0/0.06, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:21 revomix postfix/cleanup[7351]: 523CC840A65: message-id=<20120429010021.523CC840A65@mail.ducsu.com>
Apr 29 10:00:21 revomix postfix/bounce[7355]: 2FCA7840B98: sender non-delivery notification: 523CC840A65
Apr 29 10:00:21 revomix postfix/qmgr[2094]: 523CC840A65: from=<>, size=3707, nrcpt=1 (queue active)
Apr 29 10:00:21 revomix postfix/qmgr[2094]: 2FCA7840B98: removed
Apr 29 10:00:24 revomix postfix/virtual[7353]: 523CC840A65: to=<root@ducsu.com>, relay=virtual, delay=3.1, delays=0.07/3/0/0.07, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:24 revomix postfix/qmgr[2094]: 523CC840A65: removed
Apr 29 10:00:27 revomix postfix/smtpd[7352]: connect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:27 revomix postfix/smtpd[7352]: 79B5D840A65: client=localhost.localdomain[127.0.0.1]
Apr 29 10:00:27 revomix postfix/cleanup[7346]: 79B5D840A65: message-id=<20120429010003.A0D9B840B77@mail.ducsu.com>
Apr 29 10:00:27 revomix postfix/qmgr[2094]: 79B5D840A65: from=<root@ducsu.com>, size=1858, nrcpt=1 (queue active)
Apr 29 10:00:27 revomix postfix/smtpd[7352]: disconnect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:27 revomix amavis[4543]: (04543-12) Passed CLEAN, <root@ducsu.com> -> <root@ducsu.com>, Message-ID: <20120429010003.A0D9B840B77@mail.ducsu.com>, mail_id: z-4oIEwnY2dv, Hits: -1.901, size: 1258, queued_as: 79B5D840A65, 3192 ms
Apr 29 10:00:27 revomix postfix/smtp[7348]: A0D9B840B77: to=<root@ducsu.com>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10024, delay=25, delays=0.83/21/0/3.2, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 79B5D840A65)
Apr 29 10:00:27 revomix postfix/qmgr[2094]: A0D9B840B77: removed
Apr 29 10:00:27 revomix postfix/virtual[7353]: 79B5D840A65: to=<root@ducsu.com>, relay=virtual, delay=0.16, delays=0.1/0/0/0.07, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:27 revomix postfix/cleanup[7351]: A164F840B77: message-id=<20120429010027.A164F840B77@mail.ducsu.com>
Apr 29 10:00:27 revomix postfix/bounce[7355]: 79B5D840A65: sender non-delivery notification: A164F840B77
Apr 29 10:00:27 revomix postfix/qmgr[2094]: A164F840B77: from=<>, size=3655, nrcpt=1 (queue active)
Apr 29 10:00:27 revomix postfix/qmgr[2094]: 79B5D840A65: removed
Apr 29 10:00:31 revomix postfix/virtual[7353]: A164F840B77: to=<root@ducsu.com>, relay=virtual, delay=3.8, delays=0.07/3/0/0.75, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:31 revomix postfix/qmgr[2094]: A164F840B77: removed
Apr 29 10:00:33 revomix postfix/smtpd[7352]: connect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:33 revomix postfix/smtpd[7352]: CAFC9840A65: client=localhost.localdomain[127.0.0.1]
Apr 29 10:00:33 revomix postfix/cleanup[7346]: CAFC9840A65: message-id=<20120429010003.B75C1840B78@mail.ducsu.com>
Apr 29 10:00:33 revomix postfix/smtpd[7352]: disconnect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:33 revomix postfix/qmgr[2094]: CAFC9840A65: from=<root@ducsu.com>, size=1874, nrcpt=1 (queue active)
Apr 29 10:00:33 revomix amavis[4541]: (04541-13) Passed CLEAN, <root@ducsu.com> -> <root@ducsu.com>, Message-ID: <20120429010003.B75C1840B78@mail.ducsu.com>, mail_id: kVdsCLPnTPwR, Hits: -1.901, size: 1274, queued_as: CAFC9840A65, 3184 ms
Apr 29 10:00:33 revomix postfix/smtp[7348]: B75C1840B78: to=<root@ducsu.com>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10024, delay=31, delays=1/27/0/3.2, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as CAFC9840A65)
Apr 29 10:00:33 revomix postfix/qmgr[2094]: B75C1840B78: removed
Apr 29 10:00:34 revomix postfix/virtual[7353]: CAFC9840A65: to=<root@ducsu.com>, relay=virtual, delay=1.2, delays=0.08/1/0/0.07, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:34 revomix postfix/cleanup[7351]: F0EDD840B78: message-id=<20120429010034.F0EDD840B78@mail.ducsu.com>
Apr 29 10:00:35 revomix postfix/bounce[7355]: CAFC9840A65: sender non-delivery notification: F0EDD840B78
Apr 29 10:00:35 revomix postfix/qmgr[2094]: F0EDD840B78: from=<>, size=3671, nrcpt=1 (queue active)
Apr 29 10:00:35 revomix postfix/qmgr[2094]: CAFC9840A65: removed
Apr 29 10:00:37 revomix postfix/virtual[7353]: F0EDD840B78: to=<root@ducsu.com>, relay=virtual, delay=2.2, delays=0.07/2/0/0.08, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:37 revomix postfix/qmgr[2094]: F0EDD840B78: removed
Apr 29 10:00:39 revomix postfix/smtpd[7352]: connect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:39 revomix postfix/smtpd[7352]: 2B960840A65: client=localhost.localdomain[127.0.0.1]
Apr 29 10:00:39 revomix postfix/cleanup[7346]: 2B960840A65: message-id=<20120429010003.D815A840AF5@mail.ducsu.com>
Apr 29 10:00:39 revomix postfix/smtpd[7352]: disconnect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:39 revomix postfix/qmgr[2094]: 2B960840A65: from=<root@ducsu.com>, size=1878, nrcpt=1 (queue active)
Apr 29 10:00:39 revomix amavis[4543]: (04543-13) Passed CLEAN, <root@ducsu.com> -> <root@ducsu.com>, Message-ID: <20120429010003.D815A840AF5@mail.ducsu.com>, mail_id: xAtmbU0RpZz0, Hits: -1.901, size: 1278, queued_as: 2B960840A65, 3270 ms
Apr 29 10:00:39 revomix postfix/smtp[7348]: D815A840AF5: to=<root@ducsu.com>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10024, delay=36, delays=0.89/32/0/3.3, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 2B960840A65)
Apr 29 10:00:39 revomix postfix/qmgr[2094]: D815A840AF5: removed
Apr 29 10:00:40 revomix postfix/virtual[7353]: 2B960840A65: to=<root@ducsu.com>, relay=virtual, delay=1.3, delays=0.14/1/0/0.15, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:40 revomix postfix/cleanup[7351]: 7518A840B78: message-id=<20120429010040.7518A840B78@mail.ducsu.com>
Apr 29 10:00:40 revomix postfix/bounce[7355]: 2B960840A65: sender non-delivery notification: 7518A840B78
Apr 29 10:00:40 revomix postfix/qmgr[2094]: 7518A840B78: from=<>, size=3675, nrcpt=1 (queue active)
Apr 29 10:00:40 revomix postfix/qmgr[2094]: 2B960840A65: removed
Apr 29 10:00:43 revomix postfix/virtual[7353]: 7518A840B78: to=<root@ducsu.com>, relay=virtual, delay=3.3, delays=0.13/3/0/0.14, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:43 revomix postfix/qmgr[2094]: 7518A840B78: removed
Apr 29 10:00:47 revomix postfix/smtpd[7352]: connect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:47 revomix postfix/smtpd[7352]: 48A7F840A65: client=localhost.localdomain[127.0.0.1]
Apr 29 10:00:47 revomix postfix/cleanup[7346]: 48A7F840A65: message-id=<20120429010003.F09F6840BF4@mail.ducsu.com>
Apr 29 10:00:47 revomix postfix/smtpd[7352]: disconnect from localhost.localdomain[127.0.0.1]
Apr 29 10:00:47 revomix postfix/qmgr[2094]: 48A7F840A65: from=<root@ducsu.com>, size=1910, nrcpt=1 (queue active)
Apr 29 10:00:47 revomix amavis[4541]: (04541-14) Passed CLEAN, <root@ducsu.com> -> <root@ducsu.com>, Message-ID: <20120429010003.F09F6840BF4@mail.ducsu.com>, mail_id: EzHhUvTk8KZj, Hits: -1.901, size: 1310, queued_as: 48A7F840A65, 4826 ms
Apr 29 10:00:47 revomix postfix/smtp[7348]: F09F6840BF4: to=<root@ducsu.com>, orig_to=<root>, relay=127.0.0.1[127.0.0.1]:10024, delay=44, delays=0.98/39/0/4.8, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 48A7F840A65)
Apr 29 10:00:47 revomix postfix/qmgr[2094]: F09F6840BF4: removed
Apr 29 10:00:47 revomix postfix/virtual[7353]: 48A7F840A65: to=<root@ducsu.com>, relay=virtual, delay=0.27, delays=0.14/0/0/0.13, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:47 revomix postfix/cleanup[7351]: 8B66E840B78: message-id=<20120429010047.8B66E840B78@mail.ducsu.com>
Apr 29 10:00:47 revomix postfix/bounce[7355]: 48A7F840A65: sender non-delivery notification: 8B66E840B78
Apr 29 10:00:47 revomix postfix/qmgr[2094]: 8B66E840B78: from=<>, size=3707, nrcpt=1 (queue active)
Apr 29 10:00:47 revomix postfix/qmgr[2094]: 48A7F840A65: removed
Apr 29 10:00:50 revomix postfix/virtual[7353]: 8B66E840B78: to=<root@ducsu.com>, relay=virtual, delay=3.2, delays=0.09/3/0/0.1, dsn=5.1.1, status=bounced (unknown user: "root@ducsu.com")
Apr 29 10:00:50 revomix postfix/qmgr[2094]: 8B66E840B78: removed



---

### Post by duceduc on 2012-04-29
I've found out why I was getting this message. I use zerigo for dns service. Thus, their dynamic updates for changes in public ip uses a cronjob setup as wget. I have 7 of these setup to run every 30 mins. When this happens, my server throws this [email]root@domain.com[/email] message out. I may have tamed it down by not having all seven to ping at once but in 1 min interval. It seems to be working. I wish I could figure out why the message. The cronjob is setup as so.
> 
*/30 * * * * /usr/bin/wget -q 'http://domain.com/at/some/other/link'


---

### Post by SeijiSensei on 2012-04-29
If a command that runs as root from cron generates output, and that output isn't piped to a file, it will be mailed to the local root account.

You can stop this from happening by adding "> /dev/null 2>&1" to the end of the wget command.  That will send any output appearing on the "sysout" device to the null device; the "2>&1" part sends errors destined for the syserr device, represented by "2" in this case, to sysout, represented as "&1", which, in turn, sends it to /dev/null. It's the equivalent of "> /dev/null 2> /dev/null".

---

### Post by duceduc on 2012-04-29
Thank you for the reply. My next question is how can I fix my local root mail going to a valid root account?

---

### Post by SeijiSensei on 2012-04-29
Is the machine running Postfix or sendmail?  You need to have a "Mail Transfer Agent" like these to handle delivery.  See this guide for details: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by CharlesA on 2012-04-29
> **duceduc said:**
> Thank you for the reply. My next question is how can I fix my local root mail going to a valid root account?
You should be able to place a file named .forward in /root/ with the email address you want mail forwarded to.

[http://www.feep.net/sendmail/tutorial/intro/forward.html](http://www.feep.net/sendmail/tutorial/intro/forward.html)
[http://www.postfix.org/local.8.html](http://www.postfix.org/local.8.html)

EDIT: Maybe I got ahead of myself, thanks Seiji

---

### Post by SeijiSensei on 2012-04-29
> **CharlesA said:**
> EDIT: Maybe I got ahead of myself, thanks Seiji

Actually, no. I didn't look at the log he posted carefully enough.  He clearly has Postfix installed, but the log shows bounces to the root account.  It looks more like he hasn't configured Postfix to accept mail for the ducsu.com domain.

@duceduc
Is this the machine called mail.ducsu.com for which you have an MX record?  If so, look at the Postfix guide to determine how to have it accept mail for the ducsu.com domain.  

If this isn't the mail.ducsu.com host, then maybe there's a problem with sending mail out with SMTP.  Try "telnet mail.ducsu.com 25" and make sure you can connect to that machine.  If you can't, your ISP may be blocking outbound connections to remote servers on port 25.

I get this result when I try to send mail to [email]root@ducsu.com[/email]:

```

[seiji@mail ~]$ telnet mail.ducsu.com 25
Trying 114.158.22.69...
Connected to mail.ducsu.com.
Escape character is '^]'.
220 mail.ducsu.com
ehlo mail.mydomain.com
250-mail.ducsu.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: test@example.com
250 2.1.0 Ok
rcpt to: root@ducsu.com
450 4.2.0 <root@ducsu.com>: Recipient address rejected: The email address will be queue for 180sec.
quit
221 2.0.0 Bye
Connection closed by foreign host.

```

---

### Post by duceduc on 2012-04-30
seifisensei,

I used flurdy guide to setup the mail server, thus, it is postfix. The address rejected message when you telnet is possibly coming from postgrey. It sends new email address to queue before sending to destination. I am getting the same message when I telnet to different addresses. 

mail.ducsu.com is a mx record on the same host. I am not sure what to look for to have postfix accepts mail for ducsu.com with the link you provided. Comparing the main.cf example with mine, 'mydestination=' is left blank. Should I have input that root address in there? Also, [email]root@ducsu.com[/email] doesn't exist in my 'maildb' database. Is this the cause of the error 'unknown user'?

I may not have been making sense since I am not too familiar with setting up a mail server. Revisiting [flurdy's guide](http://flurdy.com/docs/postfix/#config-simple-mta), I noticed I may have over looked the alias section. In my aliases file, it reads:

> 
postmaster: root


Do I need to add more to this?

---

### Post by SeijiSensei on 2012-04-30
I don't use Postfix; I run sendmail instead. I recommend reading [http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination](http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination) for details.  It looks like setting 

```
mydomain=ducsu.com
``` 

and adding "$mydomain" to the end of mydestination might do the trick.

I'd disable postgrey until you have finished testing and have everything working properly.

---

