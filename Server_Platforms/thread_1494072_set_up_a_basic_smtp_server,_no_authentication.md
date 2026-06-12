---
title: "set up a basic smtp server, no authentication?"
date: 2010-05-26
forum: Server Platforms
---

### Post by pythonscript on 2010-05-26
I posted an earlier thread about this, but I think I'm over complicating things so I thought I'd simplify it for myself. I'm trying to set up a local smtp server on my ubuntu 10.04 machine. I would like:

an smtp server with no authentication that can use any range of hosts
a way to change the name of said server (say to localhost, myLaptop, whatever). 

How would I do this using postfix, or any other software in the repos if someone knows something better? Thanks!

---

### Post by Iowan on 2010-05-26
Moved to Server Platforms.
Is [this]("http://ubuntuforums.org/showthread.php?t=1493408") the other thread?

---

### Post by pythonscript on 2010-05-27
Yes, that is the other thread, and maybe this does belong in the server section. I'm not, however, using Ubuntu Server Edition; I'm using the desktop version, so would that still apply?

---

### Post by pythonscript on 2010-05-29
Does anyone have any ideas? I installed postfix, but when I try to send an email through my local smtp server, I get a "relay access denied" message, no matter which one of my email accounts I choose to send it through. Thanks!

---

### Post by ruuden on 2010-05-29
I believe a default postfix intall will give you a basic working smtp server with no authentication. The relay access denied error you get could be that you need to add the lan network address of your smtp server to the mynetworks parameter in /etc/postfix/main.cf

something like this:

```
mynetworks = 192.168.1.0/24
```also remember to check your mail log:

```
tail -20 /var/log/mail.log
```

---

### Post by pythonscript on 2010-05-29
I installed postfix, selected "Internet Site" as the default configuration, and this is my /etc/postfix/main.cf file:

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

myhostname = *HOSTNAME*
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost, *HOSTNAME*, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```Would I simply change the mynetworks field to your suggestion to be able to send email through an unauthenticated SMTP server (from any of my email accounts)? Also, do I *need *the references to my hostname in this file, or can I change that field (in this file only) to something as simple as localhost?

EDIT:  I'm also trying to send email to addresses not on my same LAN, if that makes any difference. Thanks!

---

### Post by ruuden on 2010-05-29
simply add your lan network similar to this:

```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24
```and change the myhostname to the name of your server to something like this:

```
myhostname = localhost, mx1.example.com
```

---

### Post by pythonscript on 2010-05-29
I'm still having problems getting this to work. I updated the appropriate sections of my main.cf file, as shown:

```

<snip>
myhostname = localhost
<snip>
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24
<snip>

```Everything else is the same. However, as the output of my mail log shows, "no route to host" is the main error. What am I missing?

Here's the log file:
```
HOSTNAME postfix/smtpd[15891]: connect from localhost[127.0.0.1]
HOSTNAME postfix/smtpd[15891]: A093160692: client=localhost[127.0.0.1]
HOSTNAME postfix/smtpd[15891]: warning: Illegal address syntax from localhost[127.0.0.1] in RCPT command: <>
HOSTNAME postfix/smtpd[15891]: warning: Illegal address syntax from localhost[127.0.0.1] in RCPT command: <>
HOSTNAME postfix/cleanup[15896]: A093160692: message-id=<20100530015247.A093160692@localhost>
HOSTNAME postfix/qmgr[15600]: A093160692: from=<FOO@BAR.COM>, size=590, nrcpt=1 (queue active)
HOSTNAME postfix/smtpd[15891]: disconnect from localhost[127.0.0.1]
HOSTNAME postfix/smtp[15897]: connect to gmail-smtp-in.l.google.com[74.125.95.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt1.gmail-smtp-in.l.google.com[209.85.211.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt2.gmail-smtp-in.l.google.com[74.125.113.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt3.gmail-smtp-in.l.google.com[209.85.219.46]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt4.gmail-smtp-in.l.google.com[74.125.39.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: A093160692: to=<ADDRESS>, relay=none, delay=3.4, delays=0.05/0.01/3.3/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.39.27]:25: No route to host)
HOSTNAME postfix/qmgr[15600]: 0737F60693: from=<ADDRESS>, size=604, nrcpt=1 (queue active)
HOSTNAME postfix/smtp[15897]: connect to gmail-smtp-in.l.google.com[74.125.95.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt1.gmail-smtp-in.l.google.com[209.85.211.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt2.gmail-smtp-in.l.google.com[74.125.113.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt3.gmail-smtp-in.l.google.com[209.85.219.46]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt4.gmail-smtp-in.l.google.com[74.125.39.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: 0737F60693: to=<ADDRESS>, relay=none, delay=414, delays=410/0/3.5/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.39.27]:25: No route to host)
```and here's my futile attempt to debug it using telnet, which seems to work until the connection times out after a few minutes. 

```

telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 TEST SMTP BANNER
helo localhost
250 localhost
mail from: FOO@BAR.COM
250 2.1.0 Ok
rcpt to: ADDRESS@GMAIL.COM
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
Subject: hola
fin de correo
.
250 2.0.0 Ok: queued as D4532606A4


```

Sorry about the long post, but thank you for all the help!

---

### Post by HermanAB on 2010-05-30
Well, you either need to go to the Postfix project web site and spend the next two or three days reading, or you should give up and install Citadel.  It takes about 20 minutes using the Easy Install script, less if you use the Ubuntu deb:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

---

### Post by hictio on 2010-05-30
> **pythonscript said:**
> 

~snip~
Everything else is the same. However, as the output of my mail log shows, "no route to host" is the main error. What am I missing?

Here's the log file:
```
HOSTNAME postfix/smtpd[15891]: connect from localhost[127.0.0.1]
HOSTNAME postfix/smtpd[15891]: A093160692: client=localhost[127.0.0.1]
HOSTNAME postfix/smtpd[15891]: warning: Illegal address syntax from localhost[127.0.0.1] in RCPT command: <>
HOSTNAME postfix/smtpd[15891]: warning: Illegal address syntax from localhost[127.0.0.1] in RCPT command: <>
HOSTNAME postfix/cleanup[15896]: A093160692: message-id=<20100530015247.A093160692@localhost>
HOSTNAME postfix/qmgr[15600]: A093160692: from=<FOO@BAR.COM>, size=590, nrcpt=1 (queue active)
HOSTNAME postfix/smtpd[15891]: disconnect from localhost[127.0.0.1]
HOSTNAME postfix/smtp[15897]: connect to gmail-smtp-in.l.google.com[74.125.95.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt1.gmail-smtp-in.l.google.com[209.85.211.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt2.gmail-smtp-in.l.google.com[74.125.113.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt3.gmail-smtp-in.l.google.com[209.85.219.46]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt4.gmail-smtp-in.l.google.com[74.125.39.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: A093160692: to=<ADDRESS>, relay=none, delay=3.4, delays=0.05/0.01/3.3/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.39.27]:25: No route to host)
HOSTNAME postfix/qmgr[15600]: 0737F60693: from=<ADDRESS>, size=604, nrcpt=1 (queue active)
HOSTNAME postfix/smtp[15897]: connect to gmail-smtp-in.l.google.com[74.125.95.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt1.gmail-smtp-in.l.google.com[209.85.211.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt2.gmail-smtp-in.l.google.com[74.125.113.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt3.gmail-smtp-in.l.google.com[209.85.219.46]:25: No route to host
HOSTNAME postfix/smtp[15897]: connect to alt4.gmail-smtp-in.l.google.com[74.125.39.27]:25: No route to host
HOSTNAME postfix/smtp[15897]: 0737F60693: to=<ADDRESS>, relay=none, delay=414, delays=410/0/3.5/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.39.27]:25: No route to host)
```and here's my futile attempt to debug it using telnet, which seems to work until the connection times out after a few minutes. 

~snip~

Sorry about the long post, but thank you for all the help!

Can you actually ping (and get a reply ;) ) from any of those Gmail addresses from the Ubuntu box?
Can you open a TCP connection to port 25 of any of those Gmail addresses from the Ubuntu box?
Are you behind a firewall that blocks (or limits to a certain IP address) connections to port 25 TCP?

---

### Post by BoneKracker on 2010-05-30
I'm not sure what you're trying to accomplish, but have you looked into ssmtp, esmtp, nbsmtp, msmtp and the like?  These are light send-only (relay-only) mail transfer agents.  I haven't tried the others, but I know ssmtp and esmtp can send via gmail.  And the configuration is trivial.

If you are not actually trying to provide email service to users on other machines, then one of these may be right for you.  Esmtp can also send local mail via a local delivery agent such as procmail.

---

### Post by hictio on 2010-05-30
> **BoneKracker said:**
> I'm not sure what you're trying to accomplish, but have you looked into ssmtp, esmtp, nbsmtp, msmtp and the like?  These are light send-only (relay-only) mail transfer agents.  I haven't tried the others, but I know ssmtp and esmtp can send via gmail.  And the configuration is trivial.

If you are not actually trying to provide email service to users on other machines, then one of these may be right for you.  Esmtp can also send local mail via a local delivery agent such as procmail.

I was thinking on ssmtp as well, but AFAIK, it only allows to send from the localhost, it doesn't work as a relay for a LAN, for instance.
I mean, as I understand the OP, ssmtp will send to what ever you throw at, but, you'll still have to configure that box to accept email from another box.

---

### Post by BoneKracker on 2010-05-30
> **hictio said:**
> I was thinking on ssmtp as well, but AFAIK, it only allows to send from the localhost, it doesn't work as a relay for a LAN, for instance.
I mean, as I understand the OP, ssmtp will send to what ever you throw at, but, you'll still have to configure that box to accept email from another box.

That's correct.  These send-only MTAs are just that.  They're really just designed for two use cases:

a. get system mail off the box (mail coming from cron, scripts, etc.)

b. user has a traditional MUA (mail client) such as Mutt, which relies on being able to talk directy to an MTA on the local machine

Theoretically, you could use whatever means you wanted to move mail from one box to another and then send it, but then you're kind of defeating the purpose; why not just put ssmtp (or esmtp) on all the boxes and have them all relay via the same external host (e.g. gmail).  That's what I do.

But if he is actually wanting to set up mail services for the users on his network, this is not the solution.  That's what full-blown mail servers are for (e.g. sendmail, exim, postfix, etc.).

---

### Post by Vishal Agarwal on 2010-05-30
There is a very good tutorial at 

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

---

### Post by pythonscript on 2010-05-30
I'm trying to get postfix to relay *all *mail, so I can use it as my universal SMTP server for any of my email accounts. I've used a free SMTP server on Windows that will do this, but it seems a shame to boot into Windows just to use a local SMTP server.

---

### Post by BoneKracker on 2010-05-30
> **pythonscript said:**
> I'm trying to get postfix to relay *all *mail, so I can use it as my universal SMTP server for any of my email accounts. I've used a free SMTP server on Windows that will do this, but it seems a shame to boot into Windows just to use a local SMTP server.

It makes sense if you really have a need to run a local SMTP server (like if you are sending spam or engaged in acts of sedition against your government).  But if you're just relaying it all through your own account on somebody else's MTA (like your gmail account), then you're not really accomplishing anything.  Your email client can do that (unless you're using something like Mutt).

Even if you just want more local control, so you can do your own mail filtering beyond the capabilities of most mail clients, you can just use fetchmail to collect mail and deposit it in your system mail spool.  Then you can either access it there directly with your mail client, or use procmail to filter and deliver it to user home directories.  For sending, you can use ssmtp or esmtp.  That way, you're not running any additional daemons.

Then again, some people just like the idea of playing around with their own mail server, and if you've got the CPU cycles to spare, why not?  Just wanted you to be aware of the lighter alternative approaches. :)

If you are having trouble with postfix, you might want to try exim.  The last time I did a product selection, it seemed to be the superior product.

---

### Post by pythonscript on 2010-05-30
> **BoneKracker said:**
> 
If you are having trouble with postfix, you might want to try exim.  The last time I did a product selection, it seemed to be the superior product.

Is there any specific config file I can post for exim or do you have any tips for relaying all mail? I installed it, ran through dpkg-reconfigure exim4-config, and yet the emails to my gmail and work accounts still aren't showing up, so I figure I'm once again doing something wrong.

---

### Post by hictio on 2010-05-30
> **pythonscript said:**
> I'm trying to get postfix to relay *all *mail, so I can use it as my universal SMTP server for any of my email accounts. I've used a free SMTP server on Windows that will do this, but it seems a shame to boot into Windows just to use a local SMTP server.

Did that free SMTP server for Windows run from the same network that you are trying to setup the Ubuntu Server?
Are you sure you can establish a direct connection from the Ubuntu Server box to the -for instance- Gmail server's SMTP port? Perhaps you have to use another server to relay all the email, your ISP's perhaps? That is not uncommon nowadays.

---

### Post by BoneKracker on 2010-05-30
> **pythonscript said:**
> Is there any specific config file I can post for exim or do you have any tips for relaying all mail? I installed it, ran through dpkg-reconfigure exim4-config, and yet the emails to my gmail and work accounts still aren't showing up, so I figure I'm once again doing something wrong.

No, I personally don't use it.  I'm sure there are numerous tutorials on the web, and that they have a website with documentation.  It looks like there's a wiki as well:
[http://wiki.exim.org/FrontPage](http://wiki.exim.org/FrontPage)

In fact, I'm sure you could find plenty of ubuntu-specific guidance, probably by doing nothing more than googling for exim ubuntu.

---

### Post by helliewm on 2010-06-02
I am trying to do the exact same thing. I too do not want to use Windows to use Freesmtp and am trying to find a Linux alternative to send mail from localhost on Ubuntu as FreeSmtp does on Windows. Any suggestions on an easy way to achieve this?

Helen

Ps Would installing Zimbra be an easy way to achieve this?

PPs It seems Citadel is the answer [http://www.citadel.org/doku.php]("http://www.citadel.org/doku.php") Still figuring it out but its a Deb file so easy to install and it looks very simple. When you have installed the DEB type [http://127.0.0.1](http://127.0.0.1) into your browser to get the control panel.

---

### Post by pythonscript on 2010-06-02
The problem with Freesmtp for Windows is that it limits you to only 10 emails a day. I send out 5 a day just to my classes, and by the time I include my other job, family, etc, a maximum of 10 is too restrictive. 

Back to Linux:  I hadn't looked at Zimbra, but I'll take a look at it and Citadel. I was trying to avoid installing an *entire *groupware sweet just for one small piece of it (since I don't want to add bloat to my production machine) but if that's the best I can find, it will have to work. I'll post again once I try out Citadel.

---

