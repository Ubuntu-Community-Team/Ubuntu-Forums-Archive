---
title: "hwat"
date: 2011-04-26
forum: Server Platforms
---

### Post by num on 2011-04-26
I am testing out my test server machine to see if i can properly setup email server for one of my test domains, greensevenstudios.com

I followed this guide on how to setup postfix:


My ISP is Comcast and I got Business Package with a static IP, I port forwarded port 25, ensured it is indeed open. But nonetheless I get this error in my log:

```
Apr 26 20:59:21 server postfix/master[1686]: warning: process /usr/lib/postfix/smtpd pid 16766 exit status 1
Apr 26 20:59:21 server postfix/master[1686]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Apr 26 21:00:06 server postfix/cleanup[16773]: fatal: open database /etc/postfix/virtual/addresses.db: Invalid argument
Apr 26 21:00:07 server postfix/master[1686]: warning: process /usr/lib/postfix/cleanup pid 16773 exit status 1
Apr 26 21:00:07 server postfix/master[1686]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Apr 26 21:00:21 server postfix/smtpd[16776]: fatal: open database /etc/postfix/virtual/addresses.db: Invalid argument
Apr 26 21:00:22 server postfix/master[1686]: warning: process /usr/lib/postfix/smtpd pid 16776 exit status 1
Apr 26 21:00:22 server postfix/master[1686]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Apr 26 21:00:36 server postfix/master[1686]: reload -- version 2.7.0, configuration /etc/postfix

```

My virtual file:

```
greensevenstudios.com
```

My addresses.db:

```
greensevenstudios.com DOMAIN
test@greensevenstudios.com test

```

my main.cf:

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

myhostname = server.wp.comcast.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, /etc/postfix/virtual/domains
virtual_maps  = hash:/etc/postfix/virtual/addresses
localhost = .wp.comcast.net, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```

what is wrong here?

I also ensured that the DNS is pointed to the correct IP along with email.

---

