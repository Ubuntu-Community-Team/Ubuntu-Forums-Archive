---
title: "Deja-dup weirdness"
date: 2013-02-25
forum: Ubuntu Development Version
---

### Post by sgage on 2013-02-25
I just made a fresh install of today's build of Raring (UGR if it matters). I install and uninstall iso's all the time, and have always been meticulous about backups. I have the installation process down to a science. Install the build, do any updates, run a little script that installs all the extra packages I like, and restore my deja-dup backup. Bang zoom – it's all configured to my liking. I've been using this technique since deja-dup has been in the repos.

Everything working fine with this installation, except deja-dup did not bring in a certain set of Gnome Shell settings. Here are the ones I can think of: Desktop background, nautilus settings, panel settings, extension state, favorites on launcher, font settings. Everything else came in just fine. No error message from deja-dup.

This with a backup I made just a couple of days ago, so there can't have been a wholesale change in how Gnome stores configurations and such since then. No complicated excludes in my deja-dup settings (besides, you can't exclude .files anyway) In any case, I've been getting this behavior for at least a month, probably longer. It is unique to Raring – everything works as always when I do a quantal or precise install. Is it deja-dup? Is it GS? Do I have poltergeists?

I'd be curious to hear if anyone has any idea as to what's going on, or has a fix...

TIA

---

