---
title: "Postfix basic setup issue"
date: 2010-12-20
forum: Server Platforms
---

### Post by ldw on 2010-12-20
I've spent days troubleshooting and seem to be going in circles. I appreciate any feedback you can give.

Fresh install of Ubuntu 10.10 w/ Postfix

Simple Goal: To accept email for domain 'mail.domain.com' and match the TO: address to an (virtual?)alias table so the email then forwards out to the new address on a different domain (lets say Gmail).

Example - Email sent to [email]user1@mail.domain.com[/email] should forward to [email]user1@gmail.com[/email]

My Postfix server is receiving mail, but not forwarding the message out to the matching address in virtual.db.

/var/log/mail.log shows the emails hitting the my server then reports the following error "Recipient address rejected: User unknown in virtual alias table"

The matching entry seems to be correct in the '/etc/postfix/virtual' file:
"user1@mail.domain.com [email]user1@gmail.com[/email]"

and I've run "postmap virtual" and then reloaded Postfix "/etc/init.d/postfix reload" every time I make a change, and I rebooted the whole server just in case.

Here's a 'postconf -n' output:
__________________________________
mail1:/etc/postfix# postconf -n
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
home_mailbox = mail/
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = mail.domain.local, localhost.domain.local, localhost
myhostname = mail.corporate.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = $mydomain
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_domains = mail.domain.com
virtual_alias_maps = hash:/etc/postfix/virtual
_______________________


I think i'm screwing up some combination of the following parameters:
mydestination 
myhostname 
virtual_alias_domains
virtual_alias_maps
myorigin

Since i'm trying to forward to a matching gmail.com address, should I have 'gmail.com' listed as a 'virtual_alias_domain' ?

Any help is greatly appreciated, thank you,

---

### Post by stmiller on 2010-12-20
This should do it:

```
sudo nano /etc/postfix/virtual
```

```
user@domain.com           email@gmail.com
```


Then run:

```
sudo postmap hash:/etc/postfix/virtual
```


/etc/postfix/main.cf needs something like this:

virtual_alias_maps = hash:/etc/postfix/virtual
virtual_alias_domains = domain.com

Then restart postfix. 

That should do it...

---

### Post by ldw on 2010-12-21
You make it sound so easy..... and it's working now  :)

I think this was my problem:  sudo postmap hash:/etc/postfix/virtual

I was just using:   sudo postmap /etc/postfix/virtual
....  leaving out the "hash:" portion 

I figured it was a small detail causing the problem. Thank you,

---

