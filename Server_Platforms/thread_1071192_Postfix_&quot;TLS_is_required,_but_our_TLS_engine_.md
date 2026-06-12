---
title: "Postfix &quot;TLS is required, but our TLS engine is unavailable&quot; Error"
date: 2009-02-15
forum: Server Platforms
---

### Post by blendmaster on 2009-02-15
Hello!

I've been trying to set up a home mail server over the past few days, and I've realized that I needed to relay my mail to another mail server (as I'm on a dynamic IP).

I've chosen to use gmail's mail server, and I have everything working (I think...) except I receive the following in my mail.log file when trying to send a message from my user account to a test Gmail account:

[I]MyServer = HostName
example.com = My registered domain[/I]

> Feb 15 21:23:47 MyServer postfix/cleanup[8415]: 5AB7D8E2B0: message-id=<20090216032331.5AB7D8E2B0@MyServer>
Feb 15 21:23:47 MyServer postfix/qmgr[8409]: 5AB7D8E2B0: from=<user@example.com>, size=388, nrcpt=1 (queue active)
Feb 15 21:23:47 MyServer postfix/smtp[8416]: cannot load Certificate Authority data
Feb 15 21:23:47 MyServer postfix/smtp[8416]: 5AB7D8E2B0: TLS is required, but our TLS engine is unavailable
Feb 15 21:23:48 MyServer postfix/smtp[8416]: 5AB7D8E2B0: to=<exampleuser@gmail.com>, relay=smtp.gmail.com[72.14.205.111]:587, delay=28, delays=28/0.02/0.3/0, dsn=4.7.5, status=deferred (TLS is required, but our TLS engine is unavailable)
Feb 15 21:23:53 MyServer postfix/smtpd[8411]: disconnect from MyServer[127.0.1.1]


I assume I need to enable TLS, but I don't know for sure that I need to or how to enable it if I do. 

Here's my main.cf file from postfix:

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = MyServer
home_mailbox = Maildir/
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.example.com, MyServer, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
broken_sasl_auth_clients = yes

## Add these lines to the bottom on main.cf
##
##


## TLS Settings
#
# For no logs set = 0
smtp_tls_loglevel = 1
#
# smtp_enforce_tls = yes
# Above is commented because doing it site by site below
smtp_tls_per_site = hash:/etc/postfix/tls_per_site
#
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

## SASL Settings
# This is going in to THIS server
smtpd_sasl_auth_enable = no
# We need this
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtpd_sasl_local_domain = $myhostname
smtp_sasl_security_options = noanonymous
#smtp_sasl_security_options =
smtp_sasl_tls_security_options = noanonymous
smtpd_sasl_application_name = smtpd


## Gmail Relay
relayhost = [smtp.gmail.com]:587

## Good for Testing
# sender_bcc_maps = hash:/etc/postfix/bcc_table

# Disable DNS Lookups
disable_dns_lookups = yes
#
# Great New feature Address Mapping
# for example may mchirico@localhost to [email]mchirico@gmail.com[/email]
smtp_generic_maps = hash:/etc/postfix/generic
#
#
transport_maps = hash:/etc/postfix/transport

virtual_alias_domains = example.com
virtual_alias_maps = hash:/etc/postfix/virtual


I followed [this tutorial]("http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps") to set up the server.

Thanks for the help!

Edit:

It seems the certificate /etc/postfix/cacert.pem didn't contain gmail's certificate file. Now I can send mail with squirrelmail, but telnet doesn't seem to be able to send the mail... I also cannot see received mail in squirrelmail. These are most likely squirrelmail issues though.

---

### Post by songshu on 2009-02-17
did you try
```
apt-get install openssl
```

---

