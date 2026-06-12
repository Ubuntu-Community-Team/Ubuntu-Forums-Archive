---
title: "Postfix Qmail style"
date: 2008-12-19
forum: Server Platforms
---

### Post by pauljones_666 on 2008-12-19
Hey,

I've got postfix running, and i've set it up to deliver in the Qmail style (one message = one file) Work. However i added the lines

```
local_recipient_maps =
luser_relay = allmail
```
to redirect my mail for other users to this account.

However now my Qmail style has not stopped working and it is appending all the message to /var/spool/mail/allmail

any ideas what i done wrong?
below is my main.cf
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

#home_mailbox = Maildir/
myhostname = workrealtime
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = something.com, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
local_recipient_maps =
luser_relay = allmail
```

Cheers,
Paul

---

### Post by MJN on 2008-12-19
You've got **home_mailbox = Maildir/** commented out

Uncomment this to set where to deliver the mail, relative to the users' home directory. The trailing slash implies maildir (i.e. Qmail style) format.

Mathew

---

### Post by pauljones_666 on 2008-12-19
Cheers, Mathew! 

Sorry its been a long day! many Thanks

---

