---
title: "Postfix issues on server (connect error 10060, port 587)"
date: 2012-01-03
forum: Server Platforms
---

### Post by kayfouroh on 2012-01-03
I am trying to set up a light weight Ubuntu server on a virtual machine, and I am having issues setting up Postfix to send e-mails.  I do not need to receive emails, only send outgoing mail.  I am also trying to get it to not relay off of any external SMTP host, so I am not sure if I am set up correctly.

I set up my /etc/postconf/master.cf file to listen on port 7538, since my ISP does not allow port 25 (Verizon FIOS).

Here is a tail of my** /var/log/mail.log**:

Jan  3 18:35:34 ubuntu postfix/smtp[25986]: 4E782203EF: to=<test@test.com>, relay=alt4.gmail-smtp-in.l.google.com[209.85.173.26]:25, delay=3091, delays=2986/0.02/105/0, dsn=4.0.0, status=deferred (host alt4.gmail-smtp-in.l.google.com[209.85.173.26] refused to talk to me: 421 Cannot connect to SMTP server 209.85.173.26 (209.85.173.26:587), connect error 10060)

here is my **postconf -n**:
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = loopback-only
inet_protocols = ipv4
local_transport = error:local delivery is disabled
mailbox_size_limit = 0
mydestination = ubuntu, localhost.localdomain, localhost
myhostname = ubuntu
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.254.0/24
myorigin = localhost
readme_directory = no
recipient_delimiter = +
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes



Any ideas?

Thanks :)

---

### Post by kayfouroh on 2012-01-04
Anyone? :)

---

### Post by smtp on 2012-01-05
As per provided logs your ISP blocks _outgoing_ connections on 25 port:

relay=alt4.gmail-smtp-in.l.google.com[209.85.173.26]_:25_

The easiest way to have that solved is to use your's ISP mail server as a relay host. You have to add something similar in postfix transport file:

*   smtp:[relayserver.yourISP.com]:587

The wildcard (*) indicates that all mail should be sent via smtp to relayserver.yourISP.com via port 587

I hope this will help.

---

### Post by kayfouroh on 2012-01-05
> **smtp said:**
> As per provided logs your ISP blocks _outgoing_ connections on 25 port:

relay=alt4.gmail-smtp-in.l.google.com[209.85.173.26]_:25_

The easiest way to have that solved is to use your's ISP mail server as a relay host. You have to add something similar in postfix transport file:

*   smtp:[relayserver.yourISP.com]:587

The wildcard (*) indicates that all mail should be sent via smtp to relayserver.yourISP.com via port 587

I hope this will help.
Yeah I was trying to avoid using any outside mail server (is that possible)?  I am setting up a deployable application that should have its own mail server.  I thought this is what postfix did?  I may be mistaken, though.

---

