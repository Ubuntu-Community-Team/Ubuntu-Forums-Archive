---
title: "Shorewall has no compiler?"
date: 2009-12-31
forum: Server Platforms
---

### Post by Goatie on 2009-12-31
Hi everybody and happy new year :)

I'm in the middle of setting up a server for the first time following [this guide]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/") and now I've run into trouble with the Shorewall firewall.
Shorewall is installed and I've changed STARTUP_ENABLED to Yes in shorewall.conf and startup is set to 1 in shorewall. And it is now the problem begins. When I want to start Shorewall it simply wont do it. When I check the log file it says "No shorewall compiler installed" which confuses me a bit. Shouldn't the compiler get installed when shorewall is installed?

I hope somebody has a fix for this problem.
And remember people, this is the first time I'm messing around with this stuff, so be gentle :)

**[EDIT]**
After some heavy reading on the [Shorewall website]("http://www.shorewall.net/") I found out there isn't any compilers installed with the new version. So a simple [FONT="Courier New"]sudo aptitude install shorewall-perl[/FONT] fixed the problem.
Sorry for bothering you ppl with such a simple problem.

---

### Post by HeXaDeC on 2010-03-20
I for one am glad you posted this...it solved my problem right away (without me looking a prat :P)

Cheers m8 :popcorn:

---

### Post by jchammons on 2010-04-01
Thank you.

---

### Post by phitbull on 2010-05-01
I had this problem too. Thanks for your help. It solved.

---

### Post by wscheer on 2010-11-27
Goatie,
I spent a lot of time searching for this fix. I was following a nettuts tutorial on setting up an ubuntu server([http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)) and ran into this issue.

Thank you so much for sharing this fix.

---

