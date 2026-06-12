---
title: "Anyone else have/still have a Gateway 500se?"
date: 2010-03-06
forum: The Cafe
---

### Post by MasterNetra on 2010-03-06
I'm asking because I still have my old 500se and for whatever reason it freezes completely at random times. And does this with Ubuntu, Kubuntu, Opensuse, and fedora. And by freeze I mean completely frozen as in no Ctrl+alt+f1 to get to a command line and no ctrl+alt+backspace to get out of it. Only way is to hard reset it. I suspect its just the Kernel but meh. Hoping someone who has a 500se has figured/ found out a fix. :/

---

### Post by mdmarmer on 2010-03-07
Did you try Raising Skinny Elephants ??

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

I have 450se and sometimes it does freeze hard -- but i think that's related to acx wireless (Netgear wg311v2) card that i have installed. And yes it does depend on the kernel.  Remove knetworkmanager -- it's very buggy.  Use wicd or the command line for  your network. I don't use ubuntu or suse or fedora, only debian.  I have the most lockups with bfs kernel like liquorix.  But I have lockups with other kernels too.  Make sure you don't have conflicting drivers like ndiswrapper and a native driver.  I suspect my problems are unique to acx which you probably don't have -- but they could occur with other wireless cards too.

---

