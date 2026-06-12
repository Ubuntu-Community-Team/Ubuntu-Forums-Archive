---
title: "postfix / smtp  and the barkley db"
date: 2007-02-26
forum: Server Platforms
---

### Post by TheCaptain2000 on 2007-02-26
Hi, I am trying to setup  a mal server using edgy/postgres/postfix/postfixadmin. I managed to get pop3/imap working fine, but when I was trying to  send emails I get: 

on the server:
warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory

warning: SASL authentication failure: Password verification failed
warning: unknown[192.168.2.4]: SASL PLAIN authentication failed: authentication failure



 I have libsasl2-modules-sql installed and I have created /etc/postfix/sasl/smtpd.conf as:

asl_pwcheck_method: auxprop
sasl_auxprop_plugin: pgsql
srp_mda: md5
password_format: crypt
mech_list: login plain
#mech_list: CRAM-MD5 DIGEST-MD5
#log_level: 3

sql_engine: pgsql
sql_hostnames: localhost
sql_database: postfix
sql_user: postfix
sql_passwd: *************
sql_select: SELECT password FROM mailbox WHERE username='%u@%r'
sql_usessl: no


permissions are :
-rw-r--r-- 1 root root 342 2007-02-26 11:57 smtpd.conf


I have modified /etc/postfix/master.cf for:
smtp      inet  n       -       n       -       -       smtpd

 and 

smtps     inet  n       -       n       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes


my main.cf includes:

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unauth_destination,check_policy_service inet:127.0.0.1:60000, permit_sasl_authenticated, permit

smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

if Anybody could give me a hand I would **really** apreciated

---

### Post by The Foz on 2007-06-06
I have exactly the same problem.

What is postfix looking for in /etc/sasldb2 ? There are no references to this directory in any of the config file. Nor is there any reference to the use of Berkley databases, unless this has something to do with the ue of B-Tree for the session caches.

---

