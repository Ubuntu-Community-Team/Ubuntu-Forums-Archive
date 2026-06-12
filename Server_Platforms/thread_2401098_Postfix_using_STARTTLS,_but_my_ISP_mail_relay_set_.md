---
title: "Postfix using STARTTLS, but my ISP mail relay set for SSL and the result is no encryp"
date: 2018-09-13
forum: Server Platforms
---

### Post by jeanathon2 on 2018-09-13
I have just set up an email server on a dynamic ip.  Because of that I am using my ISP's mail server as a relayhost.  Postfix is configured to use STARTTLS, but in order to connect to my ISP mail server I had to set the relay to use SSL on port 587 instead of 465, or STARTTLS.  In the logs postfix makes a secure connection to my ISP mobile.charter.net:587, but when my test emails arrive at gmail they are showing as unsecured.  My mail client is configured to use STARTTLS.
So the question is why is the encryption not making it to the endpoint email?

syslog file
```
Sep 13 11:51:53 mail postfix/submission/smtpd[26361]: connect from myserver.com[192.168.1.8]
Sep 13 11:51:53 mail postfix/submission/smtpd[26361]: Anonymous TLS connection established from theheists.com[192.168.1.8]: TLSv1.2 with cipher ECDHE-RSA-AES128-GCM-SHA256 (128/128 bits)
Sep 13 11:51:54 mail postfix/submission/smtpd[26361]: 36E6D300017: client=myserver.com[192.168.1.8], sasl_method=PLAIN, sasl_username=me
Sep 13 11:51:54 mail postfix/cleanup[26366]: 36E6D300017: message-id=<f9eea120-2756-8a18-c71f-6058a215ab8b@theheists.com>
Sep 13 11:51:54 mail postfix/qmgr[5764]: 36E6D300017: from=<me@myserver.com>, size=3014, nrcpt=1 (queue active)
Sep 13 11:51:54 mail postfix/submission/smtpd[26361]: disconnect from myservers.com[192.168.1.8] ehlo=2 starttls=1 auth=1 mail=1 rcpt=1 data=1 quit=1 commands=8
Sep 13 11:51:54 mail dovecot: imap(jonn): Connection closed (IDLE running for 0.001 + waiting input for 927.836 secs, 2 B in + 10+0 B out, state=wait-input) in=3569 out=3303
Sep 13 11:51:54 mail postfix/smtp[26367]: Trusted TLS connection established to mobile.charter.net[68.114.188.72]:587: TLSv1.2 with cipher AES256-GCM-SHA384 (256/256 bits)
Sep 13 11:51:55 mail postfix/smtp[26367]: 36E6D300017: to=<me@gmail.com>, relay=mobile.charter.net[68.114.188.72]:587, delay=1.1, delays=0.21/0.4/0.33/0.15, dsn=2.0.0, status=sent (250 2.0.0 Message received: 20180913155155.XQZL7358.mtaout006.msg.strl.va.charter.net@impout006 E0000)
Sep 13 11:51:55 mail postfix/qmgr[5764]: 36E6D300017: removed

```
/etc/postfix/main.cf

```
readme_directory = no
compatibility_level = 2
# TLS parameters
smtpd_tls_cert_file=/etc/letsencrypt/live/mail.myserver.com/fullchain.pem
smtpd_tls_key_file=/etc/letsencrypt/live/mail.myserver.com/privkey.pem
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
#smtpd_use_tls=yes
smtp_tls_security_level = encrypt
smtp_tls_wrappermode = yes
smtp_tls_loglevel = 1
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_tls_security_level=may
smtpd_tls_protocols = !SSLv2, !SSLv3
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mail.myserver.com
mydomain = myserver.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
myorigin = $mydomain
mydestination = $myhostname, $mydomain, localhost.$mydomain, localhost
relayhost = [mobile.charter.net]:587
transport_maps = hash:/etc/postfix/transport
smtp_use_tls=yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
#inet_protocols = all
inet_protocols = ipv4
home_mailbox = Maildir/
#SMTP-Auth settings
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
smtpd_recipient_restrictions = permit_mynetworks,permit_auth_destination,permit_sasl_authentication,reject
```

---

### Post by TheFu on 2018-09-13
SMTP connections are negotiated between the 2 servers communicating.  Clients don't have any control over that connection.  On port 587, that is a client connection, not server-to-server.

---

### Post by jeanathon2 on 2018-09-14
Ok.  I understand that, but why is the encryption not going all the way to the end recipient.  Is it because my isp mail relay uses straight up ssl, and then it can't switch to starttls?

---

### Post by jeanathon2 on 2018-09-14
Put another way.  Do you see anything wrong with my configuration or does the problem lie with the behemoth charter?

---

### Post by TheFu on 2018-09-15
> **jeanathon2 said:**
> Ok.  I understand that, but why is the encryption not going all the way to the end recipient.  Is it because my isp mail relay uses straight up ssl, and then it can't switch to starttls?

If you want end-to-end encryption, use gpg.  You and I have no control over what other SMTP servers choose.

---

### Post by TheFu on 2018-09-15
> **jeanathon2 said:**
> Put another way.  Do you see anything wrong with my configuration or does the problem lie with the behemoth charter?

I cannot say. I looked at a few settings in your setup that seemed odd, but turned out to be fine.  I don't know anything about Charter's email servers.

The SMTP was designed as a postcard-like protocol.  If you want it to carry only encrypted information, then  encrypt it outside the protocol for 100% compliance. A social agreement on the encryption method used will be required with the people you are sending emails at.  Plus, everything in the SMTP headers isn't encrypted, to know that the TO/FROM/SUBJECT are available to any intermediate server even when SSL SMTP is working.

Clients receive email using non-SMTP protocols. They use IMAP or POP3 with or without SSL. It is completely up to that remote client system to decide.

I think your server can be setup to reject non-encrypted connections, but you'll loose 90% of the email in the world.  Most of that is spam, but a few email servers still don't support encrypted connections.

---

### Post by jeanathon2 on 2018-09-16
Thank you.

---

