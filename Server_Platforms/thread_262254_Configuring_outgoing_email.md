---
title: "Configuring outgoing email"
date: 2006-09-21
forum: Server Platforms
---

### Post by timelord726 on 2006-09-21
I just set up a brand new Ubuntu 6.06 web server, and everything's running great except for outgoing email.  I run a vBulletin message board on the web server and it can't send outgoing email either through sendmail or SMTP and I know I haven't configured something properly.

I followed this tutorial on setting up all the mail functionality:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5)

I've done it once before using this tutorial and both SMTP and sendmail worked, so I'm not sure what I might be doing wrong this time.  Can someone walk me through some basic troubleshooting steps to ensure that the server is able to send outgoing mail through itself?

Thanks!

---

### Post by skymt on 2006-09-21
The first step is to try to send a message and check the log file. I'm not at a computer with Postfix at the moment, but I think the log is at "/var/log/mail.log". Post the errors you get with both sendmail and SMTP.

One possible reason for mail not working is (black|white)listing on the other end. Verizon, for example, blacklists all customer IPs on their incoming mail servers, under the assumption that the only reason a customer would be running an SMTP server is if they're infected with a spam trojan. You should try to send a message to an account on the same machine, to help eliminate that possibility.

---

### Post by timelord726 on 2006-09-21
Thank you for your response.  I've done as you asked and attempted to test it out, and I've attached the log file it's produced.  I hope it's valuable!

---

### Post by skymt on 2006-09-21
Starting from toward the top:

```
Sep 21 12:40:02 pods-us01 postfix/pickup[11597]: 0E85E2E42D5: uid=110 from=<smmsp>
Sep 21 12:40:02 pods-us01 postfix/cleanup[11648]: 0E85E2E42D5: message-id=<20060921164002.0E85E2E42D5@pods-us01.dannystewart.com>
Sep 21 12:40:02 pods-us01 postfix/qmgr[11598]: 0E85E2E42D5: from=<smmsp@dannystewart.com>, size=657, nrcpt=1 (queue active)
Sep 21 12:40:03 pods-us01 postfix/local[11650]: 0E85E2E42D5: to=<danny@dannystewart.com>, orig_to=<root>, relay=local, delay=1, status=sent (delivered to command: procmail -a "$EXTENSION")
Sep 21 12:40:03 pods-us01 postfix/qmgr[11598]: 0E85E2E42D5: removed
```

You should have recieved this message. If you didn't, the problem is with your .procmailrc.

```
Sep 21 12:47:06 pods-us01 postfix/pickup[11784]: CD7252E42D9: uid=33 from=<www-data>
Sep 21 12:47:06 pods-us01 postfix/cleanup[11839]: CD7252E42D9: message-id=<200609211606.c70cce970219@www.dannystewart.com>
Sep 21 12:47:06 pods-us01 postfix/qmgr[11785]: CD7252E42D9: from=<www-data@dannystewart.com>, size=1099, nrcpt=1 (queue active)
Sep 21 12:47:06 pods-us01 postfix/local[11841]: CD7252E42D9: to=<danny@dannystewart.com>, relay=local, delay=0, status=sent (delivered to command: procmail -a "$EXTENSION")
Sep 21 12:47:06 pods-us01 postfix/qmgr[11785]: CD7252E42D9: removed
```

Same for this one.

```
Sep 21 12:48:24 pods-us01 postfix/smtpd[11859]: 9E6192E42D8: client=localhost.localdomain[127.0.0.1], sasl_method=LOGIN, sasl_username=danny
Sep 21 12:48:24 pods-us01 postfix/cleanup[11839]: 9E6192E42D8: message-id=<200609211624.706b0d461814@www.dannystewart.com>
Sep 21 12:48:24 pods-us01 postfix/qmgr[11785]: 9E6192E42D8: from=<danny@dannystewart.com>, size=1172, nrcpt=1 (queue active)
Sep 21 12:48:24 pods-us01 postfix/smtpd[11859]: disconnect from localhost.localdomain[127.0.0.1]
Sep 21 12:48:24 pods-us01 postfix/local[11841]: 9E6192E42D8: to=<danny@dannystewart.com>, relay=local, delay=0, status=sent (delivered to command: procmail -a "$EXTENSION")
Sep 21 12:48:24 pods-us01 postfix/qmgr[11785]: 9E6192E42D8: removed
```

See above, again. So, it looks like local delivery, sendmail, and smtp work. The only part that doesn't work is outgoing smtp.

Lines 53-54 are interesting:

```
Sep 21 12:52:45 pods-us01 sendmail[12855]: k8LGojj4012855: from=www-data, size=953, class=0, nrcpts=1, msgid=<200609211645.1faafd520835@www.dannystewart.com>, relay=www-data@localhost
Sep 21 12:52:45 pods-us01 sendmail[12855]: k8LGojj4012855: to=danny@dannystewart.com, delay=00:02:00, mailer=esmtp, pri=30953, dsn=4.4.3, stat=queued
```

This message never gets sent. In fact, this is the only time this message shows up in the log. Can you tell me what you were doing for this one?

Many entries look like this:

```
Sep 21 15:40:01 pods-us01 postfix/pickup[14260]: 7C3D32E42E8: uid=110 from=<smmsp>
Sep 21 15:40:01 pods-us01 postfix/cleanup[14543]: 7C3D32E42E8: message-id=<20060921194001.7C3D32E42E8@pods-us01.dannystewart.com>
Sep 21 15:40:01 pods-us01 postfix/qmgr[13924]: 7C3D32E42E8: from=<smmsp@pods-us01.dannystewart.com>, size=677, nrcpt=1 (queue active)
Sep 21 15:40:21 pods-us01 postfix/smtp[14545]: 7C3D32E42E8: to=<root@pods-us01.dannystewart.com>, orig_to=<root>, relay=none, delay=20, status=deferred (Host or domain name not found. Name service error for name=pods-us01.dannystewart.com type=MX: Host not found, try again)
```

This might indicate an error in the myhostname, myorigin, or mydomain settings. What are they set to in /etc/postfix/main.cf?

---

### Post by timelord726 on 2006-09-21
> **skymt said:**
> Starting from toward the top:

You should have recieved this message. If you didn't, the problem is with your .procmailrc.

Same for this one.

See above, again. So, it looks like local delivery, sendmail, and smtp work. The only part that doesn't work is outgoing smtp.
I haven't gotten anything from the server at all.  What could be wrong with .procmailrc or outgoing SMTP?

> **skymt said:**
>  Lines 53-54 are interesting:

This message never gets sent. In fact, this is the only time this message shows up in the log. Can you tell me what you were doing for this one?
Honestly, I have no idea.  This is not just the test I performed just now, but the entire day's activities so far.  Mostly I've just been sending test messages through vBulletin's diagnostic page.

> **skymt said:**
>  Many entries look like this:

This might indicate an error in the myhostname, myorigin, or mydomain settings. What are they set to in /etc/postfix/main.cf?
The lines you mention look like this:
```
myhostname = pods-us01.dannystewart.com
myorigin = /etc/mailname
mydestination = dannystewart.com, PODS-US01-UBL.hsd1.md.comcast.net., localhost.hsd1.md.comcast.net., localhost
```
I didn't see a mydomain anywhere in there but I did notice mydestination so I included that instead.  The hostname I made up during setup... is that supposed to be something specific?  If so, what should it be?

Thanks so much for your help!

---

### Post by skymt on 2006-09-21
Try setting mydomain to "dannystewart.com", and myorigin to "$mydomain". That may solve the MX errors. EDIT: Make sure mydomain comes before myorigin in the file.

For information on MX, see [Wikipedia](http://en.wikipedia.org/wiki/MX_record).

---

### Post by timelord726 on 2006-09-21
I just finished reconfiguring it accordingly and restarting the postfix server.  Unfortunately I'm still not getting any email from the server.  (I'm sending it to my [email]danny@dannystewart.com[/email] address, which is *not* maintained through this server but instead through Google.)

vBulletin doesn't seem to be aware of a problem when it sends a test message.  Here's what it spits back:

**Pertinent PHP Settings**
**SMTP:**     localhost (disabled)
**sendmail_from:**     [email]danny@dannystewart.com[/email]
**sendmail_path:**     /usr/sbin/sendmail -t -i

**Results**
No errors were returned while attempting to send the email. Check [email]danny@dannystewart.com[/email] shortly to confirm you've received the email. If you don't receive the email, try sending the test to a different address. If that fails, check your mail server's configuration.

---

### Post by skymt on 2006-09-21
Can you please post the log entries from your latest attempt?

---

### Post by timelord726 on 2006-09-21
Sure... sorry about that.  I'm not sure where exactly it occurred but it's in here somewhere:

```
Sep 21 20:40:01 pods-us01 postfix/qmgr[16595]: 8BF9D2E42F7: removed
Sep 21 20:53:34 pods-us01 postfix/qmgr[16595]: B536F2E42F4: from=<smmsp@pods-us01.dannystewart.com>, size=677, nrcpt=1 (queue active)
Sep 21 20:53:34 pods-us01 postfix/qmgr[16595]: 43BF42E42F6: from=<smmsp@pods-us01.dannystewart.com>, size=667, nrcpt=1 (queue active)
Sep 21 20:53:34 pods-us01 postfix/qmgr[16595]: 8C04E2E42E1: from=<smmsp@pods-us01.dannystewart.com>, size=677, nrcpt=1 (queue active)
Sep 21 20:53:34 pods-us01 postfix/qmgr[16595]: 1D2DB2E42EE: from=<smmsp@pods-us01.dannystewart.com>, size=677, nrcpt=1 (queue active)
Sep 21 20:53:34 pods-us01 postfix/qmgr[16595]: A38F72E42E5: from=<smmsp@pods-us01.dannystewart.com>, size=677, nrcpt=1 (queue active)
Sep 21 20:53:34 pods-us01 postfix/qmgr[16595]: E724C2E42F1: from=<smmsp@pods-us01.dannystewart.com>, size=677, nrcpt=1 (queue active)
Sep 21 20:53:34 pods-us01 postfix/qmgr[16595]: EF0DD2E42F5: from=<smmsp@pods-us01.dannystewart.com>, size=677, nrcpt=1 (queue active)
Sep 21 20:53:34 pods-us01 postfix/qmgr[16595]: 2BEE72E42F2: from=<smmsp@pods-us01.dannystewart.com>, size=677, nrcpt=1 (queue active)
Sep 21 20:53:54 pods-us01 postfix/smtp[16746]: B536F2E42F4: to=<root@pods-us01.dannystewart.com>, orig_to=<root>, relay=none, delay=4433, status=deferred (Host or domain name not found. Name service error for name=pods-us01.dannystewart.com type=MX: Host not found, try again)
Sep 21 20:53:54 pods-us01 postfix/smtp[16747]: 43BF42E42F6: to=<root@pods-us01.dannystewart.com>, orig_to=<root>, relay=none, delay=2033, status=deferred (Host or domain name not found. Name service error for name=pods-us01.dannystewart.com type=MX: Host not found, try again)
Sep 21 20:53:54 pods-us01 postfix/smtp[16748]: 8C04E2E42E1: to=<root@pods-us01.dannystewart.com>, orig_to=<root>, relay=none, delay=27233, status=deferred (Host or domain name not found. Name service error for name=pods-us01.dannystewart.com type=MX: Host not found, try again)
Sep 21 20:53:54 pods-us01 postfix/smtp[16749]: 1D2DB2E42EE: to=<root@pods-us01.dannystewart.com>, orig_to=<root>, relay=none, delay=11633, status=deferred (Host or domain name not found. Name service error for name=pods-us01.dannystewart.com type=MX: Host not found, try again)
Sep 21 20:53:54 pods-us01 postfix/smtp[16750]: A38F72E42E5: to=<root@pods-us01.dannystewart.com>, orig_to=<root>, relay=none, delay=22433, status=deferred (Host or domain name not found. Name service error for name=pods-us01.dannystewart.com type=MX: Host not found, try again)
Sep 21 20:53:54 pods-us01 postfix/qmgr[16595]: E724C2E42F1: to=<root@pods-us01.dannystewart.com>, orig_to=<root>, relay=none, delay=8033, status=deferred (delivery temporarily suspended: Host or domain name not found. Name service error for name=pods-us01.dannystewart.com type=MX: Host not found, try again)
Sep 21 20:53:54 pods-us01 postfix/qmgr[16595]: EF0DD2E42F5: to=<root@pods-us01.dannystewart.com>, orig_to=<root>, relay=none, delay=3233, status=deferred (delivery temporarily suspended: Host or domain name not found. Name service error for name=pods-us01.dannystewart.com type=MX: Host not found, try again)
Sep 21 20:53:54 pods-us01 postfix/qmgr[16595]: 2BEE72E42F2: to=<root@pods-us01.dannystewart.com>, orig_to=<root>, relay=none, delay=6833, status=deferred (delivery temporarily suspended: Host or domain name not found. Name service error for name=pods-us01.dannystewart.com type=MX: Host not found, try again)
Sep 21 21:00:01 pods-us01 postfix/pickup[16594]: C2F3C2E42F7: uid=110 from=<smmsp>
Sep 21 21:00:01 pods-us01 postfix/cleanup[16773]: C2F3C2E42F7: message-id=<20060922010001.C2F3C2E42F7@dannystewart.com>
Sep 21 21:00:01 pods-us01 postfix/qmgr[16595]: C2F3C2E42F7: from=<smmsp@dannystewart.com>, size=637, nrcpt=1 (queue active)
Sep 21 21:00:01 pods-us01 postfix/local[16775]: C2F3C2E42F7: to=<danny@dannystewart.com>, orig_to=<root>, relay=local, delay=0, status=sent (delivered to command: procmail -a "$EXTENSION")
Sep 21 21:00:01 pods-us01 postfix/qmgr[16595]: C2F3C2E42F7: removed
```

---

### Post by skymt on 2006-09-21
Please post your ~/.procmailrc. There may be a problem there.

---

### Post by timelord726 on 2006-09-21
By ~ do you mean my home directory?  If so there's no such file there...  (Sorry... haven't gone this deep into the configuration before.)

---

### Post by timelord726 on 2006-09-21
Update: I've just checked (through Webmin) and apparently I have no procmail configuration file at all.  It's blank.

---

### Post by skymt on 2006-09-22
Well, in many of the log entries ("...(delivered to command: procmail -a "$EXTENSION")"), Postfix says it's delivering to procmail. Without a .procmailrc, I think (not sure) procmail dumps the message.

I don't use procmail myself, but [this FAQ](http://partmaps.org/era/procmail/mini-faq.html) looks like a good place to start.

Unless you don't want to use procmail? If so, you should look at your Postfix local delivery configuration.

---

### Post by timelord726 on 2006-09-22
I honestly don't know what's best.  If Procmail is best, how do I set up an initial config?  If not, what's the best alternative and how can I get it up and running?

---

### Post by steven43126 on 2006-09-23
As a side note if you just want to get outgoing email up and running quickly use exim4 instead. It is a much easier MTA to get working in my opinion. There is very little config file editing required at all.

Steve.

---

### Post by skymt on 2006-09-23
I like procmail. I've used it in the past, and it's powerful and fairly easy to set up. I don't know the details of your setup, but [this Howto](http://userpages.umbc.edu/~ian/procmail.html) may help.

---

### Post by timelord726 on 2006-09-23
I don't think I need any filtering right now.  I just want to see some messages get out.

Here's my Postfix config if it will help.
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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = dannystewart.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = dannystewart.com, PODS-US01-UBL.hsd1.md.comcast.net., localhost.hsd1.md.comcast.net., localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
```

Anything suspicious in there?  In an attempt to get Procmail working, I entered a basic config as follows:
```
# .procmailrc
# routes incoming mail to appropriate mailboxes
PATH=/usr/bin:/usr/local/bin
MAILDIR=$HOME/.mailspool   # all mailboxes are in .mailspool/
DEFAULT=$HOME/.mailspool/ian
LOGFILE=/dev/null
SHELL=/bin/sh
```

---

### Post by timelord726 on 2006-10-05
Okay, I'm still having no luck getting email working from my server.  Let's tackle this from a different perspective -- rather than trying to fix a broken email system, what should I do in order to implement outgoing email functionality on a server with no email functionality at all?  Let's start from scratch and look at things that way.

---

