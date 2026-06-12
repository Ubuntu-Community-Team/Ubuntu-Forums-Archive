---
title: "Cannot Receive External E-Mail"
date: 2013-11-27
forum: Server Platforms
---

### Post by fobos3 on 2013-11-27
Hi,

I have an Ubuntu server running 12.04 and I can't receive external e-mail. I can send to external e-mail and I can receive internal messages. I checked my DNS records and they point to the correct address and my ports are open. I think my problem is connected with /etc/hosts and /etc/resolv.conf.

My /etc/resolv.conf:
```

nameserver 8.8.8.8

```
Which is Google's DNS. I added that because the file was empty and I couldn't resolve domain names.

My /etc/hosts:
```

127.0.0.1       localhost  
127.0.0.1       ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

I have postfix/dovecot running. There is no errors in /var/log/mail.err and nothing interesting in /var/log/mail.log (just connect and disconnect from Thunderbird to retrieve e-mails). My /etc/postfix/main.cf:
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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = xxx
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = xxx, ubuntu
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
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

```
Where xxx is my domain name.

Any ideas?

P.S. I also tried adding:
```

127.0.0.1 xxx
server IP xxx

```
But nothing changed.

---

### Post by nerdtron on 2013-11-27
```
127.0.0.1       mail.domainname.com localhost localhost.localdomain
127.0.1.1       mail.domainname.com
Server IP     mail.domainname.com mail

```

That is a part of our mail server /etc/hosts file. Just replace the "domainname" with your domain name.
Still you should test if the MX record and A record address of the server is reachable from the public.
I used the website [http://mxtoolbox.com/SuperTool.aspx](http://mxtoolbox.com/SuperTool.aspx)
Just input your domain name (don't include the mail. part) and it should return the public address of the MX record of your server. If not, you might have problems with your DNS configuration.

---

### Post by fobos3 on 2013-11-27
I tried the hosts files and it didn't help, so I guess the problem is somewhere else. Also, I did test my domain name and I retrieve the proper MX and A records.

---

