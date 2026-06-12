---
title: "power point 2007 don't start ubu maverick 10.10 after updates"
date: 2011-03-25
forum: Wine
---

### Post by Claus7 on 2011-03-25
Hello,

version of wine: 1.3.16
version of ubuntu: 10.10 maverick meerkat

During the latest updates from winehq I had faced a problem opening power point. While I was trying to do so, the pop up with the power point was on screen and then it crushed. The problem I had was the one found here:
 [http://bugs.winehq.org/show_bug.cgi?id=25154](http://bugs.winehq.org/show_bug.cgi?id=25154)

I already had chosen xp as my option for wine, so in order to fix that I had to do the following:

Applications-> Wine-> Configure wine

and then select the tab Libraries.
There in the tab "New override for Library" selected the riched20 (native,builtin) and pressed Add.

And power point was up and running again!

Regards!

---

