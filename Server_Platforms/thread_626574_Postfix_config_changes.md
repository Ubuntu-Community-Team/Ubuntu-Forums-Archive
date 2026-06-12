---
title: "Postfix config changes"
date: 2007-11-29
forum: Server Platforms
---

### Post by MattPenfold on 2007-11-29
I am trying to get postfix working on 6.10 server.

I need to edit the main.cf in /etc/postfix to change the mydomain value which I did.

The main.cf file is as follows:

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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = huxley.dandderwen.co.uk
mydomain = dandderwen.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = dandderwen.co.uk, Huxley, localhost.localdomain, localhost
relayhost = smtp.dandderwen.co.uk
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


```

I then ran:

sudo postfix reload 

which as I understand it will cause any changes made to main.cf to take effect. However when I run

postconf -d 

I see mydomain set as "Huxley", not as in the main.cf file where it is set to "dandderwen.co.uk".

I have tried running:

sudo /etc/init.d postfix restart 

without luck. I also tried rebooting the server but still the wrong value for mydomain appears when you run postconf -d. 

Can anyone tell me what step I am missing to get the change made effective ?

---

### Post by MJN on 2007-11-29
**postconf -d** gives the *default* Postfix settings - I suspect what you actually wanted to do was **postconf -n**.
 
See **man postconf** for details.
 
Mathew

---

