---
title: "Postfix log files claim mail sent but never mail arrives"
date: 2014-01-05
forum: Server Platforms
---

### Post by roy-bottomley on 2014-01-05
Hi guys
I would really appreciate any pointers on where to look next to get my Postfix/Dovecot running.
I have it almost running but the situation I am left in is that the Postfix log files claims  the mail has been sent but the mail never arrives( i can definitely send to the  email address from elsewhere)
If i try sendmail -bv [EMAIL="kimberley.bottomley@virginmedia.com"]kimberley.bottomley@virginmedia.com[/EMAIL] postfix says the mail is deliverable, and sendmail -v looks ok as well.
below is the log output, the mail I received when using sendmail -bv and sendmail -v , and postconf -n output.

I'd be grateful of any help on where to go next, i've run out of strings to pull, the log files look ok to me and I just don't know how to proceed with debugging this.


Log file
Jan  4 14:22:19 localhost postfix/submission/smtpd[11037]: connect from unknown[198.199.124.252]
Jan  4 14:22:19 localhost postfix/submission/smtpd[11037]: 45AF442A68:  client=unknown[198.199.124.252], sasl_method=PLAIN, sasl_username=admin
Jan  4 14:22:19 localhost postfix/cleanup[11042]: 45AF442A68:  message-id=<52c8191ad974b_2b10c41e1855446@behappyhost.mail  >
Jan  4 14:22:19 localhost postfix/submission/smtpd[11037]: disconnect from unknown[198.199.124.252]
Jan  4 14:22:19 localhost postfix/qmgr[9011]: 45AF442A68:  from=<admin@traintobehappy.com>, size=1090, nrcpt=1 (queue active)
Jan  4 14:22:19 localhost postfix/smtp[11043]: 45AF442A68:  to=<kimberley.bottomley@virginmedia.com>,  relay=aspmx.l.google.com[173.194.70.27]:25, delay=0.6,  delays=0.05/0.01/0.27/0.27, dsn=2.0.0, status=sent (250 2.0.0 OK  1388845339 m49si75713217eeg.178 - gsmtp)

postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = ipv4
local_recipient_maps = proxy:unix[IMG]http://www.howtoforge.com/forums/images/smilies/tongue.gif[/IMG]asswd.byname $alias_maps
mailbox_size_limit = 0
mydestination = mail.traintobehappy.com, traintobehappy.com, localhost, localhost.localdomain
myhostname = mail.traintobehappy.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
smtpd_tls_cert_file = /etc/ssl/private/mail.traintobehappy.crt
smtpd_tls_key_file = /etc/ssl/private/mail.key
smtpd_tls_protocols = !SSLv2, !SSLv3
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

reply from sendmail -v
This is the mail system at host mail.traintobehappy.com.

Enclosed is the mail delivery report that you requested.

                   The mail system

<kimberley.bottomley@virginmedia.com>: delivery via
    aspmx.l.google.com[173.194.70.27]:25: 250 2.0.0 OK 1388846660
    m49si75804958eeg.199 - gsmtp



Reporting-MTA: dns; mail.traintobehappy.com
X-Postfix-Queue-ID: 2872E42AC0
X-Postfix-Sender: rfc822; [EMAIL="roy@traintobehappy.com"]roy@traintobehappy.com[/EMAIL]
Arrival-Date: Sat,  4 Jan 2014 14:44:15 +0000 (UTC)

Final-Recipient: rfc822; [EMAIL="kimberley.bottomley@virginmedia.com"]kimberley.bottomley@virginmedia.com[/EMAIL]
Action: relayed
Status: 2.0.0
Remote-MTA: dns; aspmx.l.google.com
Diagnostic-Code: smtp; 250 2.0.0 OK 1388846660 m49si75804958eeg.199 - gsmtp



Return-Path: <roy@traintobehappy.com>
Received: by mail.traintobehappy.com (Postfix, from userid 1000)
	id 2872E42AC0; Sat,  4 Jan 2014 14:44:20 +0000 (UTC)
Message-Id: <20140104144420.2872E42AC0@mail.traintobehappy.com  >
Date: Sat,  4 Jan 2014 14:44:15 +0000 (UTC)
From: [EMAIL="roy@traintobehappy.com"]roy@traintobehappy.com[/EMAIL]

reply from sendmail -bv
This is the mail system at host mail.traintobehappy.com.

Enclosed is the mail delivery report that you requested.

                   The mail system

<kimberley.bottomley@virginmedia.com>: delivery via
    aspmx.l.google.com[173.194.70.27]:25: 250 2.1.5 OK a9si75865444eew.33 -
    gsmtp



Reporting-MTA: dns; mail.traintobehappy.com
X-Postfix-Queue-ID: 179A242AC0
X-Postfix-Sender: rfc822; [EMAIL="roy@traintobehappy.com"]roy@traintobehappy.com[/EMAIL]
Arrival-Date: Sat,  4 Jan 2014 14:41:59 +0000 (UTC)

Final-Recipient: rfc822; [EMAIL="kimberley.bottomley@virginmedia.com"]kimberley.bottomley@virginmedia.com[/EMAIL]
Action: deliverable
Status: 2.1.5
Remote-MTA: dns; aspmx.l.google.com
Diagnostic-Code: smtp; 250 2.1.5 OK a9si75865444eew.33 - gsmtp



Return-Path: <roy@traintobehappy.com>
Received: by mail.traintobehappy.com (Postfix, from userid 1000)
	id 179A242AC0; Sat,  4 Jan 2014 14:41:59 +0000 (UTC)
From: [EMAIL="roy@traintobehappy.com"]roy@traintobehappy.com[/EMAIL]
Subject: probe
To:	[EMAIL="kimberley.bottomley@virginmedia.com"]kimberley.bottomley@virginmedia.com[/EMAIL]
Message-Id: <20140104144159.179A242AC0@mail.traintobehappy.com  >
Date: Sat,  4 Jan 2014 14:41:59 +0000 (UTC)

---

### Post by SeijiSensei on 2014-01-05
Maybe it was tagged as spam at gmail?  Did the recipient check her spam folder?

---

