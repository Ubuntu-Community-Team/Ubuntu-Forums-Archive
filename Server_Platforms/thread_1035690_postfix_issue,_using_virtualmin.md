---
title: "postfix issue, using virtualmin"
date: 2009-01-10
forum: Server Platforms
---

### Post by anwoke8204 on 2009-01-10
Hi, when I try to send an email to my domain, I get the following:

Mail Delivery System <MAILER-DAEMON@srv1.rooksystems.com.rooksystems.com> to [email]xxxxxxxxxxx@gmail.com[/email] 2:59am
This is the mail system at host srv1.rooksystems.com.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                  The mail system

<astevens.rooksystems@srv1.rooksystems.com.rooksystems.com> (expanded from
   <astevens@rooksystems.com>): Host or domain name not found. Name service
   error for name=srv1.rooksystems.com.rooksystems.com type=A: Host not found

I the virtual domain and the virtual mailbox astevens and astevens.rooksystems do exist, I have them created.  anyone know why it is comming back as host or domain not found.  Also  my host name is shown twice, I have removed all duplicates I can find, but it still shows up twice, anyone know how I can remove that as well.


TIA

---

### Post by volkswagner on 2009-01-10
It may help if you post your  /etc/postfix/main.cf file.

---

### Post by anwoke8204 on 2009-01-10
here is my main.cf file

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

myhostname = srv1.rooksystems.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = srv1.rooksystems.com, localhost.rooksystems.com, rooksystems.com, realdealcars.org,  localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
virtual_alias_maps = hash:/etc/postfix/virtual
sender_bcc_maps = hash:/etc/postfix/bcc
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination

---

### Post by HidekiAI on 2009-02-21
My first guess is, try adding "mydomain = rooksystem.com" (since your myhostname = srv1.rooksystem.com").  As the error indicates:

> name=srv1.rooksystems.com.rooksystems.com

Your domain name looks like "rooksystems.com.rooksystems.com"

---

### Post by HidekiAI on 2009-02-21
> **anwoke8204 said:**
> 
                  The mail system

<astevens.rooksystems@srv1.rooksystems.com.rooksystems.com> (expanded from
   <astevens@rooksystems.com>): Host or domain name not found. Name service
   error for name=srv1.rooksystems.com.rooksystems.com type=A: Host not found

TIA

Most likely, you don't have **_mydomain _**set, that is why it resolves as "*.rooksystems.com.rooksystems.com".

---

