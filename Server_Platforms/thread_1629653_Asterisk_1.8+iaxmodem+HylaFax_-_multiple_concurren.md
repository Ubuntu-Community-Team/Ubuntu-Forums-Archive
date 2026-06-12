---
title: "Asterisk 1.8+iaxmodem+HylaFax - multiple concurrent calls"
date: 2010-11-24
forum: Server Platforms
---

### Post by GraysonPeddie on 2010-11-24
Hi. What does this tell me when I get something like this?

```
HylaFAX scheduler on g-server.domainhidden.com: Running
Modem ttyIAX0 (+1 407 218 6927): Initializing server
Modem ttyIAX1 (+1 407 218 6927): Initializing server

JID  Pri S  Owner Number       Pages Dials     TTS Status
23   126 W grayso 329           0:10  2:12         Busy signal detected
12   126 W    fax root          0:1   1:12         No local dialtone
8    125 W    fax gp            0:11  2:12         No local dialtone
6    127 P    fax root          0:1   1:12   00:40 No local dialtone
14   127 B    fax root          0:1   0:12         Blocked by concurrent cal
34   127 B    fax root          0:1   0:12         Blocked by concurrent cal
26   127 B grayso 329           0:10  0:12         Blocked by concurrent cal
30   127 B    fax root          0:1   0:12         Blocked by concurrent cal
10   127 B    fax root          0:1   0:12         Blocked by concurrent cal
20   127 B    fax root          0:1   0:12         Blocked by concurrent cal
17   127 B    fax root          0:1   0:12         Blocked by concurrent cal
13   127 B    fax root          0:1   0:12         Blocked by concurrent cal
27   127 B    fax root          0:1   0:12         Blocked by concurrent cal
22   127 B    fax root          0:1   0:12         Blocked by concurrent cal
28   127 B    fax root          0:1   0:12         Blocked by concurrent cal
37   127 B    fax root          0:1   0:12         Blocked by concurrent cal
9    127 B    fax root          0:1   0:12         Blocked by concurrent cal
16   127 B    fax root          0:1   0:12         Blocked by concurrent cal
29   127 B    fax root          0:1   0:12         Blocked by concurrent cal
19   126 W grayso 329           0:10  2:12         Busy signal detected
15   126 W    fax FaxMaster     0:1   1:12         No local dialtone
11   125 P    fax FaxMaster     0:1   2:12   00:40 No local dialtone
24   127 B    fax root          0:1   0:12         Blocked by concurrent cal
36   127 B    fax root          0:1   0:12         Blocked by concurrent cal
25   127 B    fax root          0:1   0:12         Blocked by concurrent cal
21   127 B    fax root          0:1   0:12         Blocked by concurrent cal
33   127 B    fax root          0:1   0:12         Blocked by concurrent cal
18   127 B    fax root          0:1   0:12         Blocked by concurrent cal
7    127 B    fax root          0:1   0:12         Blocked by concurrent cal
5    126 P    fax root          0:1   2:12   00:39 No local dialtone
32   127 B    fax root          0:1   0:12         Blocked by concurrent cal
35   127 B    fax root          0:1   0:12         Blocked by concurrent cal
31   127 B    fax root          0:1   0:12         Blocked by concurrent cal
```

I'm using Postfix to send incoming faxes to e-mail.

```
mydomain=hiddendomain.com
myhostname=hiddendomain.com
smtp_sasl_auth_enabled=yes
smtp_sasl_password=maps=hash:/etc/postfix/sasl_password
smtp_sasl_security_options=
smtp_tls_security_level=may
relayhost = smtp.comcast.net
myorigin = /etc/mailname
#mydestination = $myhostname, localhost.$mydomain, localhost
mydestination = hiddendomain.com
mynetworks = 127.0.0.0/8 68.63.36.0/22 192.168.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all
transport_maps = hash:/etc/postfix/transport
fax_destination_receipient_limit = 1
```

/etc/postfix/master.cf

```
fax       unix  -       n       n       -       1       pipe
  flags=   user=fax  argv=/usr/bin/faxmail -d -n -N -T ${user}
```

```
hiddendomain.com fax:hylafax:4559
```

I'm using Ubuntu Server 10.04.1 and I have created a user named "fax." What could cause HylaFax to get so many concurrent calls?

---

