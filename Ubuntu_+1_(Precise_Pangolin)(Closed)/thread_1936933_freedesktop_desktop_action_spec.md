---
title: "freedesktop desktop action spec"
date: 2012-03-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-03-06
There have been a couple of updates today mentioning this, most recent nautilus

If anyone has link to info on would be interesting.
Seems to be a new way to 'create' actions ? in .desktops
Notice that now nautilus.desktop uses this instead of X-Ayatana-Desktop-Shortcuts= though most users are using nautilus-home.desktop which retains X-Ayatana-Desktop .. way


> [COLOR="Blue"]Actions=Window;[/COLOR]
X-Ubuntu-Gettext-Domain=nautilus

[[COLOR="Blue"]Desktop Action Window[/COLOR]]
Name=Open a New Window
Exec=nautilus
OnlyShowIn=Unity;

Edit: currently not functional - maybe something down the road?

---

### Post by jbicha on 2012-03-07
It's not quite in Unity yet, but Ubuntu is switching to using the new freedesktop standard instead of the X-Ayatana method.

[https://bugs.launchpad.net/unity/+bug/942042](https://bugs.launchpad.net/unity/+bug/942042)

 The cool part about it being a standard is that apps that were  reluctant to take the patch before are more likely to take it now. Perhaps GNOME Shell's Activities Overview will support jumplists in GNOME 3.6.

---

### Post by jbicha on 2012-03-07
```

nautilus ([1:3.3.91-0ubuntu3]("https://launchpad.net/ubuntu/+source/nautilus/1:3.3.91-0ubuntu3"))  precise; urgency=low

  * Update nautilus-home.desktop for freedesktop action spec too
     Thanks Doug McMahon for reporting this!

```

---

### Post by mc4man on 2012-03-08
Thanks for the link bug report, ect., should prove interesting some of the new, upcoming things.
Noticed also the new addition to light-themes of the 'unfocused theme', again not really seen yet though with a local in progress mod of  ambiance dark I guess I see in nautilus - 
(when opening another window some elements in the now unfocused window like the sidebar items/text, toolbar text, ect.  will go dim.

---

### Post by mc4man on 2012-03-11
small atm? snafu in nautilus-home.desktop (at least seen here, new install

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/952665](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/952665)

Edit 
with the 5.6 unity the new method for quicklists can be used (though the previous X-Ayatana-Desktop-Shortcuts= & [Whatever Shortcut Group] is still accepted

---

