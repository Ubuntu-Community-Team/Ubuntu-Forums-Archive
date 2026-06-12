---
title: "I can't send mail using PostFix, I can only receive mail"
date: 2011-06-30
forum: Server Platforms
---

### Post by Linksku on 2011-06-30
I set up my mail server using the guide here: [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
I am able to receive mail, I can send mail locally, but I can't send to external addresses.

This is in my mail.log:
> Jun 30 14:40:43 Server postfix/smtp[10725]: 2FD9322015BF: to=<myemail@gmail.com>, relay=none, delay=1634, delays=1484/0.02/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.65.27]:25: Connection timed out)

This is my main.cf:
> myorigin = mysite.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
inet_interfaces = all

smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.mysite.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydomain = mysite.com
mydestination = $myhostname localhost.$mydomain localhost $mydomain
relay_domains =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
content_filter = smtp-amavis:[127.0.0.1]:10024
home_mailbox = Maildir/

---

### Post by Bachstelze on 2011-06-30
Can you telnet to the SMTP server on port 25? Maybe your ISP blocks this port, it's quite common.

---

### Post by Linksku on 2011-06-30
**telnet localhost 25** and **telnet mysite.com 25** both work. But **telnet hotmail.com 25**, **telnet mx2.hotmail.com 25**, etc do not work.

---

### Post by Bachstelze on 2011-06-30
I mean the SMTP server you are trying to connect to, which is alt4.gmail-smtp-in.l.google.com (74.125.65.27).

---

### Post by Linksku on 2011-06-30
That doesn't work either:
> root@Server:~# telnet alt4.gmail-smtp-in.l.google.com 25
Trying 74.125.95.27...
Then it just stays like that.

---

### Post by Linksku on 2011-06-30
I found out that my ISP (Rogers) only allows outbound mail relayed on their servers. I followed this person's advice:
> if anyone runs postfix as their MTA locally on a Rogers line, here are the quick steps to configure postfix to relay to the Rogers smtp servers.

You need to build postfix with Cyrus SASL (if you haven't already done so).

add the following lines to your postfix main.cf file..
#begin
# needed for rogers yaho sasl
smtp_sasl_auth_enable = yes
# leaving blank, indicates plain text.. which we need
smtp_sasl_security_options =
# location of your sasl_paswd file
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
# rogers/yahoo smtpd : port
relayhost = [smtp.broadband.rogers.com]:587
#end


edit the following file
$ cat /etc/postfix/sasl_passwd
smtp-rog.mail.yahoo2.akadns.net [email]rogers_email_address@rogers.com[/email]:rogers_password

after modifying sasl_passwd, run the following to build the sasl_passwd db
$ postmap /etc/postfix/sasl_passwd

Restart your postfix process..

if your machine is relaying successfully you should see the following in your mail logs..

Jul 1 04:19:22 tb303 postfix/smtp[30683]: 5C25D6B639: to=<XXX@myblackberry.com>, orig_to=<XXX@housejunkie.ca>, relay=smtp-rog.mail.yahoo2.akadns.net[206.190.36.18], delay=1, status=sent (250 ok 1120209643 qp 56045)


I tried sending an email and I get this in my mail.log, the email still didn't send:
> Jun 30 19:00:05 Server postfix/smtpd[22411]: connect from CPE0026829a2959-CM00252eac3806.cpe.net.cable.rogers.com[99.227.56.228]
Jun 30 19:00:05 Server postfix/smtpd[22411]: setting up TLS connection from CPE0026829a2959-CM00252eac3806.cpe.net.cable.rogers.com[99.227.56.228]
Jun 30 19:00:05 Server postfix/smtpd[22411]: SSL_accept error from CPE0026829a2959-CM00252eac3806.cpe.net.cable.rogers.com[99.227.56.228]: 0
Jun 30 19:00:05 Server postfix/smtpd[22411]: warning: TLS library problem: 22411:error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca:s3_pkt.c:1102:SSL alert number 48:
Jun 30 19:00:05 Server postfix/smtpd[22411]: lost connection after STARTTLS from CPE0026829a2959-CM00252eac3806.cpe.net.cable.rogers.com[99.227.56.228]
Jun 30 19:00:05 Server postfix/smtpd[22411]: disconnect from CPE0026829a2959-CM00252eac3806.cpe.net.cable.rogers.com[99.227.56.228]

Edit: I forgot to restart PostFix. I restarted PostFix, tried again and got this in mail.log:
> Jun 30 19:08:40 Server postfix/master[12414]: terminating on signal 15
Jun 30 19:08:41 Server postfix/master[22864]: daemon started -- version 2.8.2, configuration /etc/postfix
Jun 30 19:08:51 Server postfix/smtpd[22877]: connect from CPE0026829a2959-CM00252eac3806.cpe.net.cable.rogers.com[99.227.56.228]
Jun 30 19:08:51 Server postfix/smtpd[22877]: setting up TLS connection from CPE0026829a2959-CM00252eac3806.cpe.net.cable.rogers.com[99.227.56.228]
Jun 30 19:08:51 Server postfix/smtpd[22877]: Anonymous TLS connection established from cpe0026829a2959-cm00252eac3806.cpe.net.cable.rogers.com[99.227.56.228]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Jun 30 19:08:57 Server postfix/smtpd[22877]: 9B4FF2201591: client=CPE0026829a2959-CM00252eac3806.cpe.net.cable.rogers.com[99.227.56.228], sasl_method=PLAIN, sasl_username=leo
Jun 30 19:08:57 Server postfix/cleanup[22882]: 9B4FF2201591: message-id=<4E0D0203.3080105@linksku.com>
Jun 30 19:08:57 Server postfix/qmgr[22868]: 9B4FF2201591: from=<leo@linksku.com>, size=717, nrcpt=1 (queue active)
Jun 30 19:08:57 Server postfix/smtpd[22877]: disconnect from CPE0026829a2959-CM00252eac3806.cpe.net.cable.rogers.com[99.227.56.228]
Jun 30 19:08:57 Server dovecot: imap-login: Disconnected (no auth attempts): rip=99.227.56.228, lip=192.168.1.104, TLS
Jun 30 19:08:58 Server postfix/smtpd[22888]: connect from localhost[127.0.0.1]
Jun 30 19:08:58 Server postfix/smtpd[22888]: 0624A2201592: client=localhost[127.0.0.1]
Jun 30 19:08:58 Server postfix/cleanup[22882]: 0624A2201592: message-id=<4E0D0203.3080105@linksku.com>
Jun 30 19:08:58 Server postfix/smtpd[22888]: disconnect from localhost[127.0.0.1]
Jun 30 19:08:58 Server postfix/qmgr[22868]: 0624A2201592: from=<leo@linksku.com>, size=1188, nrcpt=1 (queue active)
Jun 30 19:08:58 Server amavis[10075]: (10075-02) Passed CLEAN, [99.227.56.228] [99.227.56.228] <leo@linksku.com> -> <leojiang000@gmail.com>, Message-ID: <4E0D0203.3080105@linksku.com>, mail_id: DgtTsRPYDHrV, Hits: -1, size: 717, queued_as: 0624A2201592, 393 ms
Jun 30 19:08:58 Server postfix/smtp[22883]: 9B4FF2201591: to=<leojiang000@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.47, delays=0.07/0.01/0/0.39, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 0624A2201592)
Jun 30 19:08:58 Server postfix/qmgr[22868]: 9B4FF2201591: removed
Jun 30 19:08:58 Server postfix/smtp[22889]: 0624A2201592: to=<leojiang000@gmail.com>, relay=smtp.broadband.rogers.com[98.139.221.125]:587, delay=0.25, delays=0.07/0.01/0.13/0.04, dsn=5.0.0, status=bounced (host smtp.broadband.rogers.com[98.139.221.125] said: 530 authentication required - for help go to [http://help.yahoo.com/help/us/mail/pop/pop-11.html](http://help.yahoo.com/help/us/mail/pop/pop-11.html) (in reply to MAIL FROM command))
Jun 30 19:08:58 Server postfix/cleanup[22882]: 5F29B2201593: message-id=<20110630230858.5F29B2201593@mail.linksku.com>
Jun 30 19:08:58 Server postfix/bounce[22890]: 0624A2201592: sender non-delivery notification: 5F29B2201593
Jun 30 19:08:58 Server postfix/qmgr[22868]: 5F29B2201593: from=<>, size=3321, nrcpt=1 (queue active)
Jun 30 19:08:58 Server postfix/qmgr[22868]: 0624A2201592: removed
Jun 30 19:08:58 Server postfix/local[22891]: 5F29B2201593: to=<leo@linksku.com>, relay=local, delay=0.12, delays=0.07/0/0/0.05, dsn=2.0.0, status=sent (delivered to maildir)
Jun 30 19:08:58 Server postfix/qmgr[22868]: 5F29B2201593: removed

---

### Post by SeijiSensei on 2011-07-01
Looks like Rogers uses "POP-before-SMTP," meaning you need to log in to one of their legitimate POP accounts before you can send.  Maybe you should try calling technical support and asking if there's another relay they can offer you that doesn't require POP logins.

Since I don't use Postfix, I can't tell you if it has an option to handle this situation.  Perhaps someone else can chime in here.

If you can't work this out with Rogers, browse some of the recent threads for related postings.  One member reported that he had signed up with a third-party relaying firm that charges something like $25/year.  That might have only handled inbound mail, but you should take a look and see if that's a solution for you as well.

---

