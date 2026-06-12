---
title: "fail2ban not working postfix"
date: 2010-09-28
forum: Server Platforms
---

### Post by SlugSlug on 2010-09-28
Hi

My fail2ban won't block relay attempts (it does block ssh)
can anyone help?

mail.log contains lots of
```
NOQUEUE: reject: RCPT from 118-167-6-196.dynamic.hinet.net[118.167.6.196]: 554 5.7.1 <333@fgytry.myip.org>: Relay access denied
```

jail.conf
```
[postfix]

enabled  = true
port     = smtp,ssmtp
filter   = postfix
logpath  = /var/log/mail.log
maxretry = 3
```

filter.d/postfix.conf 
```
failregex = reject: RCPT from (.*)\[<HOST>\]: 554
```

Thanks

---

### Post by SlugSlug on 2010-09-30
~bump~

---

### Post by lisati on 2010-09-30
I get similar messages in my server's logs regularly. It looks like the messages are being blocked. Most of the time I've found that the offending IP address is listed in one or more of the DNSBL lists run by u[ceprotect]("http://www.uceprotect.net/") and other DNSBL lists, so on my system they'd be blocked even if relay access wasn't being blocked.

---

### Post by SlugSlug on 2010-09-30
Ahh Ok never really thought about a block list,

But I'd like fail2ban to block attempts even if they get rejected via ISP's relay -- just to stop them going through my server really.

---

### Post by SlugSlug on 2010-10-22
Solved with

cat /etc/fail2ban/filter.d/postfix.conf
```
# Fail2Ban configuration file
#
# Author: Cyril Jaquier
#
# $Revision: 728 $
#

[Definition]

# Option:  failregex
# Notes.:  regex to match the password failures messages in the logfile. The
#          host must be matched by a group named "host". The tag "<HOST>" can
#          be used for standard IP/hostname matching and is only an alias for
#          (?:::f{4,6}:)?(?P<host>[\w\-.^_]+)
# Values:  TEXT
#
#failregex = reject: RCPT from (.*)\[<HOST>\]: 554
failregex = reject: RCPT from (.*)\[<HOST>\]: 550 5.1.1
            reject: RCPT from (.*)\[<HOST>\]: 450 4.7.1
            reject: RCPT from (.*)\[<HOST>\]: 554 5.7.1

# Option:  ignoreregex
# Notes.:  regex to ignore. If this regex matches, the line is ignored.
# Values:  TEXT
#
```

and 

 cat /etc/fail2ban/filter.d/sasl.conf
```
# Fail2Ban configuration file
#
# Author: Yaroslav Halchenko
#
# $Revision: 728 $
#

[Definition]

# Option: failregex
# Notes.: regex to match the password failures messages in the logfile. The
#          host must be matched by a group named "host". The tag "<HOST>" can
#          be used for standard IP/hostname matching and is only an alias for
#          (?:::f{4,6}:)?(?P<host>[\w\-.^_]+)
# Values: TEXT
#
#failregex = (?i): warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed(: [A-Za-z0-9+/]*={0,2})?$
#failregex = (?i: warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed: \w+
failregex = (?i): warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed


# Option:  ignoreregex
# Notes.:  regex to ignore. If this regex matches, the line is ignored.
# Values:  TEXT
#
ignoreregex =
```

---

### Post by retexe on 2012-05-28
I have done what you said with these configurations:

jail.local:
```
[postfix]
enabled  = true
port     = smtp,ssmtp
filter   = postfix
logpath  = /var/log/mail.log
```

postfix.conf:
```
failregex = reject: RCPT from (.*)\[<HOST>\]: 550 5.1.1
            reject: RCPT from (.*)\[<HOST>\]: 450 4.7.1
            reject: RCPT from (.*)\[<HOST>\]: 554 5.7.1
ignoreregex =
```


fail2ban.log:
```
2012-05-28 13:03:24,217 fail2ban.jail   : INFO   Jail 'postfix' started
```

mail.log
```
May 28 13:15:28 myserver postfix/smtpd[2740]: NOQUEUE: reject: RCPT from unknown[1.2.3.4]: 550 5.1.1 <something1@myserver>: Recipient address rejected: User unknown in local recipient table; from=<mail_address1> to=<something1@myserver> proto=ESMTP helo=<Static-_some_IP>
May 28 13:15:28 myserver postfix/smtpd[2740]: NOQUEUE: reject: RCPT from unknown[1.2.3.4]: 550 5.1.1 <something2@myserver>: Recipient address rejected: User unknown in local recipient table; from=<mail_address2> to=<something2@myserver> proto=ESMTP helo=<Static-_some_IP>
May 28 13:15:28 myserver postfix/smtpd[2740]: NOQUEUE: reject: RCPT from unknown[1.2.3.4]: 550 5.1.1 <something3@myserver>: Recipient address rejected: User unknown in local recipient table; from=<mail_address3> to=<something3@myserver> proto=ESMTP helo=<Static-_some_IP>
May 28 13:15:29 myserver postfix/smtpd[2740]: NOQUEUE: reject: RCPT from unknown[1.2.3.4]: 550 5.1.1 <something4@myserver>: Recipient address rejected: User unknown in local recipient table; from=<mail_address4> to=<something4@myserver> proto=ESMTP helo=<Static-_some_IP>
May 28 13:15:29 myserver postfix/smtpd[2740]: NOQUEUE: reject: RCPT from unknown[1.2.3.4]: 550 5.1.1 <something5@myserver>: Recipient address rejected: User unknown in local recipient table; from=<mail_address5> to=<something5@myserver> proto=ESMTP helo=<Static-_some_IP>
```

iptables:
```
fail2ban-postfix  tcp  --  anywhere             anywhere             multiport dports smtp,ssmtp
```

Still, fail2ban doesn't seem to work for the postfix rule.
Any ideas why?

---

