---
title: "Problem with QT applications after Virtualbox is launched in ubuntu 9.04"
date: 2009-06-16
forum: Virtualisation
---

### Post by sayantandas on 2009-06-16
HI all,

I have noticed a very weird problem in my computer. After I run virtualbox2.24 , any qt application that I open loses its colour (the applis include dolphin, virtualbox,digicam,amarok,skype). It becomes a grey shaded application.  I have no idea why , this is the first time it is happening to me. Have been using ubuntu since 7.04 days never encountered such a problem.
I'm attaching some screenshots of qt applications with grey shade problem.
[IMG]http://profile.imageshack.us/user/sayantandas/[/IMG][[IMG]http://img189.imageshack.us/img189/9176/screenshotdolphin.th.png[/IMG]]("http://img189.imageshack.us/my.php?image=screenshotdolphin.png")
[[IMG]http://img188.imageshack.us/img188/3607/screenshotdigikam.th.png[/IMG]]("http://img188.imageshack.us/my.php?image=screenshotdigikam.png")
[[IMG]http://img36.imageshack.us/img36/9740/screenshotsunvirtualbox.th.png[/IMG]]("http://img36.imageshack.us/my.php?image=screenshotsunvirtualbox.png")

[IMG]http://profile.imageshack.us/user/sayantandas/[/IMG]

---

### Post by Clorow on 2009-06-17
Weird, that's never happened to me before. I know that VirtualBox uses Qt.

1) Are you using VirtualBox OSE or proprietary VirtualBox?
2) Have you tried going to System > Preferences > Qt 4 Settings and changing anything around?
3) Have you tried reinstalling VirtualBox via Synaptic?

---

### Post by nfox on 2009-06-17
Try removing Trolltech.conf before starting VB and if it persists, log out and in again (to regenerate the file) then launch VB and remove Trolltech.conf. Then try to reproduce the problem. Or you can just rename the file if you don't want to log out/in again.

The file is located at "~/.config/Trolltech.conf"

This file is core to many QT dependencies (just look through the file) and there was even a bug about this that while the status states fixed, doesn't mean it's not occurring for you.

> If Qt finds the file ~/.config/Trolltech.conf it will not load X11 resources (color, font, etc) at all. This happens even if the only entry in Trolltech.conf concerns plugins.
[http://www.qtsoftware.com/developer/task-tracker/index_html?method=entry&id=79074]("http://www.qtsoftware.com/developer/task-tracker/index_html?method=entry&id=79074")

I used to get the "cannot mix incompatible QT libraries" issue with Intrepid and the solution for me was to make a wrapper script that removed that file before launching VB.

---

### Post by sayantandas on 2009-06-18
I use virtualbox from the virtualbox repos. It is happening even with virtualbox3.0. The thing is.. it only happens when this script is used

#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
VirtualBox

But if i dont use the above script, I get the transparent background problem with virtualbox.

---

### Post by nfox on 2009-06-18
> **sayantandas said:**
> I use virtualbox from the virtualbox repos. It is happening even with virtualbox3.0. The thing is.. it only happens when this script is used

#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
VirtualBox

But if i dont use the above script, I get the transparent background problem with virtualbox.

So did you try to remove that file? And what transparent problem do you mean? I don't have any issues with VBox through several versions of Ubuntu.

---

### Post by sayantandas on 2009-06-18
> **nfox said:**
> So did you try to remove that file? And what transparent problem do you mean? I don't have any issues with VBox through several versions of Ubuntu.

[http://forums.virtualbox.org/viewtopic.php?f=7&t=17831](http://forums.virtualbox.org/viewtopic.php?f=7&t=17831)

this bug . it still bugs ubuntu users running 9.04

by the way, ur solution did not work.i did remove the file but still the problem persists

---

