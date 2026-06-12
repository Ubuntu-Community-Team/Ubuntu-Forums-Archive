---
title: "TLS is not working in Postfix"
date: 2009-03-20
forum: Server Platforms
---

### Post by thundersnows on 2009-03-20
Hi,
I just installed Postfix and everything working fine except TLS.
I followed this tutorial
[http://workaround.org/articles/ispmail-etch/#step-10-amavis-filtering-spam-and-viruses]("http://workaround.org/articles/ispmail-etch/#step-10-amavis-filtering-spam-and-viruses")

When I send email from Outlook Express, I got error message 
> The server does not support a SSL connection. Account: 'Postfix', Server: '192.168.171.130', Protocol: SMTP, Server Response: '250 DSN', Port: 25, Secure(SSL): Yes, Server Error: 250, Error Number: 0x800CCC7D

and this from mail.log
> Mar 20 03:10:38 mailserver postfix/smtpd[12783]: connect from unknown[192.168.171.1]
Mar 20 03:10:38 mailserver postfix/smtpd[12783]: lost connection after EHLO from unknown[192.168.171.1]

When I send email from Thunderbird (I checked TLS on the setting), I got message 
> Sending of message failed.
An error occured sending mail: Unable to connect to SMTP Server 192.168.171.130 via STARTTLS since it doesn't offer STARTTLS In EHLO response. Please verify that your Mail/News account settings are correct and try again.

and this is from the mail.log
> 
Mar 20 03:24:48 mailserver postfix/smtpd[13017]: connect from unknown[192.168.171.1]
Mar 20 03:24:48 mailserver postfix/smtpd[13017]: disconnect from unknown[192.168.171.1]


I am able to POP3 using POP3 (port 995) only, but there is a message that the certificate certificate cannot be verified (I generated the certificate myself as in the tutorial)

Here's my main.cf
> 
# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_auth_only = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_tls_loglevel = 3


Can someone help to direct me how to fix this issue ?
Thanks.

---

### Post by hyper_ch on 2009-03-20
look at the perfect howtos over at [http://www.howtoforge.com](http://www.howtoforge.com) --> the perfect howtos from Falko work just fine for me. Just have a look at the mail setup - I think page 5 it is.

---

