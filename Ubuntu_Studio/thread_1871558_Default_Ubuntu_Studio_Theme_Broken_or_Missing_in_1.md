---
title: "Default Ubuntu Studio Theme Broken or Missing in 11.04."
date: 2011-10-29
forum: Ubuntu Studio
---

### Post by deckerry on 2011-10-29
Hi.

I just installed Ubuntu Studio a few hours ago. I enabled my Nvidia drivers at first, thinking that it would be the right thing to do. Then Blender wouldn't open so I disabled Nvidia drivers.

After restarting my computer, the default Ubuntu Studio theme changed to an ugly Windows-95-esque looking theme.

I even looked at the Theme tab in Appearance Preferences and the UbuntuStudio theme is selected.

Does anybody know what I should do to get the default theme working on here again?

Look how ugly this looks! (Try not to puke!)[IMG]http://dl.dropbox.com/u/43610008/uglytheme.png[/IMG]

---

### Post by MrRandomPerson on 2012-02-12
Bumping this thread because my Ubuntu Studio has just started doing this (11.04 as well). I didn't even do anything special with graphics, I just installed updates and when it restarted it looked like that. It even stays the same when I change to different appearances; the appearance window is the only one that displays correctly.

Here are the updates it installed:
[LIST]
[*]linux-image-2.6.38-13-generic (2.6.38-13.54, 2.6.38-13.55)
[*]thunderbird-globalmenu (3.1.16+build2+nobinonly-0ubuntu-.11.04.1, 3.1.18+build2+nobinonly-0ubuntu0.11.04.1)
[*]thunderbird (3.1.16+build2+nobinonly-0ubuntu0.11.04.1, 3.1.18+build2+nobinonly-0ubuntu0.11.04.1)
[*]linux-libc-dev (2.6.38-13.54, 2.6.38-13.55)
[*]linux-headers-2.6.38.13-generic-pae (2.6.38-13.54, 2.6.38-13.55)
[*]linux-headers-2.6.38-13 (2.6.38-13.54, 2.6.38-13.55)
[*]linux-image-2.6.38-13-generic-pae (2.6.38-13.54, 2.6.38-13.55)
[*]linux-headers-2.6.38-13-generic (2.6.38-13.54, 2.6.38-13.55)
[*]libssl0.9.8 (0.9.8o-5ubuntu1, 0.9.8o-5ubuntu1.2)
[*]openssl (0.9.8o-5ubuntu1, 0.9.8o-5ubuntu1.2)
[*]acroread (9.4.6-0natty1, 9.4.7-1natty1)
[*]acroread-common (9.4.2.0-0natty1, 9.4.7-1natty1)
[/LIST]

Anyone have any ideas which of these might be the cause for this and how I go about reverting it?

**EDIT:**Fixed the problem. In the login window, go to the "Session" drop-down bar and make sure it's set to "Ubuntu" and not "Ubuntu Classic" or anything else.

---

### Post by cfhowlett on 2012-02-12
11.04 and 11.10 are not fully converted to the new XFCE desktop environment.  

Personally, I'm running 10.04 LTS and have no urgent plans to immediately upgrade to 12.04 upon release.

---

### Post by hildenbrandsteven on 2012-02-13
I'd also suggest the LTE releases since they've gone through much more extensive testing, and are generally more stable! I hope switching solves your issue!

---

### Post by deckerry on 2012-02-13
Since the first post on this thread, I have gone through an irrecoverable system crash unrelated to this topic and have re-installed US11.04. (Not a recommended fix, by the way.)

Anyway, relevant to the problem at hand:
I think the best thing to do for this problem is to make sure you log into the correct default [COLOR="Red"]session [/COLOR](as *[I]MrRandomPerson*[/I] has discovered) and use the default [COLOR="red"]drivers[/COLOR] that US11.04 comes with. At least that worked for me.

This might or might not help you but **Good Luck!** :P

---

