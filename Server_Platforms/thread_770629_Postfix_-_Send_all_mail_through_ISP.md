---
title: "Postfix - Send all mail through ISP"
date: 2008-04-27
forum: Server Platforms
---

### Post by darwin2kx on 2008-04-27
I am trying to config Postfix to send all it's mail through my ISP's SMTP server. I want to set it so that no matter what user sends mail, it gets passed through the ISP and addressed with my login creds there. 

So, root@box sends mail, Postfix grabs it, logs into the SMTP server as [email]user@isp.com[/email] and sends the mail as [email]user@isp.com[/email].

Can anyone help me out?

---

### Post by Monicker on 2008-04-27
I think these will help:

[http://freelock.com/kb/Postfix_relayhost]("http://freelock.com/kb/Postfix_relayhost")

[http://ubuntuforums.org/showthread.php?t=138377]("http://ubuntuforums.org/showthread.php?t=138377")

---

### Post by darwin2kx on 2008-04-28
I have configured everything, and I am now having SASL authentication problems. Any suggestions? User and password is correct and sasl_passwd.db is updated.

main.cf
```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ahost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = ahost, localhost.localdomain, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# We need this
smtp_sasl_auth_enable = yes
#smtp_sasl_security_options =
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

transport_maps = hash:/etc/postfix/transport
relayhost = [smtp.mailhost.com]:587

smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
```

mail.info
```
Apr 28 21:29:03 sunray postfix/smtp[6920]: 5409634208D: to=<email@hotmail.com>, relay=smtp.efireball.com[208.118.72.78]:587, delay=90286, delays=90281/0.04/5.3/0, dsn=4.0.0, status=deferred (SASL authentication failed; server smtp.efireball.com[208.118.72.78] said: 535 authorization failed (#5.7.0))
```

---

### Post by MJN on 2008-04-29
Your ISP probably requires the use of plaintext passwords (protected by TLS if desired). The default authentication method forbids anonymous and/or plaintext passwords so try relaxing this restriction with **smtp_sasl_security_options = noanonymous**
 
Mathew

---

### Post by darwin2kx on 2008-04-29
That solved the problem. Thank you.

---

