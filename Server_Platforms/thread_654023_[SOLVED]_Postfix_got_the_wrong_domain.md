---
title: "[SOLVED] Postfix got the wrong domain"
date: 2007-12-30
forum: Server Platforms
---

### Post by vaxen on 2007-12-30
Hi, I've setup postfix using the guide in the wiki. My mails are going to the wrong place. Instead of going to [email]user@domain.com[/email], its going to [email]user@hostname.domain.com[/email]. 

Here is my main.cf

> 
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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mugen.ext9.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mugen.ext9.org, localhost.ext9.org, localhost.localdomain, localhost, ext9.org
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


and here is my /etc/host
> 
127.0.0.1   localhost.localdomain   localhost
#67.18.187.77  mugen.ext9.org   mugen

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



and /etc/hostname
> mugen.ext9.org


How do I fix this? Thanks

---

### Post by andol on 2007-12-30
How about?

```
myorigin = $mydomain
```

(postfix resolves $mydomain from $myhostname)

---

### Post by vaxen on 2007-12-31
didnt work.

---

### Post by MJN on 2007-12-31
Give us an illustrative example (with logs etc) of exactly what's happening - it's not clear from your post.

Mathew

---

### Post by andol on 2007-12-31
Well, for debuging I guess you could try a more direct approach

```
myorigin = ext9.org
```

By the way, I hope you noticed that you already had a $myorigin ( myorigin = /etc/mailname ). That one should be deleted/replaced, or at least commented.

---

### Post by vaxen on 2008-01-01
Solved on a different forum. My MX record was mail.ext9.org and I do not have a A record for it. 

The question is pretty clear, mails that are sent to [email]user@domain.com[/email] cannot be received, while  mails to [email]user@hostname.domain.com[/email] works fine.

---

### Post by MJN on 2008-01-01
Well, when you put it like that it is indeed clear - but that's not how you phrased your original question.

Anyway, good to hear you're now up and running.

Mathew

---

