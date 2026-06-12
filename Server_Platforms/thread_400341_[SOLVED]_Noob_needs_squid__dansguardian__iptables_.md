---
title: "[SOLVED] Noob needs squid / dansguardian / iptables help"
date: 2007-04-03
forum: Server Platforms
---

### Post by knichel on 2007-04-03
Please help a noob.  I have a server running squid (2.6.5), dansguardian, and iptables.  I want my workstations to use this server as a transparent proxy/web filter.  I have read many how-to's on the subject and have had no success.  I am running Ubuntu 7.04 with Apache as well.

I need to understand how this all works.  So far, what I think I understand is this...

Squid is configured to listen on port 3128 (default) and is currently running.  I have set 
[INDENT]http_port 3128 transparent[/INDENT]

I created an entry in iptables...
[INDENT]iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128[/INDENT]

I added a site to the banned sites for dansguardian
[INDENT]myspace.com[/INDENT]

I see entried in...

[INDENT]tail -f /var/log/squid/access.log[/INDENT] 

as I browse websites, so I know squid is running and watching.

Can someone please help me with this config?

TIA,
Mike

---

### Post by Randy R on 2007-04-07
Usually dansguardian listens on either port 8080 or 8888. you have transparent proxying set to redirect to squid, not to dansguardian.

By the way, you will also need to block direct acess by the computers that you want to use dansguardian to port 3128, or it is very easy to bypass your filter.

---

### Post by knichel on 2007-04-07
Thank you for your reply.  I do not understand entirely.  Are you saying that my students can bypass the filter (dansguardian)?  How? All traffic (http port 80) gets directed through dg/squid.

Mike

---

### Post by Randy R on 2007-04-07
Yes. That is exactly what I am saying. The way it is supposed to work is this:

browser ==> Dansguardian ==> Squid ==> internet

If you do not block port 3128 internally (the squid port), your students can do this:

browser ==> Squid ==> internet

Effectively bypassing the filter.

They can do that by setting up the proxy in the browser. That is user controlled.

---

### Post by knichel on 2007-04-08
What about using iptables to hijack port 3128 as well and redirecting it to DG?  Would that be sufficient?

Mike

---

### Post by Randy R on 2007-04-09
I believe you can setup a squid acess control list (ACL) in /etc/squid/squid.conf to prevent access by any computer other than the one running dansguardian or to localhost if running on the same machine. Do not redirect 3128 to dansguardian. That would create a loop. I have not tried it but it will not work.

---

### Post by knichel on 2007-04-10
OK, thanks for the help.  I will check this configuration when I return back to school after our spring break.  I appreciate the assistance.


--
Mike

---

### Post by Randy R on 2007-04-10
Happy to help

---

### Post by knichel on 2007-04-17
Thanks to both for the reply. I returned to work today and un-installed squid, dansguardian and iptables, just to get a clean start.
I read the how-to's and configured as follows...

Squid :
installed and added
http_port 3128 transparent
visible_hostname myServer
acl myNet src 192.168.6.0/24
http_allow myNet
listens on 3128

Dansguardian :
added some addresses to the bannedsitelist
commented the line saying UNCONFIGURED
left other stuff alone
listens on 8080
forwards to 3128 for proxy

IPTables :
installed and added
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080

Here is where I stand...

From a workstation I have the gateway set as the squid,dg,iptables box. If I set the proxy settings in the browser to the ip of the squid box port 8080, I can browse fine and the things I want blocked are blocked. If I remove the proxy settings, then I cannot browse. I do not get any entries in the squid/access.log file when I view with tail -f.

So, it appears that the proxy and filter are working fine. Something must be missing/wrong with my iptables entries?

Any ideas?

Mike

---

