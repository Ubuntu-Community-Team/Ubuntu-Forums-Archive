---
title: "Can't get SeaMonkey to work"
date: 2010-07-21
forum: Ubuntuzilla
---

### Post by graceful1 on 2010-07-21
After following the [instructions]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page") at SourceForge.net, for some reason SeaMonkey will not run at all, whether I use the Applications menu or whether I try to run it from the command line. Can anyone help? I am using Lucid.

---

### Post by nanotube on 2010-07-22
hi,
is package seamonkey-mozilla-build properly installed? do you see the "mozilla build of seamonkey" menu item in your menu? what happens when you run 'seamonkey' from the terminal - any error output?

---

### Post by graceful1 on 2010-07-22
> **nanotube said:**
> hi,
is package seamonkey-mozilla-build properly installed? do you see the "mozilla build of seamonkey" menu item in your menu? what happens when you run 'seamonkey' from the terminal - any error output?

I do see the "Mozilla Build of Seamonkey" menu item in my Applications|Internet menu. When I run 'seamonkey' from the terminal, nothing happens, except maybe the cursor blinks for a few seconds, and then I get the bash prompt. No error message. When I select the "Mozilla Build of Seamonkey" menu item, I get the tab at the bottom of the screen that says "Starting Mozilla Build...", but then it disappears and the application doesn't run.

I am wondering if certain dependencies were not installed, but I did follow the instructions at SourceForge carefully. It seems to have installed only the one package.

---

### Post by nanotube on 2010-07-22
Hi

yes, only one package is necessary... i have personally tested this on all ubuntus up to karmic.
maybe something is different in lucid...? but i doubt it.

is it possible you have something borked in your profile? would you try moving the ~/.mozilla/seamonkey directory out of the way, and try with a fresh profile? or maybe even the whole ~/.mozilla directory?

(and remember, always make backups of your profile before fiddling with it! :) )

---

