---
title: "Ubuntu Studio: What's the benefit?"
date: 2009-10-21
forum: Ubuntu Studio
---

### Post by Shekibobo on 2009-10-21
I just bought a brand new laptop and am about to reinstall Ubuntu 9.10 Beta for a dual boot system.  However, I've had my eye on Ubuntu Studio for a while, because I want to do musical production with midi and recording equipment.  However, there is surprisingly little information as to the real differences and benefits of using Studio over the Desktop version of Ubuntu.  I know there is a real-time kernal, but don't know much about what good it does.  I've tried running various midi mixing programs on Ubuntu 9.04 before, but had little success in connecting.

All I ever really see about Ubuntu Studio is the software bundled with it, but I'm pretty sure I can get all of those for regular Ubuntu.  So again, I ask, is there really something special that makes multimedia, particularly sound production, easier, more effective, or just plain better?

I've been searching for a while now and have found very little in the way of reviews or support for Ubuntu Studio.  Makes me very wary of installing it on my new machine.

---

### Post by Stochastic on 2009-10-21
The essential difference between Ubuntu and Ubuntu Studio is the default setup upon first installation.  Really, that's all.

The realtime kernel (which is very stable in Karmic) allows users to run jack in realtime mode, giving audio processes a higher priority in the kernel stack.  This allows for lower latency audio settings without xruns (aka dropouts).  If none of the audio packages are selected on the install, no realtime kernel is installed, rather the default Ubuntu kernel is used.

The realtime kernel and all the programs bundled with Ubuntu Studio are available from the regular Ubuntu repositories so one can setup Ubuntu Studio on top of their Vanilla Ubuntu install, and one can setup Vanilla Ubuntu on top of their Ubuntu Studio install.  The goal of Ubuntu Studio is to help artists get the tools they need, and to help the development of multimedia production tools in Ubuntu.

I agree, more documentation on this needs to be written.  I hope this clarifies things a little bit.

---

### Post by sdpiowa on 2009-10-22
Ubuntu Studio comes with lots of multimedia programs installed already.  Everything is configured to help you make the most out of your hardware.

However, Ubuntu Studio does not come on a "Live Disk" and must be burned onto a DVD (as opposed to a CD; I'm not counting flash drives).

---

