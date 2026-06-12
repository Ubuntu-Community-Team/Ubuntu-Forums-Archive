---
title: "Home Server Proxy question"
date: 2008-09-24
forum: Server Platforms
---

### Post by manqueller on 2008-09-24
I'm interested in running a server at home similar to a proxy like Squid so all network traffic goes through this box.  What I want is something that is more like a firewall that allows me to see what everyone is doing on the network and block by URL, Port, etc.

Basically I want to see what my kids are doing when they think I am not looking.  I'm not so much doing it like a proxy, for saving bandwidth although that is a plus.

Does anyone run Squid and know if it would be able to do what I want or should I use something else?

---

### Post by HermanAB on 2008-09-24
Squid with Dan's Guardian or SquidGuard.

BTW, Mandriva has a wizard for that - well, it pretty much has wizards for everything - but if you need to do it on Ubuntu, then it may be quite a chore.

---

### Post by Dr Small on 2008-09-24
You need to setup Squid and DansGuardian for this to work. Then you need to configure each client (in Firefox) to use the proxy for browsing. This can easily be bypassed, unless you install Squid+DansGuardian on the Firewall/Router and route everything through DansGuardian.

---

### Post by koenn on 2008-09-24
> **HermanAB said:**
> Squid with Dan's Guardian or SquidGuard.

BTW, Mandriva has a wizard for that - well, it pretty much has wizards for everything - but if you need to do it on Ubuntu, then it may be quite a chore.
You could probably borrow a package from ubuntu CE

---

### Post by devonps on 2008-09-25
I'm doing something similar and have decided to use Untangle, which does what you want and a lot more. It is configurable so that if you only want certain modules then that's what you enable. It has it's own GUI which makes configuration easy.

I should add that Untangle likes to live on it's own box - maybe that's too much for you?

---

### Post by manqueller on 2008-10-02
Thanks for all the info everyone.  It doesn't have to run on Ubuntu; I just knew I could run squid on Ubuntu and I wasn't sure if Squid alone would do what i want.  

I'm not in a big rush so I'll do some more research.  My kids aren't old enough to be interested in surfing the web yet, but I'm getting ready for that day.  Untangle looks like it can do alot so maybe I'll install that on an old box just to test it out.

---

### Post by whitegourd on 2008-10-02
I have Squid and SquidGuard set up using Shallalist's blacklist for both home and at work and it seems to be working out flawlessly.  The following are the links that I used to get rolling on this setup.

[http://mkeadle.org/index.php?p=14](http://mkeadle.org/index.php?p=14)
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)
[http://www.linux.com/feature/60050](http://www.linux.com/feature/60050)
[http://www.tenon.com/support/webten/papers/squidlog.shtml](http://www.tenon.com/support/webten/papers/squidlog.shtml)

---

### Post by TreeFinger on 2008-10-02
I installed Squid on my router/firewall at home. Watching the cache.log I am able to see what sites are being browsed.. not sure how in depth you would like to monitor but I can see domain names.

---

### Post by Antar Hydrus on 2008-10-02
I have a dedicated machine running pfSense (based on FreeBSD [http://www.pfsense.com/](http://www.pfsense.com/)) as a Firewall/Router with Squid. You can set ACLs, define which machines are allowed to access which websites, view a report as to where and when each user or machine went to. Its pretty simple to install and configure. Be sure the machine you install it on has two NICs. It doesn't have to be a powerful machine either. This may be what you are looking for.

---

