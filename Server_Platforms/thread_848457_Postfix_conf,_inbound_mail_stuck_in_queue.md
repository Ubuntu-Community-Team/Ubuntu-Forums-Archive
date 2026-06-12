---
title: "Postfix conf, inbound mail stuck in queue"
date: 2008-07-03
forum: Server Platforms
---

### Post by chucksteel on 2008-07-03
Hello all,
I am a newbie... I have installed Ubuntu server 8.0.4 and had no problem with the installation. The web server and webmin work flawlessly.
I also installed Postfix for a mail server. I have a good MX record at my ISP, I can send out through the internet but when I receive mail (internet or local) it just hangs in the queue. In other words it won't delivery it to the mailbox directories for the users. 
I have been through my config file several times but being a newbie I can't find my mistake.
could the problem be the mailbox command?
***
copy of my config below
****
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
# is /etc/mailname.
myorigin = $mydomain
proxy_interfaces = 70.62.40.131
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 1m

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = zmail.edisonplus.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = zmail.edisonplus.net localhost.edisonplus.net localhost edisonplus.net
mynetworks = 172.16.32.0/19; 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = 
mailbox_size_limit = 1000000
recipient_delimiter = +
swap_bangpath = no
smtpd_recipient_restrictions = permit_mynetworks reject_unauth_destination permit_inet_interfaces permit_sasl_authenticated
home_mailbox = Maildir/

---

### Post by ZabiGG on 2008-07-04
Hi and welcome to Ubuntu;)

I've found a Postfix page on the community documentation site:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

This might help you solve your problem.

If you want to learn more about your new system and how to take advantage of it, I'd suggest reading up  bit on the terminal and Ubuntu/linux in general.

There are very informative links available if you click the "Look here" link in m signature below.

Hope this helps,

Z.

---

### Post by iyayan on 2009-06-11
> **chucksteel said:**
> Hello all,
I am a newbie... I have installed Ubuntu server 8.0.4 and had no problem with the installation. The web server and webmin work flawlessly.
I also installed Postfix for a mail server. I have a good MX record at my ISP, I can send out through the internet but when I receive mail (internet or local) it just hangs in the queue. In other words it won't delivery it to the mailbox directories for the users. 
I have been through my config file several times but being a newbie I can't find my mistake.
could the problem be the mailbox command?
***
copy of my config below
****
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
# is /etc/mailname.
myorigin = $mydomain
proxy_interfaces = 70.62.40.131
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 1m

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = zmail.edisonplus.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = zmail.edisonplus.net localhost.edisonplus.net localhost edisonplus.net
mynetworks = 172.16.32.0/19; 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = 
mailbox_size_limit = 1000000
recipient_delimiter = +
swap_bangpath = no
smtpd_recipient_restrictions = permit_mynetworks reject_unauth_destination permit_inet_interfaces permit_sasl_authenticated
home_mailbox = Maildir/

same with my postfix server, and now Iam still find the solutions, have U a solutions for that problem now?

---

### Post by iyayan on 2009-06-12
OMG, last year ago

---

