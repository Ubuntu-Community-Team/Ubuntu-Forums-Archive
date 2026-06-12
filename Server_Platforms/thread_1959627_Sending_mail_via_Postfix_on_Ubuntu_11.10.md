---
title: "Sending mail via Postfix on Ubuntu 11.10"
date: 2012-04-16
forum: Server Platforms
---

### Post by Frankincense93 on 2012-04-16
Hi guys,

I have recently changes ISP to BT and I need to re-configure my Postfix again. But I am having lots of trouble with is, and I cant seem to find anyone with a similar problem on google or on forums etc.

Currently I am getting the error message: 
"smtp; 530 authentication required - Your email could not be
    sent. To fix this you must make a simple change to your email (known as
    SMTP authentication). For advice visit www.btyahoo.com/smtp"

I have followed through this walkthrough 'http://www.adomas.org/2006/08/postfix-dovecot/' to get my smtp authentication running (and it is successful). But I still get the emails returned to me with the above error.

Are there any specific settings I can check? Am I missing something?


This is my main.cf config file for Postfix:

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

#myhostname = mail.btinternet.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = mail.btinternet.com, btinternet.com, hotmail.co.uk, mail.hotmai$
relayhost = [mail.btinternet.com]
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

myorigin = /etc/mailname


# smtp sasl auth
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_application_name = smptd
broken_sasl_auth_clients = yes

smptd_recipient_restrictions =
        permit_sasl_authenticated,
        permit_mynetworks,
        check_relay_domains

```

---

### Post by nsnidanko on 2012-04-16
Your postfix doesn't have any info on have to authenticate to the relaying server.
Please refer to the bottom of this guide:

[http://www.lucidlynx.com/how-to-install-postfix-to-relay-mail-through-gmail-in-ubuntu/](http://www.lucidlynx.com/how-to-install-postfix-to-relay-mail-through-gmail-in-ubuntu/)

create:
smtp_sasl_password_maps

---

