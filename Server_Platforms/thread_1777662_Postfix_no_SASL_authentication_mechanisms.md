---
title: "Postfix: no SASL authentication mechanisms"
date: 2011-06-08
forum: Server Platforms
---

### Post by ZuOverture on 2011-06-08
Hello again.

This time I tried to add mail server to AD, built on Samba4. Nothing to do with AD for now, actually. Following [https://help.ubuntu.com/11.04/serverguide/C/email-services.html](https://help.ubuntu.com/11.04/serverguide/C/email-services.html) I've managed to make Postfix send outgoing mails (without LDAP authentication).

Problem is: incoming mail is lost somewhere. Obvious reason for that is in mail.log:
```
Jun  8 11:40:36 PDC1 postfix/smtpd[5944]: Anonymous TLS connection established from mail-pz0-f43.google.com[209.85.210.43]: TLSv1 with cipher RC4-SHA (128/128 bits)
Jun  8 11:40:36 PDC1 postfix/smtpd[5944]: warning: SASL: Connect to private/dovecot-auth failed: No such file or directory
Jun  8 11:40:36 PDC1 postfix/smtpd[5944]: fatal: no SASL authentication mechanisms
Jun  8 11:40:37 PDC1 postfix/master[5931]: warning: process /usr/lib/postfix/smtpd pid 5944 exit status 1
Jun  8 11:40:37 PDC1 postfix/master[5931]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
```

Don't know what should be the full path to dovecot-auth, but the only one is located in /usr/lib/dovecot/dovecot-auth. Does it have something to do with chroot'ing? I believe it is off.

```
pdcadmin@PDC1:/$ cat /etc/postfix/master.cf
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       n       -       -       smtpd
```


```
pdcadmin@PDC1:/$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases, ldap:/etc/postfix/ldap-aliases.cf
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
mydestination = mydomain.dyndns.com, PDC1, localhost.localdomain, localhost
myhostname = PDC1
mynetworks = 192.168.0.0/24 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname <- contains "mydomain.dyndns.com"
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_tls_loglevel = 2
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```

One more question is if saslauthd should take part in auth process, or dovecot have all what's necessary by itself?

```
pdcadmin@PDC1:/$ ps ax | grep sasl
  916 ?        Ss     0:00 /usr/sbin/saslauthd -a pam -c -m /var/run/saslauthd -n 5
  917 ?        S      0:00 /usr/sbin/saslauthd -a pam -c -m /var/run/saslauthd -n 5
  918 ?        S      0:00 /usr/sbin/saslauthd -a pam -c -m /var/run/saslauthd -n 5
  919 ?        S      0:00 /usr/sbin/saslauthd -a pam -c -m /var/run/saslauthd -n 5
  921 ?        S      0:00 /usr/sbin/saslauthd -a pam -c -m /var/run/saslauthd -n 5
 5977 pts/0    S+     0:00 grep --color=auto sasl
pdcadmin@PDC1:/$ saslauthd -v
saslauthd 2.1.23
authentication mechanisms: sasldb getpwent kerberos5 pam rimap shadow ldap
```

Any advices?

---

### Post by venol on 2011-06-08
Do you use TLS? If you use it, We have same problem. So, I don't use TLS. 

may be you can change dovecot.conf
> path = /var/spool/postfix/private/auth-client

to

> path = /var/spool/postfix/private/auth

and then change smtpd_sasl_path to private/auth.

---

### Post by venol on 2011-06-08
Do you use TLS? If you use it, We have same problem. So, I don't use TLS. 

may be you can change dovecot.conf
> path = /var/spool/postfix/private/auth-client

to

> path = /var/spool/postfix/private/auth

and then change smtpd_sasl_path to private/auth in main.cf.

---

### Post by ZuOverture on 2011-06-08
Well, my bad. After purging first unsuccessful dovecot installation, I've forgotten to restore client socket description in dovecot.conf. So this question is resolved, but not the issue itself. On to the next one :)

[QUOTE="venol"]Do you use TLS? If you use it, We have same problem. So, I don't use TLS.[/QUOTE]
Anonymous TLS connections are established successfully (as far as I can see - tested by sending mails from GMail only).

---

