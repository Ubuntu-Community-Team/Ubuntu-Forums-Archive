---
title: "Postfix Virtual Mailbox --"
date: 2011-05-10
forum: Server Platforms
---

### Post by charmcity on 2011-05-10
Hi, and thanks for reading.

I am trying to change my previously working postfix configuration and switch over to virtual mailboxes.  

I *have* had luck receiving "LOCAL" mail ie. something sent from root to myuser @ bakeaffinity.com but I can't receive from the outside world.  I get "Unknown local recipient" error in syslog.   I have been googling for a while now - can anyone spot my problem? 

main.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost
mydomain = bakeaffinity.com
mailbox_transport = lmtp:unix:/var/run/cyrus/socket/lmtp
#alias_maps = hash:/etc/aliases
#alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = /etc/postfix/vhosts
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/

smtpd_sasl_auth_enable = no
smtpd_sasl_type = cyrus
smtpd_sasl_path = smtpd
smtpd_sasl_authenticated_header = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
broken_sasl_auth_clients = no
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination
smtpd_sender_restrictions =
smtp_use_tls = no
smtpd_tls_received_header = no
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = no
tls_random_source = dev:/dev/urandom

virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000


```

my vhosts looks like:
```

bakeaffinity.com

```

and vmaps looks like:
```

user@bakeaffinity.com bakeaffinity.com/user/

```

I have run postmap ./vmaps on vmaps

Thanks for helping!!! in advance!!
Tom

---

### Post by primal23 on 2011-05-11
What do you get if you do a dig on your domain?

---

### Post by charmcity on 2011-05-11
Primal 

Thanks alot for the comment -- I decided to abandon virtual mailboxes and went back to plain old account based setup and instead I'm gonna make use of aliasing to get what I need.  I don't really have that many accounts that I can't live with it.

Thanks alot tho!
Tom

---

