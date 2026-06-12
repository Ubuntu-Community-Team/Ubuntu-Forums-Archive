---
title: "postfix realy on ms exchange using tls+ssl"
date: 2010-01-08
forum: Server Platforms
---

### Post by maq21 on 2010-01-08
Hi all,

Im trying to make postfix to relay on exchanger server using account to authenticate, the exchange requires tls + ssl connection and here is my configs:

relayhost=remotehost.com:587
smtpd_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_enforce_tls = yes
smtp_helo_name = myhost.com
smtp_tls_cert_file = /etc/postfix/smtp-client.pem
smtp_tls_key_file = $smtp_tls_cert_file
smtp_tls_CAfile = /etc/postfix/CAcert.pem
smtp_sasl_tls_security_options = $smtp_sasl_security_options
smtp_sasl_tls_verified_security_options = $smtp_sasl_security_options

but it replies with "offered null AUTH mechanism list"
if I used telnet to the remote host and I issued EHLO command it does not provide me with any auth mechanism just "AUTH" .
But if I used 
openssl s_client -starttls smtp -crlf -connect  remotehost.com:587 it provide the "AUTH LOGIN" mechanism.

I believe that postfix doesn't start ssl connection, please any help ??

---

