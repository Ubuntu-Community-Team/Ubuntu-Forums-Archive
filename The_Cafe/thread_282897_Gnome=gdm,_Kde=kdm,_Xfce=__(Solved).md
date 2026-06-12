---
title: "Gnome=gdm, Kde=kdm, Xfce= ? (Solved)"
date: 2006-10-23
forum: The Cafe
---

### Post by user1397 on 2006-10-23
what dm (display manager) does xubuntu (xfce) use? i know that ubuntu (and probably edubuntu, since they're both gnome), uses gdm, or gnome display manager, and i know that kubuntu (kde) uses kdm, or kde display manager.  but i have absolutely no idea what xubuntu uses.  it's not xdm, as i have looked at it in the ubuntu package search website, and it says that xdm is the X server display manager, not exclusively for any desktop environment. :confused:

---

### Post by plb on 2006-10-23
Not sure, never tried it but I don't think it would be kdm. It's likely gdm since xfce is gtk+ based.

---

### Post by taurus on 2006-10-23
If you don't want to use gdm or kdm, then there is a generic xdm!!!

---

### Post by ago on 2006-10-23
It uses gdm. Xfce is based on gtk (but not other gnome libraries), gdm is also based on gtk. In the past gdm used to depend also on gnome libraries, what the devs have done was to strip most (all?) gnome dependencies out of gdm. So these days gdm is a good fit for Xfce as it is for any other gtk based window manager/desktop environment.

---

### Post by user1397 on 2006-10-23
> **ago said:**
> It uses gdm. Xfce is based on gtk (but not other gnome libraries), gdm is also based on gtk. In the past gdm used to depend also on gnome libraries, what the devs have done was to strip most (all?) gnome dependencies out of gdm. So these days gdm is a good fit for Xfce as it is for any other gtk based window manager/desktop environment.ah, i see.  well thanks for the info, now i can update my guide on installing the different DE's.

---

### Post by fuscia on 2006-10-23
wdm is pretty small, if you're looking for something like that.

---

### Post by bruce89 on 2006-10-23
> **ago said:**
> It uses gdm. Xfce is based on gtk (but not other gnome libraries), gdm is also based on gtk. In the past gdm used to depend also on gnome libraries, what the devs have done was to strip most (all?) gnome dependencies out of gdm. So these days gdm is a good fit for Xfce as it is for any other gtk based window manager/desktop environment.

Not quite true, Xubuntu uses gdm, I believe it probably should use xdm.

---

### Post by Brunellus on 2006-10-23
or you could just be hard core and startx from the commandline

---

### Post by user1397 on 2006-10-23
i wasn't looking for replacing any dm, i just wanted to know which one xfce uses, out of curiosity.  thanks for all the help.

---

### Post by ago on 2006-10-23
> **erik1397 said:**
> i just wanted to know which one xfce uses

I can tell you which one Xubuntu uses. Xfce is a desktop manager, and as such it does not really use a DM per se. You can associate any desktop manager with any display manager, they are mostly independent... Obviously you will want to avoid to use a DE and a DM with different dependencies. Xubuntu has chosen gdm, as mentioned xdm and possibly wdm are also good matches for Xfce. Kdm is not.

---

