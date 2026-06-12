---
title: "Startup Apps"
date: 2012-07-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cecilpierce on 2012-07-11
What happen to the 'Startup Applications' from the top right pull down menu ?

---

### Post by OM55 on 2012-07-11
> **cecilpierce said:**
> What happen to the 'Startup Applications' from the top right pull down menu ?

It is still there, that is if you install the 'gnome-fallback-session' desktop.

You can also launch it from the command line:
```
gnome-session-properties
```

---

### Post by cecilpierce on 2012-07-11
OK, Thanks for that info, I would have never found it.

---

### Post by mc4man on 2012-07-11
It was removed from indicator-session today, either intentionally or otherwise

Edit:
While not in the package changelog this was in the source changelog

```
2012-06-04  Charles Kerr  <charles.kerr@canonical.com>

	remove the startup applications menuitem; it's no longer in the spec
```

---

### Post by scradock on 2012-07-12
> **OM55 said:**
> It is still there, that is if you install the 'gnome-fallback-session' desktop.

You can also launch it from the command line:
```
gnome-session-properties
```

The package is actually "gnome-session-fallback"

Installing this fails to complete, with configuration errors for ubuntu-drivers-common due to python3 errors.

The command "gnome-session-properties" cannot be found through the Dash, so without a menu entry to it there is no way anyone (who doesn't know to call it from the terminal to add or edit a startup command) can find it.

---

### Post by mc4man on 2012-07-12
> **scradock said:**
> The package is actually "gnome-session-fallback"

Installing this fails to complete, with configuration errors for ubuntu-drivers-common due to python3 errors.

The command "gnome-session-properties" cannot be found through the Dash, so without a menu entry to it there is no way anyone (who doesn't know to call it from the terminal to add or edit a startup command) can find it.

session-properties.desktop, (display name Startup Applications) is hidden by default so it will not show in the Dash
If desired you can edit the "NoDisplay=true" line to "NoDisplay=false"
& it will then show.

Edit: The app will be be made visible in an upcoming update 
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1018031](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1018031)

(gnome-session-properties is in the gnome-session-bin package which is default installed & has nothing to do with gnome-session-fallback

---

