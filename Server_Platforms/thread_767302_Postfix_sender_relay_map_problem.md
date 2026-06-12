---
title: "Postfix: sender relay map problem"
date: 2008-04-25
forum: Server Platforms
---

### Post by zazuge on 2008-04-25
I'm totaly mad
I spent days and weeks turning on the same spot without any progress at all, not say that i didn't find the answer searching on the web.
so her's my situation
I have two account one on yahoo ,and the other on gmail
I configured postfix and fetchmail to send and recive mail throught
my yahoo account , with proper adress rewriting and all.
after that  I did the same with gmail and added the certificate to let me send and recive throught gmail but the side effect is that i can no longer send with yahoo smtp server.
next i wanted to cohabitate the 2 setups
I used these line 
smtp_sender_dependent_authentication = yes
sender_dependent_relayhost_maps = hash:/etc/postfix/sender_relay
and my sasl password file is like this
```
#Per-sender authentication; see also /etc/postfix/sender_relay
myname@yahoo.fr       myname:pass1
myname@gmail.com      myname:pass2
# Login information for the default relayhost.
smtp.gmail.com:587 myname:pass2
#smtp.mail.yahoo.fr:465 myname:pass1
#smtp.mail.yahoo.fr:587 myname:pass1

```
and my sender relay file is like this
```
#myname@yahoo.fr smtp.mail.yahoo.fr:465
#myname@yahoo.fr smtp.mail.yahoo.fr:587
#myname@gmail.com smtp.gmail.com:587
@yahoo.fr       relay:smtp.mail.yahoo.fr:587
@gmail.com      relay:smtp.gmail.com:587

```
I tried different setups "commanted line" but without any change
the result is the same
```

connect to yahoo.fr[217.12.6.29]: Connection timed out (port 25)
connect to gmail.com[72.14.253.83]: Connection timed out (port 25)

```
as if sender_dependent_relayhost_maps  isn't there!
and if I uncomment the line relayhost = smtp.gmail.com:587
everything will work (only on gmail not on yahoo)
and her is the result of postconf -n
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
disable_dns_lookups = yes
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
masquerade_domains = /etc/mailname
maximal_backoff_time = 1000s
minimal_backoff_time = 100s
mydestination = localhost,localhost.localdomain,localdomain
myhostname = desktop
mynetworks = 192.168.1.0/24 192.168.0.0/24
mynetworks_style = subnet
myorigin = localhost
notify_classes = resource, software, bounce, delay, policy,protocol,
queue_run_delay = 60s
recipient_delimiter = +
relay_domains = 
sender_dependent_relayhost_maps = hash:/etc/postfix/sender_relay
smtp_generic_maps = hash:/etc/postfix/generic
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/smtp_auth
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_sender_dependent_authentication = yes
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_loglevel = 2
smtp_tls_note_starttls_offer = yes
smtp_tls_per_site = hash:/etc/postfix/tls_per_site
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination
smtpd_sasl_auth_enable = no
smtpd_sasl_local_domain = $myhostname
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
tls_random_source = dev:/dev/urandom
transport_maps = hash:/etc/postfix/transport

```
and pls, i didn't forget postmap!:(

---

### Post by zazuge on 2008-04-30
I've found the solution myself
it seems i had to put relay: before the smtp servers so is worked

---

### Post by ihuerta on 2010-03-10
Hi.

Could you please provide more details with the final working setup? I'm struggling with it for hours without success :P.

---

### Post by zazuge on 2010-03-11
> **ihuerta said:**
> Hi.

Could you please provide more details with the final working setup? I'm struggling with it for hours without success :P.

sorry i switched back to one smtp relay solution
and i stoped trying to learn postfix
(i didn't just for the fun i don't use postfix for workplace or anything)

---

