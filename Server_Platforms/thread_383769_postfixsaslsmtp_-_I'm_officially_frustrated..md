---
title: "postfix/sasl/smtp - I'm officially frustrated."
date: 2007-03-13
forum: Server Platforms
---

### Post by nucklebone on 2007-03-13
I have installed postfix and sasl support as prescribed in this tutorial:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5)
After following the instructions VERY carefully (twice) I get ~close~ to a working postfix.

In a nutshell, I cannot relay any messages to or from the server. Local traffic works fine, however. Basically, this is my setup:

UBUNTU MACHINE - located in my house that runs apache/postfix...

LAPTOP - located with me wherever I go.

I want to (using my laptop not located in my home):
1. Log into my UBUNTU MACHINE with my favorite MTU to check incoming emails.

2. While I'm on the road, use the UBUNTU MACHINE'S SMTP server to send mail.

Using this setup, when someone tries to email me, their email bounces back and they get this error:

[email]ME@MYDOMAIN.com[/email]
SMTP error from remote mail server after RCPT TO:<ME@MYDOMAIIN.com>:
host mail.MYDOMAIN.com [xxx.xxx.xxx.xxx]: 554 5.7.1 <ME@MYDOMAIN.com>:
Relay access denied

If I try to send an email (on my laptop, not from the UBUNTU MACHINE) using the UBUNTU MACHINE's smtp server, I am prompted for my password, my password fails repeatedly until I get this error:

The message could not be sent because connecting to
SMTP server mail.MYDOMAIN.com failed. The server
may be unavailable or is refusing SMTP connections.
Please verify that your SMTP server setting is correct and
try again, or else contact your network administrator.

Here is my main.cf file with my personal info obscured for security reasons.
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = mail.MYDOMAINNAME.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.MYDOMAINNAME.com, ubuntubox, localhost.localdomain, localhost
relayhost =
mynetworks_style = class
# mynetworks = 127.0.0.0/8, xxx.xxx.xxx.xxx/24, xxx.xxx.xxx.xxx/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes         
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
```

Any help is GREATLY appreciated.

---

### Post by Mr. C. on 2007-03-13
Reject relay access denied means that postfix is not the final destination for the domain MYDOMAIN.com.  You need to set mydomain in main.cf.  The default is myhostname, and mail.MYDOMAIN.com does not match MYDOMAIN.com.

# The mydomain parameter specifies the local internet domain name.
# The default is to use $myhostname minus the first component.
# $mydomain is used as a default value for many other configuration
# parameters.
#
mydomain = MYDOMAIN.com

MrC

---

### Post by nucklebone on 2007-03-13
Mr. C,
i just tried these two parameters and still the same problem:

using $myhostname
```
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = mail.MYDOMAIN.com
mydomain = $myhostname
alias_maps = hash:/etc/aliases
```

using the actual hostname
```

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = mail.MYHOSTNAME.com
mydomain = MYHOSTNAME.com
alias_maps = hash:/etc/aliases
```

is that what you meant?

very sorry to be such a noob. i'm mildly dangerous with a terminal and an ssh connection.

thanks.

---

### Post by Mr. C. on 2007-03-13
... and mydestination 
```

mydestination (default: $myhostname, localhost.$mydomain, localhost)
       The list of domains that are delivered via  the  $local_transport  mail
       delivery  transport.  By  default this is the Postfix local(8) delivery
```

MrC

---

### Post by nucklebone on 2007-03-13
no dice. here's what that portion of my .cf file looks like now:

```
myhostname = mail.MYDOMAIN.com
mydomain = $myhostname
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, ubuntubox, localhost.$mydomain, localhost
```

---

### Post by Mr. C. on 2007-03-13
No, you're still missing the point.

Postfix will deliver local mail to only those destinations listed in mydestination.  You do not have "mydomain.com" there.  You do have "mail.mydomain.com", but your email was attempting to deliver to [email]me@mydomain.com[/email] .

mydomain = $myhostname  gets expanded to mydomain = mail.mydomain.com,  which is incorrect for mydomain.com.  You want mydomain to be:

mydomain = mydomain.com

mail.mydomain.com does not equal mydomain.com


MrC

---

### Post by MJN on 2007-03-13
Once $mydomain is defined (to be mydomain.com as Mr C says) it also needs adding to mydestination i.e. [B]mydestination = $myhostname, _$mydomain_, ubuntubox, localhost.$mydomain, localhost

[/B]Mathew

---

### Post by nucklebone on 2007-03-13
I am so very sorry for my lack of understanding. How painful it must be to have to explain something obviously simple to a person who wasn't getting it, BUT I FINALLY GOT IT. I see now.

So that solves half of my problem (the most important half). I can now receive mail at that address from outside the local host.

Now I just need to get SMTP working and this is a complete web/email server (at least for my needs).

Here again is my main.cf file as it is now:


```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
myhostname = XXXXXXXXXX.com
mydomain = $myhostname
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, $mydomain, ubuntubox, localhost.$mydomain, localhost
relayhost =
mynetworks_style = class
# mynetworks = 127.0.0.0/8, 67.113.19.174/24, 67.113.19.170/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all                 
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_d$
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
```

Thanks again for helping me get this far.

---

### Post by Mr. C. on 2007-03-13
Sweet!

Enjoy the server,
MrC

---

