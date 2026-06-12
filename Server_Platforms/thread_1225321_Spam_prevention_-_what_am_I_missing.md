---
title: "Spam prevention - what am I missing?"
date: 2009-07-28
forum: Server Platforms
---

### Post by ChurdCFG on 2009-07-28
Hello all,

I've been using Ubuntu for several years now to handle mail for my personal domain, but recently I've been getting fed up with the amount of spam I am receiving.  It seems every new measure I take works for a little while, but I continue to lose the war.

I figured I'd turn to the forums to see if there's anything glaring that I'm missing in my current setup.  At the moment I'm using postfix+amavisd+spamassassin, I have postgrey enabled as well, and my postfix configuration has spamhaus and spamcop configured.

In addition, I am training spamassassin using sa-learn every few days manually (to ensure the proper messages are marked as ham/spam while I sort this out).

I am including my postfix configuration below in case I'm missing anything else.  What other effective methods besides the ones mentioned are you using to attack spam?  Are there any recommendations for what I should add/change in my current environment?

**Postconf output**
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
mydestination = mail.xxxxxx.net, localhost, xxxxxx.net, hostname.xxxxxx.net, localhost.localdomain
myhostname = xxxxxx.net
mynetworks = 127.0.0.0/8, 192.168.1.0/24
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = [outgoing.verizon.net]
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_helo_restrictions = reject_invalid_hostname,reject_non_fqdn_hostname
smtpd_recipient_restrictions = reject_invalid_hostname, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unknown_sender_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_rbl_client bl.spamcop.net, reject_rbl_client zen.spamhaus.org, check_policy_service inet:127.0.0.1:10023
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = reject_non_fqdn_sender,reject_unknown_sender_domain
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

```

---

### Post by dlmarti on 2009-07-28
you do know that google will now do mail for your domain?
I switched over to letting google handle my entire company's domain, and I would never go back.  The employees love it, and its dead simple for me.

---

