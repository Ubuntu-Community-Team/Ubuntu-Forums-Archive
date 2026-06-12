---
title: "Failure on Test Virtual Mailbox Setup"
date: 2007-11-08
forum: Server Platforms
---

### Post by satimis on 2007-11-08
Hi folks,


Ubuntu 7.04 server amd64
postfix 2.3.8


Following;
PostfixBasicSetupHowto
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

building a mail server which is now working.


Then I followed;
PostfixVirtualMailBoxClamSmtpHowto
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

continue to build Postfix virtual mailboxes.  No complaint was found on each step performed.

domain1 = satimis.com
domain2 = satimis.changeip.net


$ cat /etc/postfix/main.cf```

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

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $myhostname
mydestination = mail.satimis.com, ubuntu.satimis.com, satimis.com, localhost.satimis.com, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
virtual_alias_maps = hash:/etc/postfix/virtual
# Specify your NAT/proxy EXTERNAL address here.
#proxy_interfaces = 220.232.213.178
proxy_interfaces = 1.2.3.4
virtual_alias_domains = satimis.com satimis.changeip.net

virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

```
here I changed;```

myhostname = localhost

```

from:```

myhostname = ubuntu.satimis.com

```

I haven't made any change on /etc/hosts```

$ cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost
127.0.1.1       ubuntu.satimis.com      ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


Re: Test Virtual Mailbox Setup

$ mail [email]info@satimis.com[/email]```

Subject: Test

Hi

satimis
.
Cc: stephen@satimis.com

```

user, [email]stephen@satimis.com[/email], receives the mail.

But I can't find /home/vmail/satimis.com
directory.

$ ls -al /home/vmail/```

total 20
drwxr-xr-x  2 vmail vmail 4096 2007-11-08 18:56 .
drwxr-xr-x 11 root  root  4096 2007-11-08 18:56 ..
-rw-r--r--  1 vmail vmail  220 2007-11-08 18:56 .bash_logout
-rw-r--r--  1 vmail vmail 2298 2007-11-08 18:56 .bashrc
-rw-r--r--  1 vmail vmail  566 2007-11-08 18:56 .profile

```


$ sudo find / -name satimis.com -type d
No printout


Please advise where I have to check and how to fix the problem.  TIA


B.R.
satimis

---

