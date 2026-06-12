---
title: "Firefox Window"
date: 2009-10-14
forum: System76 Support
---

### Post by Eyore15 on 2009-10-14
When booting Firefox on my Starling Netbook, I no long have any control over the window.  I can't drag the window to make it bigger or smaller and the minimize, reduce, close icons are missing.  I also can't drag the window to different locations on the screen.  I used to be able to do all that.  I'd like to be able to do it again.

tnx

mcm

---

### Post by wojox on 2009-10-14
Try this link: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

Scroll down to Solution [FOT002]:

---

### Post by thomasaaron on 2009-10-15
Is it because the window decorations (i.e. the bar across the top of firefox that has the "x" in it) is *missing* or is it because the top bar is behind the upper panel of Ubuntu netbook remix?

---

### Post by Eyore15 on 2009-10-15
> **thomasaaron said:**
> Is it because the window decorations (i.e. the bar across the top of firefox that has the "x" in it) is *missing* or is it because the top bar is behind the upper panel of Ubuntu netbook remix?

The bar with the "X" is missing.  I can't "grab" the window to move it around either.

---

### Post by thomasaaron on 2009-10-15
Try turning off Desktop effects (Prefs > Appearance > Visual Effects > None) and see if that brings it back. If you've made any modifications to compiz, you might have found a bug.

---

### Post by HotShotDJ on 2009-10-15
> **Eyore15 said:**
> I can't "grab" the window to move it around either.If you use Alt + "left mouse" you'll be able to grab the window to move it around when you can't get at the title bar.

---

### Post by jdb on 2009-10-16
> **HotShotDJ said:**
> If you use Alt + "left mouse" you'll be able to grab the window to move it around when you can't get at the title bar.

Alt + "left mouse" moves it
Alt + "right mouse" resizes it

jdb

---

### Post by thomasaaron on 2009-10-16
This may be related to this bug with the desktop switcher...
[https://bugs.edge.launchpad.net/desk...er/+bug/349519](https://bugs.edge.launchpad.net/desk...er/+bug/349519)

Please run this command...
gconftool-2 --recursive-unset /apps/panel
...and then reboot.

Did that fix it?

---

