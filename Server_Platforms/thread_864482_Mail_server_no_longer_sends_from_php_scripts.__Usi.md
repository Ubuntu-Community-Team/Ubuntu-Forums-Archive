---
title: "Mail server no longer sends from php scripts.  Using Postfix."
date: 2008-07-19
forum: Server Platforms
---

### Post by bbvdd on 2008-07-19
Hi,

I set up a mail server using postfix to send emails from php scripts using the mail() function.  After the initial configuration everything worked fine.  At some point though, I restarted the computer and now my scripts do not send email.  The mail server is running, and I haven't changed any settings - so, I'm not sure where the configuration is wrong.

/etc/postfix/main.cf:
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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = bbvdd.hopto.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = trentlb-ubuntu, localhost.localdomain, , localhost, bbvdd.hopto.org
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

Also - using the following command returns an error.  I have the mx record set up on no-ip.com:
```

$ dig @76.160.120.223 bbvdd.hopto.org mx

; <<>> DiG 9.4.2-P1 <<>> @76.160.120.223 bbvdd.hopto.org mx
; (1 server found)
;; global options:  printcmd
;; connection timed out; no servers could be reached


```

Thanks in advance!

---

### Post by skunkbad on 2008-07-20
When I had problems sending email from php, the issue was DNS.

/etc/resolv.conf needs to have your ISPs DNS servers listed.

Take a look also at /etc/hosts and verify it is normal.

---

