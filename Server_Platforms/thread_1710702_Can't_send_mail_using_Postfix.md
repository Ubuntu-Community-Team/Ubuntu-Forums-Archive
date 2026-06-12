---
title: "Can't send mail using Postfix"
date: 2011-03-20
forum: Server Platforms
---

### Post by stefangr1 on 2011-03-20
I would like to use Ubuntu to run my own mailserver. After going trough some tutorials (on Postfix + Dovecot + Squirrelmail), I got 'almost' everything up and running. The only problem is that I can't send mail to the outside world. 

I'm with an ISP that doesn't block anything (xs4all). I can telnet to mailservers from a terminal and send mail. Different users on the local network can also mail to each others.

The errors show up in my /var/log/mail.log as follows (I tried to send to different mailservers, and it's always the same):
```
Mar 20 15:00:21 linux postfix/smtp[4199]: connect to hotmail.com[64.4.20.186]:25: Connection timed out
```

When it attemtps to send, the network traffic contains several entries like:

```
14:35:56.881724 IP linux.local.44036 > dp4.mail.live.com.smtp: Flags [S], seq 4090956843, win 5840, options [mss 1460,sackOK,TS val 2139913 ecr 0,nop,wscale 7], length 0
E..<."@.@.y2....@..........+.........~.........
. .	........
```

My /etc/postfix/main.cf is as follows:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
mydomain = something.net
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

#message_size_limit = 204800000

myhostname = something.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $myhostname, linux.lan, localhost.lan, localhost
#mydestination = $myhostname
relay_domains = $myhostname
relayhost =
mynetworks = 10.0.0.0/24, 192.168.1.0/24, 127.0.0.0/8
mailbox_size_limit = 2048000000
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_enforce_tls = no
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_sasl_authenticated permit_mynetworks reject_invalid_helo_hostname reject_non_fqdn_helo_hostname


# how long to wait when servers connect before receiving rest of data 
smtp_helo_timeout = 60s 
# how many address can be used in one message. 
# effective stopper to mass spammers, accidental copy in whole address list 
# but may restrict intentional mail shots. 
smtpd_recipient_limit = 16 
# how many error before back off. 
smtpd_soft_error_limit = 3 
# how many max errors before blocking it.
smtpd_hard_error_limit = 12
```

I've been looking on the internet for a solution for over tho hours now, so I really hope somebody knows something...

---

### Post by stefangr1 on 2011-03-20
I'm getting a little closer. Postfix seems to connect to the wrong mail servers. For example, for an @hotmail.com address it contacts hotmail.com in stead of mx1.hotmail.com. Almost all mail servers are on something like mail.domain.com or mx1.domain.com, whereas Postfix on my system always attempts to connect to domain.com.

I have obviously misconfigured something, such that Postfix can't find the smtp server corresponding to an email address, but what...

Any ideas?

---

### Post by stefangr1 on 2011-03-20
Okay, I finally solved it. It was a DNS problem. I had the ip-address of my router in my /etc/resolv.conf. I've never experienced any problems with that, and if I would do 'dig domain.com' it would work fine. I just found ou that if I do 'dig -t MX domain.com', however, it returns nothing at all...

The solution was thus to simply replace my router with a 'real' domain server.

---

