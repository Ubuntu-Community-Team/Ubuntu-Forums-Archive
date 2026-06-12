---
title: "Firefox uses Oxygen gtk theme in Unity"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jokerdino on 2012-09-25
I just installed kubuntu-desktop over Unity and Firefox now looks ugly in Unity. It seems to use oxygen-gtk theme in Unity and I don't particularly like it especially when most other applications look perfectly normal. 

I also removed kubuntu-firefox-installer package and that doesn't help. 

See image -- [http://i.imgur.com/wvHBH.png](http://i.imgur.com/wvHBH.png)

Do you know how to make Firefox look normal in Unity?

---

### Post by bra|10n on 2012-09-25
Well firstly I don't use Unity but I believe if you go to the Add-Ons page in firefox under the Appearance tab is there not an Ubuntu/Unity theme? Perhaps it is disabled, or can be reset?

---

### Post by jokerdino on 2012-09-25
> **bra|10n said:**
> Well firstly I don't use Unity but I believe if you go to the Add-Ons page in firefox under the Appearance tab is there not an Ubuntu/Unity theme? Perhaps it is disabled, or can be reset?
There isn't any regarding this in the Addons > Theme. I think it is more of a theming issue but I can't quite figure it.

---

### Post by bra|10n on 2012-09-25
You could try looking at the profile.ini file from within Unity and from within kde and see if it is pointing to the same or a different profile (check name). If you intend on switching between both desktops you may need two profiles, with the second profile needing a different location to the other.

Or you could just delete the prefs.js file in ~/.mozilla but be **warned**, this will reset firefox to its default setting in every way.

---

### Post by jokerdino on 2012-09-25
> **bra|10n said:**
> You could try looking at the profile.ini file from within Unity and from within kde and see if it is pointing to the same or a different profile (check name). If you intend on switching between both desktops you may need two profiles, with the second profile needing a different location to the other.

Or you could just delete the prefs.js file in ~/.mozilla but be **warned**, this will reset firefox to its default setting in every way.
Well, I just purge Kubuntu because I don't seem to have much of a need for it any time soon. Firefox looks normal again.

---

