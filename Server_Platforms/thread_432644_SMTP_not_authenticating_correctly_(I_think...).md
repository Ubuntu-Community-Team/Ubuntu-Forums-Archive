---
title: "SMTP not authenticating correctly (I think...)"
date: 2007-05-04
forum: Server Platforms
---

### Post by t_ras on 2007-05-04
AMD64 Kubuntu 7.04 using full ISPConfig configuration (postfix+sasl+mysql+.....)
After upgrading through automatic upgrade from 6.10 to 7.04 (big mistake....) my smtp is not accepting authentication from clients( like evolution and outlook) but is works fine with locally installed squirrelmail and mail2web.com site.

This is my main.cf:
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
delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = terrenisrv1.terrenis.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = terrenisrv1.terrenis.net, terrenisrv1, localhost.localdomain, localhost,terrenis.net
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_path =  /etc/postfix/sasl:/usr/lib/sasl2
#/etc/init.d/saslauthd *(also tried just using smtpd)*
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = yes *(tried also no)*
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names
unknown_local_recipient_reject_code = 450

```

When I use smtpd_tls_auth_only = yes then I get the "do not relay" message, when I use smtpd_tls_auth_only = no I get authentication failure.


Here is Logs when using yes:
```
NOQUEUE: reject: RCPT from unknown[212.143.241.131]: 554 5.7.1 <martin_t@netvision.net.il>: Relay access denied; from=<postmaster@terrenis.net> to=<martin_t@netvision.net.il> proto=ESMTP helo=<[212.143.241.131]>
```

Here is the log when using no:
```
warning: SASL authentication failure: Password verification failed
```
```
warning: unknown[212.143.241.131]: SASL PLAIN authentication failed: authentication failure
```

Any Idea how to solve it?
I tried resintalling postfix and sasl (and some other mail related crap...)
but nothing help :(

Thanks for the help!!

---

### Post by t_ras on 2007-05-05
This are the errors I got when trying to send mail (sent from local postmaster):
When using yes or no seems to be is the same (I'm not sure):
```
Transcript of session follows.

 Out: 220 terrenisrv1.terrenis.net ESMTP Postfix (Ubuntu)
 In:  EHLO [212.143.241.131]
 Out: 250-terrenisrv1.terrenis.net
 Out: 250-PIPELINING
 Out: 250-SIZE 10240000
 Out: 250-VRFY
 Out: 250-ETRN
 Out: 250-STARTTLS
 Out: 250-AUTH PLAIN NTLM LOGIN DIGEST-MD5 CRAM-MD5
 Out: 250-AUTH=PLAIN NTLM LOGIN DIGEST-MD5 CRAM-MD5
 Out: 250-ENHANCEDSTATUSCODES
 Out: 250-8BITMIME
 Out: 250 DSN
 In:  STARTTLS
 Out: 454 4.3.0 TLS not available due to local problem

Session aborted, reason: lost connection
```

---

