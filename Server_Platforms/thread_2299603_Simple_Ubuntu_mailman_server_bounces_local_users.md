---
title: "Simple Ubuntu mailman server bounces local users"
date: 2015-10-19
forum: Server Platforms
---

### Post by cwall64 on 2015-10-19
Oct 19 17:14:23 mail postfix/pipe[1670]: F00A7160AB0: to=<safety@fortbendhelis.com>, relay=mailman, delay=2.2, delays=2.2/0.01/0/0.06, dsn=5.1.1, status=bounced (user unknown)

Basically followed the Ubuntu server guide for 14.04 for Postfix and Mailman.  I have had this configuration working in the past, but lost the SAN the server was running on and had to rebuild...

safety is a local user with a .forward in the home directory.  I have tried removing the fortbendhelis.com from mydestination line.  I can send mail from a mail client connected to the server, but when replying to that mail it bounces.

```
I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<safety@fortbendhelis.com>: user unknown

Final-Recipient: rfc822; safety@fortbendhelis.com
Original-Recipient: rfc822;safety@fortbendhelis.com
Action: failed
Status: 5.1.1
Diagnostic-Code: x-unix; user unknown

```

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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mail.fortbendhelis.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = fortbendhelis.com, mail.fortbendhelis.com, localhost.fortbendhelis.com, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
relay_domains = fortbendhelis.com
transport_maps = hash:/etc/postfix/transport
mailman_destination_recipient_limit = 1
home_mailbox = Maildir/
```

---

