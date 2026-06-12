---
title: "Friends reach my server but not me. What's up?"
date: 2011-09-01
forum: Server Platforms
---

### Post by Hazle on 2011-09-01
I have a weird problem; it's so weird I decided to post a thread about it. I don't usually post threads in forums but rather search for an endless amount of time until I eventually fix it or ***** it.

So to the problem:
I can only access my own server through LAN (192.168.0.103) and everything runs smooth, websites(websvn/phpmyadmin), svn and utorrent-server is all good. 
However for some reason as soon as I try to access them through WAN (81.***.143.***) it doesn't work at all.
Yeah.. "n00b open ports wtf lol", except I already did. Even tried to put it in the DMZ.

Here's the weird part which I don't understand and would like some input on: All my friends can access my server via WAN-IP. Why the **** can everyone, except I, access my WAN-IP and my websites/ftp/ut-server/svn ?

If anyone have a slightest clue and maybe need some more information, please reply!

Thanks for your time :)

---

### Post by haqking on 2011-09-01
> **Hazle said:**
> I have a weird problem; it's so weird I decided to post a thread about it. I don't usually post threads in forums but rather search for an endless amount of time until I eventually fix it or ***** it.

So to the problem:
I can only access my own server through LAN (192.168.0.103) and everything runs smooth, websites(websvn/phpmyadmin), svn and utorrent-server is all good. 
However for some reason as soon as I try to access them through WAN (81.***.143.***) it doesn't work at all.
Yeah.. "n00b open ports wtf lol", except I already did. Even tried to put it in the DMZ.

Here's the weird part which I don't understand and would like some input on: All my friends can access my server via WAN-IP. Why the **** can everyone, except I, access my WAN-IP and my websites/ftp/ut-server/svn ?

If anyone have a slightest clue and maybe need some more information, please reply!

Thanks for your time :)


routers do not usually support loopback to your WAN IP.

as long as you can do it locally and others outside can then no worries.

you can sometimes get round this by forwarding the specific ports from your WAN IP to your LAN IP

---

### Post by Hazle on 2011-09-01
Of course it's router related, thanks for the help :)

---

### Post by haqking on 2011-09-01
> **Hazle said:**
> Of course it's router related, thanks for the help :)

no worries.  mark the thread as solved using thread tools

---

