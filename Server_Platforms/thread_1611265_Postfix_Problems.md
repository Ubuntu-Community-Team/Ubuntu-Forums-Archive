---
title: "Postfix Problems"
date: 2010-11-01
forum: Server Platforms
---

### Post by trundlenut on 2010-11-01
I'm trying to configure postfix to forward emails via an exchange server.  All I want is for notifications from backuppc to be sent to my email address on the exchange server (which is on the same network

I have set postfix up as a satellite system but when I try to send emails I get the following error:

```
5.7.1 Client was not authenticated (in reply to MAIL FROM command))

```

The problem is I don't know at which end the problem lies, any ideas?

Below is my main.cf file:


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

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = XXX.XXX.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = XXX.XXX.local, localhost.XXX, localhost
relayhost = 192.168.0.1:25
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all

```

---

### Post by trundlenut on 2010-11-02
Bump

---

### Post by trundlenut on 2010-11-03
Another bump.

Anyone got an ideas?

---

### Post by Groodles on 2010-11-04
I guess exchange is refusing connection because it cannot determine that the sender is authorised.

[http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/](http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/)

That's a link to a tutorial for relaying via Gmail's SMTP.  Obviously the relay/port/connection type are GMail specific, but I would imagine that the authentication part would be similiar.

---

### Post by SeijiSensei on 2010-11-04
I find it helpful to try sending a message manually using telnet.  Let's suppose we're sending a message from postfix.example.com to exchange.example.com.  On postfix.example.com, use the following sequence.  Items in [brackets] are replies from the Exchange server.

```

$telnet exchange.example.com 25
[Exchange server sends its banner in reply]
EHLO postfix.example.com
[reply]
MAIL FROM: someone@example.com
[reply]
RCPT TO: someone@destination.com
[reply]
DATA
[reply]
Type in some bogus message.
.
[confirmation]

```

Make sure you enter that line with just a period to denote the end of message.  Also make sure you use the correct sender's email address to test authentication.

Hold down Ctrl and hit "]" to escape the session, then type quit.

---

### Post by trundlenut on 2010-11-04
Right, I get the same error when I try to send a message via telnet.  That seems to suggest that the problem is at the exchange end.

---

### Post by trundlenut on 2010-11-05
Right, I have solved it.  The issue was with the exchange server not allowing mail to be sent from the Ubuntu server.

---

