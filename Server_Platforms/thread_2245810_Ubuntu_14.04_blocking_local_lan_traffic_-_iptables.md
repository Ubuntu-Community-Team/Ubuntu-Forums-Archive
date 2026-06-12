---
title: "Ubuntu 14.04 blocking local lan traffic - iptables doing this?"
date: 2014-09-26
forum: Server Platforms
---

### Post by scojopa on 2014-09-26
Trying to access https locally - 

Based on the below IPtable rules I thought I was allowing all local LAN traffic to make connections - is DNS setup incorrectly? I have checked my bind files and everything looks normal  - I can route out to the internet without a problem even though syslog shows deny. 

The problem is port 443 is being denied when I try to access https on this server (connection reset or 404I figured the first rule below would allow access - Can someone please lend me some insight on this?

```
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:LOG_AND_DROP - [0:0]
-A INPUT -s 192.168.5.0/24 -i eth0 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 993 -m state --state NEW -m recent --set --name imapssl --rsource
-A INPUT -p tcp -m tcp --dport 993 -m state --state NEW -m recent --update --seconds 10 --hitcount 20 --name imapssl --rsource -j LOG_AND_DROP
-A INPUT -p tcp -m tcp --dport 993 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 587 -m state --state NEW -m recent --set --name imap --rsource
-A INPUT -p tcp -m tcp --dport 587 -m state --state NEW -m recent --update --seconds 10 --hitcount 20 --name imap --rsource -j LOG_AND_DROP
-A INPUT -p tcp -m tcp --dport 587 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 465 -m state --state NEW -m recent --set --name smtps --rsource
-A INPUT -p tcp -m tcp --dport 465 -m state --state NEW -m recent --update --seconds 10 --hitcount 20 --name smtps --rsource -j LOG_AND_DROP
-A INPUT -p tcp -m tcp --dport 465 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 25 -m state --state NEW -m recent --set --name smtp --rsource
-A INPUT -p tcp -m tcp --dport 25 -m state --state NEW -m recent --update --seconds 10 --hitcount 20 --name smtp --rsource -j LOG_AND_DROP
-A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A LOG_AND_DROP -j LOG --log-prefix "iptables deny: " --log-level 7
-A LOG_AND_DROP -j DROP
COMMIT

```

But all of my DNS requests - from my machine (while getting out to the internet) are showing up as denied in syslog

```
Sep 26 08:56:34 mail named[955]: client 192.168.5.105#46713 (clients4.google.com): query (cache) 'clients4.google.com/A/IN' denied
Sep 26 08:57:41 mail named[955]: client 192.168.5.105#43633 (arstechnica.com): query (cache) 'arstechnica.com/A/IN' denied
Sep 26 09:00:50 mail named[955]: client 192.168.5.105#26461 (plus.google.com): query (cache) 'plus.google.com/A/IN' denied
Sep 26 09:01:23 mail named[955]: client 192.168.5.105#5044 (gist.github.com): query (cache) 'gist.github.com/A/IN' denied
Sep 26 09:06:08 mail named[955]: client 192.168.5.105#8327 (help.ubuntu.com): query (cache) 'help.ubuntu.com/A/IN' denied
Sep 26 09:06:36 mail named[955]: client 192.168.5.105#38498 (ubuntuforums.org): query (cache) 'ubuntuforums.org/A/IN' denied
Sep 26 09:08:33 mail named[955]: client 192.168.5.105#6587 (clients4.google.com): query (cache) 'clients4.google.com/A/IN' denied
Sep 26 09:09:01 mail CRON[2504]: (root) CMD (  [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Sep 26 09:12:10 mail named[955]: client 192.168.5.105#38586 (safebrowsing.google.com): query (cache) 'safebrowsing.google.com/A/IN' denied
Sep 26 09:12:59 mail named[955]: client 192.168.5.105#43172 (clients4.google.com): query (cache) 'clients4.google.com/A/IN' denied
```

---

### Post by The Cog on 2014-09-26
I don't see any rules that would drop DNS  in your iptables rules there. You seem to be allowing everything except some TCP stuff.

The syslog messages are coming from **named**, which I guess is a DNS server that you installed. I'm not familiar with it, but I think it is **named** which is choosing to deny name requests from 192.168.5.105, and I think it is probably the named configuration that you need to check. Nothing to do with iptables.

---

### Post by Michael_McKenney on 2014-09-26
Did you open port 443 traffic on the firewall of that server?

---

### Post by scojopa on 2014-09-26
probably not - drrrr

whats the best way to do this? iptables?

---

### Post by scojopa on 2014-09-26
I added 443 but still not working

:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:LOG_AND_DROP - [0:0]
-A INPUT -s 192.168.5.0/24 -i eth0 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -m state --state NEW -m recent --set --name imapssl --rsource
-A INPUT -p tcp -m tcp --dport 443 -m state --state NEW -m recent --update --seconds 10 --hitcount 20 --name imapssl --rsource -j LOG_AND_DROP
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT

---

### Post by Michael_McKenney on 2014-09-26
Which web server are you using?  Did you create the SSL Certificate for it?

---

### Post by scojopa on 2014-09-26
I am using nginx w/ roundcube

I do have an ssl cert installed but that has only been configured for postfix/dovecot config. (its a test server so all thrown on one box).

What would I check in bind? I do have bind9 up an running. forwarders and reverse setup

Do you know where I should look?

---

### Post by The Cog on 2014-09-27
> **scojopa said:**
> What would I check in bind? I do have bind9 up an running. forwarders and reverse setup. Do you know where I should look?
No, sorry. But I did google for named and it is the name of the binary for bind, the DNS name server. It's named that is logging denied messages in syslog, so I am certain that is your problem.

---

### Post by scojopa on 2014-09-28
I had been in all the bind/conf files and all looked good. Finally I just blew it away and rebuilt. All is good. 

Thanks foo your help

---

