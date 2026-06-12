---
title: "Apache::VMonitor"
date: 2009-07-29
forum: Server Platforms
---

### Post by parsim on 2009-07-29
Hello! I'm trying to track down a memory leak in one of my Perl scripts, and from what I've read, Apache::VMonitor is a useful tool. However I can't install it for the life of me.

I can't find any suitable Ubuntu package, and have been wrestling with CPAN from the command-line for a couple of hours. (Apache::VMonitor wants Apache::Scoreboard, which wants mod_perl... which is installed, via libapache2-mod-perl2, but CPAN doesn't seem to know that and wants to install another one.)

Any tips?

---

