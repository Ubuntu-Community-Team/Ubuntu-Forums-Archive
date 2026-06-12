---
title: "Cant Send Mail"
date: 2010-05-02
forum: Server Platforms
---

### Post by fortune2008 on 2010-05-02
The problem i'm having is i cant get to send mail from php scripts here is my error log

```
May  2 05:14:17 server1 postfix/master[31361]: daemon started -- version 2.6.5, configuration /etc/postfix
May  2 05:14:17 server1 postfix/qmgr[31363]: 9D7E4E0D4C: from=<website@triniwiz.com>, size=3004, nrcpt=1 (queue active)
May  2 05:14:17 server1 postfix/qmgr[31363]: 072A7E0DA3: from=<website@triniwiz.com>, size=2985, nrcpt=1 (queue active)
May  2 05:14:17 server1 postfix/smtp[31369]: connect to kamelot-clan.com[174.120.120.151]:25: Connection refused
May  2 05:14:17 server1 postfix/smtp[31370]: connect to mail.sexy-meet.com[95.168.177.250]:25: Connection refused
May  2 05:14:17 server1 postfix/smtp[31369]: 9D7E4E0D4C: to=<bqepztqnz54@kamelot-clan.com>, relay=none, delay=15704, delays=15704/0.03/0.31/0, dsn=4.4.1, status=deferred (connect to kamelot-clan.com[174.120.120.151]:25: Connection refused)
May  2 05:14:17 server1 postfix/smtp[31370]: 072A7E0DA3: to=<maximator@sexy-meet.com>, relay=none, delay=16020, delays=16019/0.01/0.35/0, dsn=4.4.1, status=deferred (connect to mail.sexy-meet.com[95.168.177.250]:25: Connection refused)
May  2 05:14:18 server1 postfix/pickup[31362]: 2DCABE04D1: uid=33 from=<www-data>
May  2 05:14:18 server1 postfix/cleanup[31364]: 2DCABE04D1: message-id=<20100502091418.2DCABE04D1@server1.chatalker.com>
May  2 05:14:18 server1 postfix/qmgr[31363]: 2DCABE04D1: from=<www-data@server1.chatalker.com>, size=923, nrcpt=1 (queue active)
May  2 05:14:23 server1 postfix/smtpd[31378]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:14:23 server1 postfix/smtpd[31378]: warning: TLS library problem: 31378:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:14:23 server1 postfix/smtpd[31378]: connect from localhost[127.0.0.1]
May  2 05:14:23 server1 postfix/smtpd[31378]: 0718AE0440: client=localhost[127.0.0.1]
May  2 05:14:23 server1 postfix/cleanup[31364]: 0718AE0440: message-id=<20100502091418.2DCABE04D1@server1.chatalker.com>
May  2 05:14:23 server1 postfix/qmgr[31363]: 0718AE0440: from=<www-data@server1.chatalker.com>, size=1391, nrcpt=1 (queue active)
May  2 05:14:23 server1 amavis[26899]: (26899-01) Passed CLEAN, <www-data@server1.chatalker.com> -> <dbmaster@example.com>, Message-ID: <20100502091418.2DCABE04D1@server1.chatalker.com>, mail_id: QqzzpRReuLKQ, Hits: 2.43, size: 922, queued_as: 0718AE0440, 4859 ms
May  2 05:14:23 server1 postfix/smtp[31373]: 2DCABE04D1: to=<dbmaster@example.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=139, delays=134/0.01/0.01/4.9, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=26899-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 0718AE0440)
May  2 05:14:23 server1 postfix/qmgr[31363]: 2DCABE04D1: removed
May  2 05:14:53 server1 postfix/smtp[31369]: connect to example.com[192.0.32.10]:25: Connection timed out
May  2 05:14:53 server1 postfix/smtp[31369]: 0718AE0440: to=<dbmaster@example.com>, relay=none, delay=30, delays=0.09/0.03/30/0, dsn=4.4.1, status=deferred (connect to example.com[192.0.32.10]:25: Connection timed out)
May  2 05:15:01 server1 pop3d: Connection, ip=[::ffff:127.0.0.1]
May  2 05:15:01 server1 pop3d: Disconnected, ip=[::ffff:127.0.0.1]
May  2 05:15:01 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:15:01 server1 imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
May  2 05:15:01 server1 postfix/smtpd[31406]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:15:01 server1 postfix/smtpd[31406]: warning: TLS library problem: 31406:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:15:01 server1 postfix/smtpd[31406]: connect from localhost[127.0.0.1]
May  2 05:15:01 server1 postfix/smtpd[31406]: lost connection after CONNECT from localhost[127.0.0.1]
May  2 05:15:01 server1 postfix/smtpd[31406]: disconnect from localhost[127.0.0.1]
May  2 05:15:43 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:43 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:43 server1 pop3d-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:43 server1 pop3d-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:44 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:48 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:48 server1 postfix/smtpd[31406]: connect from unknown[192.168.10.6]
May  2 05:15:48 server1 postfix/smtpd[31406]: lost connection after STARTTLS from unknown[192.168.10.6]
May  2 05:15:48 server1 postfix/cleanup[31364]: 8BFDDE04D3: message-id=<20100502091548.8BFDDE04D3@server1.chatalker.com>
May  2 05:15:48 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:48 server1 postfix/smtpd[31406]: disconnect from unknown[192.168.10.6]
May  2 05:15:48 server1 postfix/qmgr[31363]: 8BFDDE04D3: from=<double-bounce@server1.chatalker.com>, size=922, nrcpt=1 (queue active)
May  2 05:15:48 server1 postfix/local[31431]: 8BFDDE04D3: to=<root@server1.chatalker.com>, orig_to=<postmaster>, relay=local, delay=0.22, delays=0.1/0.04/0/0.08, dsn=2.0.0, status=sent (delivered to mailbox)
May  2 05:15:48 server1 postfix/qmgr[31363]: 8BFDDE04D3: removed
May  2 05:15:48 server1 pop3d-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:49 server1 pop3d-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:49 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:49 server1 postfix/smtpd[31406]: connect from unknown[192.168.10.6]
May  2 05:15:49 server1 postfix/smtpd[31406]: lost connection after STARTTLS from unknown[192.168.10.6]
May  2 05:15:49 server1 postfix/cleanup[31364]: 332D5E04D3: message-id=<20100502091549.332D5E04D3@server1.chatalker.com>
May  2 05:15:49 server1 postfix/smtpd[31406]: disconnect from unknown[192.168.10.6]
May  2 05:15:49 server1 postfix/qmgr[31363]: 332D5E04D3: from=<double-bounce@server1.chatalker.com>, size=922, nrcpt=1 (queue active)
May  2 05:15:49 server1 pop3d-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:49 server1 postfix/local[31431]: 332D5E04D3: to=<root@server1.chatalker.com>, orig_to=<postmaster>, relay=local, delay=0.14, delays=0.07/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
May  2 05:15:49 server1 postfix/qmgr[31363]: 332D5E04D3: removed
May  2 05:15:49 server1 postfix/smtpd[31406]: connect from unknown[192.168.10.6]
May  2 05:15:49 server1 postfix/smtpd[31406]: lost connection after STARTTLS from unknown[192.168.10.6]
May  2 05:15:49 server1 postfix/cleanup[31364]: 664E9E04D3: message-id=<20100502091549.664E9E04D3@server1.chatalker.com>
May  2 05:15:49 server1 postfix/smtpd[31406]: disconnect from unknown[192.168.10.6]
May  2 05:15:49 server1 postfix/qmgr[31363]: 664E9E04D3: from=<double-bounce@server1.chatalker.com>, size=922, nrcpt=1 (queue active)
May  2 05:15:49 server1 postfix/local[31431]: 664E9E04D3: to=<root@server1.chatalker.com>, orig_to=<postmaster>, relay=local, delay=0.14, delays=0.07/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
May  2 05:15:49 server1 postfix/qmgr[31363]: 664E9E04D3: removed
May  2 05:15:49 server1 postfix/smtpd[31406]: connect from unknown[192.168.10.6]
May  2 05:15:49 server1 postfix/smtpd[31406]: lost connection after STARTTLS from unknown[192.168.10.6]
May  2 05:15:49 server1 postfix/cleanup[31364]: E51CEE04D3: message-id=<20100502091549.E51CEE04D3@server1.chatalker.com>
May  2 05:15:49 server1 postfix/smtpd[31406]: disconnect from unknown[192.168.10.6]
May  2 05:15:49 server1 postfix/qmgr[31363]: E51CEE04D3: from=<double-bounce@server1.chatalker.com>, size=922, nrcpt=1 (queue active)
May  2 05:15:50 server1 postfix/local[31431]: E51CEE04D3: to=<root@server1.chatalker.com>, orig_to=<postmaster>, relay=local, delay=0.11, delays=0.06/0/0/0.05, dsn=2.0.0, status=sent (delivered to mailbox)
May  2 05:15:50 server1 postfix/qmgr[31363]: E51CEE04D3: removed
May  2 05:15:57 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:57 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:57 server1 pop3d-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:57 server1 pop3d-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:15:57 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:16:15 server1 imapd-ssl: last message repeated 3 times
May  2 05:16:15 server1 pop3d-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:16:15 server1 pop3d-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:16:15 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:16:19 server1 imapd-ssl: couriertls: /etc/ssl/certs/74860f22.0: No such file or directory
May  2 05:16:49 server1 postfix/smtpd[31406]: connect from localhost[127.0.0.1]
May  2 05:16:49 server1 postfix/smtpd[31406]: 0FA0DE0C15: client=localhost[127.0.0.1]
May  2 05:16:49 server1 postfix/cleanup[31364]: 0FA0DE0C15: message-id=<308856724c8c00a41cf7fe5c0d6d058f.squirrel@192.168.10.52>
May  2 05:16:49 server1 postfix/qmgr[31363]: 0FA0DE0C15: from=<admin@tubeinn.com>, size=711, nrcpt=1 (queue active)
May  2 05:16:49 server1 postfix/smtpd[31406]: disconnect from localhost[127.0.0.1]
May  2 05:16:49 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:16:49 server1 imapd: LOGIN, user=admin@tubeinn.com, ip=[::ffff:127.0.0.1], port=[49043], protocol=IMAP
May  2 05:16:49 server1 imapd: LOGOUT, user=admin@tubeinn.com, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=603, sent=203, time=0
May  2 05:16:49 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:16:49 server1 imapd: LOGIN, user=admin@tubeinn.com, ip=[::ffff:127.0.0.1], port=[49046], protocol=IMAP
May  2 05:16:49 server1 imapd: LOGOUT, user=admin@tubeinn.com, ip=[::ffff:127.0.0.1], headers=221, body=0, rcvd=294, sent=1400, time=0
May  2 05:16:49 server1 postfix/smtpd[31476]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:16:49 server1 postfix/smtpd[31476]: warning: TLS library problem: 31476:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:16:49 server1 postfix/smtpd[31476]: connect from localhost[127.0.0.1]
May  2 05:16:49 server1 postfix/smtpd[31476]: ADF4FE0D9F: client=localhost[127.0.0.1]
May  2 05:16:49 server1 postfix/cleanup[31364]: ADF4FE0D9F: message-id=<308856724c8c00a41cf7fe5c0d6d058f.squirrel@192.168.10.52>
May  2 05:16:49 server1 postfix/qmgr[31363]: ADF4FE0D9F: from=<admin@tubeinn.com>, size=1183, nrcpt=1 (queue active)
May  2 05:16:49 server1 amavis[26900]: (26900-01) Passed CLEAN, LOCAL [127.0.0.1] [127.0.0.1] <admin@tubeinn.com> -> <fortune.osei@yahoo.com>, Message-ID: <308856724c8c00a41cf7fe5c0d6d058f.squirrel@192.168.10.52>, mail_id: 9lxg5ofiTMxJ, Hits: 3.89, size: 711, queued_as: ADF4FE0D9F, 634 ms
May  2 05:16:49 server1 postfix/smtp[31469]: 0FA0DE0C15: to=<fortune.osei@yahoo.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.79, delays=0.13/0.01/0.01/0.64, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=26900-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as ADF4FE0D9F)
May  2 05:16:49 server1 postfix/qmgr[31363]: 0FA0DE0C15: removed
May  2 05:16:52 server1 postfix/smtp[31478]: ADF4FE0D9F: to=<fortune.osei@yahoo.com>, relay=g.mx.mail.yahoo.com[98.137.54.238]:25, delay=2.8, delays=0.1/0.04/1.8/0.86, dsn=2.0.0, status=sent (250 ok dirdel)
May  2 05:16:52 server1 postfix/qmgr[31363]: ADF4FE0D9F: removed
May  2 05:19:23 server1 postfix/smtpd[31378]: timeout after END-OF-MESSAGE from localhost[127.0.0.1]
May  2 05:19:23 server1 postfix/smtpd[31378]: disconnect from localhost[127.0.0.1]
May  2 05:20:01 server1 pop3d: Connection, ip=[::ffff:127.0.0.1]
May  2 05:20:01 server1 pop3d: Disconnected, ip=[::ffff:127.0.0.1]
May  2 05:20:01 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:20:01 server1 imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
May  2 05:20:01 server1 postfix/smtpd[31538]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:20:01 server1 postfix/smtpd[31538]: warning: TLS library problem: 31538:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:20:01 server1 postfix/smtpd[31538]: connect from localhost[127.0.0.1]
May  2 05:20:01 server1 postfix/smtpd[31538]: lost connection after CONNECT from localhost[127.0.0.1]
May  2 05:20:01 server1 postfix/smtpd[31538]: disconnect from localhost[127.0.0.1]
May  2 05:20:09 server1 postfix/anvil[31429]: statistics: max connection rate 4/60s for (smtp:192.168.10.6) at May  2 05:15:49
May  2 05:20:09 server1 postfix/anvil[31429]: statistics: max connection count 1 for (smtp:192.168.10.6) at May  2 05:15:48
May  2 05:20:09 server1 postfix/anvil[31429]: statistics: max cache size 1 at May  2 05:15:48
May  2 05:21:49 server1 postfix/smtpd[31476]: timeout after END-OF-MESSAGE from localhost[127.0.0.1]
May  2 05:21:49 server1 postfix/smtpd[31476]: disconnect from localhost[127.0.0.1]
May  2 05:24:17 server1 postfix/qmgr[31363]: 0718AE0440: from=<www-data@server1.chatalker.com>, size=1391, nrcpt=1 (queue active)
May  2 05:24:47 server1 postfix/smtp[31697]: connect to example.com[192.0.32.10]:25: Connection timed out
May  2 05:24:47 server1 postfix/smtp[31697]: 0718AE0440: to=<dbmaster@example.com>, relay=none, delay=625, delays=594/0.05/30/0, dsn=4.4.1, status=deferred (connect to example.com[192.0.32.10]:25: Connection timed out)
May  2 05:24:51 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:24:51 server1 imapd: LOGIN, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], port=[34547], protocol=IMAP
May  2 05:24:51 server1 imapd: LOGOUT, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=30, sent=238, time=0
May  2 05:24:52 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:24:52 server1 imapd: LOGIN, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], port=[34548], protocol=IMAP
May  2 05:24:52 server1 imapd: LOGOUT, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], headers=1463, body=0, rcvd=453, sent=4960, time=0
May  2 05:24:52 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:24:52 server1 imapd: LOGIN, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], port=[34549], protocol=IMAP
May  2 05:24:52 server1 imapd: LOGOUT, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=328, sent=1121, time=0
May  2 05:25:00 server1 postfix/smtpd[31706]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:25:00 server1 postfix/smtpd[31706]: warning: TLS library problem: 31706:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:25:00 server1 postfix/smtpd[31706]: connect from localhost[127.0.0.1]
May  2 05:25:00 server1 postfix/smtpd[31706]: D4CBAE0D9F: client=localhost[127.0.0.1]
May  2 05:25:00 server1 postfix/cleanup[31711]: D4CBAE0D9F: message-id=<253d32d6eb27d3d992773783191154ec.squirrel@192.168.10.52>
May  2 05:25:01 server1 postfix/qmgr[31363]: D4CBAE0D9F: from=<admin@chatalker.com>, size=715, nrcpt=1 (queue active)
May  2 05:25:01 server1 postfix/smtpd[31706]: disconnect from localhost[127.0.0.1]
May  2 05:25:01 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:25:01 server1 imapd: LOGIN, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], port=[34558], protocol=IMAP
May  2 05:25:01 server1 imapd: LOGOUT, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=607, sent=204, time=0
May  2 05:25:01 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:25:01 server1 imapd: LOGIN, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], port=[34560], protocol=IMAP
May  2 05:25:01 server1 imapd: LOGOUT, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], headers=1463, body=0, rcvd=296, sent=4431, time=0
May  2 05:25:02 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:25:02 server1 imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
May  2 05:25:02 server1 postfix/smtpd[31706]: connect from localhost[127.0.0.1]
May  2 05:25:02 server1 postfix/smtpd[31706]: lost connection after CONNECT from localhost[127.0.0.1]
May  2 05:25:02 server1 postfix/smtpd[31706]: disconnect from localhost[127.0.0.1]
May  2 05:25:02 server1 pop3d: Connection, ip=[::ffff:127.0.0.1]
May  2 05:25:02 server1 pop3d: Disconnected, ip=[::ffff:127.0.0.1]
May  2 05:25:04 server1 postfix/smtpd[31757]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:25:04 server1 postfix/smtpd[31757]: warning: TLS library problem: 31757:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:25:04 server1 postfix/smtpd[31757]: connect from localhost[127.0.0.1]
May  2 05:25:04 server1 postfix/smtpd[31757]: 82044E0DB5: client=localhost[127.0.0.1]
May  2 05:25:04 server1 postfix/cleanup[31711]: 82044E0DB5: message-id=<253d32d6eb27d3d992773783191154ec.squirrel@192.168.10.52>
May  2 05:25:04 server1 postfix/qmgr[31363]: 82044E0DB5: from=<admin@chatalker.com>, size=1187, nrcpt=1 (queue active)
May  2 05:25:04 server1 postfix/smtpd[31757]: disconnect from localhost[127.0.0.1]
May  2 05:25:04 server1 amavis[26899]: (26899-02) Passed CLEAN, LOCAL [127.0.0.1] [127.0.0.1] <admin@chatalker.com> -> <fortune.osei@gmail.com>, Message-ID: <253d32d6eb27d3d992773783191154ec.squirrel@192.168.10.52>, mail_id: eZQmKdySj3eY, Hits: 3.74, size: 715, queued_as: 82044E0DB5, 3628 ms
May  2 05:25:04 server1 postfix/smtp[31712]: D4CBAE0D9F: to=<fortune.osei@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=3.8, delays=0.16/0.01/0.01/3.6, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=26899-02, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 82044E0DB5)
May  2 05:25:04 server1 postfix/qmgr[31363]: D4CBAE0D9F: removed
May  2 05:25:21 server1 postfix/smtp[31697]: 82044E0DB5: to=<fortune.osei@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.113.27]:25, delay=17, delays=0.1/0.02/16/0.81, dsn=2.0.0, status=sent (250 2.0.0 OK 1272792321 q11si8833432vch.54)
May  2 05:25:21 server1 postfix/qmgr[31363]: 82044E0DB5: removed
May  2 05:27:04 server1 postfix/smtpd[31767]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:27:04 server1 postfix/smtpd[31767]: warning: TLS library problem: 31767:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:27:04 server1 postfix/smtpd[31767]: connect from localhost[127.0.0.1]
May  2 05:27:04 server1 postfix/smtpd[31767]: DBD23E0D9F: client=localhost[127.0.0.1]
May  2 05:27:04 server1 postfix/cleanup[31770]: DBD23E0D9F: message-id=<a8dec0aeec0ba331c967778199e26864.squirrel@192.168.10.52>
May  2 05:27:05 server1 postfix/qmgr[31363]: DBD23E0D9F: from=<admin@chatalker.com>, size=715, nrcpt=1 (queue active)
May  2 05:27:05 server1 postfix/smtpd[31767]: disconnect from localhost[127.0.0.1]
May  2 05:27:05 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:27:05 server1 imapd: LOGIN, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], port=[34579], protocol=IMAP
May  2 05:27:05 server1 imapd: LOGOUT, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=607, sent=204, time=0
May  2 05:27:05 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:27:05 server1 imapd: LOGIN, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], port=[34581], protocol=IMAP
May  2 05:27:05 server1 imapd: LOGOUT, user=admin@chatalker.com, ip=[::ffff:127.0.0.1], headers=1463, body=0, rcvd=296, sent=4431, time=0
May  2 05:27:05 server1 postfix/smtpd[31777]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:27:05 server1 postfix/smtpd[31777]: warning: TLS library problem: 31777:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:27:05 server1 postfix/smtpd[31777]: connect from localhost[127.0.0.1]
May  2 05:27:05 server1 postfix/smtpd[31777]: 89F83E0DB5: client=localhost[127.0.0.1]
May  2 05:27:05 server1 postfix/cleanup[31770]: 89F83E0DB5: message-id=<a8dec0aeec0ba331c967778199e26864.squirrel@192.168.10.52>
May  2 05:27:05 server1 postfix/smtpd[31777]: disconnect from localhost[127.0.0.1]
May  2 05:27:05 server1 postfix/qmgr[31363]: 89F83E0DB5: from=<admin@chatalker.com>, size=1187, nrcpt=1 (queue active)
May  2 05:27:05 server1 amavis[26900]: (26900-02) Passed CLEAN, LOCAL [127.0.0.1] [127.0.0.1] <admin@chatalker.com> -> <fortune.osei@yahoo.com>, Message-ID: <a8dec0aeec0ba331c967778199e26864.squirrel@192.168.10.52>, mail_id: nnimt76zFfo7, Hits: 3.742, size: 715, queued_as: 89F83E0DB5, 634 ms
May  2 05:27:05 server1 postfix/smtp[31771]: DBD23E0D9F: to=<fortune.osei@yahoo.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.81, delays=0.16/0.01/0.01/0.64, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=26900-02, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 89F83E0DB5)
May  2 05:27:05 server1 postfix/qmgr[31363]: DBD23E0D9F: removed
May  2 05:27:07 server1 postfix/smtp[31779]: 89F83E0DB5: to=<fortune.osei@yahoo.com>, relay=e.mx.mail.yahoo.com[67.195.168.230]:25, delay=2, delays=0.11/0.04/1.1/0.73, dsn=2.0.0, status=sent (250 ok dirdel)
May  2 05:27:07 server1 postfix/qmgr[31363]: 89F83E0DB5: removed
May  2 05:30:06 server1 pop3d: Connection, ip=[::ffff:127.0.0.1]
May  2 05:30:06 server1 pop3d: Disconnected, ip=[::ffff:127.0.0.1]
May  2 05:30:06 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:30:06 server1 imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
May  2 05:30:06 server1 postfix/smtpd[31836]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:30:06 server1 postfix/smtpd[31836]: warning: TLS library problem: 31836:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:30:06 server1 postfix/smtpd[31836]: connect from localhost[127.0.0.1]
May  2 05:30:06 server1 postfix/smtpd[31836]: lost connection after CONNECT from localhost[127.0.0.1]
May  2 05:30:06 server1 postfix/smtpd[31836]: disconnect from localhost[127.0.0.1]
May  2 05:32:45 server1 postfix/smtpd[31872]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:32:45 server1 postfix/smtpd[31872]: warning: TLS library problem: 31872:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:32:45 server1 postfix/smtpd[31872]: connect from unknown[117.200.61.78]
May  2 05:32:47 server1 postfix/smtpd[31872]: 20766E0DCB: client=unknown[117.200.61.78]
May  2 05:32:48 server1 postfix/cleanup[31876]: 20766E0DCB: message-id=<>
May  2 05:32:48 server1 postfix/qmgr[31363]: 20766E0DCB: from=<admin@wizgames.net>, size=3459, nrcpt=1 (queue active)
May  2 05:32:50 server1 postfix/smtpd[31872]: lost connection after UNKNOWN from unknown[117.200.61.78]
May  2 05:32:50 server1 postfix/smtpd[31872]: disconnect from unknown[117.200.61.78]
May  2 05:32:51 server1 postfix/smtpd[31881]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:32:51 server1 postfix/smtpd[31881]: warning: TLS library problem: 31881:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:32:51 server1 postfix/smtpd[31881]: connect from localhost[127.0.0.1]
May  2 05:32:51 server1 postfix/smtpd[31881]: 59D9CE0DCC: client=unknown[117.200.61.78]
May  2 05:32:51 server1 postfix/cleanup[31876]: 59D9CE0DCC: message-id=<>
May  2 05:32:51 server1 postfix/qmgr[31363]: 59D9CE0DCC: from=<admin@wizgames.net>, size=4517, nrcpt=1 (queue active)
May  2 05:32:51 server1 postfix/smtpd[31881]: disconnect from localhost[127.0.0.1]
May  2 05:32:51 server1 amavis[26899]: (26899-03) Passed SPAMMY, [117.200.61.78] [117.200.61.78] <admin@wizgames.net> -> <admin@wizgames.net>, mail_id: A1ODaCx2T4qt, Hits: 26.246, size: 3454, queued_as: 59D9CE0DCC, 2660 ms
May  2 05:32:51 server1 postfix/smtp[31877]: 20766E0DCB: to=<admin@wizgames.net>, relay=127.0.0.1[127.0.0.1]:10024, delay=4.9, delays=2.2/0.01/0/2.7, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=26899-03, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 59D9CE0DCC)
May  2 05:32:51 server1 postfix/qmgr[31363]: 20766E0DCB: removed
May  2 05:32:51 server1 postfix/pipe[31882]: 59D9CE0DCC: to=<admin@wizgames.net>, relay=maildrop, delay=0.24, delays=0.1/0.02/0/0.12, dsn=2.0.0, status=sent (delivered via maildrop service)
May  2 05:32:51 server1 postfix/qmgr[31363]: 59D9CE0DCC: removed
May  2 05:35:01 server1 pop3d: Connection, ip=[::ffff:127.0.0.1]
May  2 05:35:01 server1 imapd: Connection, ip=[::ffff:127.0.0.1]
May  2 05:35:01 server1 pop3d: Disconnected, ip=[::ffff:127.0.0.1]
May  2 05:35:01 server1 imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
May  2 05:35:01 server1 postfix/smtpd[31928]: warning: cannot get RSA private key from file /etc/postfix/smtpd.key: disabling TLS support
May  2 05:35:01 server1 postfix/smtpd[31928]: warning: TLS library problem: 31928:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:399:
May  2 05:35:01 server1 postfix/smtpd[31928]: connect from localhost[127.0.0.1]
May  2 05:35:01 server1 postfix/smtpd[31928]: lost connection after CONNECT from localhost[127.0.0.1]
May  2 05:35:01 server1 postfix/smtpd[31928]: disconnect from localhost[127.0.0.1]

```

I can send mail from squirrel mail but not any thing else

---

### Post by dipeshmehta on 2010-05-02
Which howto guide you have followed?  and please post your main.cf here

Dipesh

---

