---
title: "Postfix refusing external connections"
date: 2013-09-02
forum: Server Platforms
---

### Post by kdude63 on 2013-09-02
I'm having issues connecting to postfix on port 25. 
Running telnet to port 25 from anything but the server itself, the connection times out.
It was working before, and I have no idea what caused it to stop working.

My main.cf:
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
smtpd_tls_cert_file = /etc/dovecot/dovecot.pem
smtpd_tls_key_file = /etc/dovecot/private/dovecot.pem
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mail.kdude63.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot.conf -m "${EXTENSION}"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/


smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 
broken_sasl_auth_clients = yes


smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain


smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom


# Getting rid of unwanted headers. See: https://posluns.com/guides/header-removal/
header_checks = regexp:/etc/postfix/header_checks
# getting rid of x-original-to
enable_original_recipient = no


# This specifies where the virtual mailbox folders will be located.
virtual_mailbox_base = /var/vmail
# This is for the mailbox location for each user. The domainaliases
# map allows us to make use of Postfix Admin's domain alias feature.
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf, mysql:/etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf
# and their user id
virtual_uid_maps = static:150
# and group id
virtual_gid_maps = static:8
# This is for aliases. The domainaliases map allows us to make 
# use of Postfix Admin's domain alias feature.
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf, mysql:/etc/postfix/mysql_virtual_alias_domainaliases_maps.cf
# This is for domain lookups.
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
```

---

### Post by newbie-user on 2013-09-02
You need to add your local subnets to mynetworks if you want to access postfix externally. For example, adding a 192.168.0.0/24 network would make it look like this:
```

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/24

```
Without setting that, only your server can send mail.

---

### Post by kdude63 on 2013-09-02
So if I've got my mail server running on a VPS, how would I go about setting that? As far as I'm aware, it's not running on a subnet.

---

### Post by CharlesA on 2013-09-03
Run this please:

```
sudo netstat -nlp | grep 25
```

---

### Post by kdude63 on 2013-09-03
> **CharlesA said:**
> Run this please:

```
sudo netstat -nlp | grep 25
```

```

tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1964/master     
tcp6       0      0 :::25                   :::*                    LISTEN      1964/master

```

---

### Post by CharlesA on 2013-09-03
Should be fine.. Are you trying to send mail using port 25 from an email client, or what are you doing?

---

### Post by kdude63 on 2013-09-03
I'm trying to send mail from an email client on my phone.

---

### Post by CharlesA on 2013-09-03
Normally port 25 is blocked by ISP unless you are on a business connection. Transfering mail via port 25 is usually for server-to-server transfer, with port 587 being the default for mail clients.

Double check your setup and/or call your ISP/phone carrier and see if they are blocking port 25 outbound.

---

### Post by kdude63 on 2013-09-03
Okay, so as it turns out, scumbag Comcast is blocking port 25 outbound.
I was able to telnet from another machine just fine. (I don't know why I didn't try that first off.)
The reason it was working before is because I tested it from school, as opposed to home.
Thanks!

---

### Post by CharlesA on 2013-09-03
Glad you got it sorted.

---

