---
title: "Postfix with Gmail"
date: 2015-11-04
forum: Server Platforms
---

### Post by seanmancini2010 on 2015-11-04
Hello All,

I am trying to setup postfix to relay through Gmail  I am running into a roadblock  I am getting authentication is required but I am not sure where I am going wrong Ive gone over the config 


Here is my config


# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
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
#smtp_sasl_auth_enable = yes

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

relayhost = [smtp.gmail.com]:587
smtp_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_tls_CAfile = /etc/ssl/certs/ca-bundle.crt
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous





Here is the error I am getting from the bounce back

This is the mail system at host debian.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

host smtp.gmail.com[173.194.205.109] said:
    530-5.5.1 Authentication Required. Learn more at 530 5.5.1
    [https://support.google.com/mail/answer/14257](https://support.google.com/mail/answer/14257) u200sm1213882qka.14 - gsmtp
    (in reply to MAIL FROM command)

Any help would be awsome ! 

Thank you

---

### Post by watfordjc on 2015-11-05
Did you follow the link in the rejection notice? [https://support.google.com/mail/answer/14257](https://support.google.com/mail/answer/14257)

---

### Post by Elizine on 2015-11-06
Please check for the steps in the link - [https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/](https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/)

---

