---
title: "Postfix rejects all external emails"
date: 2011-02-27
forum: Server Platforms
---

### Post by brodo on 2011-02-27
Hi,
i've set up Postfix and Dovecot using this tutorial:  [https://help.ubuntu.com/10.10/serverguide/C/postfix.html](https://help.ubuntu.com/10.10/serverguide/C/postfix.html)

After that it worked fine, but sadly, I wanted more. (A mailing list, virtual aliases...) During the process of trying to get the stuff running I somehow managed to misconfigure Postfix, so it does not take any emails form the outside world anymore.

From mail.log:
```

 postfix/smtpd[13704]: NOQUEUE: reject: RCPT from somemailserver[someip]: 554 5.7.1 <admin@mydomain.tld>: Recipient address rejected: Access denied; from=<emailaddress@someserver.tld> to=<admin@mydomain.tld> proto=ESMTP helo=<somemailserver>

```

postconf -n:
>                                                                                                                                ~
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
mydestination = mydomain.tld, localhost.localdomain, localhost
mydomain = mydomain.tld
myhostname = mydomain.tld
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom


The "admin" account is a real shell account. I'm on Ubuntu 10.10.

What could be the reason for postfix to reject the emails?

---

### Post by SeijiSensei on 2011-02-27
> mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

I believe that limits Postfix to accepting only mail from the local machine.  I'm not a Postfix user so any further help will have to come from knowledgeable folks or from Googling.

---

### Post by brodo on 2011-03-02
[This]("http://ubuntuforums.org/showthread.php?t=1277902") solved my problem.

---

