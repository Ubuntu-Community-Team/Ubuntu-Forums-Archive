---
title: "Please, please help me set up POSTFIX"
date: 2008-07-29
forum: Server Platforms
---

### Post by grandsatrap on 2008-07-29
I am stuck with Postfix. The online instructions are all too complicated and miss some explanations.

Here is my setup:
My ISP = myisp.com
My ubuntu computer = kubu
so it thinks its fqdn is kubu.myisp.com
my username = fred
I want to send email from [email]fred@kubu.myisp.com[/email]
to (i) [email]andrew@myisp.com[/email]  [this user is another customer of my ISP]
(ii) [email]helen@yahoo.com[/email]

Here is what I type:
====================
fred@kubu:~$ mail [email]andrew@myisp.com[/email]
Subject: testing postfix

hello again
.
Cc: 
fred@kubu:~$ 

This is: sudo tail -20 /var/log/mail.log
========================================
Jul 29 10:10:12 kubu postfix/pickup[5818]: 5707B7A3B7: uid=1000 from=<fred>
Jul 29 10:10:12 kubu postfix/cleanup[5835]: 5707B7A3B7: message-id=<20080729141012.5707B7A3B7@myisp.com>
Jul 29 10:10:12 kubu postfix/qmgr[4521]: 5707B7A3B7: from=<fred@net>, size=305, nrcpt=1 (queue active)
Jul 29 10:10:22 kubu postfix/smtp[5837]: 5707B7A3B7: to=<andrew@myisp.com>, relay=smtp.myisp.com[209.1.1.1]:25, delay=10, delays=0.08/0.02/10/0.04, dsn=5.0.0, status=bounced (host smtp.myisp.com[209.1.1.1] said: 550-Verification failed for <fred@net> 550-Unrouteable address 550 Sender verify failed (in reply to RCPT TO command))
Jul 29 10:10:22 kubu postfix/cleanup[5835]: 816F37A3C4: message-id=<20080729141022.816F37A3C4@myisp.com>
Jul 29 10:10:22 kubu postfix/qmgr[4521]: 816F37A3C4: from=<>, size=2197, nrcpt=1 (queue active)
Jul 29 10:10:22 kubu postfix/bounce[5838]: 5707B7A3B7: sender non-delivery notification: 816F37A3C4
Jul 29 10:10:22 kubu postfix/qmgr[4521]: 5707B7A3B7: removed
Jul 29 10:10:32 kubu postfix/smtp[5837]: 816F37A3C4: to=<fred@net>, relay=smtp.myisp.com[209.1.1.1]:25, delay=10, delays=0.01/0/10/0.07, dsn=2.0.0, status=sent (250 OK id=1KNq2t-00031X-EG)
Jul 29 10:10:32 kubu postfix/qmgr[4521]: 816F37A3C4: removed


What am I doing wrong?
Why is it saying "fred@net"?

Thanks.

---

### Post by brian_p on 2008-07-30
> 

Jul 29 10:10:22 kubu postfix/smtp[5837]: 5707B7A3B7: to=<andrew@myisp.com>, relay=smtp.myisp.com[209.1.1.1]:25, delay=10, delays=0.08/0.02/10/0.04, dsn=5.0.0, status=bounced (host smtp.myisp.com[209.1.1.1] said: 550-Verification failed for <fred@net> 550-Unrouteable address 550 Sender verify failed (in reply to RCPT TO command))

What am I doing wrong?
Why is it saying "fred@net"?

Thanks.

Presumably because fred@net is what you have as the envelope from header and your ISP does a lookup on it and finds it does not exist. Does

```
sudo dpkg-reconfigure postfix
```

help to resolve the problem.

---

### Post by Oldsoldier2003 on 2008-07-30
moved to server platforms for better response

---

### Post by StickyStyle on 2008-07-30
can you post the output of ```
$postconf -n
``` and ```
$cat /etc/mailname
```

---

### Post by MJN on 2008-07-31
> **grandsatrap said:**
> What am I doing wrong?Not posting your Postfix config hence making us guess as to why the default domain appending for submissions with incomplete addresses is not working...
 
Seriously, post it and we can take a look! :)
 
Ideally, it is the responsibility of the mail client to correctly (and fully) define the sender's address but I'm not sure if 'mail' can do this.
 
Mathew

---

### Post by grandsatrap on 2008-07-31
I have the very basic sending of email working. YAY!!!

For any others who have problems:
1. use tail -20 /var/mail/mail.log
   The line that has postfix/smtp will tell you what happened to your message.

2. Fiddle with /etc/postfix/main.cf, then sudo postfix reload, then send email, then check the mail log.

3. Try sending to various email addresses. 
Specifically: 
Assume that my ISP is called "mycybernet.net" I am sending from an account called "mars" on my linux computer, thus [email]mars@mycbernet.net[/email]
I added a new email address to my account at my ISP: [email]venus@mycybernet.net[/email] . When I send email from Ubuntu (mars@mycybernet.net) to [email]venus@mycybernet.net[/email] my ISP deletes this email for some reason. I don't understand why. Maybe it is just delayed for hours, or maybe my ubuntu computer thinks that venus is a local account. This led me to believe that nothing was working. I finally sent it to somewhere out to a completely different email address on the internet and it got there!  YAY!!

Here is my stripped down postfix/main.cf for any who are interested. (My account name has been changed for sec. reasons.)

mars@buntu99:/etc/postfix$ cat main.cf

[FONT="Courier New"]#myorigin = /etc/mailname
# this makes it buntu99.mycybernet.net
myhostname = mycybernet.net
myorigin = mycybernet.net
#myorigin = $mydomain

# this line does not seem to work!
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

# TLS parameters
smtpd_use_tls=no

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

mydestination = buntu99.mycybernet.net, buntu99, localhost.localdomain, localhost
# leave relayhost blank if you want to handle the sending of your own mail
#relayhost = 
relayhost = smtp.mycybernet.net
# the next line limits mail relaying to only these IPs (no open relay)
mynetworks = 127.0.0.0/8

# Is the next line needed (for being behind an NAT?)
proxy_interfaces = 192.168.1.1
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# Are the following lines needed?
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet
# modify the existing smtpd_sender_restrictions
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit[/FONT]
mars@buntu99:/etc/postfix$

---

### Post by MJN on 2008-08-01
Your config is broken. You say your ISP is mycybernet.net yet you have told Postfix *it* is mycybernet.net. This confusion will lead to missing mail.
 
What domain does your mail server accept mail for? That is the domain that should mydestination and other related directives.
 
Mathew

---

### Post by grandsatrap on 2008-08-01
Thanks for taking the time to read my config. All I need is to send email - which I can do anywhere except to the mycybernet.net domain. I am not trying to receive email.
I have not set up my own domain, although my machine is named buntu99. I don't really know what "myorigin" and "myhostname" should be, except that this way they work and my email gets routed through my ISP. Can you tell me how they should be fixed properly?

Note: I think that this thread should have been posted to "Server Platforms" forum. I'll do that next time.

---

### Post by MJN on 2008-08-01
You might be better off with something like 'nullmailer' - this will act as a local SMTP server to relay all outgoing mail via your ISP. Or, just configure your clients to use your ISP's outgoing mail server but I can see benefits with a more centralised approach.
 
Incidentally, this thread is in the Server Platforms forum!
 
Mathew

---

### Post by BigbobOz on 2008-08-05
Continuing from here
[http://ubuntuforums.org/showpost.php?p=5521641&postcount=3](http://ubuntuforums.org/showpost.php?p=5521641&postcount=3)

Thanks for the link Grandsatrap, good to see someone else's main.cf, the guide's example link is broken.

I think (at this stage) my problem is that postfix cannot not "access /private/auth-client 'Permission denied'"

I don't have root user active but it doesn't seem from the guides that I need to. Is there a way to change the permission's? Would this create a security issue?

Thanks Rob

---

### Post by BigbobOz on 2008-08-05
Here's a dump of my mail.log. Permissions don't seem to be my only error but from I can tell the other errors seem to stem from that...except the 'terminating on signal 15' in the first line, that doesn't look good either.

Aug  6 00:23:57 kuitam postfix/master[5445]: terminating on signal 15
Aug  6 00:23:58 kuitam postfix/master[25934]: daemon started -- version 2.5.1, configuration /etc/postfix
Aug  6 00:24:08 kuitam postfix/smtpd[25943]: warning: SASL: Connect to private/auth-client failed: Permission denied
Aug  6 00:24:08 kuitam postfix/smtpd[25943]: fatal: no SASL authentication mechanisms
Aug  6 00:24:09 kuitam postfix/master[25934]: warning: process /usr/lib/postfix/smtpd pid 25943 exit status 1
Aug  6 00:24:09 kuitam postfix/master[25934]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

Does that helpl?

Thanks

Robert

---

### Post by grandsatrap on 2008-08-05
I don't know how to help you because I am not using SASL. Sorry.
You may want to start a new thread with SASL in the title.

---

### Post by HermanAB on 2008-08-05
Seriously, I have given up with Postfix a year ago.  It is much better than sendmail, but it is just not worth the trouble for most applications.  I would only use Postfix in applications with millions of users and most admins don't have that problem.

You should look at Citadel at [http://www.citadel.org](http://www.citadel.org).  Using that, you can have a full featured system up and running in less than an hour and it can handle tens of thousands of users, which is enough for most situations.  Citadel does every mail protocol ever invented by mankind, including the secure protocols.

Cheers,

Herman

---

### Post by BigbobOz on 2008-08-05
> **grandsatrap said:**
> I don't know how to help you because I am not using SASL. Sorry.
You may want to start a new thread with SASL in the title.

I don't have to use SASL? Happy not to, I was just following the guide. How do you have it working?

Thanks

Rob

---

### Post by BigbobOz on 2008-08-05
> **HermanAB said:**
> Seriously, I have given up with Postfix a year ago.  It is much better than sendmail, but it is just not worth the trouble for most applications.  I would only use Postfix in applications with millions of users and most admins don't have that problem.

You should look at Citadel at [http://www.citadel.org](http://www.citadel.org).  Using that, you can have a full featured system up and running in less than an hour and it can handle tens of thousands of users, which is enough for most situations.  Citadel does every mail protocol ever invented by mankind, including the secure protocols.

Cheers,

Herman

Thanks, I'll check it out.

Rob

---

