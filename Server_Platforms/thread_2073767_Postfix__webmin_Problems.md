---
title: "Postfix / webmin Problems"
date: 2012-10-20
forum: Server Platforms
---

### Post by AvengerX9 on 2012-10-20
I'm using Postfix now, but its probably not setup correctly yet :)

Its currently installed through Webmin and I've got lots of mails in the queue and when I try to flush I get this

> 
Forcing the attempted delivery of mail with the command /usr/sbin/postqueue -c /etc/postfix -f ..
postqueue: warning: unable to look up public/qmgr: No such file or directory
postqueue: fatal: Cannot flush mail queue - mail system is down


And its probably more stuff I need to check. I tried using this guide to do it

[http://postfixmail.com/blog/index.php/using-webmin-to-set-up-postfix/](http://postfixmail.com/blog/index.php/using-webmin-to-set-up-postfix/)

I also click the "start postfix" button, but everytime I return its stopped so its probably more problems with my setup. I would appreciate some help on this cause I need my site to be able to auto send mails

Thanks for looking :)

---

### Post by AvengerX9 on 2012-10-20
I went in and stopped the previous sendmail and started postfix and my last problem on my previous post seem fixed. I dont get any errors when I flush, but the mails don't seem to be sent anyway.

So I guess there is something with the alias setup and the general setup

Hope someone can help me :)

Thanks

---

### Post by AvengerX9 on 2012-10-20
In my error logs I got this
> 
postdrop: warning: unable to look up public/pickup: No such file or directory

---

### Post by AvengerX9 on 2012-10-20
in my postfix mail queue all outgoing mails are having Connection timed out OR Network is unreachable as status.


My server is not blacklisted afaik.

---

### Post by dalitso on 2012-10-20
please paste your /var/log/mail.log and /etc/postfix/main.cf

---

### Post by AvengerX9 on 2012-10-20
Postfix main.cf

> 

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
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

myhostname = mail.mydomain.com
mydomain = mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = xxx.xxx.xxx.xxx/8 [::ffff:xxx.xxx.xxx.xxx]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
smtpd_recipient_restrictions = reject_non_fqdn_recipient reject_unknown_recipient_domain permit_mynetworks permit_sasl_authenticated reject_unauth_destination reject_non_fqdn_hostname reject_invalid_hostname check_helo_access pcre:/etc/postfix/helo_checks check_sender_mx_access cidr:/etc/postfix/bogus_mx reject_rbl_client zen.spamhaus.org reject_rbl_client cbl.abuseat.org reject_rbl_client dnsbl-1.uceprotect.net permit


and the mail.log (last few lines)

> 
Oct 20 21:06:43 roger-G31T-M7 postfix/postfix-script[24436]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Oct 20 21:07:07 roger-G31T-M7 postfix/smtp[24329]: connect to alt2.gmail-smtp-in.l.google.com[74.125.142.26]:25: Connection timed out
Oct 20 21:07:07 roger-G31T-M7 postfix/smtp[24331]: connect to alt2.gmail-smtp-in.l.google.com[74.125.142.26]:25: Connection timed out
Oct 20 21:07:07 roger-G31T-M7 postfix/smtp[24329]: 25241144AB6: to=<roger.andersen@gmail.com>, relay=none, delay=1541, delays=1450/0.01/90/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[74.125.142.26]:25: Connection timed out)
Oct 20 21:07:07 roger-G31T-M7 postfix/smtp[24331]: 439ED144AC9: to=<roger.andersen@gmail.com>, relay=none, delay=1146, delays=1056/0.01/90/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[74.125.142.26]:25: Connection timed out)
Oct 20 21:07:30 roger-G31T-M7 postfix/postfix-script[24585]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Oct 20 21:10:37 roger-G31T-M7 postfix/qmgr[23663]: 2FD68144ACA: from=<www-data@truckstop24.no>, size=1034, nrcpt=1 (queue active)
Oct 20 21:11:07 roger-G31T-M7 postfix/smtp[24726]: connect to gmail-smtp-in.l.google.com[74.125.143.27]:25: Connection timed out
Oct 20 21:11:07 roger-G31T-M7 postfix/smtp[24726]: connect to gmail-smtp-in.l.google.com[2a00:1450:4010:c03::1a]:25: Network is unreachable
Oct 20 21:11:37 roger-G31T-M7 postfix/smtp[24726]: connect to alt1.gmail-smtp-in.l.google.com[173.194.64.26]:25: Connection timed out
Oct 20 21:11:37 roger-G31T-M7 postfix/smtp[24726]: connect to alt1.gmail-smtp-in.l.google.com[2607:f8b0:4003:c02::1b]:25: Network is unreachable
Oct 20 21:12:07 roger-G31T-M7 postfix/smtp[24726]: connect to alt2.gmail-smtp-in.l.google.com[74.125.133.26]:25: Connection timed out
Oct 20 21:12:07 roger-G31T-M7 postfix/smtp[24726]: 2FD68144ACA: to=<igolid@gmail.com>, relay=none, delay=1446, delays=1356/0.01/90/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[74.125.133.26]:25: Connection timed out)



---

### Post by dalitso on 2012-10-20
Are you using a static public IP address? Is this server getting internet at all?

What is in your /etc/hosts and /etc/hostname


Try adding a relay host, that is your ISP's smtp server in /etc/postfix/main.cf

```
relayhost = smtp.yourisp.com
```

---

### Post by AvengerX9 on 2012-10-20
its a static IP, the website is running now. I can try add the relay

---

### Post by AvengerX9 on 2012-10-20
It works when I added the relay :)

Thanks, thats awesome :) I've been messing with this stuff for like 10 hours now :D

---

### Post by dalitso on 2012-10-20
You are welcome. There is too much security with email servers. You cannot easily send mail without authentication. The other mail servers need comfirmation about your domain, your FQDN....things like that.

Some steps have to be arranged for your server to send mail on its own.

By default, your server was sending emails as a stand alone server, adding the relay host made it use your ISP's smtp, thereby giving you some authentication to pass mail through.

---

### Post by AvengerX9 on 2012-10-20
I see, well I'm happy it works and thanks again :)

---

### Post by dalitso on 2012-10-20
No problem, remember to mark this thread as "solved"

---

