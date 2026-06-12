---
title: "Mutter crashes (Ricotz Testing and Gnome3 Team PPA's)"
date: 2012-01-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-21
Just tested the new mutter release, version 3.3.4 from both of these PPA's:
- Ricotz Gnome-shell Testing PPA
- Gnome3 Team PPA

Both suffer from some issues (crash). In fact the window borders vanish and so does Gnome-shell main panel too.
Downgrading to the previous version 3.3.3+git20120117 is a good workaround.

---

### Post by ricotz on 2012-01-21
> **Harry33 said:**
> Both suffer from some issues (crash). In fact the window borders vanish and so does Gnome-shell main panel too.
Downgrading to the previous version 3.3.3+git20120117 is a good workaround.

Please try to provide a trace of this such crashes if you can.

---

### Post by Harry33 on 2012-01-21
> **ricotz said:**
> Please try to provide a trace of this such crashes if you can.

Hi Rico,
Well I just noticed that I did not upgrade packages gnome-shell and gnome-shell-common to the version 3.3.4.
Having done that, there are no longer problems, no crashes.

Also the clutter (1.9.7+git20120120) works fine.

---

### Post by jbicha on 2012-01-21
Mutter and gnome-shell generally have to be updated at the same time during the development cycle (in this case, both were being updated for the new GNOME menus). For the 3.1 cycle, gjs also usually had to be updated at the same time.

---

### Post by Harry33 on 2012-01-21
> **jbicha said:**
> Mutter and gnome-shell generally have to be updated at the same time during the development cycle (in this case, both were being updated for the new GNOME menus). For the 3.1 cycle, gjs also usually had to be updated at the same time.

Right it is.
And now the latest gnome-shell depends on gir1.2-gjs-1.0 too.

---

### Post by paul_in_london on 2012-01-21
> **Harry33 said:**
> Right it is.
And now the latest gnome-shell depends on gir1.2-gjs-1.0 too.

Sounds as if we've run into the same problem (well maybe not exactly the same because I don't think I'm using the Gnome3 Team ppa). I'm back in oneiric right now because of the ricotz-testing breakage after I discovered that in precise I no lonnger have the option to choose gnome classic or gnome fallback (for example) from the lightdm screen. Don't know when that happened, but I only noticed it today!

EDIT: It's also a bit unfortunate that I can't chroot into my precise install from here to check for updates because the oneiric install is 32 bit and my precise install is 64 bit.

EDIT2: Just mounted my precise partition to check and I'm not using the Gnome3 Team ppa any more.

---

### Post by Harry33 on 2012-01-22
> **paul_in_london said:**
> Sounds as if we've run into the same problem (well maybe not exactly the same because I don't think I'm using the Gnome3 Team ppa). I'm back in oneiric right now because of the ricotz-testing breakage after I discovered that in precise I no lonnger have the option to choose gnome classic or gnome fallback (for example) from the lightdm screen. Don't know when that happened, but I only noticed it today!

EDIT: It's also a bit unfortunate that I can't chroot into my precise install from here to check for updates because the oneiric install is 32 bit and my precise install is 64 bit.

EDIT2: Just mounted my precise partition to check and I'm not using the Gnome3 Team ppa any more.

I don't think gnome-shell affects lightdm or session packages in a way that you would have lost gnome classic session. Something else has happened.

---

### Post by paul_in_london on 2012-01-22
> **Harry33 said:**
> I don't think gnome-shell affects lightdm or session packages in a way that you would have lost gnome classic session. Something else has happened.

Yes, thanks Harry. I posted separately about that yesterday. It's a known bug (with 3 duplicates) that has nothing to do with GS. Clicking on Guest brings the session chooser back!

---

