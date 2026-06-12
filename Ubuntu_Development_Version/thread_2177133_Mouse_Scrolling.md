---
title: "Mouse Scrolling"
date: 2013-09-27
forum: Ubuntu Development Version
---

### Post by PJs Ronin on 2013-09-27
Pretty sure I didn't have this problem in 13.04 or earlier in 13.10.

Mouse scrolling.   Open a browser (Firefox or Chrome), load a page and I can use the mouse scroll wheel to smoothly scroll the page up and down.   Open a Terminal window, enter something like 'sudo apt-get update' and I can use the mouse scroll wheel to move up and down the listing. Fire up Libre Writer, load War and Peace and I can use the mouse scroll wheel to scroll up and down the text.   Select Files from the launcher and I used to be able to scroll up and down a directory's file listing, but that no longer works.   Open a largish file in Gedit and I can no longer scroll up and down using the mouse scroll wheel.   And so on.

Btw, I use one of Bill's cordless mouse/keyboard combos.   I do seem to remember reverting to the old fashioned style of scroll slider as I could not get a grip on a slider control that chased off after my mouse.

It appears that mouse scroll wheel action is arbitrary.   Am I going nuts or has something changed while my attention was diverted?

---

### Post by mc4man on 2013-09-27
Most likely - 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1200829](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1200829)
(if so please confirm, not that'll do any real good

Referenced also here - 
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1184159](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1184159)
Orig bug
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1171156](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1171156)

 I don't see a compiz fix coming soon or ever. In that case you can not use scroll on desktop or I maintain a ppa to revert the offending gtk commit

[https://launchpad.net/~mc3man/+archive/test-scroll](https://launchpad.net/~mc3man/+archive/test-scroll)

Edit: I see that gtk has just updated so i'll need to do a new build, today is a slow day so may take 4-7 hrs. to build & publish, if using wait for both archs to publish

---

### Post by PJs Ronin on 2013-09-27
Ty... added a 'me too'.

---

### Post by mc4man on 2013-09-27
Well the new gtk builds are in the ppa, atm that's the only way to use any bindings for desktop based viewport scrolling & not get either poor scrolling or with a wireless mouse no scrolling in some windows

As far as them?? fixing, not too confident there is anyone in compiz dev that will in the near future or maybe no one that can anymore..
This bug report should get confirmed just for the hell of it
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1200829](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1200829)

---

### Post by PJs Ronin on 2013-09-28
Thanks for your work mc4man.   I added your ppa and now scrolling works in gedit, [s]but nautilus/files is still out to lunch[/s].   Although, if I press the mouse wheel as I try and scroll it 'sort of' works in nautlius.

Mine is a pure Unity partition (which seems to be the heart of Ubuntu) so I'm damned if I know why the devs aren't  jumping all over this bug.   Perhaps mobile systems are taking precedence.

Edit:   Correction, Nautilus is now back on the mouse scroll team.

---

