---
title: "Postfix config issue: Helo command rejected: need fully-qualified hostname"
date: 2008-12-05
forum: Server Platforms
---

### Post by Pitt Stains on 2008-12-05
Hello,

I'm using postfix to send email, and on about 1% of messages (from a small group of domains), I am getting auto-responses like this one:

> From: Mail Delivery System <MAILER-DAEMON@mydomain.com>
Subject: Undelivered Mail Returned to Sender
To: [email]undead0@mydomain.com[/email]
Auto-Submitted: auto-replied

[-- Attachment #1: Notification --]
[-- Type: text/plain, Encoding: 7bit, Size: 0.5K --]

This is the mail system at host undead0.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<recipient@otherdomain.org>: host smtp.cybergnostic.com[63.76.208.166] said: 504 5.5.2
    <undead0>: Helo command rejected: need fully-qualified hostname (in reply
    to RCPT TO command)

[-- Attachment #2: Delivery report --]
[-- Type: message/delivery-status, Encoding: 7bit, Size: 0.4K --]

Reporting-MTA: dns; undead0
X-Postfix-Queue-ID: 585C39FF5D
X-Postfix-Sender: rfc822; [email]undead0@mydomain.com[/email]
Arrival-Date: Fri,  5 Dec 2008 14:33:41 -0500 (EST)

Final-Recipient: rfc822; [email]recipient@otherdomain.org[/email]
Action: failed
Status: 5.5.2
Remote-MTA: dns; smtp.cybergnostic.com
Diagnostic-Code: smtp; 504 5.5.2 <undead0>: Helo command rejected: need
    fully-qualified hostname

[-- Attachment #3: Undelivered Message --]
[-- Type: message/rfc822, Encoding: 7bit, Size: 2.3K --]


In /etc/postfix/main.cf, I've got (among other things):
```
mydomain = mydomain.com
myhostname = undead0
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $mydomain, $myhostname, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```

The first line of my /etc/hosts file is:
```
127.0.0.1       localhost       undead0         undead0.mydomain.com
```

Mail admin isn't really my bag, so any help would be appreciated.

Thanks!

---

### Post by Wayne_V on 2008-12-05
**myhostname (default: see "postconf -d" output)**   The internet hostname of this mail system. The default is to use the fully-qualified domain name from gethostname(). $[myhostname]("http://www.postfix.org/postconf.5.html#myhostname") is used as a default value for many other configuration parameters. 
   Example: 
  [myhostname]("http://www.postfix.org/postconf.5.html#myhostname") = host.domain.tld
myhostname should be fully qualified.  see [B][http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

[/B]

---

### Post by Pitt Stains on 2008-12-07
Thanks, this seems to have solved my problem.  And now I have a useful link should any other postfix issues arise.

---

