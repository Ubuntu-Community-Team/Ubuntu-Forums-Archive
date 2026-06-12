---
title: "Window Borders gone after latest update..."
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-03-16
That about sums it up. Anyone else noticing this?

---

### Post by lonniehenry on 2012-03-16
Not seeing  it in unity, but am in my gnome-shell partion.  I thought it was part of the gs updates that are not uploaded.

---

### Post by kaldor on 2012-03-16
This is a feature of GNOME Shell 3.3, if that's what you are referring to.

---

### Post by neu5eeCh on 2012-03-17
> **kaldor said:**
> This is a feature of GNOME Shell 3.3, if that's what you are referring to.

After I logged out and back in, the borders re-appeared. Also, curiously, I had to unplug and plug my wireless mouse back in. That's the first time I had to do that with any distribution. Guess I'll see if this is a one-off occurrence?

So... what's this feature in Gnome Shell 3.3? Is that like XFCE?

---

### Post by kaldor on 2012-03-17
Guess that's a different thing then. GNOME Shell is working on integrating their core applications differently.

See attachments:

---

### Post by neu5eeCh on 2012-03-17
> **kaldor said:**
> Guess that's a different thing then. GNOME Shell is working on integrating their core applications differently.

Sweet! That's a nice feature (and necessary given Gnome's absurdly oversized window decoration). I've installed the Gnome Desktop in 12.04 but haven't spent too much time with it (since there are so few extensions available). Is this version 3.3 (in the repositories)? Also, did you have to tweak any settings to get the "borderless" firefox?

---

### Post by kaldor on 2012-03-17
> **VTPoet said:**
> Sweet! That's a nice feature (and necessary given Gnome's absurdly oversized window decoration). I've installed the Gnome Desktop in 12.04 but haven't spent too much time with it (since there are so few extensions available). Is this version 3.3 (in the repositories)? Also, did you have to tweak any settings to get the "borderless" firefox?

This is available for very few applications so far. It's actually not Firefox, rather "Web". Web is the new rebrand of the old Epiphany browser and it's becoming really awesome. Neat, tidy UI with a modern and stable webkit engine. Install the *epiphany-browser* package and try it out in Shell :)

---

### Post by robwilkens on 2012-03-19
> **VTPoet said:**
> That about sums it up. Anyone else noticing this?

I found a work-around for this... Without logging out or rebooting..  I first noticed that someitmes when this happened i'd be told compiz died and sometimes i didn't, but it seemed it died anyway

So i open a terminal, and type 'compiz --replace' and wait a minute or three, and after some desktop cycling, my window borders are back without having to log out or exit running programs.  

One catch, i think once you run this from a terminal, you have to keep that terminal open (if minimized), I'm not sure how to detach the compiz from that terminal session and let it just run in the bakground, my unix skills are stale.

---

### Post by cariboo on 2012-03-19
> **robwilkens said:**
> I found a work-around for this... Without logging out or rebooting..  I first noticed that someitmes when this happened i'd be told compiz died and sometimes i didn't, but it seemed it died anyway

So i open a terminal, and type 'compiz --replace' and wait a minute or three, and after some desktop cycling, my window borders are back without having to log out or exit running programs.  

One catch, i think once you run this from a terminal, you have to keep that terminal open (if minimized), I'm not sure how to detach the compiz from that terminal session and let it just run in the bakground, my unix skills are stale.

Gnome-shell doesn't and can't use compiz, so this solution won't work.

---

### Post by tekstr1der on 2012-03-19
> **VTPoet said:**
> That about sums it up. Anyone else noticing this?

Yes.

There was a thread on this last week:
[http://ubuntuforums.org/showthread.php?t=1940352](http://ubuntuforums.org/showthread.php?t=1940352)

with links to associated bug reports.

---

