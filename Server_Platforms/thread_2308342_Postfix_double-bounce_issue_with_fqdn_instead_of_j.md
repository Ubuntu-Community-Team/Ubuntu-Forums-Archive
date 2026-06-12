---
title: "Postfix double-bounce issue with fqdn instead of just using domain name"
date: 2016-01-02
forum: Server Platforms
---

### Post by Seb_Boffen on 2016-01-02
Jan  2 11:05:17 svr1 postfix/smtpd[10361]: NOQUEUE: reject: RCPT from google.com[x.x.x.x]: 450 4.1.2 double-bounce@fqnd: Recipient address rejected: Domain not found; from=<> to=double-bounce@fqnd proto=ESMTP helo=<google.com>
Jan  2 11:05:17 svr1 postfix/smtpd[10361]: disconnect from google.com[x.x.x.x]

Issue started when I placed an backup over an new install and never had the issue before, did search google for double-bounce@$mydomain but ended up with main.cf: double_bounce_sender = double-bounce@domainname and still sending to double_bounce_sender = double-bounce@fqnd and google replies: double-bounce@fqnd: Recipient address rejected: Domain not found; from=<>

Postfix email sents and recieves fine, but log is overloaded with the above. I noticed the fqnd being used in the log is my former domain name: srv1 instead of the new domain name svr1

tried to run sudo postsuper -d ALL and run dpkg-reconfigure postfix

Jan  3 13:22:28 svr1 postfix/smtpd[4161]: connect from mail-lf0-f101.google.com[209.85.215.101]
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: setting up TLS connection from mail-lf0-f101.google.com[209.85.215.101]
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: mail-lf0-f101.google.com[209.85.215.101]: TLS cipher list "aNULL:-aNULL:ALL:+RC4:@STRENGTH"
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:before/accept initialization
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 read client hello A
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 write server hello A
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 write certificate A
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 write key exchange A
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 write server done A
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 flush data
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 read client key exchange A
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 read finished A
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 write change cipher spec A
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 write finished A
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: SSL_accept:SSLv3 flush data
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: mail-lf0-f101.google.com[209.85.215.101]: save session D221AE52662765CD31B3F120056F69103DA1DC029E8A0919D7D41ABEBAF8A53A&s=smtp&l=268439663 to smtpd cache
Jan  3 13:22:29 svr1 postfix/tlsmgr[4163]: put smtpd session id=D221AE52662765CD31B3F120056F69103DA1DC029E8A0919D7D41ABEBAF8A53A&s=smtp&l=268439663 [data 159 bytes]
Jan  3 13:22:29 svr1 postfix/tlsmgr[4163]: write smtpd TLS cache entry D221AE52662765CD31B3F120056F69103DA1DC029E8A0919D7D41ABEBAF8A53A&s=smtp&l=268439663: time=1451823749 [data 159 bytes]
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: Anonymous TLS connection established from mail-lf0-f101.google.com[209.85.215.101]: TLSv1.2 with cipher ECDHE-RSA-AES128-GCM-SHA256 (128/128 bits)
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: NOQUEUE: reject: RCPT from mail-lf0-f101.google.com[209.85.215.101]: 454 4.7.1 [EMAIL="double-bounce@srv1.domain.com"]double-bounce@srv1.domain.com[/EMAIL]: Relay access denied; from=<> to=[EMAIL="double-bounce@srv1.domain.com"]double-bounce@srv1.domain.com[/EMAIL] proto=ESMTP helo=<mail-lf0-f101.google.com>
Jan  3 13:22:29 svr1 postfix/smtpd[4161]: disconnect from mail-lf0-f101.google.com[209.85.215.101]

Resolved the issue by adding in main.cf relay domains = former hostname and the current domainname this got the messages delivered the logfile cleared.
Also a temporary dns record was created for the former hostname at the domain registrar. And in the local dns server.

---

