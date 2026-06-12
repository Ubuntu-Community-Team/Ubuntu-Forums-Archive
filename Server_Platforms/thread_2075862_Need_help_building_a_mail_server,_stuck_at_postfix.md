---
title: "Need help building a mail server, stuck at postfix and/or courier config"
date: 2012-10-24
forum: Server Platforms
---

### Post by Kethinov on 2012-10-24
Hi all.

Trying to build a mail server for a custom domain we'll call example.com for now. Server is currently running on 12.04 LTS.

The guides weren't kidding when they said "Setting up an email server is a difficult process." ([https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer))

I started with this guide: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Did all that. No issues. :)

Then I followed these steps: [https://help.ubuntu.com/community/Courier](https://help.ubuntu.com/community/Courier)

Did all that, but the first sign of trouble was when I ran "telnet localhost imap"

I only got this far:

```
telnet localhost imap
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2011 Double Precision, Inc.  See COPYING for distribution information.
01 "login" "kethinov password"
01 NO Error in IMAP command received by server.
```

I also tried a different test:

```
netcat mail.example.com 143
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2011 Double Precision, Inc.  See COPYING for distribution information.
a login kethinov password
a NO Login failed.
```

I also decided to run postfix through some more rigorous tests. But that didn't go so well either:

```
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 example.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: root@localhost
250 2.1.0 Ok
rcpt to: kethinov@localhost
451 4.3.0 <kethinov@localhost>: Temporary lookup failure
data
554 5.5.1 Error: no valid recipients
Subject: My first mail on Postfix
221 2.7.0 Error: I can break rules, too. Goodbye.
Connection closed by foreign host.
```

The user is valid and the guides don't cover these errors so I don't get what's going on here. And no amount of Googling is shedding light on this. Anybody got any tips?

---

### Post by duesentriebchen on 2012-10-25
hmm...
 
I am using exim4-heavy-daemon with courier-imap-ssl
mine is working after installation from scratch.
 
Can you post the output of
```
sudo service courier-imap status
```
and
```
sudo service courier-imap-ssl status
```
and
```
sudo service postfix status
```
and
```
sudo lsof -nPi | grep LISTEN
```
and
```
sudo lsof -nPi | grep courier
```
and
```
sudo lsof -nPi | grep postfix
```
 
also please
```
cat /var/log/mail.log
```
and
```
cat /var/log/mail.err
```
for courier logging.
 
Please also post the logging of postfix
Are you using sasl-authd?
Please post the line in /etc/passwd from user kethinov

---

### Post by Kethinov on 2012-10-25
Ran those commands and noticed this in mail.err:

```
Oct 25 15:59:29 myhostname postfix/smtpd[9338]: error: unsupported dictionary type: mysql
Oct 25 15:59:29 myhostname postfix/proxymap[9339]: error: unsupported dictionary type: mysql
Oct 25 15:59:43 myhostname postfix/trivial-rewrite[9340]: error: unsupported dictionary type: mysql
Oct 25 15:59:43 myhostname postfix/proxymap[9339]: error: unsupported dictionary type: mysql
```

Those broken MySQL configs were from previous guides I followed that didn't work out too well.

I purged the MySQL configs and now my telnet and netcat tests of postfix and courier seem to be working. I'm able to see mail get delivered to the user's Maildir using the telnet/netcat methods. :)

However, when trying to configure my mail client on a desktop machine (Mail.app on a Mac), the login is failing:

```
sudo tail -f /var/log/mail.log
Oct 25 16:28:12 myhostname imapd: Connection, ip=[::ffff:x.x.x.x]
Oct 25 16:28:12 myhostname imapd: LOGIN FAILED, method=PLAIN, ip=[::ffff:x.x.x.x]
Oct 25 16:28:17 myhostname imapd: Disconnected, ip=[::ffff:x.x.x.x], time=5, starttls=1
```

I'm not sure how to debug further. :(

---

### Post by Ron Jones on 2012-10-25
I feel your pain.

Last week I finally upgraded the hardware to something that cost less to run (Atom D525). We (our family) has been on Qmail (of qmailrocks.org, then qmailtoaster.com) for the last 9 years. But, after a bit of research, I decided to go with Postfix for the new mail server. I was ambivalent about Courier vs Dovecot (there's only 5 or 6 users), but I wanted Amavis, Spamassassin, and ClamAV (plus a flashy web interface for my Mother).

First, I started out with Flurdy's guide at [http://flurdy.com/docs/postfix/index.html](http://flurdy.com/docs/postfix/index.html) 
When it didn't work, I had to admit that it was NOT the guide which was lacking, but my lack of understanding. So, I spent the next couple of days reviewing the basics at [http://workaround.org/ispmail/squeeze](http://workaround.org/ispmail/squeeze) 

Three complete wipes of the hard drive later.....

Finally, I wound up at [http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/](http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/) Which was written for at 12.04.

While the ExRatione guide uses Horde, we don't need anything so complex. So, after step 17 (Restart everything and test the server) was completed successfully (which means, I can use my Thunderbird client and send/receive mail from my desk)... I jumped back to Flurdy's guide, and picked up at the Roundcube webmail client instructions he gives as an alternative to SquirrelMail.

(I've used Squirrelmail for years now, it's decent and solid. But, like most middle-aged men, I wanted an exciting little diversion, so the "Ajax-y" allure of Roundcube did the trick).

Works like a charm so far. But now I need to figure out how to get my web server's logwatch utility able to send it's morning report through the webserver and onto my desk....

---

### Post by duesentriebchen on 2012-10-26
hy kethinov.

ok, nice to hear that the sending is working :)
did you try to send a mail to a mailaddress of your's like
```
echo "this a imap test" | mail -s "postfixmailtest" USER_NAME@SOME_DOMAIN
```you seem to be using the plain authentication method on your mail client.

did you try to change to login?

it would be interesting to see the output of ```
cat /etc/passwd |  grep YOUR_USER_NAME
```i am using vsftpd also, and therefor i set the  
```
/bin/bash
```to
```
/bin/false
```i hope you did not set it on
```
/bin/nologin
```ps.: for tail you would not need sudoers rights

---

### Post by Kethinov on 2012-11-05
> **duesentriebchen said:**
> hy kethinov.

ok, nice to hear that the sending is working :)
did you try to send a mail to a mailaddress of your's like
```
echo "this a imap test" | mail -s "postfixmailtest" USER_NAME@SOME_DOMAIN
```you seem to be using the plain authentication method on your mail client.

No output.

> **duesentriebchen said:**
> it would be interesting to see the output of ```
cat /etc/passwd |  grep YOUR_USER_NAME
```

It's just an ordinary unix user.

```
kethinov:x:1000:1000:,,,:/home/kethinov:/bin/bash
```

---

### Post by Kethinov on 2012-11-05
Okay, my problem was /etc/courier/authdaemonrc.

When I altered the "authmodulelist" line back to the default config, I was able to configure Mail.app to download the email account's mail. :)

```
authmodulelist="authuserdb authpam authpgsql authldap authmysql authcustom authpipe"
```

But now I have two new problems. :(

The first new problem is SMTP isn't working. There doesn't appear to be an SMTP server running; my mail client can't connect to one.

The second new problem is I can't seem to receive new mail from an external email address. I tried sending email from my GMail account and the mail.log didn't like that much at all.

```
Nov  5 09:37:43 mydomain postfix/smtpd[3121]: warning: database /etc/aliases.db is older than source file /etc/aliases
Nov  5 09:37:43 mydomain postfix/smtpd[3121]: cannot load Certificate Authority data: disabling TLS support
Nov  5 09:37:43 mydomain postfix/smtpd[3121]: warning: TLS library problem: 3121:error:02001002:system library:fopen:No such file or directory:bss_file.c:169:fopen('/etc/ssl/certs/cacert.pem','r'):
Nov  5 09:37:43 mydomain postfix/smtpd[3121]: warning: TLS library problem: 3121:error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:172:
Nov  5 09:37:43 mydomain postfix/smtpd[3121]: warning: TLS library problem: 3121:error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib:by_file.c:274:
Nov  5 09:37:43 mydomain postfix/smtpd[3121]: connect from mail-pb0-f52.google.com[209.85.160.52]
Nov  5 09:37:43 mydomain postfix/cleanup[3124]: AB02F192A2: message-id=<20121105093743.AB02F192A2@mydomain.com>
Nov  5 09:37:43 mydomain postfix/smtpd[3121]: disconnect from mail-pb0-f52.google.com[209.85.160.52]
Nov  5 09:37:43 mydomain postfix/qmgr[2632]: AB02F192A2: from=<double-bounce@mydomain.com>, size=984, nrcpt=1 (queue active)
Nov  5 09:37:43 mydomain postfix/local[3126]: warning: database /etc/aliases.db is older than source file /etc/aliases
Nov  5 09:37:43 mydomain postfix/local[3126]: warning: alias database loop for root
Nov  5 09:37:43 mydomain postfix/local[3126]: AB02F192A2: to=<root@mydomain.com>, orig_to=<postmaster>, relay=local, delay=0.03, delays=0.01/0.01/0/0.01, dsn=5.4.6, status=bounced (alias database loop for root)
Nov  5 09:37:43 mydomain postfix/bounce[3127]: warning: AB02F192A2: undeliverable postmaster notification discarded
Nov  5 09:37:43 mydomain postfix/qmgr[2632]: AB02F192A2: removed
```

---

### Post by duesentriebchen on 2012-11-08
Hy kethinov.
 
Quote:
Originally Posted by **duesentriebchen** [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12318809#post12318809") 
*hy kethinov.*
 
*ok, nice to hear that the sending is working :smile:*
*did you try to send a mail to a mailaddress of your's like*
*Code:*
*echo "this a imap test" | mail -s "postfixmailtest" USER_NAME@SOME_DOMAIN*
*you seem to be using the plain authentication method on your mail client.*
 
No output. -> Did you get a Mail? With this command you will send a mail, not getting an output kethinov. 
 
Quote:
Originally Posted by **duesentriebchen** [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12318809#post12318809") 
[I]it would be interesting to see the output of Code:
cat /etc/passwd |  grep YOUR_USER_NAME
[/I]

It's just an ordinary unix user. -> Should be /bin/false for Security.
 
Please post the output of
```
sudo lsof -nPi | grep LISTEN
```
```
sudo lsof -nPi | grep postfix
```
```
sudo ps -A | grep postix
```
```
cat /etc/aliases
```
 
did you build a certificate with openssl?
 
I am not sure, if your smtp supports SSL/TSL ...
 
To check your smtp for the AUTH capability please do as follows. We will install a nice tool to check this :)
```
sudo aptitude install swaks libnet-ssleay-perl
```
 
POSTE the output of
```
swaks -a -tls -q HELO -s localhost -au kethinov -ap '<>'
```
 
It would help, if you would poste your postfix /etc/postfix/main.cf
 
Greetings.

---

