---
title: "Troubleshooting a system crash"
date: 2005-08-31
forum: Server Platforms
---

### Post by Moif on 2005-08-31
I have a server setup on a laptop.  It is being used to sniff traffic at a remote site.  It has gone down twice in a week in a half.  I have looked at the /var/log/messages and syslog and I don't see any errors.  It just says --Mark-- --Mark-- and then shows the messages of it booting up.  The weird thing is the machine doesn't lock up it just turns off.  I thought it might be suspend but it was up for a week.  I thought it might be overheating so I started monitoring the temp and it is only at 42 degrees C.  I'm outta ideas on how to troubleshoot and I was looking for suggestions.  Thanks for your help

---

### Post by Moif on 2005-09-02
I did some searching on the web and I think I am going to try setting up some snmp-traps and alter the syslog to log everything debug priority level and higher.  I'll post here to let you know how it works out for me.  Just incase anyone else is having problems like this.

---

### Post by Moif on 2005-09-12
Well this hasn't helped out like I had hoped.  The syslog still comes up clean and the snmp-traps having yeilded anything.  Don't know what else to do.   ](*,)

---

### Post by PokerFacePenguin on 2005-12-08
[QUOTE=Moif]I have a server setup on a laptop.  It is being used to sniff traffic at a remote site.  It has gone down twice in a week in a half.  I have looked at the /var/log/messages and syslog and I don't see any errors.  It just says --Mark-- --Mark-- and then shows the messages of it booting up.  The weird thing is the machine doesn't lock up it just turns off.  I thought it might be suspend but it was up for a week.  I thought it might be overheating so I started monitoring the temp and it is only at 42 degrees C.  I'm outta ideas on how to troubleshoot and I was looking for suggestions.  Thanks for your help[/QUOTE]


The exact same thing just happened to me....twice.  Both times I was using DVD shrink under wine.  It has got me really curious.  I replaced the hard drive in my laptop several months ago and it has run like a top ever since....until these two weird shutdowns...no weird errors...just powers off.

Did you get anywhere with this?

---

### Post by TheDanMan on 2005-12-08
I'd be more suspicious of hardware problems. I've never had a system, even windows, just reboot on me that didn't end up being a power supply or another physical issue.

---

