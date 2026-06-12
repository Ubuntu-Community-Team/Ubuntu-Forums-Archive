---
title: "Setting up Postfix: telnet test gives no response"
date: 2011-05-02
forum: Server Platforms
---

### Post by Demented ZA on 2011-05-02
I'm setting up Postfix as per the [Community Postfix Page]("https://help.ubuntu.com/community/Postfix"). When I get to the part where I test my server using telnet, I get the following:
```
$ telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
ehlo localhost




^]
telnet>quit
$

```
I get no output from Postfix stating capabilities and security mechanisms.

Some information:
```
$ sudo netstat -plntu | grep 25
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      2159/master
tcp6       0      0 :::25                   :::*                    LISTEN      2159/master
udp        0      0 192.168.0.255:137       0.0.0.0:*                           1089/nmbd
udp        0      0 192.168.0.255:138       0.0.0.0:*                           1089/nmbd
```

My /etc/postfix/main.cf
```
biff = no
readme_directory = no

# TLS parameters
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

alias_maps = hash:/etc/aliases
#myorigin = /etc/mailname
mydestination = localhost

mailbox_size_limit = 0
inet_protocols = all
home_mailbox = /Maildir/

#relayhost = smtp.myispsmtpserver.com
notify_classes = $myhostname, localhost.$mydomain, $mydomain
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
inet_interfaces = all
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
myhostname = myhostname #edited for privacy
disable_vrfy_command = yes

```

---

### Post by Demented ZA on 2011-05-03
I solved my own problem. First I restored back to an easier setup (a closer to the default setup) and even that didn't work. I then did the following:
```
$sudo tail /var/log/mail.err
```
Witch yielded plenty of the following:
```
May  3 08:21:07 hostname postfix/local[23627]: fatal: open database /etc/aliases.db: No such file or directory
```

Since aliases.db is a hashed file of /etc/aliases, it probably hasn't been hashed yet, hence the missing file. This is a new Ubuntu server installation.

So I did this:
```
$sudo newaliases
$sudo service postfix restart
```

Problem solved!

At least now I need to re-implement authentication and ssl etc.

Guess I have to remember to get the simple things working first, and then build on that.

---

