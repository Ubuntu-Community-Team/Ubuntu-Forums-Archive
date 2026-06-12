---
title: "Can't receive email from external domains (Postfix/Dovecot)"
date: 2009-10-18
forum: Server Platforms
---

### Post by a_bains on 2009-10-18
Hello,
 
I am new to Ubuntu and linux. I have one server running at home. I am trying to get a mail server running using Postfix/Dovecot and I have followed a few guides to get running. I have setup virtual users and am able to connect using outlook and send emails through my ISP's SMTP server (using Postfix as a relay). I can send emails externally and internally perfectly. The only problem is that I can't receive emails from external domains. Receiving emails works fine from internal domains. I have posted my postconf -n output for my Postfix configuration. My ISP is Bell Sympatico and I know that they at least block outgoing port 25.
 
```
 
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
mydestination = ubuntu.gateway.2wire.net, localhost.gateway.2wire.net, localhost
myhostname = viewsatcanadasales.com
mynetworks = 127.0.0.0/8 192.168.1.0/24 [::1]/128 [fe80::%eth0]/64
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = smtphm.sympatico.ca
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_tls_mandatory_ciphers = medium, high
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000


```

---

### Post by a_bains on 2009-10-18
Any ideas? There seems to be no sign of an incoming message in the logs when I send an email from an external domain like Gmail.
 
My MX record is like so (according to intoDNS.com):
0   mail.viewsatcanadasales.com   70.51.2.244 (no glue)

---

### Post by a_bains on 2009-10-18
It seems my ISP was blocking the incoming port as well. So I changed my ISP and moved server to remote location. When I try to connect through outlook, POPS works but connecting to the outgoing SMTP doesnt work. Although it works when I connect at from the same network the server is running on. My postfix is no longer a relay.

---

### Post by a_bains on 2009-10-18
From WIKI:
 
"If you want to use port 587 as the submission port for SMTP mail rather than 25 (many ISPs block port 25), you will need to edit /etc/postfix/master.cf to uncomment the relevant line for port 587 there. "
 
Which lines do I need to uncomment? How do I enable TLS on port 587?

---

### Post by Dullstar on 2009-10-18
I wish I knew, so I could help you.  Be patient, though; someone will come along who knows.

---

### Post by a_bains on 2009-10-18
Thats okay, I was able to solve the problem. The comment that needs to be removed in master.cf is the submission line and the options below it. The main problem I was having was a bug in the dovecot-postfix configuration file, main.cf . The line is,
 
smtpd_tls_mandatory_ciphers = medium, high
 
which is wrong and should be corrected to:
 
smtpd_tls_mandatory_ciphers = medium
 
If you don't fix the above line you will end up seeing an error in the mail.log as:
"invalid tls cipher grade: "medium, high": aborting TLS session"
 
hopefully, this helps anyone out in the future!

---

