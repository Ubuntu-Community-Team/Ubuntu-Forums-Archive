---
title: "Tor &amp; privoxy"
date: 2008-03-22
forum: Security Discussions
---

### Post by ameba on 2008-03-22
u

---

### Post by update_manager on 2008-03-22
> **ameba said:**
> What kinds of websites would i use these tools for?


Websites where you would like to hide your identity from. For example, if you suspected an online retailer was offering different prices on the same product depending on your IP, tor might let you check this.

> 
I know not to use them for websites that use passwords etc.


Tor will not hide your traffic from the exit node. So, if you should not submit private information like usernames and passwords over HTTP. However, HTTPS sites should be ok to use over tor.

---

### Post by ameba on 2008-03-22
let me see

---

### Post by ameba on 2008-03-22
i'm trying to access

---

### Post by ameba on 2008-03-22
anybody know

---

### Post by update_manager on 2008-03-22
> **ameba said:**
> Also, i have a external firewall; Would tor & privoxy compromise it in any way. :KS:KS

Tor will essentially bypass your firewall, and expose your computer to another Internet (not quite right, but close) on a select few ports.

---

### Post by ameba on 2008-03-22
if

---

### Post by update_manager on 2008-03-23
> **ameba said:**
> if my firewall only allows outbound traffic, i should be ok. Right?


Tor will create a tunnel through your firewall. All traffic to/from the tor network will go through this tunnel.

> 
Given what you know, is it even worth me to take a stab at it?

Maybe try something like one of the free online proxies.

For example:
[https://www.the-cloak.com/login.html](https://www.the-cloak.com/login.html)

Its possible that the owners any proxy set it up just to collect webmail usernames/passwords, so proceed with caution. :-)

---

### Post by ameba on 2008-03-23
lets say hypothetically

---

### Post by thewanderer on 2008-03-24
> 
Is my firewall is useless while using tor?

No it is not useless your firewall is still blocking any external attempts to connect to your open ports while using tor.

> So lets say i'm using Tor, is my firewall still block inbound traffic while allowing outbound traffic on the configured ports.

Yes - however by running tor you have opened a tunnel between your computer and the computer at the end of the onion router. The tunnel you have opened will allow you to open external connections via the tunnel.

I believe the only way an attacker could come in through this tunnel is through exploiting the tor protocol. Which I would think is a difficult thing to do, unless perhaps you are the NSA!!

However by using TOR for something like web browsing you are still able to be exploited through an application exploit in your browser or plugin etc. The same as when you browse the web through your firewall - you could be compromised by a malicious web page.

> Regarding you warning about Tor, I've read that people(or governments) setting up proxies to spy on peeps for there own agendas. Not Good!!

Yes it is well documented that TOR exit nodes are used to collect logins / passwords and other data. Use SSL (https) on any page you are going to be entering login / password information or use fake information. The same goes for POP / SMTP and others. Always use encrypted protocols.

TOR is a powerful tool but should be used with caution.

---

### Post by ameba on 2008-03-24
For a moment there

---

