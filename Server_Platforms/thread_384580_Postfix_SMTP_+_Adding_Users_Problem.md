---
title: "Postfix SMTP + Adding Users Problem"
date: 2007-03-14
forum: Server Platforms
---

### Post by Zuph on 2007-03-14
I'm running an Ubuntu 6.06 server in a local network that has NO ACCESS to the outside internet.  I have a DNS server on the local network.

My postfix install is a very basic one, from the community documentation.  At that point, I tested the install by creating another use (fmaster).  Email sent and received from both with no issue.  I then installed courier and squirrelmail, both very basic installs.  Testing these, mail could be sent and received between fmaster and admin (my administrative account) perfectly, but upon creating a new user (BradLuyster), I ran into problems.  I could not sent mail to this use from any account.

In an attempt to solve the problem, I copied the Maildir directory structure from fmaster to BradLuyster, and chowned the directory structure to BradLuyster.  Now, BradLuyster could log into squirrelmail and SEND email to other users, but email could not be sent TO BradLuyster still.

I'm at my wits end.  I've tried (in main.cf) setting local_recipient_maps to all the values indicated in main.cf.dist, to no avail.  I've read the postfix documentation on local_recipient_maps, and it hasn't addressed my situation.

The exact error postfix will throw is a 550 user not in local recipient table error.

Here are some associated files:

the result of postconf -n:
```
root@marathon:~# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
local_recipient_maps =
mailbox_command =
mailbox_size_limit = 0
mydestination = marathon.localdomain, localhost.localdomain, marathon.krcfl.lan, krcfl.lan, localhost
myhostname = marathon.krcfl.lan
mynetworks = 127.0.0.0/8, 192.170.0.0/24
myorigin = /etc/mailname
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes

```

The last section of /var/log/mail.info:

```
Mar 14 16:08:08 marathon postfix/smtpd[4620]: disconnect from localhost[127.0.0.1]
Mar 14 16:08:08 marathon postfix/smtpd[4620]: connect from localhost[127.0.0.1]
Mar 14 16:08:08 marathon postfix/smtpd[4620]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <BradLuyster@krcfl.lan>: Recipient address rejected: User unknown in local recipient table; from=<admin@krcfl.lan> to=<BradLuyster@krcfl.lan> proto=ESMTP helo=<mail.krcfl.lan>
Mar 14 16:08:08 marathon postfix/smtpd[4620]: lost connection after RCPT from localhost[127.0.0.1]
Mar 14 16:08:08 marathon postfix/smtpd[4620]: disconnect from localhost[127.0.0.1]
Mar 14 16:08:09 marathon postfix/smtpd[4620]: connect from localhost[127.0.0.1]
Mar 14 16:08:09 marathon postfix/smtpd[4620]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <BradLuyster@krcfl.lan>: Recipient address rejected: User unknown in local recipient table; from=<admin@krcfl.lan> to=<BradLuyster@krcfl.lan> proto=ESMTP helo=<mail.krcfl.lan>
Mar 14 16:08:09 marathon postfix/smtpd[4620]: lost connection after RCPT from localhost[127.0.0.1]
Mar 14 16:08:09 marathon postfix/smtpd[4620]: disconnect from localhost[127.0.0.1]
Mar 14 16:08:19 marathon postfix/smtpd[4620]: connect from localhost[127.0.0.1]
Mar 14 16:08:19 marathon postfix/smtpd[4620]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <BradLuyster@marathon.krcfl.lan>: Recipient address rejected: User unknown in local recipient table; from=<admin@krcfl.lan> to=<BradLuyster@marathon.krcfl.lan> proto=ESMTP helo=<mail.krcfl.lan>
Mar 14 16:08:19 marathon postfix/smtpd[4620]: lost connection after RCPT from localhost[127.0.0.1]
Mar 14 16:08:19 marathon postfix/smtpd[4620]: disconnect from localhost[127.0.0.1]
Mar 14 16:08:20 marathon postfix/smtpd[4620]: connect from localhost[127.0.0.1]
Mar 14 16:08:20 marathon postfix/smtpd[4620]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <BradLuyster@marathon.krcfl.lan>: Recipient address rejected: User unknown in local recipient table; from=<admin@krcfl.lan> to=<BradLuyster@marathon.krcfl.lan> proto=ESMTP helo=<mail.krcfl.lan>
Mar 14 16:08:20 marathon postfix/smtpd[4620]: lost connection after RCPT from localhost[127.0.0.1]
Mar 14 16:08:20 marathon postfix/smtpd[4620]: disconnect from localhost[127.0.0.1]
Mar 14 16:08:20 marathon postfix/smtpd[4620]: connect from localhost[127.0.0.1]
Mar 14 16:08:20 marathon postfix/smtpd[4620]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <BradLuyster@marathon.krcfl.lan>: Recipient address rejected: User unknown in local recipient table; from=<admin@krcfl.lan> to=<BradLuyster@marathon.krcfl.lan> proto=ESMTP helo=<mail.krcfl.lan>
Mar 14 16:08:20 marathon postfix/smtpd[4620]: lost connection after RCPT from localhost[127.0.0.1]
Mar 14 16:08:20 marathon postfix/smtpd[4620]: disconnect from localhost[127.0.0.1]
Mar 14 16:14:38 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:14:38 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:21:39 marathon postfix/smtpd[4668]: connect from localhost[127.0.0.1]
Mar 14 16:21:39 marathon postfix/smtpd[4668]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <BradLuyster@marathon.krcfl.lan>: Recipient address rejected: User unknown in local recipient table; from=<admin@krcfl.lan> to=<BradLuyster@marathon.krcfl.lan> proto=ESMTP helo=<mail.krcfl.lan>
Mar 14 16:21:39 marathon postfix/smtpd[4668]: lost connection after RCPT from localhost[127.0.0.1]
Mar 14 16:21:39 marathon postfix/smtpd[4668]: disconnect from localhost[127.0.0.1]
Mar 14 16:21:41 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:21:42 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=709, body=0, time=1
Mar 14 16:21:49 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:21:49 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:21:49 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:21:49 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:21:49 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:21:49 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:22:04 marathon postfix/pickup[4618]: 2F48647203: uid=0 from=<root>
Mar 14 16:22:04 marathon postfix/cleanup[4690]: 2F48647203: message-id=<20070314202204.2F48647203@marathon.krcfl.lan>
Mar 14 16:22:04 marathon postfix/qmgr[4619]: 2F48647203: from=<root@krcfl.lan>, size=295, nrcpt=1 (queue active)
Mar 14 16:22:04 marathon postfix/local[4691]: 2F48647203: to=<BradLuyster@localhost>, relay=local, delay=0, status=bounced (unknown user: "bradluyster")
Mar 14 16:22:04 marathon postfix/cleanup[4690]: 6B69C47402: message-id=<20070314202204.6B69C47402@marathon.krcfl.lan>
Mar 14 16:22:04 marathon postfix/qmgr[4619]: 6B69C47402: from=<>, size=1943, nrcpt=1 (queue active)
Mar 14 16:22:04 marathon postfix/qmgr[4619]: 2F48647203: removed
Mar 14 16:22:04 marathon postfix/local[4691]: 6B69C47402: to=<admin@krcfl.lan>, orig_to=<root@krcfl.lan>, relay=local, delay=0, status=sent (delivered to maildir)
Mar 14 16:22:04 marathon postfix/qmgr[4619]: 6B69C47402: removed
Mar 14 16:22:06 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:06 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:22:07 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:07 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=1
Mar 14 16:22:07 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:08 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=1
Mar 14 16:22:08 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:08 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:22:10 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:10 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=1
Mar 14 16:22:10 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:10 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:22:10 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:10 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:22:10 marathon imaplogin: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:10 marathon imaplogin: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:22:18 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:18 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:22:19 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:19 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:22:19 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:19 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=978, body=0, time=0
Mar 14 16:22:21 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:21 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=955, time=0
Mar 14 16:22:24 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:22:24 marathon imaplogin: DISCONNECTED, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=296, time=0
Mar 14 16:24:09 marathon postfix/master[4616]: terminating on signal 15
Mar 14 16:24:11 marathon postfix/master[4824]: daemon started -- version 2.2.10, configuration /etc/postfix
Mar 14 16:24:23 marathon postfix/smtpd[4828]: connect from unknown[192.170.0.17]
Mar 14 16:24:23 marathon postfix/smtpd[4828]: disconnect from unknown[192.170.0.17]
Mar 14 16:24:34 marathon courierpop3login: LOGIN, user=BradLuyster, ip=[::ffff:127.0.0.1]
Mar 14 16:24:39 marathon courierpop3login: LOGOUT, user=BradLuyster, ip=[::ffff:127.0.0.1], top=0, retr=0, time=5
Mar 14 16:24:51 marathon postfix/smtpd[4828]: connect from unknown[192.170.0.17]
Mar 14 16:24:51 marathon postfix/smtpd[4828]: disconnect from unknown[192.170.0.17]
Mar 14 16:25:06 marathon courierpop3login: LOGIN, user=BradLuyster, ip=[::ffff:192.170.0.17]
Mar 14 16:25:06 marathon courierpop3login: LOGOUT, user=BradLuyster, ip=[::ffff:192.170.0.17], top=0, retr=0, time=0
Mar 14 16:25:11 marathon postfix/smtpd[4828]: connect from unknown[192.170.0.17]
Mar 14 16:25:11 marathon postfix/smtpd[4828]: disconnect from unknown[192.170.0.17]
Mar 14 16:25:16 marathon postfix/smtpd[4838]: connect from unknown[192.170.0.17]
Mar 14 16:25:16 marathon postfix/smtpd[4838]: disconnect from unknown[192.170.0.17]
Mar 14 16:25:24 marathon postfix/smtpd[4828]: connect from unknown[192.170.0.17]
Mar 14 16:25:24 marathon postfix/smtpd[4828]: disconnect from unknown[192.170.0.17]
Mar 14 16:25:31 marathon postfix/smtpd[4828]: connect from localhost[127.0.0.1]
Mar 14 16:25:32 marathon postfix/smtpd[4838]: connect from unknown[192.170.0.17]
Mar 14 16:25:32 marathon postfix/smtpd[4838]: disconnect from unknown[192.170.0.17]
Mar 14 16:26:13 marathon postfix/smtpd[4828]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <bradluyster@krcfl.lan>: Recipient address rejected: User unknown in local recipient table; from=<admin> to=<bradluyster@krcfl.lan> proto=ESMTP helo=<dreelf.krcfl.lan>
Mar 14 16:26:22 marathon postfix/smtpd[4828]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <bradluyster>: Recipient address rejected: User unknown in local recipient table; from=<admin> to=<bradluyster> proto=ESMTP helo=<dreelf.krcfl.lan>
Mar 14 16:26:35 marathon postfix/smtpd[4828]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <bradluyster@marathon.localdomain>: Recipient address rejected: User unknown in local recipient table; from=<admin> to=<bradluyster@marathon.localdomain> proto=ESMTP helo=<dreelf.krcfl.lan>
Mar 14 16:29:33 marathon postfix/smtpd[4828]: disconnect from localhost[127.0.0.1]
Mar 14 16:30:06 marathon postfix/master[4824]: terminating on signal 15
Mar 14 16:30:08 marathon postfix/master[4929]: daemon started -- version 2.2.10, configuration /etc/postfix
Mar 14 16:30:18 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:30:18 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=978, body=0, time=0
Mar 14 16:30:19 marathon postfix/smtpd[4933]: connect from unknown[192.170.0.17]
Mar 14 16:30:19 marathon postfix/smtpd[4933]: disconnect from unknown[192.170.0.17]
Mar 14 16:30:20 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:30:20 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=387, time=0
Mar 14 16:30:22 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:30:22 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=387, time=0
Mar 14 16:30:26 marathon postfix/smtpd[4933]: connect from localhost[127.0.0.1]
Mar 14 16:30:26 marathon postfix/smtpd[4933]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <BradLuyster@krcfl.lan>: Recipient address rejected: User unknown in local recipient table; from=<admin@krcfl.lan> to=<BradLuyster@krcfl.lan> proto=ESMTP helo=<mail.krcfl.lan>
Mar 14 16:30:26 marathon postfix/smtpd[4933]: lost connection after RCPT from localhost[127.0.0.1]
Mar 14 16:30:26 marathon postfix/smtpd[4933]: disconnect from localhost[127.0.0.1]
Mar 14 16:30:28 marathon postfix/smtpd[4933]: connect from localhost[127.0.0.1]
Mar 14 16:30:28 marathon postfix/smtpd[4933]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 <BradLuyster@krcfl.lan>: Recipient address rejected: User unknown in local recipient table; from=<admin@krcfl.lan> to=<BradLuyster@krcfl.lan> proto=ESMTP helo=<mail.krcfl.lan>
Mar 14 16:30:28 marathon postfix/smtpd[4933]: lost connection after RCPT from localhost[127.0.0.1]
Mar 14 16:30:28 marathon postfix/smtpd[4933]: disconnect from localhost[127.0.0.1]
Mar 14 16:31:56 marathon postfix/master[4929]: terminating on signal 15
Mar 14 16:31:58 marathon postfix/master[5039]: daemon started -- version 2.2.10, configuration /etc/postfix
Mar 14 16:31:59 marathon postfix/smtpd[5043]: connect from localhost[127.0.0.1]
Mar 14 16:31:59 marathon postfix/smtpd[5043]: 50864471FD: client=localhost[127.0.0.1]
Mar 14 16:31:59 marathon postfix/cleanup[5046]: 50864471FD: message-id=<4591.192.170.0.17.1173904319.squirrel@mail.krcfl.lan>
Mar 14 16:31:59 marathon postfix/smtpd[5043]: disconnect from localhost[127.0.0.1]
Mar 14 16:31:59 marathon postfix/qmgr[5042]: 50864471FD: from=<admin@krcfl.lan>, size=852, nrcpt=1 (queue active)
Mar 14 16:31:59 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:31:59 marathon postfix/local[5049]: 50864471FD: to=<BradLuyster@krcfl.lan>, relay=local, delay=0, status=bounced (unknown user: "bradluyster")
Mar 14 16:31:59 marathon postfix/cleanup[5046]: 9697E47402: message-id=<20070314203159.9697E47402@marathon.krcfl.lan>
Mar 14 16:31:59 marathon postfix/qmgr[5042]: 9697E47402: from=<>, size=2568, nrcpt=1 (queue active)
Mar 14 16:31:59 marathon postfix/qmgr[5042]: 50864471FD: removed
Mar 14 16:31:59 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:31:59 marathon postfix/local[5049]: 9697E47402: to=<admin@krcfl.lan>, relay=local, delay=0, status=sent (delivered to maildir)
Mar 14 16:31:59 marathon postfix/qmgr[5042]: 9697E47402: removed
Mar 14 16:32:00 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:32:00 marathon imaplogin: DISCONNECTED, user=admin, ip=[::ffff:127.0.0.1], headers=1248, body=0, time=0
Mar 14 16:32:00 marathon postfix/smtpd[5043]: connect from localhost[127.0.0.1]
Mar 14 16:32:00 marathon postfix/smtpd[5043]: 4BEB5471FD: client=localhost[127.0.0.1]
Mar 14 16:32:00 marathon postfix/cleanup[5046]: 4BEB5471FD: message-id=<4592.192.170.0.17.1173904320.squirrel@mail.krcfl.lan>
Mar 14 16:32:00 marathon postfix/qmgr[5042]: 4BEB5471FD: from=<admin@krcfl.lan>, size=852, nrcpt=1 (queue active)
Mar 14 16:32:00 marathon postfix/smtpd[5043]: disconnect from localhost[127.0.0.1]
Mar 14 16:32:00 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:32:00 marathon postfix/local[5049]: 4BEB5471FD: to=<BradLuyster@krcfl.lan>, relay=local, delay=0, status=bounced (unknown user: "bradluyster")
Mar 14 16:32:00 marathon postfix/cleanup[5046]: 7CE4847402: message-id=<20070314203200.7CE4847402@marathon.krcfl.lan>
Mar 14 16:32:00 marathon postfix/qmgr[5042]: 7CE4847402: from=<>, size=2568, nrcpt=1 (queue active)
Mar 14 16:32:00 marathon postfix/qmgr[5042]: 4BEB5471FD: removed
Mar 14 16:32:00 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Mar 14 16:32:00 marathon postfix/local[5049]: 7CE4847402: to=<admin@krcfl.lan>, relay=local, delay=0, status=sent (delivered to maildir)
Mar 14 16:32:00 marathon postfix/qmgr[5042]: 7CE4847402: removed
Mar 14 16:32:00 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:32:00 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=1518, body=0, time=0
Mar 14 16:32:02 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:32:02 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=989, time=0
Mar 14 16:32:16 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:32:16 marathon imaplogin: DISCONNECTED, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=297, time=0
Mar 14 16:32:19 marathon imaplogin: LOGIN, user=admin, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 14 16:32:19 marathon imaplogin: LOGOUT, user=admin, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0

```

Does anyone have any insight?

---

### Post by MJN on 2007-03-14
The config looks fine to me but then with these things it's often all too easy to not see the wood for the trees.

I noticed you kept mentioning the user 'BradLuyster' i.e. with capitals. Was this intended? I could be wrong but aren't system usernames case-sensitive? Or, more to the point, Postfix is downcasing the addresses and hence could be unable to find the user in lowercase form.

Try changing the user BradLuyster to be lower case....

Mathew

---

### Post by Zuph on 2007-03-15
> **MJN said:**
> The config looks fine to me but then with these things it's often all too easy to not see the wood for the trees.

I noticed you kept mentioning the user 'BradLuyster' i.e. with capitals. Was this intended? I could be wrong but aren't system usernames case-sensitive? Or, more to the point, Postfix is downcasing the addresses and hence could be unable to find the user in lowercase form.

Try changing the user BradLuyster to be lower case....

Mathew

Bingo, that was the problem.  Now I'm having trouble getting outlook to connect to the SMTP #-o

---

