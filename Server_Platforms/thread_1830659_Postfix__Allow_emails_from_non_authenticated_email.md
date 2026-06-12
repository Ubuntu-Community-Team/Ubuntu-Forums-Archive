---
title: "Postfix : Allow emails from non authenticated email address"
date: 2011-08-22
forum: Server Platforms
---

### Post by psykro on 2011-08-22
Good day

I could use some server admin level help with a small problem I am having.

I want to create an smtp mail server that will allow me to send emails from a specific email address. In essence I want to replicate the idea of an open relay, but for a specific email address only.

I have installed Postfix and configured it as a smarthost using SendGrid for delivery.

What I want to be able to do now is allow any emails being sent from a specific email address (ie [email]specificuser@company.com[/email]) to be delivered.

Currently I get relay access denied errors if I try to do this.

Here is my /etx/postfix/main.cf file

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

myhostname = mail.psykro.za.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.psykro.za.net, localhost.psykro.za.net, localhost
relayhost = smtp.psykro.za.net
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = static:yourSendgridUsername:yourSendgridPassword
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = may
header_size_limit = 4096000
relayhost = [smtp.sendgrid.net]:587
```

Any assistance would be appreciated.

---

