---
title: "[POSTFIX] User Unknown in Virtual Alias Table Error - Unable to Forward Mail to Gmail"
date: 2014-01-01
forum: Server Platforms
---

### Post by andy33 on 2014-01-01
I have installed PostFix on Ubuntu and am receiving an error forwarding mail to Gmail. This is my first time setting up PostFix, so I do appreciate your help. Below are the files that may be of importance:


**Mail.log**
```
Jan  1 16:52:06 magmoz postfix/anvil[15784]: statistics: max connection rate 1/60s for (smtp:74.125.82.45) at Jan  1 21:48:45
Jan  1 16:52:06 magmoz postfix/anvil[15784]: statistics: max connection count 1 for (smtp:74.125.82.45) at Jan  1 21:48:45
Jan  1 16:52:06 magmoz postfix/anvil[15784]: statistics: max cache size 1 at Jan  1 21:48:45
Jan  1 17:22:29 magmoz postfix/smtpd[15995]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jan  1 17:22:29 magmoz postfix/smtpd[15995]: connect from mail-wi0-f169.google.com[209.85.212.169]
Jan  1 17:22:30 magmoz postfix/smtpd[15995]: 385AC20078: client=mail-wi0-f169.google.com[209.85.212.169]
Jan  1 17:22:30 magmoz postfix/cleanup[15999]: 385AC20078: message-id=<CAP_6=3X88gdef0GvNVLD=Mg0yqDkiVb5FTp3QR0WDyU+uFBmFw@mail.gmail.com>
Jan  1 17:22:30 magmoz postfix/qmgr[15633]: 385AC20078: from=<andyfang1998@gmail.com>, size=2428, nrcpt=1 (queue active)
Jan  1 17:22:30 magmoz postfix/error[16000]: 385AC20078: to=<Moz@magmoz.com>, relay=none, delay=0.27, delays=0.26/0/0/0.01, dsn=5.0.0, status=bounced (User unknown in virtual alias table)
Jan  1 17:22:30 magmoz postfix/cleanup[15999]: 65CB92007E: message-id=<20140101222230.65CB92007E@magmoz.com>
Jan  1 17:22:30 magmoz postfix/qmgr[15633]: 65CB92007E: from=<>, size=4160, nrcpt=1 (queue active)
Jan  1 17:22:30 magmoz postfix/bounce[16001]: 385AC20078: sender non-delivery notification: 65CB92007E
Jan  1 17:22:30 magmoz postfix/qmgr[15633]: 385AC20078: removed
Jan  1 17:22:30 magmoz postfix/smtpd[15995]: disconnect from mail-wi0-f169.google.com[209.85.212.169]
Jan  1 17:22:31 magmoz postfix/smtp[16003]: 65CB92007E: to=<andyfang1998@gmail.com>, relay=gmail-smtp-in.l.google.com[173.194.74.27]:25, delay=1.2, delays=0/0.01/0.5/0.68, dsn=2.0.0, status=sent (250 2.0.0 OK 1388614951 l5si833481qaf.133 - gsmtp)
Jan  1 17:22:31 magmoz postfix/qmgr[15633]: 65CB92007E: removed
Jan  1 17:25:50 magmoz postfix/anvil[15997]: statistics: max connection rate 1/60s for (smtp:209.85.212.169) at Jan  1 22:22:29
Jan  1 17:25:50 magmoz postfix/anvil[15997]: statistics: max connection count 1 for (smtp:209.85.212.169) at Jan  1 22:22:29
Jan  1 17:25:50 magmoz postfix/anvil[15997]: statistics: max cache size 1 at Jan  1 22:22:29

```


**Test Email from Gmail to Server(error received from server)**
```

 
This is the mail system at host magmoz.com.
 
I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.
 
For further assistance, please send mail to postmaster.
 
If you do so, please include this problem report. You can
delete your own text from the attached returned message.
 
                   The mail system
 
<Moz@magmoz.com>: User unknown in virtual alias table
 
Final-Recipient: rfc822; Moz@magmoz.com
Original-Recipient: rfc822;moz@magmoz.com
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; User unknown in virtual alias table
```


**main.cf**
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


myhostname = magmoz.com
virtual_alias_maps = hash:/etc/postfix/virtual
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_domains = magmoz.com
virtual_alias_maps = hash:/etc/postfix/virtual

```


How would I fix the error so I can properly forward mail? I appreciate your time put into helping me setup PostFix.

---

