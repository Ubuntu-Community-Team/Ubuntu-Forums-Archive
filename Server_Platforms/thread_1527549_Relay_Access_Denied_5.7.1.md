---
title: "Relay Access Denied 5.7.1"
date: 2010-07-09
forum: Server Platforms
---

### Post by comicbookcrap on 2010-07-09
Greetings -
 
Setup an Ubuntu LAMP server to house a Wordpress site. Everything is gravy but I am having some troubles getting emails to route outside my local network. I have setup Internet and also added my ISP SMTP as a smarthost - either way I get the dreaded Relay Access Denied 5.7.1.
 
I am using DynDns as I do not have a static IP - not sure if this makes a difference?
 
telnet my_dyn_dns.org 25
ehlo localhost
250-my_dyn_dns.org
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: user @ my_dyn_dns.org
250 2.1.0 Ok
rcpt to: external @ somewhere
554 5.7.1 : Relay access denied

[SIZE=2]
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

myhostname = my_dyn_dns.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost, my_dyn_dns.org, localhost.com, localhost
relayhost = 
mynetworks = 127.0.0.0/8 
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

I have also tried the above with my ISP smtp IP in relayhost - same error.
 
Fairly new at the backend email piece but the articles I have ready suggest this should not be too difficult. 
 
Thank you in advance for your assistance!
 
 
[/SIZE]

---

### Post by Devi1903 on 2010-07-09
I have come across this problem before. I fixed it by making the client authenticate with a users login to the smtp server.

---

### Post by comicbookcrap on 2010-07-09
> **Devi1903 said:**
> I have come across this problem before. I fixed it by making the client authenticate with a users login to the smtp server.
 
Do you happen to have the syntax?
 
user:
password: 
 
?
 
Thank you!

---

