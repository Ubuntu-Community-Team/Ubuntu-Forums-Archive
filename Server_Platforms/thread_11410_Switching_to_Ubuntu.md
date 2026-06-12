---
title: "Switching to Ubuntu"
date: 2005-01-16
forum: Server Platforms
---

### Post by rbrugman on 2005-01-16
Hello,
I have been wanting to migrate my Slackware 9.0 box to Ubuntu for some time now, but I'm a bit hesitant.  My server is just a simple file server and domain controller that handles my home network, but it takes quite a beating when I'm syncing my music and stuff like that.  I need an OS that is rock solid, secure and is easily patchable (something I've been having trouble with in the past).  I've been reading nothing but good things, but I'm curious to know if it's worth an upgrade.

Robert

---

### Post by mecon on 2005-01-16
[QUOTE=rbrugman]Hello,
I have been wanting to migrate my Slackware 9.0 box to Ubuntu for some time now, but I'm a bit hesitant.  My server is just a simple file server and domain controller that handles my home network, but it takes quite a beating when I'm syncing my music and stuff like that.  I need an OS that is rock solid, secure and is easily patchable (something I've been having trouble with in the past).  I've been reading nothing but good things, but I'm curious to know if it's worth an upgrade.

Robert[/QUOTE]
 swich, it will be easer to manige and its based on debian so its ez to upgrade

---

### Post by moopere on 2005-01-17
[QUOTE=mecon]swich, it will be easer to manige and its based on debian so its ez to upgrade[/QUOTE]
 Be just a little bit cautious before jumping in with a Warty server.  Many of the services you might want to run and/or the admin tools you might be used to using will only appear under warty/universe.

This is fine at first glance,.  Stuff in universe mostly seems to 'just work' as does the greater Debian software effort, but in Ubuntu Warty, Universe is unsupported, therefore security fixes will not be forthcoming.

I'll give you an example.  I got so excited by Warty when it first arrived that I installed a test bed server very shortly afterwards.  Amoungst a whole host of daemons and services I also installed Samba with Swat as the Samba admin tool (is there another admin tool that is still as complete?  Not Webmin, no where near complete).  

All its good so far.  However, not many weeks later there is a security fix for samba.  Ubuntu/Warty Samba gets it, but Swat, from Universe is dependant on the old Samba, and as its in universe it will not be upated.  Boom!  Straight away I'm in a bind.  Give up the simple yet complete admin tool Swat for the security fixed Samba or stick with a known buggy Samba but still retain the tool?

Anyone reading this post will probably find the answer to that riddle an easy one...go for the security fix every time, and yes, I'd agree, but nevertheless, what to do for administering the SMB server?  Manually?  If you have a big system its not fun.

'Debian' proper does not suffer this sort of problem.  If your production servers are running stable then you'll get the fix and the problem won't surface as there is no concept of 'universe' in Debian....well, maybe contrib is the closest thing to it, but contrib does not tend to hold important packages that are well recognised such as samba etc etc.

This is only an example, there are other ways of getting around the specifics of this particular problem, however I think it illustrates the issue - as soon as you delve into Ubuntu/Warty/Universe for any server ciritical packages you are poentially settting yourself up for a fall sometime in the future.

Installing particular packages from Debian is not really a solution - even the Ubuntu folks recommend against doing this.  Upgrades and crossgrades from Ubuntu to Debian and back are probably possible, but I wouldn't be doing this sort of jiggery-pokery on a production server by any means.

Craig

---

