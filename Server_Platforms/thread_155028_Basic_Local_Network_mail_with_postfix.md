---
title: "Basic Local Network mail with postfix"
date: 2006-04-04
forum: Server Platforms
---

### Post by BigErn on 2006-04-04
Hi, I'm really new to anything mail related so forgive my ignorance.  

I'm basically trying to set up a mail system on my local network, which is just 2 ubuntu boxes connected by a cheap router.  I have postfix, mailx, and procmail installed on both of my ubuntu boxes.  

While I am able to sendmail locally (say, from root to a user on the same machine) , nothing goes over the network.  Do I need extra software beyond postfix to accomplish this?  I know Postfix is an MTA (Mail Transfer Agent), and I'm not even sure what that is!  Does it listen on a port?

Here's my postfix main.cf:

```
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

myhostname = yosemite
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname yosemite.$mydomain yosemite
relayhost =
mynetworks = 127.0.0.0/8 192.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

```

Edit:  I just noticed I can telnet this ubuntu box with 'telnet yosemite 25' and then send mail with certain telnet commands.  What I'm trying to achieve though, is to be on my other machine and sendmail to yosemite with something like 'sendmail someuser@yosemite' .

Edit:  And when I do that, the log for the other computer (not yosemite) says:

707C197C65: to=<someuser@yosemite>, relay=none, delay=0, status=bounced (Host or domain name not found. Name service error for name=yosemite type=AAAA: Host not found)

---

