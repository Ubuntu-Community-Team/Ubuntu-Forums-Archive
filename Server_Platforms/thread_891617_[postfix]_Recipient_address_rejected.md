---
title: "[postfix] Recipient address rejected"
date: 2008-08-16
forum: Server Platforms
---

### Post by Krzysiek_PL on 2008-08-16
Hi!
I've just set up my mail server using postfix. When I try to send en email to myself from another domain (through webmail) I receive the following error message:

```
<krzysiek@dns123.mooo.com>:
83.5.180.158 does not like recipient.
Remote host said: 550 5.1.1 <krzysiek@dns123.mooo.com>: Recipient address rejected: dns123.mooo.com
Giving up on 83.5.180.158.
```

and here is my main.cf file:

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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = aaqu158.neoplus.adsl.tpnet.pl
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =	kzajac, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128, 212.77.101.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
default_transport = error
relay_transport = error
html_directory = /usr/share/doc/postfix/html

virtual_alias_domains = wp.pl
#virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf mysql:/etc/postfix/mysql-virtual_email2email.cf
#virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf mysql:/etc/postfix/mysql-virtual_email2email.cf
#virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
#virtual_uid_maps = static:5000
#virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
#smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
```

I know: "google is your friend" but I've searched it all day with no result:(

---

### Post by MJN on 2008-08-16
Assuming dns123.mooo.com is you then you need to tell Postfix it is the final destination for this domain. Do this by adding the domain to your existing virtual_alias_domains directive.

Also, you have no MX records for dns12.mooo.com (or rather the mooo.com DNS servers are not resolving the domain):

```
$ dig dns123.mooo.com mx

; <<>> DiG 9.3.2-P2.1 <<>> dns123.mooo.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 19780
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;dns123.mooo.com.               IN      MX

;; Query time: 6021 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Aug 16 18:25:34 2008
;; MSG SIZE  rcvd: 33
```Mathew

---

