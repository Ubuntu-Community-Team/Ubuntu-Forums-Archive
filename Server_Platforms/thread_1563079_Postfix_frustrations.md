---
title: "Postfix frustrations"
date: 2010-08-28
forum: Server Platforms
---

### Post by wesg on 2010-08-28
I've set up a VPS for my employers web hosting, which is running a LAMP stack + mail server. I struggled with sendmail, then moved to postfix, and have been able to get messages not rejected by an external tester [http://network-tools.com/default.asp](http://network-tools.com/default.asp) . I think postfix is where I need to be, however whenever I test a message to one of the user accounts on the server, I get a 554 Relay access denied error. Apparently this has something to do with domains and addresses, based on my Googling, but I'm still stuck. 

Using telnet I can send messages to other local users, so it must be something to do with domains. 

Any suggestions? I can post my main.cf file here if needed.

---

### Post by lisati on 2010-08-28
Have you included "permit_mynetworks" in the "smtpd_recipient_restrictions = " entry in Postfix's main.cf file? If so, the order of what you have there can sometimes make a difference. A simple example of what to include and a usable order can be found at [http://www.spamcop.net/fom-serve/cache/349.html](http://www.spamcop.net/fom-serve/cache/349.html)

---

### Post by wesg on 2010-08-28
Here is my postconf -n output. I just added the restriction line and my email test timed out. I removed the line, and it went through, but still had a relay block.

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = server1.iversoft.ca, localhost.iversoft.ca, iversoft.ca, localhost
myhostname = server1.iversoft.ca
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128, 98.158.187.0/24
myorigin = mail.iversoft.ca
readme_directory = no
recipient_delimiter = +
relayhost = iversoft.ca
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_domains = iversoft.ca

```

---

### Post by wesg on 2010-08-28
Progress! Through Telnet, I've been able to send a message to my gmail account. My problem now is that I want to forward my user account mail to another address.

I've heard putting a .forward file in the home folder works, but I just realized that my user account doesn't have a home folder, because I just want to use it for email. What other file do I edit?

---

