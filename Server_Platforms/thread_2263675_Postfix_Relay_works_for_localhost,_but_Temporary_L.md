---
title: "Postfix Relay works for localhost, but Temporary Lookup Failure for remote client"
date: 2015-02-02
forum: Server Platforms
---

### Post by rpcaston on 2015-02-02
Hi,

I've got a Postfix relay I am trying to configure to send messages via our Google Business Apps account. It works when I run a test from the Postfix server itself. When trying to use a client app on another node to create and send the message, the relay returns the error "Temporary Lookup Failure", which seems to be a DNS problem concerning the receiving address. I don't understand why I would get this error when I thought I had Postfix configured to not bother with local lookup and always send the emails through Gmail (provided it's from a trusted source, of course). I've included my main.cf below. Anybody know where I've gone wrong? I follow the instructions from this website and made a few tweaks as needed:
[https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/](https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/)

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


myhostname = hans
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = hans.local, localhost.localdomain, localhost
relayhost = [smtp.gmail.com]:587
relay_domains = companydomainhere.com, gmail.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 [192.168.3.0]/255
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_use_tls = yes


smtpd_recipient_restrictions =
   permit_sasl_authenticated,
   permit_mynetworks,
   check_relay_domains,
   permit


smtpd_sender_restrictions =
  permit_mynetworks,
  permit

```

---

