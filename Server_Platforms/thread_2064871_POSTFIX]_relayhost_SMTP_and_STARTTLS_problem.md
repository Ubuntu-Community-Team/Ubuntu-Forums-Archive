---
title: "POSTFIX] relayhost SMTP and STARTTLS problem"
date: 2012-09-30
forum: Server Platforms
---

### Post by neptunus10000 on 2012-09-30
I'm trying to get a relayhost with postfix to work

Error in my log:
```

Sep 30 17:27:18 Skyfire postfix/smtp[31799]: DA456E2016E: to=<test@familiekrikke.nl>, relay=smtp.dds.nl[85.17.178.138]:587, delay=0.62, delays=0.08/0.03/0.26/0.24, dsn=5.7.1, status=bounced (host smtp.dds.nl[85.17.178.138] said: 554 5.7.1 Service unavailable; Client host [xxx.xxx.xxx.xxx] blocked using zen.spamhaus.org; http://www.spamhaus.org/query/bl?ip=82.74.173.86 (in reply to RCPT TO command))

```I don't untherstnad why my IP is blocked by zen.spamhaus.org. If I connect direct with thunderbird of telnet, it works.
```

user@domain:/etc/postfix$ telnet smtp.dds.nl 587
Trying 85.17.178.138...
Connected to smtp.dds.nl.
Escape character is '^]'.
220 ESMTP rotring.dds.nl
ehlo nico
250-rotring.dds.nl
250-PIPELINING
250-SIZE 52428800
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250 8BITMIME
auth login
334 VXNlcm5hbWU6
<<USERNAME in  base64 encoding>>
334 UGFzc3dvcmQ6
<<PASSWD in  base64 encoding>>
235 2.7.0 Authentication successful
mail from: <<MAIL>>@dds.nl
250 2.1.0 Ok
rcpt to: <<MAIL>>@dds.nl
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
testing
.
250 2.0.0 Ok: queued as DD31A5859C
quit
221 2.0.0 Bye
Connection closed by foreign host.

```Settings used in thunderbird:
```

pop3.dds.nl:110    STARTTLS   Normal Password
smtp.dds.nl:587    STARTTLS   Normal Password

```master.cf:
```

# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
submission inet n       -       -       -       -       smtpd
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes

```main.cf:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_auth_only = no
smtpd_tls_security_level = encrypt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtp_use_tls = yes
#smtp_tls_security_level = may
smtp_tls_security_level = encrypt
smtp_always_send_ehlo = yes
#smtp_tls_note_starttls_offer = yes
#smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
tls_random_source = dev:/dev/urandom

smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = <<domain>>.lan
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
myorigin = $mydomain
mydestination = $myhostname, localhost.localdomain, localhost
relayhost = [smtp.dds.nl]:587
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = .Maildir/
mailbox_command =
smtp_sasl_auth_enable = yes
smtp_sasl_mechanism_filter = AUTH LOGIN
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_generic_maps = hash:/etc/postfix/generic
#smtp_cname_overrides_servername = no
#smtp_discard_ehlo_keywords = 8bitmime

smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

broken_sasl_auth_clients = yes

```sasl_passwd
```

smtp.dds.nl:587 <<username>>:<<passwd>>

```I'm lost, maybe somone had a good idea to fix my problem.

---

