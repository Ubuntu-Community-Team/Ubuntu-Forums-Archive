---
title: "Postfix - error sending emails to some domains"
date: 2011-09-12
forum: Server Platforms
---

### Post by f.pirani on 2011-09-12
Hello everyone,

I have a java web application that uses JavaMail to send messages with attached documents (spreadsheets). On the server (Ubuntu 10.4 64-bit) I installed postfix to send email. The server has a static address and I connect to it via ssh. Apparently I thought I did everything right, because cron and the web application are able to send emails to my address. Looking inside my application server's log, I realized that for some e-mail (or better, domains) I get this error message:

com.sun.mail.smtp.SMTPAddressFailedException: 553 sorry, That domain is not in my list of allowed rcpthosts (# 5.5.3 - chkuser).

I installed postfix and I've only done the basic configuration, bypassing the SMTP authentication.

This is the contents of the main.cf file:

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

myhostname = Ubuntu-1004-lucid-64-minimal
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = Ubuntu-1004-lucid-64-minimal, localhost.localdomain, , localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
myorigin = /etc/mailname
~
```
The server has a static IP, saying A, and a domain server.mydomain.com. I test
the web app and it works sending mail to [EMAIL="myrec@differentdomain.com"]myrec@differentdomain.com[/EMAIL] (external). 
For other domains, it doesn't work.
it seems to be only a question of which recipients are allowed to receive mail.

The files: /var/log/mail.log, /var/log/mail.log.1 and /var/log/mmessages are empty.

how do i allow to send mails to all domains? do i miss something in config process?

---

### Post by hawkmage on 2011-09-12
I assume that your server is attempting to send the mail directly to the recipients domain and that you are not using an SMTP relay.  

IF that is the case you are running into the situation that the SMTP server for the domain you are trying to send to is not allowing your server to deliver/relay messages through it.  

THis can happen for a couple of reasons.  The first is that the SMTP server for the domain you are trying to send to uses a whitelist of servers/domains it will accept mail from .  The second it that it is using a blacklist to reject connections and your domain is on that list.  The third is that the SMTP relay requires authentication to be able to relay.  

This is why I generally use either the SMTP relay of the ISP that my domain is hosted on or a well known relay SMTP service.

---

