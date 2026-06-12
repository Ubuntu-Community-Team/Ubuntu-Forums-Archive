---
title: "Open Ports and Port Scanning?"
date: 2008-06-05
forum: Server Platforms
---

### Post by warthog10 on 2008-06-05
Hi.  I have just set up a basic virtual webserver with Ubuntu 7.04, for the first time and believed I closed all external ports with IP Tables except the following:

Port 80 -- Internet
Port 443 -- HTTPS
(nonstandard port) -- SSH
(nonstandard port) -- Webmin

I have shut down non necessary services, eg telnet, as well.

When I run either from the commandline 

netstat -r

or

lsof -i

all proper ports look to be in place, with none open unnecessarily.

However:mad: as a check, when running Nmap from an outside computer, ALL and I mean ALL the ports come report back as being open! 

Properly freaked out, I also used some webbased scanning tools, which reported that all the ports were indeed closed, with the  exception of the ones listed above.

Can anyone assist with why I am getting conflicting results.  I really do not want to keep unnecessary ports open.

Thanks!:KS

---

### Post by dendrobates on 2008-06-05
First of all, *netstat -r* tells you nothing about open ports.  

Try *netstat -ltu* That will give you all open tcp and udp ports.  If it shows them listening on localhost, they are not external facing. 

 i.e.[I] tcp    0  0 localhost:smtp   *:*       LISTEN
[/I]

netstat's output is always correct, unless your system has been compromised.

If you want help with nmap, you will need to post the command line and the output. 

Rick
Manager,Ubuntu Server Team

---

### Post by HermanAB on 2008-06-05
Hmm, note that the whole 'open port firewall thing' is mainly a Windows problem.  On Unix, you always know exactly what services are running and what ports they are listening on.  Consequently, you can configure a Linux system with perfect security without any 'firewall' required.

If that wasn't true, then all Linux firewalls would need firewalls, which would need firewalls...  which also explains why you cannot use Windows as a firewall, since then you would still need to put it behind a Unix firewall. 

Just my tuppence worth.

---

### Post by warthog10 on 2008-06-05
dendrobates, Thanks for the info on netstat, I will give it a shot this evening.


HermanAB, That sounds right to me, but as a newb, I am trying to be as security conscious as possible, and i thought I just had opened certain ports.  I just don't want all of my stuff freely available on the interwebs.

---

