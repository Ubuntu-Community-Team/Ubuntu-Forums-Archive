---
title: "need Postfix help"
date: 2009-11-01
forum: Server Platforms
---

### Post by prokaryot on 2009-11-01
Hi,

I have a web site in a VPS server, and I wanted to use mailman for maillists.

so I installed postfix for it, and configured it. I can subscribe to the lists, but can't send mails to the lists' users.

Here is my /var/log/mail.log

```

Nov  2 01:50:54 GleSYS-vps postfix/postfix-script[1898]: starting the Postfix mail system
Nov  2 01:50:54 GleSYS-vps postfix/master[1899]: daemon started -- version 2.5.5, configuration /etc/postfix
Nov  2 01:51:09 GleSYS-vps postfix/master[1899]: reload configuration /etc/postfix
Nov  2 01:51:52 GleSYS-vps postfix/smtpd[17439]: connect from pcnet-web1.doganburda.com.tr[213.243.60.66]
Nov  2 01:51:55 GleSYS-vps postfix/smtpd[17439]: NOQUEUE: reject: RCPT from pcnet-web1.doganburda.com.tr[213.243.60.66]: 550 5.1.1 <admin@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<www@pcnet-web1.doganburda.com.tr> to=<admin@ozgur-yazilimcilar.org> proto=ESMTP helo=<pcnet-web1.doganburda.com.tr>
Nov  2 01:56:56 GleSYS-vps postfix/smtpd[17439]: timeout after RSET from pcnet-web1.doganburda.com.tr[213.243.60.66]
Nov  2 01:56:56 GleSYS-vps postfix/smtpd[17439]: disconnect from pcnet-web1.doganburda.com.tr[213.243.60.66]
Nov  2 02:00:16 GleSYS-vps postfix/anvil[17890]: statistics: max connection rate 1/60s for (smtp:213.243.60.66) at Nov  2 01:51:52
Nov  2 02:00:16 GleSYS-vps postfix/anvil[17890]: statistics: max connection count 1 for (smtp:213.243.60.66) at Nov  2 01:51:52
Nov  2 02:00:16 GleSYS-vps postfix/anvil[17890]: statistics: max cache size 1 at Nov  2 01:51:52
Nov  2 02:05:38 GleSYS-vps postfix/smtpd[5236]: connect from ey-out-2122.google.com[74.125.78.26]
Nov  2 02:05:38 GleSYS-vps postfix/smtpd[5236]: NOQUEUE: reject: RCPT from ey-out-2122.google.com[74.125.78.26]: 550 5.1.1 <mailman@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<mailman@ozgur-yazilimcilar.org> proto=ESMTP helo=<ey-out-2122.google.com>
Nov  2 02:05:38 GleSYS-vps postfix/smtpd[5236]: disconnect from ey-out-2122.google.com[74.125.78.26]
Nov  2 02:08:58 GleSYS-vps postfix/anvil[5238]: statistics: max connection rate 1/60s for (smtp:74.125.78.26) at Nov  2 02:05:38
Nov  2 02:08:58 GleSYS-vps postfix/anvil[5238]: statistics: max connection count 1 for (smtp:74.125.78.26) at Nov  2 02:05:38
Nov  2 02:08:58 GleSYS-vps postfix/anvil[5238]: statistics: max cache size 1 at Nov  2 02:05:38
Nov  2 02:22:13 GleSYS-vps postfix/smtpd[5341]: connect from localhost.localdomain[127.0.0.1]
Nov  2 02:22:13 GleSYS-vps postfix/smtpd[5341]: 7197265943AD: client=localhost.localdomain[127.0.0.1]
Nov  2 02:22:13 GleSYS-vps postfix/cleanup[5345]: 7197265943AD: message-id=<mailman.0.1257116260.23970.mailman@ozgur-yazilimcilar.org>
Nov  2 02:22:13 GleSYS-vps postfix/qmgr[5903]: 7197265943AD: from=<mailman-bounces@ozgur-yazilimcilar.org>, size=2193, nrcpt=1 (queue active)
Nov  2 02:22:13 GleSYS-vps postfix/smtpd[5341]: disconnect from localhost.localdomain[127.0.0.1]
Nov  2 02:22:13 GleSYS-vps postfix/smtpd[5341]: connect from localhost.localdomain[127.0.0.1]
Nov  2 02:22:13 GleSYS-vps postfix/smtpd[5341]: 7FE1D65943AA: client=localhost.localdomain[127.0.0.1]
Nov  2 02:22:13 GleSYS-vps postfix/cleanup[5345]: 7FE1D65943AA: message-id=<mailman.0.1257116393.32348.mailman@ozgur-yazilimcilar.org>
Nov  2 02:22:13 GleSYS-vps postfix/qmgr[5903]: 7FE1D65943AA: from=<mailman-bounces@ozgur-yazilimcilar.org>, size=1984, nrcpt=1 (queue active)
Nov  2 02:22:13 GleSYS-vps postfix/smtpd[5341]: disconnect from localhost.localdomain[127.0.0.1]
Nov  2 02:22:14 GleSYS-vps postfix/smtp[5353]: 7197265943AD: to=<baris.aydek@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.218.34]:25, delay=1.1, delays=0.2/0/0.21/0.7, dsn=2.0.0, status=sent (250 2.0.0 OK 1257117734 22si12456341bwz.5)
Nov  2 02:22:14 GleSYS-vps postfix/qmgr[5903]: 7197265943AD: removed
Nov  2 02:22:15 GleSYS-vps postfix/smtp[5357]: 7FE1D65943AA: to=<bushimtrak@yahoo.com>, relay=c.mx.mail.yahoo.com[68.142.202.247]:25, delay=1.5, delays=0/0.01/0.73/0.79, dsn=2.0.0, status=sent (250 ok dirdel)
Nov  2 02:22:15 GleSYS-vps postfix/qmgr[5903]: 7FE1D65943AA: removed
Nov  2 02:23:06 GleSYS-vps postfix/smtpd[5341]: connect from localhost.localdomain[127.0.0.1]
Nov  2 02:23:06 GleSYS-vps postfix/smtpd[5341]: F1C7A65943A0: client=localhost.localdomain[127.0.0.1]
Nov  2 02:23:06 GleSYS-vps postfix/cleanup[5345]: F1C7A65943A0: message-id=<mailman.0.1257117786.15865.mailman@ozgur-yazilimcilar.org>
Nov  2 02:23:06 GleSYS-vps postfix/qmgr[5903]: F1C7A65943A0: from=<mailman-bounces@ozgur-yazilimcilar.org>, size=2060, nrcpt=1 (queue active)
Nov  2 02:23:06 GleSYS-vps postfix/smtpd[5341]: disconnect from localhost.localdomain[127.0.0.1]
Nov  2 02:23:08 GleSYS-vps postfix/smtp[5353]: F1C7A65943A0: to=<bushimtrak@yahoo.com>, relay=c.mx.mail.yahoo.com[68.142.202.247]:25, delay=1.1, delays=0.01/0/0.6/0.54, dsn=2.0.0, status=sent (250 ok dirdel)
Nov  2 02:23:08 GleSYS-vps postfix/qmgr[5903]: F1C7A65943A0: removed
Nov  2 02:23:48 GleSYS-vps postfix/smtpd[5341]: connect from web43504.mail.sp1.yahoo.com[68.180.198.203]
Nov  2 02:23:48 GleSYS-vps postfix/smtpd[5341]: NOQUEUE: reject: RCPT from web43504.mail.sp1.yahoo.com[68.180.198.203]: 550 5.1.1 <mailman@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<bushimtrak@yahoo.com> to=<mailman@ozgur-yazilimcilar.org> proto=SMTP helo=<web43504.mail.sp1.yahoo.com>
Nov  2 02:23:48 GleSYS-vps postfix/smtpd[5341]: disconnect from web43504.mail.sp1.yahoo.com[68.180.198.203]
Nov  2 02:25:54 GleSYS-vps postfix/smtpd[19779]: connect from localhost.localdomain[127.0.0.1]
Nov  2 02:25:54 GleSYS-vps postfix/smtpd[19779]: 0ABE1659439E: client=localhost.localdomain[127.0.0.1]
Nov  2 02:25:54 GleSYS-vps postfix/cleanup[19782]: 0ABE1659439E: message-id=<mailman.0.1257117952.18394.mailman@ozgur-yazilimcilar.org>
Nov  2 02:25:54 GleSYS-vps postfix/qmgr[5903]: 0ABE1659439E: from=<mailman-bounces@ozgur-yazilimcilar.org>, size=1987, nrcpt=1 (queue active)
Nov  2 02:25:54 GleSYS-vps postfix/smtpd[19779]: disconnect from localhost.localdomain[127.0.0.1]
Nov  2 02:25:55 GleSYS-vps postfix/smtp[19795]: 0ABE1659439E: to=<baris.aydek@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.218.35]:25, delay=1.1, delays=0.43/0/0.2/0.51, dsn=2.0.0, status=sent (250 2.0.0 OK 1257117955 23si11743138bwz.69)
Nov  2 02:25:55 GleSYS-vps postfix/qmgr[5903]: 0ABE1659439E: removed
Nov  2 02:26:20 GleSYS-vps postfix/smtpd[19779]: connect from localhost.localdomain[127.0.0.1]
Nov  2 02:26:20 GleSYS-vps postfix/smtpd[19779]: 73AA565943A0: client=localhost.localdomain[127.0.0.1]
Nov  2 02:26:20 GleSYS-vps postfix/cleanup[19782]: 73AA565943A0: message-id=<mailman.0.1257117979.24401.mailman@ozgur-yazilimcilar.org>
Nov  2 02:26:20 GleSYS-vps postfix/qmgr[5903]: 73AA565943A0: from=<mailman-bounces@ozgur-yazilimcilar.org>, size=2063, nrcpt=1 (queue active)
Nov  2 02:26:20 GleSYS-vps postfix/smtpd[19779]: disconnect from localhost.localdomain[127.0.0.1]
Nov  2 02:26:20 GleSYS-vps postfix/smtp[19795]: 73AA565943A0: to=<baris.aydek@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.218.35]:25, delay=0.34, delays=0.01/0/0.18/0.15, dsn=2.0.0, status=sent (250 2.0.0 OK 1257117980 23si11743717bwz.69)
Nov  2 02:26:20 GleSYS-vps postfix/qmgr[5903]: 73AA565943A0: removed
Nov  2 02:26:43 GleSYS-vps postfix/smtpd[19779]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 02:26:43 GleSYS-vps postfix/smtpd[19779]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <mailman@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<mailman@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 02:26:44 GleSYS-vps postfix/smtpd[19779]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 02:27:27 GleSYS-vps postfix/pickup[21728]: 0AF0365943A1: uid=33 from=<www-data>
Nov  2 02:27:27 GleSYS-vps postfix/cleanup[19782]: 0AF0365943A1: message-id=<20091101232727.0AF0365943A1@ozgur-yazilimcilar.org>
Nov  2 02:27:27 GleSYS-vps postfix/qmgr[5903]: 0AF0365943A1: from=<www-data@ozgur-yazilimcilar.org>, size=300, nrcpt=1 (queue active)
Nov  2 02:27:27 GleSYS-vps postfix/smtp[19795]: 0AF0365943A1: to=<baris.aydek@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.218.35]:25, delay=0.52, delays=0.02/0/0.15/0.35, dsn=2.0.0, status=sent (250 2.0.0 OK 1257118047 23si6327094bwz.9)
Nov  2 02:27:27 GleSYS-vps postfix/qmgr[5903]: 0AF0365943A1: removed
Nov  2 02:30:04 GleSYS-vps postfix/anvil[24298]: statistics: max connection rate 1/60s for (smtp:68.180.198.203) at Nov  2 02:23:48
Nov  2 02:30:04 GleSYS-vps postfix/anvil[24298]: statistics: max connection count 1 for (smtp:68.180.198.203) at Nov  2 02:23:48
Nov  2 02:30:04 GleSYS-vps postfix/anvil[24298]: statistics: max cache size 1 at Nov  2 02:23:48
Nov  2 03:43:51 GleSYS-vps postfix/smtpd[25835]: connect from mail-ew0-f222.google.com[209.85.219.222]
Nov  2 03:43:51 GleSYS-vps postfix/smtpd[25835]: NOQUEUE: reject: RCPT from mail-ew0-f222.google.com[209.85.219.222]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-ew0-f222.google.com>
Nov  2 03:43:51 GleSYS-vps postfix/smtpd[25835]: disconnect from mail-ew0-f222.google.com[209.85.219.222]
Nov  2 03:47:11 GleSYS-vps postfix/anvil[25841]: statistics: max connection rate 1/60s for (smtp:209.85.219.222) at Nov  2 03:43:51
Nov  2 03:47:11 GleSYS-vps postfix/anvil[25841]: statistics: max connection count 1 for (smtp:209.85.219.222) at Nov  2 03:43:51
Nov  2 03:47:11 GleSYS-vps postfix/anvil[25841]: statistics: max cache size 1 at Nov  2 03:43:51
Nov  2 04:29:08 GleSYS-vps postfix/smtpd[32765]: connect from mail-ew0-f222.google.com[209.85.219.222]
Nov  2 04:29:08 GleSYS-vps postfix/smtpd[32765]: NOQUEUE: reject: RCPT from mail-ew0-f222.google.com[209.85.219.222]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-ew0-f222.google.com>
Nov  2 04:29:08 GleSYS-vps postfix/smtpd[32765]: disconnect from mail-ew0-f222.google.com[209.85.219.222]
Nov  2 04:32:28 GleSYS-vps postfix/anvil[1339]: statistics: max connection rate 1/60s for (smtp:209.85.219.222) at Nov  2 04:29:08
Nov  2 04:32:28 GleSYS-vps postfix/anvil[1339]: statistics: max connection count 1 for (smtp:209.85.219.222) at Nov  2 04:29:08
Nov  2 04:32:28 GleSYS-vps postfix/anvil[1339]: statistics: max cache size 1 at Nov  2 04:29:08
Nov  2 04:33:08 GleSYS-vps postfix/smtpd[13538]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 04:33:08 GleSYS-vps postfix/smtpd[13538]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 04:33:08 GleSYS-vps postfix/smtpd[13538]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 04:36:28 GleSYS-vps postfix/anvil[13540]: statistics: max connection rate 1/60s for (smtp:209.85.218.218) at Nov  2 04:33:08
Nov  2 04:36:28 GleSYS-vps postfix/anvil[13540]: statistics: max connection count 1 for (smtp:209.85.218.218) at Nov  2 04:33:08
Nov  2 04:36:28 GleSYS-vps postfix/anvil[13540]: statistics: max cache size 1 at Nov  2 04:33:08
Nov  2 05:20:05 GleSYS-vps postfix/smtpd[15554]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 05:20:05 GleSYS-vps postfix/smtpd[15554]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 05:20:05 GleSYS-vps postfix/smtpd[15554]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 05:23:25 GleSYS-vps postfix/anvil[15568]: statistics: max connection rate 1/60s for (smtp:209.85.218.218) at Nov  2 05:20:05
Nov  2 05:23:25 GleSYS-vps postfix/anvil[15568]: statistics: max connection count 1 for (smtp:209.85.218.218) at Nov  2 05:20:05
Nov  2 05:23:25 GleSYS-vps postfix/anvil[15568]: statistics: max cache size 1 at Nov  2 05:20:05
Nov  2 05:44:12 GleSYS-vps postfix/smtpd[2034]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 05:44:12 GleSYS-vps postfix/smtpd[2034]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 05:44:12 GleSYS-vps postfix/smtpd[2034]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 05:46:47 GleSYS-vps postfix/smtpd[14175]: connect from ey-out-2122.google.com[74.125.78.24]
Nov  2 05:46:47 GleSYS-vps postfix/smtpd[14175]: NOQUEUE: reject: RCPT from ey-out-2122.google.com[74.125.78.24]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<metindelen0@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<ey-out-2122.google.com>
Nov  2 05:46:47 GleSYS-vps postfix/smtpd[14175]: disconnect from ey-out-2122.google.com[74.125.78.24]
Nov  2 05:50:07 GleSYS-vps postfix/anvil[2038]: statistics: max connection rate 1/60s for (smtp:209.85.218.218) at Nov  2 05:44:12
Nov  2 05:50:07 GleSYS-vps postfix/anvil[2038]: statistics: max connection count 1 for (smtp:209.85.218.218) at Nov  2 05:44:12
Nov  2 05:50:07 GleSYS-vps postfix/anvil[2038]: statistics: max cache size 1 at Nov  2 05:44:12
Nov  2 07:35:44 GleSYS-vps postfix/smtpd[8049]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 07:35:45 GleSYS-vps postfix/smtpd[8049]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<metindelen0@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 07:35:45 GleSYS-vps postfix/smtpd[8049]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 07:39:05 GleSYS-vps postfix/anvil[8060]: statistics: max connection rate 1/60s for (smtp:209.85.218.218) at Nov  2 07:35:44
Nov  2 07:39:05 GleSYS-vps postfix/anvil[8060]: statistics: max connection count 1 for (smtp:209.85.218.218) at Nov  2 07:35:44
Nov  2 07:39:05 GleSYS-vps postfix/anvil[8060]: statistics: max cache size 1 at Nov  2 07:35:44
Nov  2 08:54:24 GleSYS-vps postfix/smtpd[7368]: connect from mail-ew0-f227.google.com[209.85.219.227]
Nov  2 08:54:24 GleSYS-vps postfix/smtpd[7368]: NOQUEUE: reject: RCPT from mail-ew0-f227.google.com[209.85.219.227]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-ew0-f227.google.com>
Nov  2 08:54:24 GleSYS-vps postfix/smtpd[7368]: disconnect from mail-ew0-f227.google.com[209.85.219.227]
Nov  2 08:57:44 GleSYS-vps postfix/anvil[7372]: statistics: max connection rate 1/60s for (smtp:209.85.219.227) at Nov  2 08:54:24
Nov  2 08:57:44 GleSYS-vps postfix/anvil[7372]: statistics: max connection count 1 for (smtp:209.85.219.227) at Nov  2 08:54:24
Nov  2 08:57:44 GleSYS-vps postfix/anvil[7372]: statistics: max cache size 1 at Nov  2 08:54:24
Nov  2 09:56:59 GleSYS-vps postfix/smtpd[9897]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 09:56:59 GleSYS-vps postfix/smtpd[9897]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 09:56:59 GleSYS-vps postfix/smtpd[9897]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 10:00:19 GleSYS-vps postfix/anvil[9901]: statistics: max connection rate 1/60s for (smtp:209.85.218.218) at Nov  2 09:56:59
Nov  2 10:00:19 GleSYS-vps postfix/anvil[9901]: statistics: max connection count 1 for (smtp:209.85.218.218) at Nov  2 09:56:59
Nov  2 10:00:19 GleSYS-vps postfix/anvil[9901]: statistics: max cache size 1 at Nov  2 09:56:59
Nov  2 10:29:17 GleSYS-vps postfix/smtpd[3836]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 10:29:17 GleSYS-vps postfix/smtpd[3836]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 10:29:17 GleSYS-vps postfix/smtpd[3836]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 10:32:37 GleSYS-vps postfix/anvil[3841]: statistics: max connection rate 1/60s for (smtp:209.85.218.218) at Nov  2 10:29:17
Nov  2 10:32:37 GleSYS-vps postfix/anvil[3841]: statistics: max connection count 1 for (smtp:209.85.218.218) at Nov  2 10:29:17
Nov  2 10:32:37 GleSYS-vps postfix/anvil[3841]: statistics: max cache size 1 at Nov  2 10:29:17
Nov  2 10:39:49 GleSYS-vps postfix/smtpd[17843]: connect from mail-ew0-f222.google.com[209.85.219.222]
Nov  2 10:39:49 GleSYS-vps postfix/smtpd[17843]: NOQUEUE: reject: RCPT from mail-ew0-f222.google.com[209.85.219.222]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-ew0-f222.google.com>
Nov  2 10:39:49 GleSYS-vps postfix/smtpd[17843]: disconnect from mail-ew0-f222.google.com[209.85.219.222]
Nov  2 10:43:09 GleSYS-vps postfix/anvil[17944]: statistics: max connection rate 1/60s for (smtp:209.85.219.222) at Nov  2 10:39:49
Nov  2 10:43:09 GleSYS-vps postfix/anvil[17944]: statistics: max connection count 1 for (smtp:209.85.219.222) at Nov  2 10:39:49
Nov  2 10:43:09 GleSYS-vps postfix/anvil[17944]: statistics: max cache size 1 at Nov  2 10:39:49
Nov  2 10:45:37 GleSYS-vps postfix/smtpd[22419]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 10:45:38 GleSYS-vps postfix/smtpd[22419]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 10:45:38 GleSYS-vps postfix/smtpd[22419]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 10:48:58 GleSYS-vps postfix/anvil[22442]: statistics: max connection rate 1/60s for (smtp:209.85.218.218) at Nov  2 10:45:37
Nov  2 10:48:58 GleSYS-vps postfix/anvil[22442]: statistics: max connection count 1 for (smtp:209.85.218.218) at Nov  2 10:45:37
Nov  2 10:48:58 GleSYS-vps postfix/anvil[22442]: statistics: max cache size 1 at Nov  2 10:45:37
Nov  2 11:34:32 GleSYS-vps postfix/smtpd[14290]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 11:34:32 GleSYS-vps postfix/smtpd[14290]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 11:34:32 GleSYS-vps postfix/smtpd[14290]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 11:37:52 GleSYS-vps postfix/anvil[14307]: statistics: max connection rate 1/60s for (smtp:209.85.218.218) at Nov  2 11:34:32
Nov  2 11:37:52 GleSYS-vps postfix/anvil[14307]: statistics: max connection count 1 for (smtp:209.85.218.218) at Nov  2 11:34:32
Nov  2 11:37:52 GleSYS-vps postfix/anvil[14307]: statistics: max cache size 1 at Nov  2 11:34:32
Nov  2 12:20:07 GleSYS-vps postfix/smtpd[3445]: connect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 12:20:07 GleSYS-vps postfix/smtpd[3445]: NOQUEUE: reject: RCPT from mail-bw0-f218.google.com[209.85.218.218]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<metindelen0@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-bw0-f218.google.com>
Nov  2 12:20:07 GleSYS-vps postfix/smtpd[3445]: disconnect from mail-bw0-f218.google.com[209.85.218.218]
Nov  2 12:23:27 GleSYS-vps postfix/anvil[3546]: statistics: max connection rate 1/60s for (smtp:209.85.218.218) at Nov  2 12:20:07
Nov  2 12:23:27 GleSYS-vps postfix/anvil[3546]: statistics: max connection count 1 for (smtp:209.85.218.218) at Nov  2 12:20:07
Nov  2 12:23:27 GleSYS-vps postfix/anvil[3546]: statistics: max cache size 1 at Nov  2 12:20:07
Nov  2 12:57:14 GleSYS-vps postfix/smtpd[16303]: connect from mail-ew0-f222.google.com[209.85.219.222]
Nov  2 12:57:14 GleSYS-vps postfix/smtpd[16303]: NOQUEUE: reject: RCPT from mail-ew0-f222.google.com[209.85.219.222]: 550 5.1.1 <admins@ozgur-yazilimcilar.org>: Recipient address rejected: User unknown in local recipient table; from=<baris.aydek@gmail.com> to=<admins@ozgur-yazilimcilar.org> proto=ESMTP helo=<mail-ew0-f222.google.com>
Nov  2 12:57:14 GleSYS-vps postfix/smtpd[16303]: disconnect from mail-ew0-f222.google.com[209.85.219.222]
Nov  2 13:00:35 GleSYS-vps postfix/anvil[16309]: statistics: max connection rate 1/60s for (smtp:209.85.219.222) at Nov  2 12:57:14
Nov  2 13:00:35 GleSYS-vps postfix/anvil[16309]: statistics: max connection count 1 for (smtp:209.85.219.222) at Nov  2 12:57:14
Nov  2 13:00:35 GleSYS-vps postfix/anvil[16309]: statistics: max cache size 1 at Nov  2 12:57:14
Nov  2 15:07:28 GleSYS-vps postfix/pickup[32531]: 4035B6594A0A: uid=33 from=<www-data>
Nov  2 15:07:28 GleSYS-vps postfix/cleanup[19978]: 4035B6594A0A: message-id=<20091102120728.4035B6594A0A@ozgur-yazilimcilar.org>
Nov  2 15:07:28 GleSYS-vps postfix/qmgr[5903]: 4035B6594A0A: from=<www-data@ozgur-yazilimcilar.org>, size=1220, nrcpt=1 (queue active)
Nov  2 15:07:28 GleSYS-vps postfix/smtp[19980]: 4035B6594A0A: to=<tuna.onur@yahoo.com>, relay=b.mx.mail.yahoo.com[66.196.82.7]:25, delay=0.72, delays=0.07/0.02/0.33/0.31, dsn=2.0.0, status=sent (250 ok dirdel)
Nov  2 15:07:28 GleSYS-vps postfix/qmgr[5903]: 4035B6594A0A: removed

```

My /etc/postfix/main.cf file
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = ozgur-yazilimcilar.org

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ozgur-yazilimcilar.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ozgur-yazilimcilar.org, localhost.localdomain, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```


/etc/postfix/master.cf file
```

#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


```


/etc/postfix/transport file
```
ozgur-yazilimcilar.org	mailman:

```

I see the errors in the mail.log file but don't know how to solve that. Could someone help me to make it work?

---

### Post by prokaryot on 2009-11-02
I added these to the /etc/aliases, then enter "newaliases" command. After that my problem solved.

## mailman mailing list
mailman:              "|/var/lib/mailman/mail/mailman post mailman"
mailman-admin:        "|/var/lib/mailman/mail/mailman admin mailman"
mailman-bounces:      "|/var/lib/mailman/mail/mailman bounces mailman"
mailman-confirm:      "|/var/lib/mailman/mail/mailman confirm mailman"
mailman-join:         "|/var/lib/mailman/mail/mailman join mailman"
mailman-leave:        "|/var/lib/mailman/mail/mailman leave mailman"
mailman-owner:        "|/var/lib/mailman/mail/mailman owner mailman"
mailman-request:      "|/var/lib/mailman/mail/mailman request mailman"
mailman-subscribe:    "|/var/lib/mailman/mail/mailman subscribe mailman"
mailman-unsubscribe:  "|/var/lib/mailman/mail/mailman unsubscribe mailman"

---

