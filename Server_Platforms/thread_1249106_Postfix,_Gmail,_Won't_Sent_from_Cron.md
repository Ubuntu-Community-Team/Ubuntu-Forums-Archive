---
title: "Postfix, Gmail, Won't Sent from Cron"
date: 2009-08-24
forum: Server Platforms
---

### Post by TaBaScO77 on 2009-08-24
I configured the following successfully for sending mail through Gmail's SMTP using this article.
[http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/](http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/)

My problem is that it works perfectly when I sent mail via mailx or sendmail, but it fails when I try to add it to cron using the root account.  This cron job needs to run from root's cron, and not an individual user account.

My system's host name is "ubuntu" on a private network.

Here is an example of the delivery failure I receive:
> This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

     root@ubuntu

Technical details of permanent failure: 
DNS Error: Domain name not found

   ----- Original message -----



Here is a copy of my main.cf from /etc/postfix:

```
root@Ubuntu:/etc/postfix# cat main.cf
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

myhostname = Ubuntu
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $HOSTNAME, localhost.localdomain, , localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
## TLS Settings
#
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
#
## SASL Settings
# This is going in to THIS server
smtpd_sasl_auth_enable = no
# We need this
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtpd_sasl_local_domain = $myhostname
smtp_sasl_security_options = noanonymous
#smtp_sasl_security_options =
smtp_sasl_tls_security_options = noanonymous
smtpd_sasl_application_name = smtpd
##
relayhost = [smtp.gmail.com]:587
transport_maps = hash:/etc/postfix/transport

```

```
root@Ubuntu:/etc/postfix# cat /etc/aliases
# See man 5 aliases for format
postmaster:   root
root: xxxxxxxxxxxxx@gmail.com

```

By using mailx I was finally able to get it start emailing me from cron, but it still sends an additional failure report email when it tries to send an email to root@ubuntu, which I don't want it to do:
mailx -s "Home Server (Ubuntu) Rsync Completed" [email]xxxxxxxxx@gmail.com[/email] < emailreport.tmp

I'm sure this is probably something simple, as I set this up it in the past with no problems.  I'm just not sure what I'm overlooking.  Any help would be appreciated.

---

### Post by flabdablet on 2009-08-25
Can't help you with postfix, but if all you need is a simple local non-SSL proxy for the Gmail SMTP server, here's how I did it:

[http://ubuntuforums.org/showthread.php?t=918335](http://ubuntuforums.org/showthread.php?t=918335)

---

