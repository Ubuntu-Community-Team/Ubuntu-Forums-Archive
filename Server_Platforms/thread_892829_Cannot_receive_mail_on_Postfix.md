---
title: "Cannot receive mail on Postfix"
date: 2008-08-17
forum: Server Platforms
---

### Post by CP1256 on 2008-08-17
Hello,

I've set up a spare PC as a server by following the tutorial on Howtoforge for Ubuntu 8. 
The only problem I've got is that I can't receive mail, I'm using Postfix. 

I get the following error from Gmail when trying to send a mail:

Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at [http://mail.google.com/support/bin/answer.py?answer=7720](http://mail.google.com/support/bin/answer.py?answer=7720)
[private-server.uni.cc. (10): Connection timed out]

The e-mail adress I'm using is [email]contact@private-server.uni.cc[/email]. I can send mail to anybody, and receive mail but only if the e-mail adres is on my server.
Also I don't have my server running 24/7, only about 12 hours a day.

PS: Excuse me for any spelling errors, I'm Dutch.

---

### Post by lexarrow on 2008-09-06
I have the same problem

---

### Post by volkswagner on 2008-09-12
Me too.  

Here is my 

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = volkswagner.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = volkswagner.com, localhost.volkswagner.com, localhost
mynetworks = 127.0.0.1
mailbox_command = 
mailbox_size_limit = 0
mynetworks_style = host
inet_protocols = ipv4
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks reject_unauth_destination permit_inet_interfaces
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
disable_vrfy_command = yes
smtpd_helo_required = yes
smtpd_recipient_limit = 16
default_destination_recipient_limit = 16
maximal_queue_lifetime = 3d
relayhost = smtp-server.hvc.rr.com
```

I had to add the relay host as I could not send mail due to dynamic ip rejection.

---

### Post by volkswagner on 2008-09-13
DUH,

Got now.  I forgot to forward port 25 to my server in my router settings.  It was still going to another test server's ip.

---

### Post by windependence on 2008-09-13
You may also have problems if you don't have reverse DNS set up (PTR), but that is usually ony for outgoing mail.

-Tim

---

