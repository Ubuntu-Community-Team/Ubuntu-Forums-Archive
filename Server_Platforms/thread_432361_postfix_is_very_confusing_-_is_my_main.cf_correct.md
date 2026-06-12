---
title: "postfix is very confusing - is my main.cf correct?"
date: 2007-05-03
forum: Server Platforms
---

### Post by nomb on 2007-05-03
Hey guys I have drupal and gallery2 working flawlessly except I can't get drupal to send emails out.  My firewall is off.  Reading online everyone said you have to insall postfix.  So I did but then i got an error during install saying my hostname was wrong.  I went into main.cf and changed it and I don't get the error anymore but it isn't working still.  Is there somewhere I have to put in my smtp server information?  Here is my cf file.

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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = nombyte.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = nombyte.com, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```

Thanks again,

nomb

---

### Post by neouser99 on 2007-05-04
how do you have drupal setup? relay, smtp login?

IIRC you need to setup the relayhost option, which isn't setup in the cnf file. i don't remember what it needs to be set to, it's been a while, but [this]("http://www.google.com/search?q=postfix+relay") might help.

-neo

---

### Post by nomb on 2007-05-04
I couldn't find the location within drupal to change those settings.
Do you know where it is located?

---

### Post by neouser99 on 2007-05-05
not sure, sorry.

you might want to get the drupal forums a shot, they are probably going to have a much more informative group for this information.

-neo

---

