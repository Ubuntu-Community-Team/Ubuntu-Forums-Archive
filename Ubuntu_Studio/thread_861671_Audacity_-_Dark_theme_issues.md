---
title: "Audacity - Dark theme issues"
date: 2008-07-16
forum: Ubuntu Studio
---

### Post by jenkinbr on 2008-07-16
I have a dark theme installed that clashes with the text color on the horizontal timeline ruler as well as the track controls and vertical ruler.  Is there any way of fixing this, short of swiching sysem themes?

---

### Post by Stochastic on 2008-07-17
switch the system theme.  It's probably easiest.


It may be possible to go though the build process for Audacity from source, and adjust some ./configure variables to force Audacity to use a different theme engine... maybe... it may even only take a straight compilation from source, as it may only be the Ubuntu package that gives it the gtk theme, but maybe not.

---

### Post by jenkinbr on 2008-07-25
I actually found something that works just as well, without having to switch system themes.  I just added a minimized time track, which is normally used to speed up/down the playback of the track.  As for the track CP, I usually don't have many more than three audio tracks at a time, so I can easily remember what's what.

If I feel brave, I may try messing around with the ./configure script in the source package after I take a snapshot of my root drive.  I've managed to screw up plenty of stuff in the past, so I like to play it safe, as I should.

---

