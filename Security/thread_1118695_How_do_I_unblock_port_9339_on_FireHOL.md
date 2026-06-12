---
title: "How do I unblock port 9339 on FireHOL?"
date: 2009-04-07
forum: Security
---

### Post by bledsoe on 2009-04-07
Hi,

I recently installed dansguardian/tinyproxy/firehol on my Ubuntu system, and am generally pretty pleased with it.  One problem I've discovered (actually, my teenage son discovered it) is in accessing the "Texas Hold 'Em" app on myspace.  The app appears to load, then sits for about 30 seconds or so, then displays the following message:

[INDENT]Connection Timeout.
The server may be down for maintenance.
Your firewall may be blocking access to port 9339.[/INDENT]

The app works fine with FireHOL disabled, and I've scoured the online FireHOL documentation but it's greek to me.  I also posted to the FireHOL forum on sourceforge, but have not received a response.  Surely this can't be a difficult thing to fix.

My firehol.conf file looks like this (it was taken from a HOWTO on one of the Ubuntu forums): 
 
[INDENT]version 5 
 
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP 
 
transparent_squid 8080 "root root" 
 
interface any world 
policy drop 
protection strong 
client all accept 
server cups accept 
[/INDENT]
 
Any help greatly appreciated,

---

### Post by Joeb454 on 2009-04-08
Please don't create duplicate threads.
Other thread here: [http://ubuntuforums.org/showthread.php?t=1119651](http://ubuntuforums.org/showthread.php?t=1119651)

---

