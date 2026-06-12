---
title: "Make KDE apps look like gnome"
date: 2009-11-06
forum: The Cafe
---

### Post by Sashin on 2009-11-06
Be default KDE apps blend really well and look nice in gnome, however I think I've deleted a package by mistake which causes this. Anyone know which one?

---

### Post by Tibuda on 2009-11-06
You need qtconfig4, and using it you set your Qt theme to "Gtk".

---

### Post by Sashin on 2009-11-06
Doesn't work.

---

### Post by Tibuda on 2009-11-06
> **Sashin said:**
> Doesn't work.

Which app are you talking about? If it uses Qt4 (as KDE4 apps does), you need to use qt4-qtconfig, but if it uses the old Qt3 (as KDE3 apps does), you use qt3-qtconfig.

EDIT: I'm not sure you can make Qt3 apps to use your Gtk+ theme.

EDIT AGAIN: What version of Ubuntu are you using? I think the Gtk+ theme for Qt4 is only available after jaunty.

---

### Post by RiceMonster on 2009-11-06
> **Sashin said:**
> Doesn't work.

You may have to set up a ~/.gtkrc-2.0 to make it work. 

For example:
```
gtk-theme-name="Clearlooks"
gtk-icon-theme-name="Mist"
gtk-font-name="Bitstream Vera Sans 10"
gtk-toolbar-style=0
```

Change everything to your liking.

---

### Post by chucky chuckaluck on 2009-11-06
i don't think qtconfig changes kde apps. you'd have to use systemsettings or that (i think it's part of either kdebase, or kdeworkspace).

---

### Post by Sashin on 2009-11-06
Program is Kalzium, it used to blend well now it looks like a kde app. I'm using Karmic.

---

### Post by FuturePilot on 2009-11-06
If it's a KDE app then the Qt settings won't have any affect on its appearance. If it's a pure Qt app then it will.

---

### Post by Tibuda on 2009-11-06
> **chucky chuckaluck said:**
> i don't think qtconfig changes kde apps. you'd have to use systemsettings or that (i think it's part of either kdebase, or kdeworkspace).

> **FuturePilot said:**
> If it's a KDE app then the Qt settings won't have any affect on its appearance. If it's a pure Qt app then it will.

This makes sense to me now. The Qt apps I use (VLC, Skype and Virtualbox) are not KDE apps, so qtconfig works for me. KDE apps use a different version of Qt or what?

---

### Post by Sashin on 2009-11-06
But by default KDE apps do look like gnome?

---

### Post by FuturePilot on 2009-11-06
> **danielrmt said:**
> This makes sense to me now. The Qt apps I use (VLC, Skype and Virtualbox) are not KDE apps, so qtconfig works for me. KDE apps use a different version of Qt or what?
Well, KDE is built upon Qt but it also extends on Qt offers and adds some extra features and whatnot that Qt doesn't offer. As for why KDE apps don't just use Qt settings I'm not sure.

> **Sashin said:**
> But by default KDE apps do look like gnome?

No, only Qt apps do.

---

### Post by Sashin on 2009-11-06
Well at least by default Kalzium looks like gnome. And so does amarok.

---

### Post by t.rei on 2009-11-06
May I suggest using "qtcurve" for both: kde and gnome apps? It's very customizable, too.

---

### Post by Sashin on 2009-11-06
I shouldn't have to though, Kalzium once blended into gnome.

---

### Post by SunnyRabbiera on 2009-11-06
Still the qtcurve suggestion is a good one, I am a big fan of it.

---

### Post by edin9 on 2009-11-06
KDE3 needs gtk-qt-engine-kde3.deb, KDE4 needs gtk-qt-engine-kde4.deb.

---

