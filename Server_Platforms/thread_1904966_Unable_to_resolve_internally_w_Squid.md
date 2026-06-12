---
title: "Unable to resolve internally w/ Squid"
date: 2012-01-05
forum: Server Platforms
---

### Post by sheld0r on 2012-01-05
I've heard a lot of good things about Squid, so I decided to install Squid 2.7(stable) on Ubuntu 11.10. I thought I would post on the forums here and get some help. I'm having some trouble with internal DNS.  For some reason I get the following error:

[B]ERROR
The requested URL could not be retrieved.
Unable to determine IP address from hose name "server name goes here"
The DNS returned:
Server Failure: The anem server was unable to process this query.[/B]

I've added dns_nameservers 192.168.100.237 which is my DNS server in the squid.conf.  I can resolve externally and get out to the Internet just fine.  

Am I missing a configuration somewhere?

*Edit* I claimed that the squid mailing list wasn't helpful, but I feel I made that assessment to quickly, a little after elico responded I got a couple responses on the mailing lists.  Thanks.

---

### Post by elico on 2012-01-05
i'm a member of squid-users list and i havnt seen you asking a question..
where did you added the dns name server at? client? server?
if it's saying it couldn't resolbe ip address it can be caused by config or other options.
try squid3 and not the old 2.7
make sure that when are doing nslookup on the sever you are getting a result..
add some more info on the server.
is this an intranet or internet server?

---

### Post by sheld0r on 2012-01-06
Heya elico,

I added the dns nameserver on the server.  As far as the config goes, I didn't do much but add the DNS nameservers.  

When installed Squid I did it through Ubuntu via the cli, so I'm not sure why it pulled the older version.  I will look into upgrading it to squid3.

nslookup works for external addresses, but not for internal.  I get a SERVFAIL from the specified DNS server I added.  When you say add more info on the server, what exactly do you mean?  This is an Internet server. 

Also, in further troubleshooting on my part I'm trying to get some logs going here, but I'm not able to.  What I've done is remove the comment from debug_options ALL,1 in the squid.conf.  Will this enable the debug_options?  At the moment I've entered the command tail -f cache.log to see the logs in real time as I attempt to browse a site.  Am I on the right path?

---

### Post by SeijiSensei on 2012-01-06
> **sheld0r said:**
> nslookup works for external addresses, but not for internal.  I get a SERVFAIL from the specified DNS server I added.

Is that server authoritative for the domain?  How about the *reverse* domain(s), which matter when resolving IPs into names?  If you run the command "host 10.1.1.1" replacing that IP with a valid one on your internal network, do you get a reply?  If not, I doubt you have configured reverse resolution for the .in-addr.arpa domains related to your network addresses. 

If you were using the 10.1.1.0/24 network, you'd need an entry in named.conf for "zone 1.1.10.in-addr.arpa" and a zone file with the IP-to-hostname mappings for that zone.

---

### Post by elico on 2012-01-07
couple of thigs:
is this server is for internal usage? means for web servers over the internet or over the internal network?
if it's for internal network also you need to be able to resolve the local network addresses using a dns server (local one)and this will solve the problem.
more info on the  server is network infrastructure and dns lookups.
get us some logs from the access.log file and as for dns lookups try using 
> debug options ALL,1 78,8
this will show info about dns stuff.
you can get more about getting specific debug information from here
[http://wiki.squid-cache.org/KnowledgeBase/DebugSections](http://wiki.squid-cache.org/KnowledgeBase/DebugSections)

i wrote response on the squid mailing list for you but i never got a reply.

---

### Post by sheld0r on 2012-01-09
This turned out to be an issue with DNS on the Ubuntu server, had nothing to do with Squid.

---

### Post by sheld0r on 2012-01-09
> **elico said:**
> couple of thigs:
is this server is for internal usage? means for web servers over the internet or over the internal network?
if it's for internal network also you need to be able to resolve the local network addresses using a dns server (local one)and this will solve the problem.
more info on the  server is network infrastructure and dns lookups.
get us some logs from the access.log file and as for dns lookups try using 

this will show info about dns stuff.
you can get more about getting specific debug information from here
[http://wiki.squid-cache.org/KnowledgeBase/DebugSections](http://wiki.squid-cache.org/KnowledgeBase/DebugSections)

i wrote response on the squid mailing list for you but i never got a reply.

Apologies elico, I must have missed that response on the mailing list.  I'm not used to working with mailing lists, I mostly use the forums.  Let me check it out.

---

