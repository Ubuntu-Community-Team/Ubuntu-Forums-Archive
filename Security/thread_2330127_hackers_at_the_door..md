---
title: "hackers at the door."
date: 2016-07-08
forum: Security
---

### Post by tross2 on 2016-07-08
I hope this is the right forum for this issue.

overview:
It appears that I have several hackers attacking my Ubuntu server, I'm seeing ip address for overseas in the access.log and error.log in the Apache2 dir.
they are either accessing my private website or trying to run tmunblock or other GET functions.
I'm in the process of setting up a pfsense firewall, blocking all BUT USA mainland IP's, in the mean time, I've added these address' in the iptables. ( 213.0.0.0/8 etc...)
( I have a dynamic ip ( not static ) I only allow family to access this server. 10-15 people and if the IP changes, I email the new address to them.)

Question:
1) (security question) how do I tell or check if they(hackers) left a Trojan, spyware or something that will allow access to my server or broadcast it's ip to them?  I intend to force the change of my IP to a new IP, and I what to be sure that they are not informed or have access thru spyware etc.., if it exist. (is there a virus/spyware scanner for Ubuntu?)
2) (general firewall question) should I block outbound traffic to all BUT USA IP's or would blocking the inbound be enough to prevent access to these hackers? 

TIA

Tim

---

### Post by TheFu on 2016-07-09
There are tools for web servers which will see failed login attempts and dynamically block those IPs for 1 minute or forever. Your choice. Check out **fail2ban**.

No way that I know to be 100% certain that a system hasn't been hacked.  If there is any doubt, *nuke it from orbit. That's the only way to be sure.*  There are a few threads here about recovering from crackers and other techniques.

The internet is world-wide. Blocking non-USA addresses will cause more hassles than it is worth, IMHO. Many corporations setup outbound proxy servers, throw which all traffic much go (and be logged).  You can do that. Just be certain to prevent any other systems from having a default route to the internet or any external DNS. Only the proxy server should have that.

There are virus scanners and spyware and root kit scanners for Linux. (no need to be ubuntu specific 95% of the time). Ubuntu is just Linux.  The AV stuff scans for Windows viruses, so if you have Windows machines on the network, it makes sense.  Also, if you run WINE, it makes sense, because systems running WINE have been infected.  With the permissions models in Unix, and provided you don't run with elevated privileges except when required, there is little that a virus can do to a system.  If you put high-risk programs into separate containers, the risks can be reduces. Check out **firejail** for this.  Compartmentalization has been park of Unix system security for decades. These days, we tend to use VMs for it and "containers" are an interesting next step.  There is an OS designed from the ground up for this purpose called Qubes - basically it is Xen VMs with a nice GUI to make management of all the different VMs per application or workspace easier to use. For my desktop needs, firejail seems the most usable of these options.  For servers, I'm still firmly in the HVM group and don't trust containers for internet-facing services at this point. More time in production - *hosting cat videos* - is needed. That just means I want someone else to get hacked with unimportant things before I'd trust containers for my "important" stuff.

Of course, there are thousands of different opinions about this subject. Hopefully, others will respond with their stance on this too.  They usually wait for my ignorance to be displayed. ;)

---

### Post by bashiergui on 2016-07-10
> **tross2 said:**
> 2) (general firewall question) should I block outbound traffic to all BUT USA IP's or would blocking the inbound be enough to prevent access to these hackers? 
Consider whitelisting your family's IPs if you only want a few people to access it. Would be easier than blacklisting the rest of the planet.

---

### Post by HermanAB on 2016-07-12
Howdy,

A typical server sees thousands of failed login attempts per hour.  That is why you should always use loooooooooong passwords and keys for authentication.

Watch your running processes with htop, watch the security logs and watch the network traffic with tcpdump.

---

