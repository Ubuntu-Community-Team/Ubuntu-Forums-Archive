---
title: "Postfix &amp; Dovecot mailserver Xubuntu. Can't recieve nor send mails"
date: 2010-01-10
forum: Server Platforms
---

### Post by freddan007 on 2010-01-10
Edited:
I can't send mails from my server other than with squirrelmail. I tried with thunderbird but i am asked for the password and when I type it I am asked for it again.

---

### Post by Barriehie on 2010-01-10
Are you running any type of spam filtering package on your server???

---

### Post by noway2 on 2010-01-10
The error messages are saying "relay access denied".  This is an authentication problem.  You need to configure the smtp_recipient_restrictions.  You are probably going to also want SASL authentication as it is a very bad idea to transmit the auth information in clear text.

There are many how to documents and threads on this subject in this forum.
A search should give you more than enough information to get started.

---

### Post by freddan007 on 2010-01-10
> **Barriehie said:**
> Are you running any type of spam filtering package on your server???No, I followed this tutorial:
[http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)
From step 3 to the  end of step 3c where you are instructed to try the server with a mail-client.



Edit: I changed the SASL settings, it appears as it wasn't starting, and installed squirrelmail. I can send mails with squirrelmail to any adress but I still can't send mails to my server. If i try i get the "554 554 5.7.1 <[EMAIL="tovell@tovell.ath.cx"]name@mysubdomain.ath.cx[/EMAIL]>: Relay access denied (state 14)." error.
Here is my etc/postfix/main.cf:
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# Dessa har jag lagt till manuellt.
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = mysubdomain.ath.cx
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_sasl_security_options = noanonymous  

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = server-laptop
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8, <CIDR Address Block e.g. 209.152.115.0/24>
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
mailbox_command = 
inet_protocols = all
```

---

### Post by freddan007 on 2010-01-10
bump

---

### Post by noway2 on 2010-01-10
Why did you bump this post after a couple of hours?

---

### Post by freddan007 on 2010-01-11
> **noway2 said:**
> Why did you bump this post after a couple of hours?Because my topic was heading down and I was going to sleep thus I thought if I bumped I would maybe get help before I woke up. But I didn't.

---

### Post by freddan007 on 2010-01-11
I've got recieving mails working now, I hadn't added my public domain in the mydestination in main.cf. However, I still have a problem. I can't send mails from my server other than with squirrelmail. I tried with thunderbird but i am asked for the password and when I type it I am asked for it again.

---

### Post by freddan007 on 2010-01-12
Bump

---

### Post by freddan007 on 2010-01-12
Bump

---

### Post by ICEB3AR on 2010-01-12
Although I found it very unfair, if someone bumps his thread after a couple of hours I'll try to help you.

In the main.cf of my old server some months ago I think I've written my defaulturl as myhostname = [defaulturl] so e.g.:

myhostname = test.com

That's something which I remebered to have different, but I'm not sure, if it's the reason or if it do also work your way.

---

### Post by noway2 on 2010-01-12
I believe this may be your problem: [http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination](http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination)

You might also like to take a look at this article: [http://en.wikipedia.org/wiki/Bump_(Internet](http://en.wikipedia.org/wiki/Bump_(Internet)).

---

