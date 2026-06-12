---
title: "ddclient won't update"
date: 2006-03-27
forum: Server Platforms
---

### Post by laffer on 2006-03-27
running ddclient for dyndns.com

on the syslog there's this message:

Mar 27 21:31:49 localhost ddclient[10908]: FAILED:   updating luisguerreiro.ath.cx: nohost: The hostname specified does not exist in the database

how do I solve this?

here's my ddclient.conf settings:
# Basic configuration file for ddclient
#
# /etc/ddclient.conf

daemon=600
syslog=yes
pid=/var/run/ddclient.pid
use=web, web=checkip.dyndns.org/, web-skip='IP Address'
#use=linksys, fw=linksys, fw-login=admin, fw-password=admin
login=xxxxxx
password=xxxxxxx
protocol=dyndns2
server=members.dyndns.org
wildcard=YES
luisguerreiro.ath.cx

---

### Post by HazelRah on 2006-03-28
[QUOTE=laffer]running ddclient for dyndns.com

on the syslog there's this message:

Mar 27 21:31:49 localhost ddclient[10908]: FAILED:   updating luisguerreiro.ath.cx: nohost: The hostname specified does not exist in the database

how do I solve this?

here's my ddclient.conf settings:
# Basic configuration file for ddclient
#
# /etc/ddclient.conf

daemon=600
syslog=yes
pid=/var/run/ddclient.pid
use=web, web=checkip.dyndns.org/, web-skip='IP Address'
#use=linksys, fw=linksys, fw-login=admin, fw-password=admin
login=xxxxxx
password=xxxxxxx
protocol=dyndns2
server=members.dyndns.org
wildcard=YES
luisguerreiro.ath.cx[/QUOTE]

Did you remember to put single quotes for the password so it's **password='xxxxxx'**.  Not sure if it makes a difference but other than that, your ddclient.conf looks just like mines.

---

### Post by truthiness on 2006-11-18
Here's something else to check.

DynDNS has 3 types of DNS service: dynamic, static, & custom. (Dynamic is the default type used by ddclient.) If you do not specify the correct service, you'll get this error.

Try this. Log into your account at [www.dyndns.com](www.dyndns.com). Click on "My Services", then look for your host "luisguerreiro.ath.cx". There should be a column labeled "DNS Service", what does it say?

If it says "Dynamic DNS", then your existing config should work. 

But if it says "Static DNS" then replace the line "luisguerreiro.ath.cx" with

[INDENT]static=yes, luisguerreiro.ath.cx[/INDENT]

If it says "Custom DNS", then replace the line "luisguerreiro.ath.cx" with
[INDENT]custom=yes, luisguerreiro.ath.cx[/INDENT]

BTW, if you have multiple hosts you can enter them like:
[INDENT]luisguerreiro1.homedns.org,luisguerreiro2.homedns.org
static=yes, luisguerreiro3.ath.cx,luisguerreiro4.ath.cx
custom=yes, luisguerreiro.ath.cx,luisguerreiro2.ath.cx[/INDENT]

Hope that helps.

---

### Post by perspectoff on 2007-07-02
If you don't have a hostname in the database (meaning at dyndns.com), it means you either didn't register one at Dyndns.com, or it has expired due to inactivity.

Log back on to dyndns.com and check your account.

---

