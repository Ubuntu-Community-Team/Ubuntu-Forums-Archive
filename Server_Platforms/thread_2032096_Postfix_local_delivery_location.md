---
title: "Postfix local delivery location"
date: 2012-07-23
forum: Server Platforms
---

### Post by Demented ZA on 2012-07-23
[Background]
I have a stupid printer scanner copier that sends mail when done with a scan. The problem is that the printer can only connect to port 25 of any smtp server (the stupid part). Our Isp has started blocking port 25 for security (spam?) reasons and now everyone is supposed to use port 587.

[Preferred solution]
I have an Ubuntu box acting as a simple firewall/mail server (aggregator) and was thinking I'd get the scanner to hand it over to postfix on the local server and have postfix relay it to the isp's server or deliver it locally for local addresses.

[The setup so far]
I'm using dovecot with virtual users and getmail to retrieve mail from the mail server (MX). Problem is telling postfix where those mailboxes are located in case of local delivery.

My virtual mailboxes are located at /var/mail/[user]@sample.com/Maildir

My postfix configuration:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = sample.com
alias_maps = hash:/etc/aliases
mailbox_size_limit = 0
recipient_delimiter = +
myorigin = /etc/mailname
home_mailbox = /Maildir/
masquerade_domains = sample.com
mydomain = sample.com
allow_untrusted_routing = yes
inet_protocols = ipv4
append_dot_mydomain = no
smtpd_recipient_restrictions = permit_mynetworks

#smtp_sasl_auth_enable = yes
relayhost = smtp.myisp.com:587
smtp_sasl_password_maps = hash:/etc/postfix/smtp_sasl_password_map
smtp_sasl_security_options =


```I looked at using virtual domains, but I'm wondering if its the right approach for what I'm trying to do, so I thought I'd just ask you guys first.

This is what I've got so far:
If I add the following to postfix main.cf:

```
virtual_mailbox_domains = sample.com
virtual_mailbox_base = /var/mail
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_minimum_uid = 8
virtual_uid_maps = static:8
virtual_gid_maps = static:8
``````
info@sample.com    info@sample.com/Maildir
root@sample.com    root@sample.com/Maildir


```Would this theoretically work? I'm a little unsure of the UID part. The mail residing under /var/mail is owned by the mail user with a UID of 8.

I would appreciate some feedback and insight. Thanks in advance.

---

