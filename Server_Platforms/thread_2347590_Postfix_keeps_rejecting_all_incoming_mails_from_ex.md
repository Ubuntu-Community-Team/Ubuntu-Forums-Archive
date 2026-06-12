---
title: "Postfix keeps rejecting all incoming mails from external networks"
date: 2016-12-27
forum: Server Platforms
---

### Post by fallex on 2016-12-27
Basically, I can forward mails to internet but somehow postfix keeps denying all emails from the internet. I don't think ISP is blocking my server because I can send and receive email on both internal and external networks when using Microsoft Exchange Server. I check /var/log/mail.log, it always rejects email, I checked recipient_restrictions in master.cf and main.cf, they seem to be fine. I disabled some restrictions in both files, but it is still not working. I need some expert to solve this question..it seems like a very hard question to me..
Rejected message from /var/log/mail.log:
```
 postfix/smtpd[6032]: NOQUEUE: reject: RCPT from [mail-wj0-f176.google.com]("http://mail-wj0-f176.google.com/")[IP]
```

My main.cf:

```

smtpd_banner = $myhostname ESMTP $mail_name
biff = no


append_dot_mydomain = no
readme_directory = no


relay_domains = example.ca


smtpd_sasl_type = dovecot


smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
smtpd_sasl_authenticated_header = yes
 


smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


smtpd_use_tls = yes
smtpd_enforce_tls = no


smtp_use_tls = yes
smtp_enforce_tls = no


smtpd_tls_security_level = may


smtp_tls_security_level = may


 
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s


smtp_helo_timeout = 60s


smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12


smtpd_helo_restrictions = permit_mynetworks, permit


smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks


smtpd_client_restrictions = 


smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, inet:127.0.0.1:10023, permit
smtpd_data_restrictions = 




smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, permit
 
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes


myhostname = mail.example.ca
myorigin = /etc/hostname


mydestination = localhost, mail.example.ca, example.ca


mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
 


virtual_mailbox_base = /var/vmail


virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf, mysql:/etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf


virtual_uid_maps = static:150


virtual_gid_maps = static:8


virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf, mysql:/etc/postfix/mysql_virtual_alias_domainaliases_maps.cf


virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
 
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
content_filter = amavis:[127.0.0.1]:10024
header_checks = regexp:/etc/postfix/header_checks
enable_original_recipient = no

```

My master.cf:
```


smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
 
# SMTP with TLS on port 587.
submission inet n       -       -       -       -       smtpd
  -o syslog_name=postfix/submission
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_enforce_tls=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
  -o smtpd_sasl_tls_security_options=noanonymous
 
# SMTP over SSL on port 465.
smtps     inet  n       -       -       -       -       smtpd
  -o syslog_name=postfix/smtps
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
 
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
  -o content_filter=
  -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       n       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache


maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}


uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)


ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
 
amavis      unix    -       -       -       -       3       smtp
  -o smtp_data_done_timeout=1200
  -o smtp_send_xforward_command=yes
  -o disable_dns_lookups=yes
  -o max_use=20
127.0.0.1:10025 inet    n       -       -       -       -       smtpd
  -o content_filter=
  -o local_recipient_maps=
  -o relay_recipient_maps=
  -o smtpd_restriction_classes=
  -o smtpd_delay_reject=no
  -o smtpd_client_restrictions=permit_mynetworks,reject_unauth_destination
  -o smtpd_helo_restrictions=
  -o smtpd_sender_restrictions=
  -o smtpd_recipient_restrictions=permit_mynetworks,reject_unauth_destination
  -o smtpd_data_restrictions=reject_unauth_pipelining
  -o smtpd_end_of_data_restrictions=
  -o mynetworks=127.0.0.0/8
  -o smtpd_error_sleep_time=0
  -o smtpd_soft_error_limit=1001
  -o smtpd_hard_error_limit=1000
  -o smtpd_client_connection_count_limit=0
  -o smtpd_client_connection_rate_limit=0
  -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
 
dovecot      unix   -        n      n       -       -   pipe
  flags=DRhu user=vmail:mail argv=/usr/lib/dovecot/dovecot-lda -d $(recipient)

```
Please advise....Thanks...

---

### Post by SeijiSensei on 2016-12-27
Is the machine connected directly to the Internet, or is it behind a router?  If the latter, try adding the IP subnet address of the router to the mynetworks parameter like this:
```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 **192.168.1.0/24**
```
if your router and server have addresses like 192.168.1.x.

Next comment out the mynetworks_style parameter by putting a hash mark at the front of the line ("#").  The "host" setting for that parameter means that only the local machine is trusted.  Then restart postfix.

Read this to learn more about mynetworks and mynetworks_style: [http://www.postfix.org/postconf.5.html#mynetworks](http://www.postfix.org/postconf.5.html#mynetworks)

If you have not yet browsed this document, I strongly recommend doing so: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

If the machine is directly exposed to the Internet, and you wish to accept inbound mail from any remote server, use 
```
mynetworks = 0.0.0.0/0
```
Be ready to handle the avalanche of spam that will come your way the longer the server is online.

---

### Post by cariboo on 2016-12-27
Moved to server platforms.

---

### Post by fallex on 2016-12-27
It seems I have to add 0.0.0.0/0 to allow any networks. Now, it does not reject all recipients from the internet anymore. But I'm having another issue, please see below:

1. /var/log/mail.log

Dec 27 12:55:56 mail postfix/master[12946]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 27 12:55:56 mail amavis[11249]: (11249-03) (!)FWD from <example@gmail.com> -> <freddie@example.ca>, 451 4.5.0 From MTA()
during fwd-connect (Negative greeting:  at (eval 134) line 479.): id=11249-03
Dec 27 12:55:56 mail amavis[11249]: (11249-03) Blocked MTA-BLOCKED {TempFailedInbound}, [74.125.82.54]:37117 <example@gmail.com> -> <freddie@example.ca>, Queue-ID: 79B0F220672, Message-ID: <CAARXFsb_-3VxEOCJAskrwzxQVQ0L9ZX8rOxbqHB9e2yPufAq8g@mail.gmail.com>, mail_id: byi6OZkLOl2C, Hits: -0.1, size: 2002, dkim_sd=20161025:gmail.com, 2477 ms
Dec 27 12:55:56 mail postfix/smtp[13108]: 79B0F220672: to=<freddie@example.ca>, relay=127.0.0.1[127.0.0.1]:10024, delay=2.9, delays=0.36/0.02/0.01/2.5, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=11249-03 - Temporary MTA failure on relaying, From MTA() during fwd-connect (Negative greeting:  at (eval 134) line 479.): id=11249-03 (in reply to end of DATA command))
Dec 27 12:56:28 mail postfix/smtpd[13101]: connect from mail-wm0-f45.google.com[74.125.82.45]
Dec 27 12:56:29 mail postfix/smtpd[13101]: Anonymous TLS connection established from mail-wm0-f45.google.com[74.125.82.45]:
TLSv1.2 with cipher ECDHE-RSA-AES128-GCM-SHA256 (128/128 bits)
Dec 27 12:56:29 mail postfix/smtpd[13101]: A1759220673: client=mail-wm0-f45.google.com[74.125.82.45]
Dec 27 12:56:30 mail postfix/cleanup[13106]: A1759220673: message-id=<CAARXFsZcqXUnjHfovFX-SWmQC-aEuamrpZJ1fVwhSeuZH4uMAw@mail.gmail.com>
Dec 27 12:56:30 mail postfix/qmgr[12950]: A1759220673: from=<example@gmail.com>, size=2011, nrcpt=1 (queue active)
Dec 27 12:56:30 mail postfix/smtpd[13101]: disconnect from mail-wm0-f45.google.com[74.125.82.45]

2. Netstat -nplt
I see amavis-new is running on port 10025, maybe 10023 and 10024 too

---

### Post by SeijiSensei on 2016-12-28
>  warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Searching for that error text on Google (always the best first step) suggests it indicates there is a misconfiguration in one of the .cf files.  I'm not a Postfix expert (I use sendmail) so I can't help much more.  I suggest you start another thread about this problem since your original question has been resolved.

---

