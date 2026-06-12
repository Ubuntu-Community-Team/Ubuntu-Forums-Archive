---
title: "Can't receive e-mail (Postfix, Courier-IMAP)"
date: 2007-08-04
forum: Server Platforms
---

### Post by yc2 on 2007-08-04
Hello,

I feel a little embarrassed to ask for this very basic help, but it seems I can't get it straight just using the guides on the Internet. I am a beginner with this subject :confused:.

I am trying to set up a very simple mailserver on Feisty. I have downloaded Postfix and it is now possible to send e-mail using Telnet, Evolution or via php-sctript.

However, I don't get the reception of e-mail to work. I have done the following:

1. Created my own ~/Maildir according to this recipe (from help.ubuntu.com):
```
maildirmake /etc/skel/Maildir
maildirmake /etc/skel/Maildir/.Drafts
maildirmake /etc/skel/Maildir/.Sent
maildirmake /etc/skel/Maildir/.Trash
maildirmake /etc/skel/Maildir/.Templates

cp -r /etc/skel/Maildir /home/username/
chown -R username:usergroup /home/myuser/Maildir
chmod -R 700 /home/username/Maildir
```

2. I have downloaded and installed Courier-IMAP. As I understand it works. Here are two excerpts from telnet:

1. Sending e-mail:
```
yngve@ubuntu:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 ubuntu ESMTP Postfix (Ubuntu)
helo localhost
250 ubuntu
mail from: info@localhost
250 2.1.0 Ok
rcpt to: yngve@localhost
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
Subject: Mail-test
Testing mail
.
250 2.0.0 Ok: queued as 33A2A28124
quit
221 2.0.0 Bye
Connection closed by foreign host.
yngve@ubuntu:~$ 
```

Contacting IMAP:
```
yngve@ubuntu:~$ telnet localhost imap
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT 

QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2005 Double Precision, Inc.  

See COPYING for distribution information.
imap login yngve <mypassword>
imap OK LOGIN Ok.
a01 capability
* CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA 

IDLE ACL ACL2=UNION
a01 OK CAPABILITY completed
a02 list "Mail" "*"
a02 OK LIST completed
a03 select inbox
* FLAGS (\Draft \Answered \Flagged \Deleted \Seen \Recent)
* OK [PERMANENTFLAGS (\* \Draft \Answered \Flagged \Deleted \Seen)] Limited
* 0 EXISTS
* 0 RECENT
* OK [UIDVALIDITY 1186140218] Ok
* OK [MYRIGHTS "acdilrsw"] ACL
a03 OK [READ-WRITE] Ok
a04 logout
* BYE Courier-IMAP server shutting down
a04 OK LOGOUT completed
Connection closed by foreign host.
yngve@ubuntu:~$ 
```

I had expected a longer listing when issuing the command "list"?? However, if I create an IMAP account via Evolution I can see the Maildir I have previously created.

Excerpt from /etc/postfix/main.cf:
```
myhostname = ubuntu
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localdomain, localhost, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
```
The imapd file is attached.

In any case, the mailboxes are empty. I have tried sending email to the following addresses:
username@127.0.0.1 (from same machine)   OR
username@192.168.1.101 (from local machine)   OR
username@123.123.123.123 (from my external account to routers current IP, forwarding port 25 to the computer in question)

The mail just doesn't arrive. Mailboxes are empty.

I have not fully understood the process. As I understand the IMAP server is used for making the Evolution MUA "look into" the Maildir. As I understand that part works in my system. The problem is that the emails are not put into the Maildir. I don't know what program is supposed to put the arriving e-mails into the Maildir (Postfix, IMAP or something I don't know of :confused:)?

Please, I am new to this, any advice is valuable :). Thanx.

---

### Post by Mr. C. on 2007-08-04
Show the output produced in the mail logs for a single message you send.

Show the output of postconf -n

MrC

---

### Post by yc2 on 2007-08-04
Still same problem: E-mails that arrive "disappear" and do not end up in the Maildir folders.

Thanks for taking interest :). I have done a little reading. If I understand correctly IMAP is only for reading the Maildir into f.ex. Evolution so I should not focus on IMAP now since nothing enters the Maildir boxes? (I have also tried procmail briefly without improvement but reset everything before sending mail as described below.)

I sent an e-mail, using Evolution, from yngve@localhost to yngve@localhost around 8:51:22. Logs are enclosed below. As you understand, my username is "yngve", computer name is "ubuntu".

postconf -n

```
yngve@ubuntu:/etc/postfix$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = localdomain, localhost, localhost.localdomain, localhost
myhostname = ubuntu
mynetworks = 127.0.0.0/8
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
yngve@ubuntu:/etc/postfix$ 
```

Here are the logs:

var/log/mail.err
is empty

var/log/mail.warn, var/log/messages
no entry for the time of sending



var/mail/username
```
From yngve@localhost  Sun Aug  5 08:51:22 2007
Return-Path: <yngve@localhost>
X-Original-To: yngve@localhost
Delivered-To: yngve@localhost
Received: from [127.0.0.1] (localhost [127.0.0.1])
	by ubuntu (Postfix) with ESMTP id 70ABB28122
	for <yngve@localhost>; Sun,  5 Aug 2007 08:51:22 +0800 (CST)
Subject: testing e-mail
From: Yngve =?ISO-8859-1?Q?L=F6=F6f?= <yngve@localhost>
To: yngve@localhost
Content-Type: text/plain
Date: Sun, 05 Aug 2007 08:51:21 +0800
Message-Id: <1186275081.6289.0.camel@ubuntu>
Mime-Version: 1.0
X-Mailer: Evolution 2.10.1 
Content-Transfer-Encoding: 7bit

testing e-mail, body

```

I seem to have some problem logging in from Evolution. (The root account has no Maildir, which maybe can explain that part?) However, I can see the boxes in Evolution and: When I look into the ~username/Maildir, the boxes are empty. Sending from Evolution to external account is OK.

var /log/mail.info
```
Aug  5 08:30:05 ubuntu authdaemond: modules="authpam", daemons=5
Aug  5 08:30:05 ubuntu authdaemond: Installing libauthpam
Aug  5 08:30:05 ubuntu authdaemond: Installation complete: authpam
Aug  5 08:30:14 ubuntu postfix/master[5017]: daemon started -- version 2.3.8, configuration /etc/postfix
Aug  5 08:37:01 ubuntu postfix/pickup[5041]: BFFD628120: uid=0 from=<root>
Aug  5 08:37:01 ubuntu postfix/cleanup[5824]: BFFD628120: message-id=<20070805003701.BFFD628120@ubuntu>
Aug  5 08:37:01 ubuntu postfix/qmgr[5042]: BFFD628120: from=<root@ubuntu>, size=438, nrcpt=1 (queue active)
Aug  5 08:37:04 ubuntu postfix/smtp[5826]: BFFD628120: to=<root@ubuntu>, orig_to=<root>, relay=none, delay=2.5, delays=0.26/0.04/2.2/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=ubuntu type=AAAA: Host not found)
Aug  5 08:37:04 ubuntu postfix/cleanup[5824]: 1CBDE28122: message-id=<20070805003704.1CBDE28122@ubuntu>
Aug  5 08:37:04 ubuntu postfix/qmgr[5042]: 1CBDE28122: from=<>, size=2199, nrcpt=1 (queue active)
Aug  5 08:37:04 ubuntu postfix/bounce[5829]: BFFD628120: sender non-delivery notification: 1CBDE28122
Aug  5 08:37:04 ubuntu postfix/qmgr[5042]: BFFD628120: removed
Aug  5 08:37:04 ubuntu postfix/smtp[5826]: 1CBDE28122: to=<root@ubuntu>, relay=none, delay=0.07, delays=0.02/0/0.05/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=ubuntu type=AAAA: Host not found)
Aug  5 08:37:04 ubuntu postfix/qmgr[5042]: 1CBDE28122: removed
Aug  5 08:45:58 ubuntu postfix/master[5017]: terminating on signal 15
Aug  5 08:45:58 ubuntu postfix/master[6148]: daemon started -- version 2.3.8, configuration /etc/postfix
Aug  5 08:50:14 ubuntu imapd: LOGIN FAILED, user=root, ip=[::ffff:127.0.0.1]
Aug  5 08:50:17 ubuntu imapd: LOGIN FAILED, user=yngve, ip=[::ffff:127.0.0.1]
Aug  5 08:50:23 ubuntu imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=59, sent=499
Aug  5 08:50:23 ubuntu imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=57, sent=499
Aug  5 08:51:22 ubuntu postfix/smtpd[6365]: connect from localhost[127.0.0.1]
Aug  5 08:51:22 ubuntu postfix/smtpd[6365]: 70ABB28122: client=localhost[127.0.0.1]
Aug  5 08:51:22 ubuntu postfix/cleanup[6370]: 70ABB28122: message-id=<1186275081.6289.0.camel@ubuntu>
Aug  5 08:51:22 ubuntu postfix/qmgr[6153]: 70ABB28122: from=<yngve@localhost>, size=483, nrcpt=1 (queue active)
Aug  5 08:51:22 ubuntu postfix/local[6371]: 70ABB28122: to=<yngve@localhost>, relay=local, delay=0.11, delays=0.05/0.03/0/0.02, dsn=2.0.0, status=sent (delivered to mailbox)
Aug  5 08:51:22 ubuntu postfix/qmgr[6153]: 70ABB28122: removed
Aug  5 08:51:22 ubuntu postfix/smtpd[6365]: disconnect from localhost[127.0.0.1]
Aug  5 08:51:55 ubuntu imapd: LOGIN FAILED, user=root, ip=[::ffff:127.0.0.1]
Aug  5 08:51:55 ubuntu imapd: LOGIN, user=yngve, ip=[::ffff:127.0.0.1], protocol=IMAP
Aug  5 08:52:02 ubuntu imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=59, sent=499

```

var/log/mail.log
```
Aug  5 08:30:05 ubuntu authdaemond: modules="authpam", daemons=5
Aug  5 08:30:05 ubuntu authdaemond: Installing libauthpam
Aug  5 08:30:05 ubuntu authdaemond: Installation complete: authpam
Aug  5 08:30:14 ubuntu postfix/master[5017]: daemon started -- version 2.3.8, configuration /etc/postfix
Aug  5 08:37:01 ubuntu postfix/pickup[5041]: BFFD628120: uid=0 from=<root>
Aug  5 08:37:01 ubuntu postfix/cleanup[5824]: BFFD628120: message-id=<20070805003701.BFFD628120@ubuntu>
Aug  5 08:37:01 ubuntu postfix/qmgr[5042]: BFFD628120: from=<root@ubuntu>, size=438, nrcpt=1 (queue active)
Aug  5 08:37:04 ubuntu postfix/smtp[5826]: BFFD628120: to=<root@ubuntu>, orig_to=<root>, relay=none, delay=2.5, delays=0.26/0.04/2.2/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=ubuntu type=AAAA: Host not found)
Aug  5 08:37:04 ubuntu postfix/cleanup[5824]: 1CBDE28122: message-id=<20070805003704.1CBDE28122@ubuntu>
Aug  5 08:37:04 ubuntu postfix/qmgr[5042]: 1CBDE28122: from=<>, size=2199, nrcpt=1 (queue active)
Aug  5 08:37:04 ubuntu postfix/bounce[5829]: BFFD628120: sender non-delivery notification: 1CBDE28122
Aug  5 08:37:04 ubuntu postfix/qmgr[5042]: BFFD628120: removed
Aug  5 08:37:04 ubuntu postfix/smtp[5826]: 1CBDE28122: to=<root@ubuntu>, relay=none, delay=0.07, delays=0.02/0/0.05/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=ubuntu type=AAAA: Host not found)
Aug  5 08:37:04 ubuntu postfix/qmgr[5042]: 1CBDE28122: removed
Aug  5 08:45:58 ubuntu postfix/master[5017]: terminating on signal 15
Aug  5 08:45:58 ubuntu postfix/master[6148]: daemon started -- version 2.3.8, configuration /etc/postfix
Aug  5 08:49:58 ubuntu imapd: Connection, ip=[::ffff:127.0.0.1]
Aug  5 08:49:58 ubuntu imapd: Connection, ip=[::ffff:127.0.0.1]
Aug  5 08:50:14 ubuntu imapd: LOGIN FAILED, user=root, ip=[::ffff:127.0.0.1]
Aug  5 08:50:17 ubuntu imapd: LOGIN FAILED, user=yngve, ip=[::ffff:127.0.0.1]
Aug  5 08:50:23 ubuntu imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=59, sent=499
Aug  5 08:50:23 ubuntu imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=57, sent=499
Aug  5 08:51:22 ubuntu postfix/smtpd[6365]: connect from localhost[127.0.0.1]
Aug  5 08:51:22 ubuntu postfix/smtpd[6365]: 70ABB28122: client=localhost[127.0.0.1]
Aug  5 08:51:22 ubuntu postfix/cleanup[6370]: 70ABB28122: message-id=<1186275081.6289.0.camel@ubuntu>
Aug  5 08:51:22 ubuntu postfix/qmgr[6153]: 70ABB28122: from=<yngve@localhost>, size=483, nrcpt=1 (queue active)
Aug  5 08:51:22 ubuntu postfix/local[6371]: 70ABB28122: to=<yngve@localhost>, relay=local, delay=0.11, delays=0.05/0.03/0/0.02, dsn=2.0.0, status=sent (delivered to mailbox)
Aug  5 08:51:22 ubuntu postfix/qmgr[6153]: 70ABB28122: removed
Aug  5 08:51:22 ubuntu postfix/smtpd[6365]: disconnect from localhost[127.0.0.1]
Aug  5 08:51:49 ubuntu imapd: Connection, ip=[::ffff:127.0.0.1]
Aug  5 08:51:49 ubuntu imapd: Connection, ip=[::ffff:127.0.0.1]
Aug  5 08:51:55 ubuntu imapd: LOGIN FAILED, user=root, ip=[::ffff:127.0.0.1]
Aug  5 08:51:55 ubuntu imapd: LOGIN, user=yngve, ip=[::ffff:127.0.0.1], protocol=IMAP
Aug  5 08:52:02 ubuntu imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=59, sent=499
```

Thanks :)

---

### Post by Mr. C. on 2007-08-04
Your mail logs show that your system is configured to send to mailbox files, not Maildirs:

Aug  5 08:51:22 ubuntu postfix/local[6371]: 70ABB28122: to=<yngve@localhost>, relay=local, delay=0.11, delays=0.05/0.03/0/0.02, dsn=2.0.0, status=sent (**delivered to mailbox**)

Set:

```
home_mailbox = Maildir/
```

in your main.cf file and restart postfix.  Maildirs will be created when mail is sent.

MrC

---

### Post by yc2 on 2007-08-05
> **Mr. C. said:**
> Your mail logs show that your system is configured to send to mailbox files, not Maildirs:

...

```
home_mailbox = Maildir/
```

...

MrC

Thank you Mr.C. :KS, you pinpointed the problem the e-mail now arrives !!

EDIT: I have removed a large part of this post. My thinking was wrong. I still have problems receiving e-mails from external machines. But not machines within the network, problems arise when sending from machines **outside** the router. The router is not yet assigned its own domain name and has to be addressed via its current (changing) IP. I don't know if it is possible to send e-mail to this network using its current IP, just for testing purposes?

Sorry and thanks again to Mr.C. for valuable help.

---

### Post by Mr. C. on 2007-08-05
Are you saying you want to use your server to send email whilst you are on the internet ?  If so, you want to ensure you have a secure connection.

Although your WAN IP may be changing because its dynamic, there is no reason why your mail server's IP needs to change.  I presume you have it NAT'd and its in private IP space.

If so, see my post #14 here:

[http://ubuntuforums.org/showthread.php?t=507926&highlight=mrc+tls+ssh&page=2](http://ubuntuforums.org/showthread.php?t=507926&highlight=mrc+tls+ssh&page=2)

MrC

---

### Post by yc2 on 2007-08-06
My system is pretty common (maybe my explanations sometimes make it sound different ;) ). My router is NAT, port 80 and 25 are forwarded to the machine that runs Postfix (and Apache).

Thanks to the help I just received here, Postfix can now send e-mails from user@localhost to user@localhost.

I am very new to servers so I may have misunderstood a lot. My intention is to send e-mail from an external account (like my Gmail account or any other account) to this server.

The Apache server can be reached via its (changing) IP number or via a domain name using Dynamic DNS. So, without deeper knowledge of the subject, I tried to do a similar thing sending e-mail: I sent two e-mails from Gmail to:
1. myuser@123.123.123.123  around 8:34
2. [email]myuser@mydomain.xx[/email]  around 8:35
Neither of the e-mails arrived in the maildir.

> **Mr. C. said:**
> 
Here are the two issues with running a mail server using a dynamic IP:
[LIST]
[*]Mail servers are likely to reject your outbound email
[*]Mail servers are likely to have difficulty reaching your domain's mail server
[/LIST]
MrC

I have already experienced the problem of outbound mail ending up in the spam-folder. Whether the second condition applies to my problem I don’t know. As I understand, the e-mails sent from Google have at least left traces in my Postfix server error log, please see below.

So the problem is this: E-mails sent from Gmail to my server don’t end up in the Maildir folder, they just don’t seem to arrive anywhere. Greatful for suggestions. The help I received last time was really valuable :)

Due to the risk of robots, I ran some editor substitute commands over this post, changing my user name to ygggg (sometimes also called “user” or “myuser”) and domain-name to ygggg.xy (sometimes “mydomain”), IP is changed to 123.123.123.123, the Google account I sent from will be [email]ygggg.looo@gmail.com[/email]

Attachments:
-----------------------------------------------------------------------------------------------------------------

Reply to G-mail regarding
E-mail from Gmail to myuser@123.123.123.123  around 8:34
```
Mail Delivery Subsystem <mailer-daemon@googlemail.com>  till mig 
 visa detaljer  08:34 (7 timmar sedan)  

This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    ygggg@123.123.123.123

Technical details of permanent failure:
PERM_FAILURE: SMTP Error (state 13): 501 5.1.3 Bad recipient address syntax

  ----- Original message -----

Received: by 10.100.31.2 with SMTP id e2mr2881177ane.1186360484197;
       Sun, 05 Aug 2007 17:34:44 -0700 (PDT)
Received: by 10.100.194.9 with HTTP; Sun, 5 Aug 2007 17:34:44 -0700 (PDT)
Message-ID: <5a69bf780708051734r5889858x42a6bae391b707a9@mail.gmail.com>
Date: Mon, 6 Aug 2007 08:34:44 +0800
From: "=?ISO-8859-1?Q?Ygggg_L=F6=F6f?=" <ygggg.looo@gmail.com>
To: ygggg@123.123.123.123
Subject: from google to IP
MIME-Version: 1.0
Content-Type: multipart/alternative;
       boundary="----=_Part_136142_24966869.1186360484176"

------=_Part_136142_24966869.1186360484176
Content-Type: text/plain; charset=ISO-8859-1
Content-Transfer-Encoding: 7bit
Content-Disposition: inline



------=_Part_136142_24966869.1186360484176
Content-Type: text/html; charset=ISO-8859-1
Content-Transfer-Encoding: 7bit

  ----- Message truncated -----
```
 

Reply to G-mail regarding
E-mail from Gmail to [email]myuser@mydomain.xx[/email]  around 8:35
```
Mail Delivery Subsystem <mailer-daemon@googlemail.com>  till mig 
 visa detaljer  08:35 (7 timmar sedan)  

This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    ygggg@ygggg.xy

Technical details of permanent failure:
PERM_FAILURE: SMTP Error (state 13): 554 5.7.1 <ygggg@ygggg.xy>: Relay access denied

  ----- Original message -----

Received: by 10.100.127.1 with SMTP id z1mr2864237anc.1186360528326;
       Sun, 05 Aug 2007 17:35:28 -0700 (PDT)
Received: by 10.100.194.9 with HTTP; Sun, 5 Aug 2007 17:35:27 -0700 (PDT)
Message-ID: <5a69bf780708051735k1d98ffdfue5ae7eda69d96358@mail.gmail.com>
Date: Mon, 6 Aug 2007 08:35:28 +0800
From: "=?ISO-8859-1?Q?Ygggg_L=F6=F6f?=" <ygggg.looo@gmail.com>
To: ygggg@ygggg.xy
Subject: =?ISO-8859-1?Q?fr=E5n_google_till_tv,_port_25_forward?=
MIME-Version: 1.0
Content-Type: multipart/alternative;
       boundary="----=_Part_136150_23214088.1186360528042"

------=_Part_136150_23214088.1186360528042
Content-Type: text/plain; charset=ISO-8859-1
Content-Transfer-Encoding: 7bit
Content-Disposition: inline



------=_Part_136150_23214088.1186360528042
Content-Type: text/html; charset=ISO-8859-1
Content-Transfer-Encoding: 7bit

  ----- Message truncated -----
```


iptables
```
ygggg@ubuntu:~$ sudo iptables --list
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ygggg@ubuntu:~$ 
```


mail.log
```
Aug  6 08:09:07 ubuntu postfix/master[5008]: daemon started -- version 2.3.8, configuration /etc/postfix
Aug  6 08:34:41 ubuntu postfix/smtpd[10719]: connect from wr-out-0506.google.com[64.233.184.235]
Aug  6 08:34:42 ubuntu postfix/smtpd[10719]: warning: Illegal address syntax from wr-out-0506.google.com[64.233.184.235] in RCPT command: <ygggg@123.123.123.123>
Aug  6 08:34:43 ubuntu postfix/smtpd[10719]: disconnect from wr-out-0506.google.com[64.233.184.235]
Aug  6 08:35:23 ubuntu postfix/smtpd[10719]: connect from wr-out-0506.google.com[64.233.184.227]
Aug  6 08:35:25 ubuntu postfix/smtpd[10719]: NOQUEUE: reject: RCPT from wr-out-0506.google.com[64.233.184.227]: 554 5.7.1 <ygggg@ygggg.xy>: Relay access denied; from=<ygggg.looo@gmail.com> to=<ygggg@ygggg.xy> proto=ESMTP helo=<wr-out-0506.google.com>
Aug  6 08:35:25 ubuntu postfix/smtpd[10719]: disconnect from wr-out-0506.google.com[64.233.184.227]
Aug  6 08:36:12 ubuntu imapd: Connection, ip=[::ffff:127.0.0.1]
Aug  6 08:36:14 ubuntu imapd: LOGIN, user=ygggg, ip=[::ffff:127.0.0.1], protocol=IMAP
Aug  6 08:36:51 ubuntu postfix/smtpd[10719]: connect from localhost[127.0.0.1]
Aug  6 08:36:51 ubuntu postfix/smtpd[10719]: 179F928692: client=localhost[127.0.0.1]
Aug  6 08:36:51 ubuntu postfix/cleanup[10837]: 179F928692: message-id=<1186360610.10754.0.camel@ubuntu>
Aug  6 08:36:51 ubuntu postfix/qmgr[5031]: 179F928692: from=<ygggg@localhost>, size=453, nrcpt=1 (queue active)
Aug  6 08:36:51 ubuntu postfix/local[10838]: 179F928692: to=<ygggg@localhost>, relay=local, delay=0.16, delays=0.12/0.02/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
Aug  6 08:36:51 ubuntu postfix/qmgr[5031]: 179F928692: removed
Aug  6 08:36:51 ubuntu postfix/smtpd[10719]: disconnect from localhost[127.0.0.1]
Aug  6 08:40:11 ubuntu postfix/anvil[10724]: statistics: max connection rate 1/60s for (smtp:64.233.184.235) at Aug  6 08:34:41
Aug  6 08:40:11 ubuntu postfix/anvil[10724]: statistics: max connection count 1 for (smtp:64.233.184.235) at Aug  6 08:34:41
Aug  6 08:40:11 ubuntu postfix/anvil[10724]: statistics: max cache size 2 at Aug  6 08:35:23
Aug  6 09:16:03 ubuntu postfix/smtpd[11634]: connect from an-out-0708.google.com[209.85.132.242]
Aug  6 09:16:05 ubuntu postfix/smtpd[11634]: NOQUEUE: reject: RCPT from an-out-0708.google.com[209.85.132.242]: 554 5.7.1 <ygggg@ygggg.xy>: Relay access denied; from=<ygggg.looo@gmail.com> to=<ygggg@ygggg.xy> proto=ESMTP helo=<an-out-0708.google.com>
Aug  6 09:16:05 ubuntu postfix/smtpd[11634]: disconnect from an-out-0708.google.com[209.85.132.242]
Aug  6 09:19:25 ubuntu postfix/anvil[11636]: statistics: max connection rate 1/60s for (smtp:209.85.132.242) at Aug  6 09:16:03
Aug  6 09:19:25 ubuntu postfix/anvil[11636]: statistics: max connection count 1 for (smtp:209.85.132.242) at Aug  6 09:16:03
Aug  6 09:19:25 ubuntu postfix/anvil[11636]: statistics: max cache size 1 at Aug  6 09:16:03
Aug  6 10:23:15 ubuntu imapd: DISCONNECTED, user=ygggg, ip=[::ffff:127.0.0.1], headers=239, body=530, rcvd=1495, sent=8873, time=6421
```

---

### Post by Mr. C. on 2007-08-06
> My system is pretty common (maybe my explanations sometimes make it sound different  )

Don't get stuck in the trap of believing that diagnosis of your system problems should be obvious to the outside world, and that there is a concept of "common" setup.  While there are "common" remedies, and "common" mistakes, there is no "common" system setup.  This line serves no purpose, and prevents you from actually describing the key details that are necessary, which have just become unveiled in your latest post.

If all you want to do is *retrieve* your email from gmail, you can retrieve it with fetchmail or procmail.  Postfix does not *retrieve* mail.

You can *forward* email from your gmail account to your home server, but that server will require a fully qualified domain name, and MX records, and an A record.  Since you have a dynamic IP, this can be a significant problem.

While you can attempt to *forward* your mail from gmail to yourname@IPofYourServer, your IP will be changing, so you will need to keep updating gmail's forwarding preferences  Forwarding email to a moving target is a very bad idea.  As I said earlier, running a mail server on a dynamic IP can be problematic.

The apache-can-do-it-so-postfix-should-be-able line of reasoning is also flawed.  Mail servers have different requirements than web servers.

You have to understand that mail servers lookup MX and/or A records for the server they need to send email to.  And the results get *cached* so, any change of IP during the lifetime of that DNS cache *will* cause mail to bounce and it can go into a black hole.

If you want to run an MX-based mail server (eg. on available on the Internet, where other servers direct your email for your domain to your server), get a static IP with a reputable ISP that allows such.

Always look at your log messages for the error.  Postfix *always* logs messages for every transaction it receives.  Here's the important one:

Aug  6 08:35:25 ubuntu postfix/smtpd[10719]: NOQUEUE: reject: RCPT from wr-out-0506.google.com[64.233.184.227]: 554 5.7.1 <ygggg@ygggg.xy>: Relay access denied; from=<ygggg.looo@gmail.com> to=<ygggg@ygggg.xy> proto=ESMTP helo=<wr-out-0506.google.com>

Google tried to send your server email with the recipient envelope of [email]ygggg@ygggg.xy[/email].  Your mail server does not believe that it is the final destination for email address [email]ygggg@ygggg.xy[/email].  Since you obfuscated the domain and email address, we can't know exactly what the cause is exactly.  Your **mydestination** parameter in main.cf does not list "ygggg.xy", so one assume that you haven't added your destination to **mydestination**, so postfix thinks it is being asked to relay that email elsewhere.

You have to add your domain name ygggg.xy to **mydestination**.

You can add your LAN IP addresses to **mynetworks**, so that your mail server knows that your LAN is trusted to send email.  But this doesn't help the gmail case.

MrC

FYI: 
Your attempt to hide from robots missed that you placed your gmail address in your last post.

---

### Post by MJN on 2007-08-07
*Edit: Having just spotted that the OP does not have a domain name, and perhaps has no intention of using one, then my post may be off the mark in that context. I'll leave it in anyway and suggest the OP proceeds by purchasing a domain name - they cost practically nothing and will eliminate many of the problems that Mr C has been alluding to.*
 
> **Mr. C. said:**
> You can *forward* email from your gmail account to your home server, but that server will require a fully qualified domain name, and MX records, and an A record. Since you have a dynamic IP, this is a significant problem.

 
Whilst not wishing to muddy the waters of your assistance I feel I must step in here before you put the guy off entirely! Having a dynamic IP is not a 'significant problem' by any stretch - loads of us have them and seem quite able to run a mail server without any problems whatsoever.
 
For the sake of the OP, dynamic DNS is your friend here - with a suitably low TTL (mine is 5 minutes) you should not be finding mail disappearing into black holes.
 
I know you know more than most about mail server operation Mr C but to say a dynamic IP is a significant problem is misrepresenting the truth I feel.
 
> The apache-can-do-it-so-postfix-should-be-able line of reasoning is also flawed. Mail servers have different requirements than web servers. You could not, for example, use apache with SSL, since SSL requires a static IP.
 
I'm not sure I follow this last bit - why does Apache require a static IP in order to use SSL? ([https://secure.newtonnet.co.uk](https://secure.newtonnet.co.uk), as an example, seems to work fine without one...?)
 
> You have to understand that mail servers lookup MX and/or A records for the server they need to send email to. And the results get *cached* so, any change of IP during the lifetime of that DNS cache *will* cause mail to bounce and it can go into a black hole.
 
So lower the TTL to work around this. During the 5 minutes (or whatever) it takes for the caches to expire mail should not be bouncing should it?
 
I don't wish to hijack the OP's plea for help but if he gives up on the basis of you telling him not to run on a dynamic IP (they may not be able to obtain/afford a static IP) then that would be a real shame and something worth butting in to prevent.
 
Mathew

---

### Post by yc2 on 2007-08-07
My heartfelt thanks to Mr. C. for his advice :KS. The e-mail sent from G-mail now arrives in my Maildir and is read by Evolution. I think the help I got shows a forum at its best; detailed analysis of the problem including  short- and long-term remedy :)

A summary of what I learnt in this thread on how to modify /etc/postfix/main.cf:
```
home_mailbox = Maildir/
mydestination = localdomain, localhost, localhost.localdomain, localhost, MYDOMAIN.XY
mynetworks = 127.0.0.0/8, 192.168.1.0/24
```
This is also a point where I personally think Ubuntu has great advantages over Windows. It is more difficult for a beginner to find his way through that comercialized jungle. Instead, using Ubuntu, "sudo apt-get install postfix" followed by good advice in a forum and the first steps towards a mail-server are taken.

I also deserve a kick in the butt. The main.cf is not Tibetan philosophy, it is short and clear. I now recall how I had a good, blank stare at the "mydestination" parameter not being able to put the pieces together.

Thanks for information on retrieving e-mail using fetchmail or procmail. Neither was I aware of the mail-forwarding possibility of G-mail. Will try that once I get a static IP. I will have to read up on what are MX-records and A-record.

Now it also works to connect another computer in my home network to the Postifx-server: Use Postfix to send e-mails from other computers in the network and also read my Maildir via IMAP over the LAN. (As I was adviced to do.)

Well, thanks again Mr. C. for very valuable support.

-----

Thank you MJN. I just read your post. If it is possible to run the server on a DynDNS line, I am naturally happy. The reason I still don't use static IP is probably mostly bad planning, I haven't yet checked out the possibilities and costs. I have a domain name connected to my router via DynDNS. The domain name is the address to where I just sent and received mail on the LAN-server I am just learning how to set up. (I also tried to send straight to user@123.123.123.123 - current IP, but that seems to fail.)

EDIT: I see now that I wrote unclearly. When I started installing the server I had not activated the DynDNS service. However, now it is activated and a domainname is connected to the server. Sorry.

---

### Post by Mr. C. on 2007-08-07
The issue I was referring to regarding dynamic IP addresses is one of DNS-based blackhole lists.  Because of the scourge of spam by infected residential and dynamic IP ranges, more and more (large and small) mail servers are using well-respected DNS-based black hole lists (eg. zen.spamhaus.org), which place entire residential and dynamic IP address blocks on their blacklists.  This isn't a matter of opinion - the data is there.

Also becoming more prevalent is the rejection of relay from mail servers which do not have matching forward and reverse DNS records.  Most residential ISP do not delegate authority for the reverse records, rejects.

In fact, I've seen more servers rejecting messages from mail servers that use popular DNS servers.

Mail servers configured to use these anti-spam strategies have become the norm, not the exception.

Some servers silently discard delivery attempts if the client does not meet certain minimal criteria, other's merely reject them.  Backscatter prevention techniques also reduce the ability to rely on bounce messages properly notifying users of failure.

It should be noted that from an end user's point of view, there is no way to reliably distinguish between received and dropped email.  And from a mail server admin's point of view, there is no way to determine silent rejection.

A quick survey of the various posts on various mail server-related mailing lists will reveal the challenges faced by numerous dynamic IP mail server admins.

My comment on SSL/TLS was a mistake. "since SSL requires a static IP" should have been "since TLS/SSL requires a FQDN".   The point was trying to indicate that different servers have different requirements.

MrC

---

### Post by MJN on 2007-08-07
All of that I generally agree with, but that is very much outgoing mail issues as opposed to the incoming issues you were discussing previously.

That said, relaying outgoing mail via your ISP's mail server surely avoids all of the problems associated with spam lists, particularly those related to residential IP lists doesn't it?

Unless mail systems are accepting mail and then checking *all* of the Received: headers, in which case my dynamic IP would be 'detected' as the first hop. Presumably they're not doing this? (if they are I haven't witnessed the effect, notwithstanding your point about messages being silently dropped but then I haven't heard (personally) the repercussions of such activity either).

Mathew

---

### Post by Mr. C. on 2007-08-07
> **MJN said:**
> All of that I generally agree with, but that is very much outgoing mail issues as opposed to the incoming issues you were discussing previously.

The general issue is one of reliability.  Key reasons for setting up a mail server are to provide a) control, b) accountability, c) reliability, and d) customization.  It serves little purpose to setup a receiving mail server, a domain name, and then use external mail services.  If the point is to simply obtain mail from a remote ISP or mail server, fetchmail serves the same purpose.  I took the OP's statement of "external machines" to mean the internet at large in the context of setting up an MX for a domain, not merely how to forward from gmail.  My statements were general statements, not absolute.  I view the requirements for mail servers as needing to meet points (b) and (c) above.

> **MJN said:**
> 
That said, relaying outgoing mail via your ISP's mail server surely avoids all of the problems associated with spam lists, particularly those related to residential IP lists doesn't it?

It depends on your ISP/provider.  Serious admins, for example, view hotmail as a plague, and some major mail providers supplied by various ISPs here in the states have horrible reputations for reliable, accountable mail relay. 
> **MJN said:**
> 
Unless mail systems are accepting mail and then checking *all* of the Received: headers, in which case my dynamic IP would be 'detected' as the first hop. Presumably they're not doing this? (if they are I haven't witnessed the effect, notwithstanding your point about messages being silently dropped but then I haven't heard (personally) the repercussions of such activity either).

In fact, spamassassin does review the Received headers, looking for obvious forgeries and trusted networks, and adjusting spam scores based on this, and various other factors.

The bottom line here is that the rules are changing, from anyone can run an MTA, to more restrictive requirements, all in the name of spam and forgery prevention.

MrC

---

