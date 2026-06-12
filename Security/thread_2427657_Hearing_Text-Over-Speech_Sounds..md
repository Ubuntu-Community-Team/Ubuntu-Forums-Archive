---
title: "Hearing Text-Over-Speech Sounds."
date: 2019-09-24
forum: Security
---

### Post by unruffledst on 2019-09-24
I am having some doubts, moved to Kubuntu as it is the system that asks  for the least resources from the computer, having 6gb ram I decided that  saving every space was worth it. So shortly after, I am noticing some  huge memory spikes, well to say the only thing I have open is 8-12 tabs  on my browser at a time, still this should not be exactly memory  expensive. Next I noticed that my computer starts to freeze up, this  being that I would be allowed to move the mouse around but do nothing  else. Now I am hearing Text-Over-Speech sounds at random, concerned as  these are usually signs of a virus.

---

### Post by #&amp;thj^% on 2019-09-24
Pressing {Alt+Super+S} will disable or enable speech dispatcher.

The last thing you should hear is "screen reader off".

The Super key is the "windows" key...

---

### Post by unruffledst on 2019-09-24
> **1fallen said:**
> Pressing {Alt+Super+S} will disable or enable speech dispatcher.

The last thing you should hear is "screen reader off".

The Super key is the "windows" key...

Tried doing so, it did nothing.

---

### Post by #&amp;thj^% on 2019-09-25
Orca has been buggy for a few years now.
This should do it though:
```
gsettings set org.gnome.desktop.a11y.applications screen-reader-enabled false
```
If you find the need to have Orca again use:
```
gsettings set org.gnome.desktop.a11y.applications screen-reader-enabled true
```
What makes you suspect a Virus? What you have written tells us nothing to believe you have one.

---

