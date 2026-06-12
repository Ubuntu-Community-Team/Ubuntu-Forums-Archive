---
title: "Postfix null client - error use postfix sendmail command"
date: 2011-05-06
forum: Server Platforms
---

### Post by alexander198728 on 2011-05-06
Hi all I am pretty new to Ubuntu server but while setting it up I have gotten to know my way around the OS.

Currently installation details:

Ubuntu 10.04 (I'm sure its 64 bit)<-VPS 
Postfix
php5
mysql
apache2 
use clamav and ufw for security

All of the above are the latest versions.

My web server is configured as a null client (mail). It relays all email needed to be sent to a remote mail server. My website uses the php Mail() function to pass mails to sendmail and then relayed to the mail server. I had everything working but then yesterday things went wrong but I did not make any changes to the server config in fact I did not even log into the server backend for the past week or so. 

This is the error when I check the mail.log:

postfix [6667]: error: to submit mail, use the Postfix sendmail command
postfix [6667]: fatal: the postfix command is reserved for the superuser

I'm not sure what happened. I have checked the php.ini file and the sendmail_path is still /usr/sbin/sendmail -t -i

I have checked the main.cf file and things look normal there:

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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = $mydomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = localhost, localhost.localdomain, localhost
relayhost = $remoteserverip
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = has:/etc/postfix/sasl_passwd
smtp_sasl_security_options = 
```
 
I have also tried reinstalling postfix: apt-get purge postfix and then apt-get install postfix
It gives me the same error. Funny thing is that in the mail.log I did see some mails being sent that wasn't part of my domain, and was being sent to some random email.

Anyone have any ideas about what is happening here?

---

