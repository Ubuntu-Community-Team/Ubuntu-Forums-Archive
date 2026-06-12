---
title: "[gazp9] Touchpad settings revert, won't respond to changes"
date: 2013-07-06
forum: System76 Support
---

### Post by rorschachwalter on 2013-07-06
When I change pointer speed in Mouse & Touchpad settings, it has no effect. In fact, if I move the slider, then leave and re-enter the settings, the slider shows that it is at the same position as before the modification.

Any ideas? The touchpad is simply too jumpy for delicate movements right now.

---

### Post by ohnonot on 2013-07-09
here's 2 similar threads:
[http://ubuntuforums.org/showthread.php?t=2150332](http://ubuntuforums.org/showthread.php?t=2150332)
[http://ubuntuforums.org/showthread.php?t=2147844](http://ubuntuforums.org/showthread.php?t=2147844)
does any of this help?

---

### Post by rorschachwalter on 2013-07-09
I'll have to play around with it later and see if those work.

For now, my biggest concern is that I spent extra money to get a machine that "works with Ubuntu", but it continues to have issues like this where it's actually less compatible with Ubuntu than other mainstream machines. I don't just want the touchpad to have good settings. I want the touchpad to do what I tell it to in Ubuntu -- that's what I bought a System76 for.

---

### Post by isantop on 2013-07-09
This appears to be a bug in Ubuntu (i.e. it's not your Gazelle; it happens on every Ubuntu computer), currently reported and being tracked here:

[https://bugs.launchpad.net/gnome-control-center/+bug/1186666](https://bugs.launchpad.net/gnome-control-center/+bug/1186666)

You can track the status there and mark it as affecting you. The more people it affects, the higher priority it will get.

For what it's worth, I'm seeing this adjusting the Mouse Speed on my desktop, so there appears to be a large underlying problem.

---

### Post by ohnonot on 2013-07-09
> **rorschachwalter said:**
> I don't just want the touchpad to have good settings. I want the touchpad to do what I tell it to in Ubuntu.aren't those two basically the same?

i can understand your frustration, but please keep in mind that you are getting a GREAT operating system for free, one that is 100% transparent, never tries to cheat you, and has been created in a global, free-spirited effort - for free! yes, i'm talking about linux.

i'm pretty sure there's a solution for this.
it probably includes using a terminal and/or tweaking some text files with or without root privileges.
in windows somebody would probably have whipped up a gui utility for this, hoping to make a few bucks.
in the linux world, the solution is out there and you have to find it yourself, or with the help of others, like right here right now.

i think this is a great thing and i always prefer it to being ripped off.

---

### Post by screaminj3sus on 2013-07-11
[https://bugzilla.gnome.org/show_bug.cgi?id=699015](https://bugzilla.gnome.org/show_bug.cgi?id=699015) is the proper upstream bug report. It appears to be fixed in gnome 3.8, meaning this should be fixed in the upcoming ubuntu 13.10 (unless ubuntu doesn't merge the fix in their forked ubuntu-control-center or something silly like that)

---

