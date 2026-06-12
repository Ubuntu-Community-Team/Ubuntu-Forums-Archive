---
title: "copy paste bug that need to be fixed"
date: 2007-09-13
forum: Ubuntu Brainstorm
---

### Post by Mr.mouse on 2007-09-13
Copy-Paste doesn't work if the source is closed before the paste

[https://bugs.launchpad.net/ubuntu/+bug/11334](https://bugs.launchpad.net/ubuntu/+bug/11334)

---

### Post by 23meg on 2007-09-13
"It's a feature, not a bug"&#8482;, and one whose status is "Invalid". Workarounds exist: Glipper, Klipper, GNOME Clipboard Daemon. If you want the behavior to change in Ubuntu, the way to go probably isn't to rewire an X essential, but maybe include one of the above, or something similar.

Does Klipper come preinstalled in Kubuntu?

---

### Post by happy-and-lost on 2007-09-13
> **23meg said:**
> Does Klipper come preinstalled in Kubuntu?

klipper is a dependency of kubuntu-desktop. Why does a ubuntu-desktop not offer similar functionality?

---

### Post by tvrg on 2007-09-13
afaik only select, middle button paste act that way, always been like that. 
I haven't had any copy paste issues in the last 5 years or so using gnome/kde while effectively copy/pasting

---

### Post by Mr.mouse on 2007-09-13
i have this problem every day !

Workarounds should be  build in by default and with no ui

---

### Post by 23meg on 2007-09-13
> **happy-and-lost said:**
> klipper is a dependency of kubuntu-desktop. Why does a ubuntu-desktop not offer similar functionality?

Perhaps because Glipper isn't part of GNOME? A GNOME vs. KDE thing.

---

### Post by balthamaisteri on 2007-10-16
It sure is very annoying when this happens :P but it think that i've learned to live with it.

---

### Post by tvrg on 2007-10-16
I don't get it, are you "copy pasting" or selecting and then pressing the middle mouse button?
When selecting something, right clicking it and doing "copy" i can close the window and paste what i just copied.

please post the exact steps you are doing (including source and destination app) because this copy/paste issue hasn't been around for me for years

---

### Post by LarsP on 2007-10-16
> **tvrg said:**
> I don't get it, are you "copy pasting" or selecting and then pressing the middle mouse button?
When selecting something, right clicking it and doing "copy" i can close the window and paste what i just copied.

please post the exact steps you are doing (including source and destination app) because this copy/paste issue hasn't been around for me for years

For me it is like this:

Select something with the mouse in firefox.
Ctrl+C
Close firefox
Open gedit
Ctrl+V
Nothing is pasted.

---

### Post by tvrg on 2007-10-16
hmm, you are right, doesn't seem consistent for me, i have it with firefox but not in all other programs, and apparently it's not the window that needs to be closed but the entire process.

---

### Post by Kow on 2007-10-16
I think the main reason one of these clipboard programs are not included is for security. Copy a password and if its remembered then somebody else could come along and paste and boom they have the password you copied. Same idea goes for any sensitive data. I'm guessing at least one of those programs has some more advanced options to drop the clipboard entries when the screen is locked, user logs out, etc.

---

