---
title: "Security of a webserver limited to only one superadmin area"
date: 2017-02-12
forum: Security
---

### Post by matteoraggi on 2017-02-12
I need to keep safe a webserver installed into a VPS with the public side that is only my superadmin area.
I need to follow all the borocracies of all normal webservers or it woul be more simple in my case to keep it safe?
Detailed explanation:
I am going to configure a untuntu 14-04 webserver with installed apache, ffmpeg and phantmjs, and the public side is only my superadmin area that will be limited only to my connection IP.
I will need to do the same many things to keep it safe like all other webservers or what should I do to keep it safe?

---

### Post by TheFu on 2017-02-12
Every different service running has different security requirements.  Every web-app has different security requirements. The general answer is here: [http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security)  This is not a checklist of things to type. That isn't possible. Every server is different and every admin has different skills, which help and hinder securing the system.  For example, I don't know too much about php security, so I won't allow a php server on the internet. I force all php services to be accessed only through a VPN connection from outside the LAN.

Staying patched matters most. That means every part of the system needs to be currently patched all the time. Weekly.  That includes any javascript libraries used. 

I don't understand what you mean by "superadmin" - best to use the normal terms everyone else uses to ensure clarity of intent. Do you just mean you have root?

At this point, it would be worth considering starting with 16.04 as the server OS. That will delay the required upgrade a few years, instead of just 2 (14.04 support ends in about 2 yrs). It might not be possible due to dependencies, but most software should have been ported to 16.04 from 14.04 by now.

I don't believe it is possible to have a 100% secure web server today. If someone really wants access, they can find a way in. Make a plan for what your team will do WHEN (not if) the server is hacked.  Think through having backups and how to restore. How will you determine that it is hacked? How will you determine HOW the bad people got in?  What will you need to change to stop that attack vector?

Do you need a reverse proxy or a security-addon for the web server?  What about specific firewall rules?  Also probably want to block all admin access from the internet and only allow that from localhost - to force the use of ssh tunnels.

But what you need is completely up to you. Things that I think are important for system and network security may not be important to others.
Hope this helps and provides some ideas.  Don't forget the *Basic Ubuntu Server Security guide* and the *Real World Linux Security* book by Bob Toxen.

---

