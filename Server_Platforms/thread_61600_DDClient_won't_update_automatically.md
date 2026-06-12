---
title: "DDClient won't update automatically"
date: 2005-09-01
forum: Server Platforms
---

### Post by wildasIwanabe on 2005-09-01
Hi,

I managed to install ddclient and it appears to update the IP when I enter
[COLOR=RoyalBlue]ddclient -daemon=0 -debug -verbose -noquiet [/COLOR] 

But it does not update automatically.  Is there something else I need to do? 

This is my configuration in ddclient.conf
[COLOR=RoyalBlue]daemon=300
syslog=yes
mail=root
pid=/var/run/ddclient.pid

use=web
protocol=dyndns2
server=members.dyndns.org
login=xxxx
password=xxx

server=members.dyndns.org, protocol=dyndns2, zzz.ath.cx[/COLOR]

---

### Post by Lofticus on 2005-12-02
My ddclient.conf looks like this:

pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=checkip.dyndns.org/, web-skip='IP Address'
server=members.dyndns.org
login=myusername
password=mypassword
myhost.dyndns.org

In your case there isn't entered your desired web address... like xyz.dyndns.org (that would be myhost.dyndns.org in my conf) 

also I don't think you need server=members.dyndns.org, protocol=dyndns2, zzz.ath.cx again, I think you can cut it out.

try my conf, maybe it will help

---

