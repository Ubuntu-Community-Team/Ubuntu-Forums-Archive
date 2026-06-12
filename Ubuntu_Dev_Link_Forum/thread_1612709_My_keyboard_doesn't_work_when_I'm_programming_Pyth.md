---
title: "My keyboard doesn't work when I'm programming Python"
date: 2010-11-03
forum: Ubuntu Dev Link Forum
---

### Post by kangoo1707 on 2010-11-03
I've started using Ubuntu for 3 weeks as a beginner Python programmer, but when I use Eclipse PyDev or Python Shell, the keyboard doesn't work at all. But it still works with other programs. Can anybody help me, please ! My laptop was HP 6530, Core2Duo 1.8Ghz, 2GB RAM. I don't even know whether it's a hardware or software problem !

P/S : I'm sorry if this thread is in a wrong location, I'm new to this forum

---

### Post by pauljwells on 2010-12-06
This is a bug. Quite what or where I'm not sure. I'm no expert! I find with Eclipse/Pydev I can type after login but not after the screensaver has kicked in or after suspend. I also find that wxPython menubars only show if you run the program as sudo, or from Eclipse.

Stuff works better in the UNR, bizzarely and I think that these bugs are related somehow to the display. There's no difference in Kubuntu, I checked.

I know this is no help, but the more voices there are for the poor Python support in Ubuntu the better! Especially considering so much of Ubuntu *is* Python!

Help me help you. Test the wxPython menubar demo and if it doesn't work, add yourself to my bug report here:

[https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/682478]("https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/682478")

Cheers

---

