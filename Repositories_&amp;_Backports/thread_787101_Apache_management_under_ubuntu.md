---
title: "Apache management under ubuntu"
date: 2008-05-08
forum: Repositories &amp; Backports
---

### Post by stupidforum on 2008-05-08
I have just installed Hardy Heron.  My other machine runs Gutsy Gibbon.  I want to develop a web project under python.  This necessitates an instance of apache. However all of my web research (and experience) indicates that the best version of apache for my purposes is apache1.3.  My question is how do I either install apache1.3 through apt or have apt ignore the fact that it is "not installed" so that I can manage php and mysql through apt.  

It seems like Ubuntu is trying to force people to use the 2.3 branch of apache.  Are the maintainers aware that apache 2.3, 2.0, and 1.3 are not just versions they are totally separate developments?  All of them are current as well, though I don't foresee much more development on the 2.0 release.

Is there a backport of 1.3?

---

### Post by tamoneya on 2008-05-08
I am pretty sure the maintainers realize this but they are probably just including the most common version in the repositories in order to simplify.  You can still install apache 1.3 if you go get the source code and compile it yourself.  You could also look for a deb package which may make it easier for you.

---

### Post by stupidforum on 2008-05-08
Actually apache isn't my problem.  I don't mind installing things from source.  I really don't want to manager php, or (especially) mysql from source.  mysql can stand alone, but apt considers apache a dependency for php and anytime I grab updates for php, it is going to try and fix that apache dependency.  Most people that use apache professionally recommend the 1.3 version.  Is there a guide to building an apache.deb so it can be registered with apt?  I understand why they might make 2.3 the default (which they should have called apache23 not 2 (as 2.0 is not the same as 2.3), I don't understand why there isn't a way to install apache1.  It would make package management easier for webservers.

---

### Post by Astinus on 2008-05-10
Heh, pretty much everyone I'm aware of with lots of WWW servers deployed in a production environment is running Apache 2.0 now and considering the ramifications involved with getting themselves upgraded to Apache 2.2; based on a quick scan of our IP blocks at work for :80 and :443 and some quick matching on version strings for folks who've not locked that down, it seems most already made the hop.

What is the reasoning for specifically wanting Apache 1.3 as I'm kinda curious?  What is the reason for people using it 'professionally' to not want to upgrade given Apache 2.0 has been very stable for quite some time now, even if Apache 2.2 is somewhat more immature.

---

### Post by wgrant on 2008-05-12
The debate about 1.x vs 2.x was going on 4 years ago. There's no reason to use 1.x any more. What gave you the idea that 1.3 was better?

---

