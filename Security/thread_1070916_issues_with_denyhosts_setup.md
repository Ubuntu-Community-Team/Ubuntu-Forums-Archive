---
title: "issues with denyhosts setup"
date: 2009-02-15
forum: Security
---

### Post by Cyked on 2009-02-15
So after installing denyhosts it is pretty much set up as default.  I have changed the listing port for SSH, I've connected from an IP outside my network with 5 failed login attempts.  The IP shows up in .deny like it should.  I have set my denyhosts.conf file to purge after 1m.  I stop denyhosts, run the purge commange, and start it up again.  I have done this several times but the blocked IP still shows up in .deny.  

Is there an issue with purging .deny?

---

### Post by bodhi.zazen on 2009-02-15
See if these threads help :

[http://ubuntuforums.org/showthread.php?t=905800](http://ubuntuforums.org/showthread.php?t=905800)

[http://ubuntuforums.org/showthread.php?t=361053](http://ubuntuforums.org/showthread.php?t=361053)

---

### Post by HermanAB on 2009-02-15
Howdy,

I prefer things thtat work and are zero maintenance.  Iptables nowadays has a very nice rate limit module which can prevent all kinds of abuse:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

Cheers,

Herman

---

### Post by Cyked on 2009-02-19
What do I have to specify to accept?  If I accept my ssh port and www and add the drop entry i have no network connection?

---

### Post by bodhi.zazen on 2009-02-20
Order of rules in iptables is important. 

What rules did you add exactly ?

See this link to see if it helps :

[http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

---

### Post by Cyked on 2009-02-20
I added my port for ssh, www, and for adapter lo, then added the drop for the rest.

Checking your link now....

---

### Post by ushills on 2009-02-20
I had the same issue and had to manually edit out the ip address from /etc/hosts.deny.

This may be what you need to do.

---

### Post by Cyked on 2009-03-07
I figure I'll just post here since I have an open thread.  Today from work I was screwing around on my system in putty was looking for info on killing sessions.  I heard one the unix guys a work talking about kill 9 commands on a conf. call for an issue I was working and started researching.

So I did ps -aux | grep ssh to see what was open because I know since I have set up the system I have had putty sessions lock up on me and wanted to look into.  So I say from the cmd above several sessions that from my perspective were open, so I did a kill -9 command on a few PIDs.  I purposefully killed the session I knew was my current ssh session and was booted, and now can not ssh in.  From work the session just times out in putty, from home I get a server unexpected closed session error.  I was running hostsdeny but that has been stopped for a while now.  I am using iptables, but every entry for that is empty now.

Not sure what is going on.  I have rebooted the system since this start, and what I have described above is the very last thing I did before this issue started.  Any advice?

Thanks again in advance.  I guess you have to break sh*t to leave stuff, right?

---

### Post by cariboo on 2009-03-07
If you use kill -9 to stop a service, it won't restart on its own, you have to restart the service manually. So in other words if you use kill -9 from a remote computer, you have to manually restart openssh-server in order to access the computer again.

Jim

---

