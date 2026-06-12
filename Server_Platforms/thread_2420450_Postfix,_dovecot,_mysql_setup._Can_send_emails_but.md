---
title: "Postfix, dovecot, mysql setup. Can send emails but can't receive."
date: 2019-06-05
forum: Server Platforms
---

### Post by sayari on 2019-06-05
[SIZE=2][FONT=arial]I have Postfix, Dovecot and mysql setup my server on Ubuntu Server 18.04 on my Raspberry Pi. I'm able to send e-mails using both SMTP and Postfix, however I'm unable to retrieve e-mails from the internet. I get the error: "550 5.1.1 <example@123.com>: Recipient address rejected: User unknown in virtual mailbox table

I have the correct email written in, just changed for this post. It should be able to access the SQL server with the email address to receive the message, but it doesn't. I have no error logs whatsoever. All the correct ports, to my knowledge(?) are forwarded.

This is my mysql-virtual-mailbox-domains.cf:
[/FONT][/SIZE][SIZE=2][FONT=arial]user = mailuser[/FONT][/SIZE]
[SIZE=2][FONT=arial]password = -zip-[/FONT][/SIZE]
[SIZE=2][FONT=arial]hosts = 127.0.0.1[/FONT][/SIZE]
[SIZE=2][FONT=arial]dbname = mailserver[/FONT][/SIZE]
[SIZE=2][FONT=arial]query = SELECT 1 FROM virtual_domains WHERE name='%s'[/FONT][/SIZE]

[SIZE=2][FONT=arial]
This is my mysql-virtual-mailbox-maps.cf:
[/FONT][/SIZE][SIZE=2][FONT=arial]user = mailuser[/FONT][/SIZE]
[SIZE=2][FONT=arial]password = -zip-[/FONT][/SIZE]
[SIZE=2][FONT=arial]hosts = 127.0.0.1[/FONT][/SIZE]
[SIZE=2][FONT=arial]dbname = mailserver[/FONT][/SIZE]
[SIZE=2][FONT=arial]query = SELECT 1 FROM virtual_domains WHERE name='%s'

This is my mysql-virtual-email2email.cf:
[/FONT][/SIZE][SIZE=2][FONT=arial]user = mailuser[/FONT][/SIZE]
[SIZE=2][FONT=arial]password = -zip-[/FONT][/SIZE]
[SIZE=2][FONT=arial]hosts = 127.0.0.1[/FONT][/SIZE]
[SIZE=2][FONT=arial]dbname = mailserver[/FONT][/SIZE]
[SIZE=2][FONT=arial]query = SELECT email FROM virtual_users WHERE email='%s'[/FONT][/SIZE]
[SIZE=2][FONT=arial]
This is my mysql-virtual-alias-maps.cf:
[/FONT][/SIZE][SIZE=2][FONT=arial]user = mailuser[/FONT][/SIZE]
[SIZE=2][FONT=arial]password = -zip-[/FONT][/SIZE]
[SIZE=2][FONT=arial]hosts = 127.0.0.1[/FONT][/SIZE]
[SIZE=2][FONT=arial]dbname = mailserver[/FONT][/SIZE]
[SIZE=2][FONT=arial]query = SELECT destination FROM virtual_aliases WHERE source='%s'


[/FONT][/SIZE]


[SIZE=2][FONT=arial]There haven't been errors in my mail.err log since I fixed the last error I had. The only errors in my mail.log are for smtp.
There are some things in my dovecot log: 
[/FONT][/SIZE][SIZE=2][FONT=arial]Jun 05 20:05:30 imap-login: Info: Disconnected (disconnected before auth was ready, waited 0 secs): user=<>, rip=198.199.98.246, lip=192.168.2.100, TLS handshaking: SSL_accept() syscall failed: Success, session=<uDDVeJyKI7vGx2L2>[/FONT][/SIZE]
[SIZE=2][FONT=arial]Jun 05 20:05:34 pop3-login: Info: Disconnected (no auth attempts in 0 secs): user=<>, rip=198.199.98.246, lip=192.168.2.100, TLS handshaking: SSL_accept() syscall failed: Success, session=<JCQbeZyKNufGx2L2>[/FONT][/SIZE]
[SIZE=2][FONT=arial]Jun 05 20:06:34 pop3-login: Info: Disconnected (no auth attempts in 0 secs): user=<>, rip=45.33.50.110, lip=192.168.2.100, TLS handshaking: SSL_accept() syscall failed: Success, session=<kqSkfJyKnp0tITJu>[/FONT][/SIZE]
[SIZE=2][FONT=arial]Jun 05 20:17:20 pop3-login: Info: Disconnected (no auth attempts in 0 secs): user=<>, rip=52.202.215.126, lip=192.168.2.100, TLS handshaking: SSL_accept() syscall failed: Success, session=<9j4po5yKrss0ytd+>

Nothing abnormal in mysql log:
[/FONT][/SIZE][SIZE=2][FONT=arial]2019-06-05T19:08:56.681796Z 0 [Note] Plugin 'FEDERATED' is disabled.[/FONT][/SIZE]
[SIZE=2][FONT=arial]2019-06-05T19:08:56.708869Z 0 [Note] Found ca.pem, server-cert.pem and server-key.pem in data directory. Trying to enable SSL support using them.[/FONT][/SIZE]
[SIZE=2][FONT=arial]2019-06-05T19:08:56.723909Z 0 [Note] InnoDB: Buffer pool(s) load completed at 190605 15:08:56[/FONT][/SIZE]
[SIZE=2][FONT=arial]2019-06-05T19:08:56.733958Z 0 [Warning] CA certificate ca.pem is self signed.[/FONT][/SIZE]
[SIZE=2][FONT=arial]2019-06-05T19:08:56.759777Z 0 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306[/FONT][/SIZE]
[SIZE=2][FONT=arial]2019-06-05T19:08:56.759919Z 0 [Note]   - '127.0.0.1' resolves to '127.0.0.1';[/FONT][/SIZE]
[SIZE=2][FONT=arial]2019-06-05T19:08:56.760123Z 0 [Note] Server socket created on IP: '127.0.0.1'.[/FONT][/SIZE]
[SIZE=2][FONT=arial]2019-06-05T19:08:56.835143Z 0 [Note] Event Scheduler: Loaded 0 events[/FONT][/SIZE]
[SIZE=2][FONT=arial]2019-06-05T19:08:56.836233Z 0 [Note] /usr/sbin/mysqld: ready for connections.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Version: '5.7.26-0ubuntu0.18.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)[/FONT][/SIZE]


I'm able to send through using smtp fine:
Jun  5 20:54:43 -snip- postfix/pickup[4134]: 1E8897A413: uid=0 from=<-snip-@-snip-.com>
Jun  5 20:54:43 -snip- postfix/cleanup[4361]: 1E8897A413: message-id=<20190606005443.1E8897A413@-snip-.com>
Jun  5 20:54:43 -snip- postfix/qmgr[3080]: 1E8897A413: from=<-snip-@-snip-.com>, size=396, nrcpt=1 (queue active)
Jun  5 20:54:46 -snip- postfix/smtp[4366]: 1E8897A413: to=<-snip-@gmail.com>, relay=gmail-smtp-in.l.google.com[108.177.120.26]:25, delay=3.1, delays=0.82/1/0.65/0.56, dsn=2.0.0, status=sent (250 2.0.0 OK  1559782486 v62si259342jaa.67 - gsmtp)
Jun  5 20:54:46 -snip- postfix/qmgr[3080]: 1E8897A413: removed


If any configuration files are needed, I'll provide them. I'm not sure what else is necessary.

Thanks.

---

