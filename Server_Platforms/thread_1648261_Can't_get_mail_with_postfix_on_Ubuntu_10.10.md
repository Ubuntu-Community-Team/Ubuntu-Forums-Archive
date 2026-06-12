---
title: "Can't get mail with postfix on Ubuntu 10.10"
date: 2010-12-18
forum: Server Platforms
---

### Post by mutercim on 2010-12-18
Hi everybody, 

I am trying to install a mail server (postfix). I followed the instructions (up until SMTP, I do not want that) on ubuntu pages, without any result. I can send mail, but I can't get any. 


My postconf: 

```

cenkhan@baskent:~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = 
mailbox_size_limit = 0
mydestination = mail.ihtisas.biz, baskent, localhost.ihtisas.biz, localhost, ihtisas.biz
myhostname = mail.ihtisas.biz
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.2.3/25
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_path = private/auth-client
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

```
I have made my MX configuration too. I assume it is right: 
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**Current Records:**[/SIZE][/FONT] [IMG]http://www.everydns.com/images/spacer.gif[/IMG]         [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**Host**[/SIZE][/FONT][/CENTER]
          [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**Type**[/SIZE][/FONT][/CENTER]
          [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**Value**[/SIZE][/FONT][/CENTER]
          [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**MX**[/SIZE][/FONT][/CENTER]
          [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**TTL**[/SIZE][/FONT][/CENTER]
          [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**Delete**[/SIZE][/FONT][/CENTER]
          [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]*.ihtisas.biz[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]A[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]78.188.217.93[/SIZE][/FONT][/CENTER]
   
  [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]3600[/SIZE][/FONT][/CENTER]
       [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][[delete]("http://www.everydns.com/dns.php?action=deleteRec&rid=7571032&domain=aWh0aXNhcy5iaXo=&did=1237793")][/SIZE][/FONT][/CENTER]
       [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]ihtisas.biz[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]A[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]78.188.217.93[/SIZE][/FONT][/CENTER]
   
  [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]3600[/SIZE][/FONT][/CENTER]
       [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][[delete]("http://www.everydns.com/dns.php?action=deleteRec&rid=7430846&domain=aWh0aXNhcy5iaXo=&did=1237793")][/SIZE][/FONT][/CENTER]
       [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]ihtisas.biz[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]MX[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]mail.ihtisas.biz[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]0[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]3600[/SIZE][/FONT][/CENTER]
       [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][[delete]("http://www.everydns.com/dns.php?action=deleteRec&rid=7569386&domain=aWh0aXNhcy5iaXo=&did=1237793")][/SIZE][/FONT][/CENTER]
       [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]www.ihtisas.biz[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]CNAME[/SIZE][/FONT][/CENTER]
   [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]ihtisas.biz[/SIZE][/FONT][/CENTER]
   
  [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]3600[/SIZE][/FONT][/CENTER]
       [CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][[delete]("http://www.everydns.com/dns.php?action=deleteRec&rid=7179865&domain=aWh0aXNhcy5iaXo=&did=1237793")][/SIZE][/FONT][/CENTER]

Also, I did not define any mail accounts like: [EMAIL="info@ihtisas.biz"]info@ihtisas.biz[/EMAIL]. Do I need to? May this be the reason why I cannot get a mail?

Thanks for help!!

---

### Post by Calimo on 2010-12-19
Hi,
There are thousands of possible issues here. You won't get anywhere if you don't look at your logs in /var/log. Your log are one of the most useful part of any system, and the most useful when it comes to debugging.

/var/log/mail.log
/var/log/mail.err
/var/log/mail.warn
/var/log/mail.info

mail.log stores everything and is the most useful here. Use the command```
tail -f /var/log/mail.log
```then send an email and see what error you get (even if you don't get a message, it's already an information!)

PS: you don't need specific accounts in postfix. I use dovecot with pam, so that any user of the system can get mail without a specific postfix account. It may or may not be what you need. If you expect several users to get mail on the system it's probably easier to setup the accounts in postfix.

---

### Post by mutercim on 2010-12-20
Here's my mail.log: 
```

cenkhan@baskent:~$ tail -f /var/log/mail.log
Dec 20 09:29:15 baskent postfix/smtpd[16464]: fatal: non-null host address bits in "192.168.2.3/25", perhaps you should use "192.168.2.0/25" instead
Dec 20 09:29:16 baskent postfix/master[8563]: warning: process /usr/lib/postfix/smtpd pid 16464 exit status 1
Dec 20 09:29:16 baskent postfix/master[8563]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 20 09:34:06 baskent postfix/qmgr[8566]: 9E627A5882: from=<cenkhan@ihtisas.biz>, size=711, nrcpt=1 (queue active)
Dec 20 09:34:27 baskent postfix/smtp[16932]: connect to gmail-smtp-in.l.google.com[74.125.39.27]:25: Connection timed out
Dec 20 09:34:48 baskent postfix/smtp[16932]: connect to alt1.gmail-smtp-in.l.google.com[74.125.127.27]:25: Connection timed out
Dec 20 09:34:48 baskent postfix/smtp[16932]: connect to alt2.gmail-smtp-in.l.google.com[74.125.67.27]:25: No route to host
Dec 20 09:34:48 baskent postfix/smtp[16932]: connect to alt3.gmail-smtp-in.l.google.com[74.125.47.27]:25: No route to host
Dec 20 09:34:48 baskent postfix/smtp[16932]: connect to alt4.gmail-smtp-in.l.google.com[209.85.229.27]:25: No route to host
Dec 20 09:34:48 baskent postfix/smtp[16932]: 9E627A5882: to=<cenkhanugur@gmail.com>, relay=none, delay=145612, delays=145570/0.02/42/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[209.85.229.27]:25: No route to host)

```

My internal ip is: 192.168.2.3. So I don't understand why it wants me to change that.

When I send mails to my account, I get late not delivered replies from gmail. Given below:

```

Delivery to the following recipient has been delayed: 
      cenkhan@ihtisas.biz
Message will be retried for 2 more day(s)

Technical details of temporary failure: 
The recipient server did not accept our requests to connect. Learn more at: http://mail.google.com/support/bin/answer.py?answer=7720 [mail.ihtisas.biz. (0): Connection dropped]


```

That's it. This mail message is somewhat old, because it comes back about a day after I try sending, I don't get an immediate failure reply. Since then, I may have made additional configurations, corrected MX problem etc. 

Thanks for reply!!

---

### Post by SeijiSensei on 2010-12-20
> **mutercim said:**
> ```

cenkhan@baskent:~$ tail -f /var/log/mail.log
Dec 20 09:29:15 baskent postfix/smtpd[16464]: fatal: non-null host address bits in "192.168.2.3/25", perhaps you should use "192.168.2.0/25" instead
```

my_networks expects a network address, not a host address.  Entries in this directive tell Postfix which networks to accept mail from.  Try using 192.168.2.0/24 instead.

> ```
Dec 20 09:34:27 baskent postfix/smtp[16932]: connect to gmail-smtp-in.l.google.com[74.125.39.27]:25: Connection timed out
Dec 20 09:34:48 baskent postfix/smtp[16932]: connect to alt1.gmail-smtp-in.l.google.com[74.125.127.27]:25: Connection timed out
```

If you have a residential Internet connection, your provider is likely blocking outbound connnections on the SMTP port, port 25.

---

### Post by furlabs on 2010-12-25
Try this command:
```
telnet gmail-smtp-in.l.google.com 25
```
If you get connection refused, your ISP is probably blocking port 25. However, they should have provided you with an SMTP server to use for sending mail. You will have to send through this by setting it as your relayhost.

---

