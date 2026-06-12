---
title: "Postfix sasl + fail2ban"
date: 2015-05-16
forum: Server Platforms
---

### Post by rhandy2 on 2015-05-16
I have lots of logs like this

> May 16 18:42:42 example postfix/smtpd[2425]: connect from unknown[64.76.125.86]
May 16 18:42:47 example postfix/smtpd[2425]: warning: unknown[64.76.125.86]: SASL LOGIN authentication failed: authentication failure
May 16 18:42:48 example postfix/smtpd[2425]: disconnect from unknown[64.76.125.86]
May 16 18:46:08 example postfix/anvil[2427]: statistics: max connection rate 1/60s for (smtp:64.76.125.86) at May 16 18:42:42
May 16 18:46:08 example postfix/anvil[2427]: statistics: max connection count 1 for (smtp:64.76.125.86) at May 16 18:42:42
May 16 18:46:08 example postfix/anvil[2427]: statistics: max cache size 1 at May 16 18:42:42

I have this on fail.conf

> [sasl]
enabled  = false
port     = smtp,ssmtp,submission,imap2,imap3,imaps,pop3,pop3s
filter   = postfix-sasl

logpath  = /var/log/mail.log


And this on postfix-sasl.conf

> [INCLUDES]
before = common.conf
[Definition]
_daemon = postfix/smtpd
failregex = ^%(__prefix_line)swarning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed(: [ A-Za-z0-9+/]*={0,2})?\s*$
   ^%(__prefix_line)swarning: [-._\w]+\[<HOST>\]: SASL  authentication failed(: [ A-Za-z0-9+/]*={0,2})?\s*$
ignoreregex =


But is not working

---

### Post by corti-nico on 2015-05-16
I think that you're having problems inside your sasl.conf, try this:

```

# Fail2Ban configuration file#
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
failregex = (?i): warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed: \w


# Option:  ignoreregex
# Notes.:  regex to ignore. If this regex matches, the line is ignored.
# Values:  TEXT
#
ignoreregex = 

```

After this you can try if filter work invoking
```

fail2ban-regex /var/log/mail.log /etc/fail2ban/filter.d/sasl.conf

```
If you fine incriminated Ip in the output then you're done ;)

---

### Post by rhandy2 on 2015-05-16
Ok!

I think is working!

The configuration I use before is the original config!

Running tests
=============


Use   failregex file : /etc/fail2ban/filter.d/postfix-sasl.conf
Use         log file : /var/log/mail.log




> Results
=======


Failregex: 483 total
|-  #) [# of hits] regular expression
|   1) [483] (?i): warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed: \w
`-


Ignoreregex: 0 total


Date template hits:
|- [# of hits] date format
|  [13424] MONTH Day Hour:Minute:Second
`-


Lines: 13424 lines, 0 ignored, 483 matched, 12941 missed
Missed line(s):: too many to print.  Use --print-all-missed to print all 12941 lines




---

### Post by rhandy2 on 2015-05-17
I test > fail2ban-regex /var/log/mail.log /etc/fail2ban/filter.d/sasl.conf

And find it more 157 entries.

 I add # ufw deny from 64.76.125.86, but ufw still AUDIT .

> grep 64.76.125.86 /var/log/ufw.log


> kernel: [274773.427931] [UFW AUDIT] IN=eth0 OUT= MAC=e0:cb:4e:5e:85:1c:a4:b1:e9:b1:45:26:08:00 SRC=64.76.125.86 DST=10.x.x.x LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=15857 DF PROTO=TCP SPT=3921 DPT=25 WINDOW=65535 RES=0x00 SYN URGP=0



more logs in var/log/mail.log

> May 16 18:42:42 example postfix/smtpd[2425]: connect from unknown[64.76.125.86]
May 16 18:42:47 example postfix/smtpd[2425]: warning: unknown[64.76.125.86]: SASL LOGIN authentication failed: authentication failure
 May 16 18:42:48 example postfix/smtpd[2425]: disconnect from unknown[64.76.125.86]
 May 16 18:46:08 example postfix/anvil[2427]: statistics: max connection rate 1/60s for (smtp:64.76.125.86) at May 16 18:42:42
 May 16 18:46:08 example postfix/anvil[2427]: statistics: max connection count 1 for (smtp:64.76.125.86) at May 16 18:42:42
 May 16 18:46:08 example postfix/anvil[2427]: statistics: max cache size 1 at May 16 18:42:42

No REVERSE DNS.

any one could help?

---

### Post by corti-nico on 2015-05-18
> **rhandy2 said:**
> 
 I add # ufw deny from 64.76.125.86, but ufw still AUDIT .


Sorry but i have not understand your question :(
Don't forget that sasl.conf check only file /var/log/mail.log
If you want to check other files you have to create other .conf files and/of jails.

> 
No REVERSE DNS.


Why you're insterested in reverse dns?

---

### Post by rhandy2 on 2015-05-19
It´s strange but I just restart Ufw. And attack stop! :-)

---

### Post by corti-nico on 2015-05-20
> **rhandy2 said:**
> It´s strange but I just restart Ufw. And attack stop! :-)
Fine :lolflag:

---

### Post by rhandy2 on 2015-06-02
Hello!!

How I can configure fail2ban to ban this actions

>  postfix/smtpd[27536]: warning: hostname client-200.106.118.149.speedy.net.pe does not resolve to address 200.106.118.149: Name or service not known


---

