---
title: "Issues with fail2ban and 9.04"
date: 2009-06-06
forum: Server Platforms
---

### Post by x404x on 2009-06-06
Hello everyone, this being my first post I wanted to start off with a quick hello before jumping in  :p

I'm running 9.04 server in a LAMP config, open ports being 22 and 80. Im running fail2ban on the server with the following config:
```
[ssh]

enabled = true
port    = ssh
filter  = sshd
logpath  = /var/log/auth.log
maxretry = 3


[ssh-ddos]

enabled = true
port    = ssh
filter  = sshd-ddos
logpath  = /var/log/auth.log
maxretry = 3

#
# HTTP servers
#

[apache]

enabled = true
port    = http,https
filter  = apache-auth
logpath = /var/log/apache*/*error.log
maxretry = 4

# default action is now multiport, so apache-multiport jail was left
# for compatibility with previous (<0.7.6-2) releases
[apache-multiport]

enabled   = true
port      = http,https
filter    = apache-auth
logpath   = /var/log/apache*/*error.log
maxretry  = 4

[apache-noscript]

enabled = true
port    = http,https
filter  = apache-noscript
logpath = /var/log/apache*/*error.log
maxretry = 4

[apache-overflows]

enabled = true
port    = http,https
filter  = apache-overflows
logpath = /var/log/apache*/*error.log
```The server has been up for about 24 hours now and I pulled the following out of /var/log/apache2/access.log:

```
221.223.44.70 - - [05/Jun/2009:23:55:26 -0400] "\xef$0\xc5\"\x0e\xcd\xfb\xd6\xd3d1\x80\x1e\x1a\x91\x1f\x8d\r\xc8\x88\xe3\xf7\x954y\xea" 400 341 "-" "-"
222.81.96.140 - - [05/Jun/2009:23:55:29 -0400] "\x13BitTorrent protocolex" 400 341 "-" "-"
222.81.96.140 - - [05/Jun/2009:23:55:46 -0400] "\x13BitTorrent protocolex" 400 341 "-" "-"
222.81.96.140 - - [05/Jun/2009:23:56:04 -0400] "\x13BitTorrent protocolex" 400 341 "-" "-"
222.81.96.140 - - [05/Jun/2009:23:56:20 -0400] "\x13BitTorrent protocolex" 400 341 "-" "-"
222.81.96.140 - - [05/Jun/2009:23:56:36 -0400] "\x13BitTorrent protocolex" 400 341 "-" "-"
221.223.44.70 - - [05/Jun/2009:23:56:56 -0400] "8\x9aN" 200 16739 "-" "-"
222.81.96.140 - - [05/Jun/2009:23:56:59 -0400] "\x13BitTorrent protocolex" 400 341 "-" "-"
222.81.96.140 - - [05/Jun/2009:23:57:21 -0400] "\x13BitTorrent protocolex" 400 341 "-" "-"
222.81.96.140 - - [05/Jun/2009:23:57:44 -0400] "\x13BitTorrent protocolex" 400 341 "-" "-"
221.223.44.70 - - [05/Jun/2009:23:58:31 -0400] "j\xfb\x99Nc\x9a\xfd\x8e4\x16\xbf\xe6\x10h\xad\xe8\x01;)\xa6M\x84\x8d\xab\xa5\xb5\xc6\x0c\xbak\xceS\xfd\xb8\xd7\xf7\xc4'U\\\xea\x17\xb7%\xbb\x14\xed\x11\x95%t\x95\xba\x9c\x84.E\x17\x1e\xe0i\x06\xd4\x86\xbf\xd1\t\xd1\x06\xa0\xccF\x8c\xc6\xe9\xab\x18\x95\xb6\xafg\xe0\x0f\xd8#\rK\x90b\x12B\x16\xb4\xb9TP\xe4\xc7\x96\xf5\xe3\xa7\x9e\"\xcc\xe0^\xe5\xba\xacup\xea\xe8\x9b\xa9z\xc8\x88}q\xca\x12w" 400 416 "-" "-"
221.223.44.70 - - [06/Jun/2009:00:00:07 -0400] "%e(\xfb\xa8\x83#7\xfb\x0er\xbf\xcb2\xb0CVL\x7f\riK<eN\xe97\xc5\xa7`\xa7\xac\x8b\x10\xa1C\xe8\xe2\x88" 400 341 "-" "-"
221.223.44.70 - - [06/Jun/2009:00:02:17 -0400] "\x8d$\x96a\xf4\xc8\x8bby*\xca\x19\xd8\x8bA\tw\xfe\\\xc6\x933\xc2\x07\x1e\xd9\x16\x87\xa6\x0f$\xbd\xda\xe5\xb2@\x8b\x17\xd2\x07\x99\x02G|\xed\x03\xf0\x18+\xa2\xd8\x14R\x1b\x1e\xcc9\xf8\xe78~4\x18\x04\xfcgQ\xe4\xf6?" 400 341 "-" "-"
```So when I checked /var/log/fail2ban.log I'm seeing the following:

```
2009-06-06 00:23:41,744 fail2ban.filter : INFO   Added logfile = /var/log/apache2/error.log
2009-06-06 00:23:41,746 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,748 fail2ban.filter : INFO   Set maxRetry = 4
2009-06-06 00:23:41,750 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,752 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,755 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,756 fail2ban.filter : INFO   Set findtime = 600
2009-06-06 00:23:41,759 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,760 fail2ban.actions: INFO   Set banTime = 600
2009-06-06 00:23:41,762 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,765 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,768 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,771 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,774 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,776 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,779 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,782 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,785 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,788 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,791 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,793 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,796 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,856 fail2ban.jail   : INFO   Jail 'apache-noscript' started
2009-06-06 00:23:41,865 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:41,976 fail2ban.jail   : INFO   Jail 'ssh-ddos' started
2009-06-06 00:23:41,979 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:42,079 fail2ban.jail   : INFO   Jail 'apache-multiport' started
2009-06-06 00:23:42,082 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:42,179 fail2ban.jail   : INFO   Jail 'apache-overflows' started
2009-06-06 00:23:42,182 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:42,249 fail2ban.jail   : INFO   Jail 'ssh' started
2009-06-06 00:23:42,307 fail2ban.server : ERROR  Unexpected communication error
2009-06-06 00:23:42,475 fail2ban.jail   : INFO   Jail 'apache' started
2009-06-06 00:23:42,492 fail2ban.server : ERROR  Unexpected communication error
```After seeing the fail2ban log I decided to manually drop the two IPs in iptables

```
DROP       all  --  221.220.47.154       anywhere            
DROP       all  --  221.223.44.70        anywhere
```I checked the version of python installed with 9.04 and it's 2.6 - Installing 2.5 and editing /usr/bin/fail2ban-server  with the following:

```

#!/usr/bin/python

to

#!/usr/bin/python2.5
```And then restarting fail2ban solves this issue. I hope this helps anyone with issues on 9.04 server and keeping the crackers out. I'm looking forward to contributing what I can to the community, I hope this is a decent first post =)

---

### Post by Rotzooi on 2009-06-26
Thanks a lot, saved my day

---

### Post by HermanAB on 2009-06-27
I prefer using a general purpose solution: An iptables rate limiting filter.

It doesn't actually lock anyone out, it just slows things down so much that any DOS or brute force attack becomes infeasible.

The advantage is that it is an extremely simple one line rule and you cannot lock yourself out by accident.

---

### Post by x404x on 2009-07-03
> **HermanAB said:**
> I prefer using a general purpose solution: An iptables rate limiting filter.

Care to elaborate? I understand the concept, can you provide an example?

---

