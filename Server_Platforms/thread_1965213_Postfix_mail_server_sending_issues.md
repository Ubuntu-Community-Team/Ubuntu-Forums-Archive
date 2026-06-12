---
title: "Postfix mail server sending issues"
date: 2012-04-25
forum: Server Platforms
---

### Post by louis vitton on 2012-04-25
Hey guys,

I have installed postfix mail server on my ubuntu 11.04 VPS and it send mails no worries and recives then no problems from each other on the same domain.
example of the mail sent from "root" to "webmaster";

from: [email]root@srv.example.com[/email]
To: [email]webmaster@example.com[/email]

This mail works fine but the "From" field has srv.example.com instead of the FQDN of example.com that i want it to be.
srv.example.com is the host name of the VPS server.

I have set up 1 record in the DNS for the mail server which is mail.example.com as an MX under example.com

The apache server with i run is working fine still. 

Code of the postfixe setup - changed the real domains to example.
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
myhostname = mail.example.com
mydomain = example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = example.com
mydestination = $mydomain, www.$mydomain, $myhostname
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
notify_classes = bounce, delay, resource
smtpd_recipient_restrictions = reject_non_fqdn_recipient reject_unknown_recipient_domain permit_mynetworks permit_sasl_authenticated reject_unauth_destination reject_non_fqdn_hostname reject_invalid_hostname check_helo_access pcre:/etc/postfix/helo_checks check_sender_mx_access cidr:/etc/postfix/bogus_mx reject_rbl_client zen.spamhaus.org reject_rbl_client cbl.abuseat.org reject_rbl_client dnsbl-1.uceprotect.net permit

```

Cheers for any help

Louis

---

### Post by louis vitton on 2012-04-25
bump still need help please.
Cheers

---

### Post by nsnidanko on 2012-04-26
You can do this with canoical mappings. Please refer to the following link for a guide:

[http://ubuntuforums.org/showthread.php?t=38429](http://ubuntuforums.org/showthread.php?t=38429)

---

