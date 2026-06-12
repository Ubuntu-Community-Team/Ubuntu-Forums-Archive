---
title: "Courier imapd-ssl, Connection LOGIN DISCONNECTED, etc"
date: 2015-12-25
forum: Server Platforms
---

### Post by Seb_Boffen on 2015-12-25
I have a mail server Ubuntu LTS 14.04 running Courier Imap-ssl 4.10.20120615-1ubuntu3 and experience an issue sinds 2 days with status DISCONNECTED after succesfull login while connecting via the internet, nothing has been changed to my configuration sinds then. Any help would be appreciated.

 Dec 25 18:55:00 host imapd-ssl: Connection, ip=[::ffff x.x.x.x]
 Dec 25 18:55:01 host imapd-ssl: LOGIN, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], port=[64823], protocol=IMAP
 Dec 25 18:55:05 host imapd-ssl: DISCONNECTED, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x, headers=0, body=0, rcvd=305, sent=5997, time=4, starttls=1
 Dec 25 18:55:06 host imapd-ssl: Connection, ip=[::ffff x.x.x.x]
 Dec 25 18:55:06 host imapd-ssl: LOGIN, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], port=[64824], protocol=IMAP
 Dec 25 18:55:16 host imapd-ssl: LOGOUT, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], headers=0, body=0, rcvd=303, sent=1688, time=36, starttls=1
 Dec 25 18:55:37 host imapd-ssl: DISCONNECTED, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], headers=0, body=0, rcvd=2131, sent=151257, time=31, starttls=1
 Dec 25 18:55:37 host imapd-ssl: Connection, ip=[::ffff x.x.x.x]
 Dec 25 18:55:38 host imapd-ssl: LOGIN, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], port=[64826], protocol=IMAP
 Dec 25 18:55:47 host imapd-ssl: DISCONNECTED, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], headers=0, body=0, rcvd=744, sent=15556, time=9, starttls=1
 Dec 25 18:55:48 host imapd-ssl: Connection, ip=[::ffff x.x.x.x]
 Dec 25 18:55:48 host imapd-ssl: LOGIN, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], port=[64829], protocol=IMAP
 Dec 25 18:56:32 host imapd-ssl: LOGOUT, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], headers=0, body=0, rcvd=124, sent=500, time=44, starttls=1

 This goes on and on.

 This a example from the logging without DISCONNECTED issue's while connected via local lan:

 Dec 21 00:27:12 host imapd-ssl: Connection, ip=[::ffff x.x.x.x]
 Dec 21 00:27:12 host imapd-ssl: Connection, ip=[::ffff x.x.x.x]
 Dec 21 00:27:12 host imapd-ssl: LOGIN, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], port=[1351], protocol=IMAP
 Dec 21 00:27:12 host imapd-ssl: LOGIN, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], port=[1352], protocol=IMAP
 Dec 21 00:27:13 host imapd-ssl: Connection, ip=[::ffff x.x.x.x]
 Dec 21 00:27:13 host imapd-ssl: Connection, ip=[::ffff x.x.x.x]
 Dec 21 00:27:13 host imapd-ssl: LOGIN, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], port=[1354], protocol=IMAP
 Dec 21 00:27:13 host imapd-ssl: LOGIN, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], port=[1356], protocol=IMAP
 Dec 21 00:27:13 host imapd-ssl: Connection, ip=[::ffff x.x.x.x]
 Dec 21 00:27:13 host imapd-ssl: LOGIN, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], port=[1358], protocol=IMAP
 Dec 21 00:28:19 host imapd-ssl: LOGOUT, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], headers=0, body=0, rcvd=8108, sent=93023, time=66, starttls=1
 Dec 21 00:28:19 host imapd-ssl: LOGOUT, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], headers=0, body=0, rcvd=65, sent=3718, time=67, starttls=1
 Dec 21 00:28:19 host imapd-ssl: LOGOUT, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], headers=0, body=4652, rcvd=13587, sent=283002, time=66, starttls=1
 Dec 21 00:28:19 host imapd-ssl: LOGOUT, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], headers=0, body=8948, rcvd=707, sent=12392, time=66, starttls=1
 Dec 21 00:28:19 host imapd-ssl: LOGOUT, [EMAIL="user=@emailaddress.com"]user=@emailaddress.com[/EMAIL], ip=[::ffff x.x.x.x], headers=0, body=0, rcvd=65, sent=6403, time=67, starttls=1

---

### Post by matt_symes on 2015-12-25
Thread moved to **Server Platforms**

You may get better help for your query in this forum.

---

### Post by Seb_Boffen on 2016-01-02
this was resolved by authenticating with a crt file instead of an pem file

---

