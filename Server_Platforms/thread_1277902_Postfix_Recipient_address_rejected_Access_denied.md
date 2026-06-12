---
title: "Postfix Recipient address rejected: Access denied"
date: 2009-09-28
forum: Server Platforms
---

### Post by Ansubaca on 2009-09-28
I have read through other older posts and am still having issues with Postfix. I can send mail but am receiving errors when messages are received by my server. I am a wee bit frustrated and am probably overlooking something simple. 

Here is an example error:

Sep 28 18:48:12 Nebula postfix/smtpd[7662]: NOQUEUE: reject: RCPT from mail4.radiobase1.clearchannel.com[207.230.157.133]: 554 5.7.1 <christine@sizzlefish.com>: Recipient address rejected: Access denied; from=<administrator@mail7.radiobase1.clearchannel.com> to=<christine@sizzlefish.com> proto=ESMTP helo=<mail4.radiobase1.clearchannel.com>
[U]
**postconf -n**[/U]
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
mailbox_command =
mailbox_size_limit = 0
mydestination = $mydomain, Nebula, localhost.localdomain, localhost
mydomain = sizzlefish.com
myhostname = mail.sizzlefish.com
mynetworks = 127.0.0.0/8, 192.168.x.y/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_alias_domains = staterevs.com, imagesofseattle.org
virtual_alias_maps = hash:/etc/postfix/virtual

Any ideas?

---

### Post by enz1m3 on 2009-09-30
Are you sure the [email]christine@sizzlefish.com[/email] account exists? Is it in the /etc/postfix/virtual ?

---

### Post by Ansubaca on 2009-09-30
Here is /etc/postfix/virtual/ Everyone receiving email on the system is here.

# Sizzlefish.com
[email]postmaster@sizzlefish.com[/email]       rich@localhost
[email]webmaster@sizzlefish.com[/email]        rich@localhost
[email]rich@sizzlefish.com[/email]             rich@localhost
[email]christine@sizzlefish.com[/email]        christine@localhost
[email]taylor@sizzlefish.com[/email]           taylor@localhost
[email]brian@sizzlefish.com[/email]            brian@localhost

# Staterevs.com
[email]postmaster@staterevs.com[/email]        kentg@localhost
[email]webmaster@staterevs.com[/email]         kentg@localhost
[email]kent@staterevs.com[/email]              kentg@localhost

# Imagesofseattle.org
[email]postmaster@imagesofseattle.org[/email]  terry@localhost
[email]webmaster@imagesofseattle.org[/email]   terry@localhost

---

### Post by noway2 on 2009-09-30
Did you run postmap to map the recipients to the hash table?

A typical meaning to this message is that an attempt was made send mail to a non-existent account.

---

### Post by Ansubaca on 2009-10-01
I ran "postfix reload" several times and postfix restarted without error. It is my understanding that the reload process forces postfix to reread the tables. Correct?

For point of clarification, I was on a static IP and postfix was running without problems. I changed to a dynamic IP and also am using the system as a firewall. This is not a new installation. Rather, a modification of the current system for different settings.

---

### Post by Ansubaca on 2009-10-06
OK, problem solved. The issue was main.cf not having "reject_unauth_destination" rather than just "reject" (below).

# smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,re
ject
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

---

