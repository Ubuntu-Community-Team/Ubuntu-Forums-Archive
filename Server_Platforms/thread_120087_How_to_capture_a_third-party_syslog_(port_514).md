---
title: "How to capture a third-party syslog (port 514)?"
date: 2006-01-20
forum: Server Platforms
---

### Post by jimwillsher on 2006-01-20
Hi all,

Looking for advice. I have a DrayTek router, and I want to log the events which it generates. It can send events to a syslog daemon on port 514, the norm. Under RedHat you follow these instructions, taken from [http://www.draytek.co.uk/forum/viewtopic.php?t=6056&highlight=linux](http://www.draytek.co.uk/forum/viewtopic.php?t=6056&highlight=linux)
:

```

Posted: Mon Aug 01, 2005 10:47 am    Subject: howto syslog on redhat linux server (with/without iptables)   

--------------------------------------------------------------------------------
 
Hi, 

if you don't want to use wallwatcher on windows, you can also use your linux machine's syslog service. This is how to do it on a RedHat 9 machine but should be very similar on other distributions: 

Modify /etc/syslog.conf to include the following: 

local0.* /var/log/router-firewall.log 
local1.* /var/log/router-vpn.log 
local2.* /var/log/router-user.log 
local3.* /var/log/router-call.log 
local4.* /var/log/router-wan.log 
local5.* /var/log/router-adsl.log 

Modify /etc/sysconfig/syslog so that SYSLOGD_OPTIONS includes "-r -x": 

SYSLOGD_OPTIONS="-m 0 -r -x" 

If you use an iptables firewall, port 514 needs to be opened to udp traffic, so modify /etc/sysconf/iptables and insert the following line (make sure RH-Lokkit-0-50-INPUT is the correct filter name and replace the ip address with the address of the router, the following is an example): 

-A RH-Lokkit-0-50-INPUT -s 192.168.0.1 -p udp -m udp --dport 514 -j ACCEPT 

Once all is done, restart syslog (and iptables): 


```


I can happily update /etc/syslog.conf to add the new entries, but I don't have /etc/sysconfig/syslog or a corresponding syslog service to restart. Can anyone tell me where I should be looking?

I'm running Breezy with no GUI.

Many thanks!


Jim

---

### Post by kdw on 2006-01-21
[QUOTE=jimwillsher]
I can happily update /etc/syslog.conf to add the new entries, but I don't have /etc/sysconfig/syslog or a corresponding syslog service to restart. Can anyone tell me where I should be looking?
[/QUOTE]

```
/etc/init.d/sysklogd {start|stop|reload|restart|force-reload|reload-or-restart}
```

All daemon scripts are in /etc/init.d/.  More info in /etc/init.d/README, which leads to more info ;).

HTH, HAND.

Oops, forgot to add this note from sysklogd script:
#   For remote UDP logging use SYSLOGD="-r"

So you want to edit that file directly with vim or whatever your favorite console text editor is.

---

### Post by jimwillsher on 2006-01-25
Hi kdw,

Really sorry for not acknowledging your post - the default when signing up to this forum is NOT to subscribe to threads, so I never saw your reply.

But I have now, and I'm pleased to report that the logging is working perfectly, thank you!

All I need to do now is work out how to write a corresponding .conf file for logwatch....


Cheers,


Jim

---

### Post by SuperMike on 2006-01-26
This is sort of related to at least your subject line, but I know it's unrelated to the body of your request. However, I think it's important enough to share. I just wanted to say that I downloaded Snare Agent for Windows off of snare.sourceforge.net and used that to forward my Windows event logs to my central Linux syslog server (Ubuntu-based, of course). Now I can write Bash scripts that watch this syslog file and email me certain alerts. I can also put up a web page with all the logs gathered together. And I can even build a web page that filters the noise events out of the logs that I care nothing about.

---

