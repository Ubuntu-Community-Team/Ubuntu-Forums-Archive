---
title: "telnetd configuration for BBS (autologin)"
date: 2013-11-21
forum: Server Platforms
---

### Post by kogz on 2013-11-21
Hi guys,

I'm trying to configure [Mystic BBS](http://www.mysticbbs.com/) on Ubuntu Server 12.04.3 64-bit using [this official guide from 2011](http://wiki.mysticbbs.com/install:linux). Yes, it can be little bit outdated and some dirty work is also included.. But..

What I want to achieve is to have autologin telnet service enabled. Example - I put command 'telnet <host>' and I don't need to put any credentials because the service is configured to always log in using one particular account (for example 'bbs').

And using mentioned guide (we use there ttysnoop) I'm not able to do it probably because of that user still have password assigned (and it should be empty I guess).. I still receive login/password request.

Other thing is that ttysnoop requires root privileges and this is not very good idea to public this kind of host on Internet.. Do you have any other suggestions how this can be resolved?

Many thanks for any suggestions,
K

---

