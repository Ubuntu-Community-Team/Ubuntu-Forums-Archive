---
title: "Postfix &amp; Amavis config problem"
date: 2010-10-30
forum: Server Platforms
---

### Post by clegends on 2010-10-30
Hi folks, have been following this official guide for the Ubuntu 10.04 server platform: [https://help.ubuntu.com/10.04/serverguide/C/mail-filtering.html](https://help.ubuntu.com/10.04/serverguide/C/mail-filtering.html)

Have followed it exactly, and keep getting this error when I restart postfix:
```
postfix: fatal: /etc/postfix/main.cf, line 64: missing '=' after attribute name: "smtp-amavis     unix    -       -       -       -       2       smtp        -o smtp_data_done_timeout = 1200        -o smtp_send_xforward_command=yes        -o disable_dns_lookups=yes?-o max_use=20"
```
Any idea what's going on here? Searching has found me nothing. 

My config file is:
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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes

smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = curiouslegends.com.au
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = curiouslegends.com.au, curioushost, localhost.localdomain, localhost
relayhost =

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, perm$
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m "${EXTENSION}"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
content_filter = smtp-amavis:[127.0.0.1]:10024

smtp-amavis     unix    -       -       -       -       2       smtp
        -o smtp_data_done_timeout = 1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20

127.0.0.1:10025 inet    n       -       -       -       -       smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8

 -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

```

Everything seems to work fine without this line and below:
```
content_filter = smtp-amavis:[127.0.0.1]:10024
```
What am I doing wrong here, and missing in the guide? The other issue with this guide is that it tells me:
```

Also add the following two lines immediately below the "pickup" transport service:

         -o content_filter=
         -o receive_override_options=no_header_body_checks

```
There doesn't seem to be a "pickup" transport service defined in this file. What am I missing. Thanks for your help.

~dinky

---

### Post by HermanAB on 2010-10-31
Howdy,

Not what you want to hear, but it has been many years since I gave up with postfix and amavis.  Citadel is so much easier to set up using the Easy Install script, that it is really not worth wasting my time with postfix.
[http://www.citadel.org](http://www.citadel.org)

---

### Post by clegends on 2010-10-31
Yes, Citadel looks interesting, but I want to work with my current setup.

Come on people.... surely there's someone who understands this...

---

### Post by clegends on 2010-11-01
Bump. Anyone?

---

### Post by clegends on 2010-11-01
And the throngs of people eager to help are inspiring... oh well, as often the case on these forums, will have to go it alone. Thanks anyway.

---

