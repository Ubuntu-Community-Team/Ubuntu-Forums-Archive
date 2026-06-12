---
title: "Enable metacity compositing in 9.04 alpha builds on trial basis"
date: 2008-09-14
forum: Ubuntu Brainstorm
---

### Post by tretle on 2008-09-14
Metacity compositing, its great. Where compiz fails Metacity thrives. Metacity compositing supports lower specs.

Problem:

An example of this would be my IBM Thinkpad t30. It sucks and let me tell you why, 16MB RADEON 7500 ATI Mobility video chipset . Yes the graphics card has a measly 16MB of onboard memory. And to make things worse is that it has only 256MB of non video memory to back that up.
I hacked it to run beryl back in the day but the performance was god awful. Its laptops like these that stop ubuntu from using compositing as default and increasing eye candy.

Solution:

Metacity compositing works on it, and it works well. Performance is great. Eye candy is great. Enables the use of things like avant window navigator on low specked hardware. Metacity compositing also works with vesa(open source driver) so people would have less reason to use closed source alternatives. Metacity compositing is impressive indeed.

Proposal:
Have metacity compositing enabled in the 9.04 alpha builds for testing purposes only. See how many people have problems with it and see if its viable to run it as default in the final version of 9.04. If it is included in 9.04 as default it should be included as normal effects, if the user goes into appearance/visual effects and clicks advanced effects it should use compiz instead.

Before you vote this down please give it a quick test to see if it works on your hardware. Even if compiz doesnt work there is a huge chance that metacity compositing does. If you want to test and have compiz enabled then disable compiz first.

To test go into applications/terminal and type xcompmgr -c -f

Metacity compositing is included in hardy and intrepid right now as default but is not enabled.

Please go to [http://brainstorm.ubuntu.com/idea/13191/](http://brainstorm.ubuntu.com/idea/13191/) and vote this up if you like it.

---

### Post by Swarms on 2008-09-14
I always hated Compiz for being too hungry with the powerusage, this is a great solution for the crowd!
+1

---

