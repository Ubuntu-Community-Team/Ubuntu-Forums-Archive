---
title: "Postfix Sending Email Issue"
date: 2011-01-24
forum: Server Platforms
---

### Post by metallica1973 on 2011-01-24
I followed these instruction specifically down to the T:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto]("https://help.ubuntu.com/community/PostfixBasicSetupHowto")

I can receive email via thunderbird and these settings fine:

[PHP]server type: pop
server 10.0.0.112
user: test
no secure connection: no encryption
authenication type: password  [/PHP]

sending is where the issue is. when trying to send an email to root@10.0.0.112.

Thunderbird SMTP settings:

[PHP]server type: smtp
server: 10.0.0.112
no server authentication
no encryption  [/PHP]

and I get these error messages via /var/log/mail.log

I added "debug_peer_list = 10.0.0.111" for debugging

Here is my postfix.conf

[PHP]# Debian specific:  Specifying a file name will cause the first
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
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = SAINTdrive
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = root@localhost

#myorigin = /etc/mailname
mydestination = $myhostname localhost.$mydomain localhost
relayhost = $mydomain
mynetworks = 127.0.0.0/8, 10.7.0.0/24, 10.0.0.0/24
mynetworks_style = subnet 
mynetworks_style = host
mailbox_size_limit = 0
recipient_delimiter = +
strict_rfc821_envelopes = no
smtpd_reject_unlisted_sender = no
inet_interfaces = all
default_transport = error
relay_transport = error
home_mailbox = Maildir/
mailbox_command = 
debug_peer_list = 10.0.0.111 [/PHP]

here is a tail from /var/log/mail.log

[PHP]Jan 21 10:36:41 testbox postfix/smtpd[6125]: warning: Illegal address syntax from unknown[10.0.0.111] in MAIL command: <test@10.0.0.112>
Jan 21 10:36:41 testbox postfix/smtpd[6125]: disconnect from unknown[10.0.0.111]
extract_addr: in: <saint@10.0.0.112>, result: saint@10.0.0.112
Jan 21 11:54:50 testbox postfix/smtpd[7071]: > unknown[10.0.0.111]: 501 5.1.7 Bad sender address syntax
Jan 21 11:54:50 testbox postfix/smtpd[7071]: watchdog_pat: 0x21092b20
Jan 21 11:54:50 testbox postfix/smtpd[7071]: < unknown[10.0.0.111]: QUIT
Jan 21 11:54:50 testbox postfix/smtpd[7071]: > unknown[10.0.0.111]: 221 2.0.0 Bye
Jan 21 11:54:50 Stestbox postfix/smtpd[7071]: match_hostname: unknown ~? 127.0.0.0/8
Jan 21 11:54:50 testbox postfix/smtpd[7071]: match_hostaddr: 10.0.0.111 ~? 127.0.0.0/8
Jan 21 11:54:50 testbox postfix/smtpd[7071]: match_hostname: unknown ~? 10.7.0.0/24
Jan 21 11:54:50 testbox postfix/smtpd[7071]: match_hostaddr: 10.0.0.111 ~? 10.7.0.0/24
Jan 21 11:54:50 testbox postfix/smtpd[7071]: match_hostname: unknown ~? 10.0.0.0/24
Jan 21 11:54:50 testbox postfix/smtpd[7071]: match_hostaddr: 10.0.0.111 ~? 10.0.0.0/24
Jan 21 11:54:50 testbox postfix/smtpd[7071]: disconnect from unknown[10.0.0.111]  
[/PHP]

---

### Post by abix_adam_pl on 2011-01-31
> when trying to send an email to root@10.0.0.112.
Try root@[10.0.0.112] instead - should work.

adasiek@abix-test-server:~$ mailx root@[192.168.0.250]
Subject: TEST email
test
.
EOT


---------- LOG: ----------------
Jan 30 23:56:01 abix-test-server postfix/pickup[21202]: DB77E42FF0: uid=0 from=<root>
Jan 30 23:56:01 abix-test-server postfix/cleanup[21247]: DB77E42FF0: message-id=<20110130225601.DB77E42FF0@abix-demo.abix.info.pl>
Jan 30 23:56:02 abix-test-server postfix/qmgr[883]: DB77E42FF0: from=<root@abix-demo.abix.info.pl>, size=746, nrcpt=1 (queue active)
Jan 30 23:56:02 abix-test-server postfix/local[21249]: DB77E42FF0: to=<root@abix-demo.abix.info.pl>, orig_to=<root>, relay=local, delay=0.38, delays=0.3/0.01/0/0.07, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jan 30 23:56:02 abix-test-server postfix/qmgr[883]: DB77E42FF0: removed
Jan 31 12:16:27 abix-test-server postfix/pickup[23148]: EAA8F42A9B: uid=1000 from=<adasiek>
Jan 31 12:16:27 abix-test-server postfix/cleanup[23359]: EAA8F42A9B: message-id=<20110131111627.EAA8F42A9B@abix-demo.abix.info.pl>
Jan 31 12:16:28 abix-test-server postfix/qmgr[883]: EAA8F42A9B: from=<adasiek@abix-demo.abix.info.pl>, size=476, nrcpt=1 (queue active)
Jan 31 12:16:28 abix-test-server postfix/local[23361]: EAA8F42A9B: to=<root@[192.168.0.250]>, relay=local, delay=0.23, delays=0.14/0.01/0/0.08, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jan 31 12:16:28 abix-test-server postfix/qmgr[883]: EAA8F42A9B: removed
---------------------------------------------


Adam

---

