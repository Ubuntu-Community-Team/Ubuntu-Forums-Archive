---
title: "Icon's don't change"
date: 2009-11-11
forum: Ubuntu System Panel
---

### Post by Ms_Angel_D on 2009-11-11
For some reason no matter what I put into the date/time icon I don't get anything to show up.(I have attached a screen shot)

I tried adding a direct path

```
/usr/share/icons/hicolor/scalable/apps/gnome-panel-clock.svg
```

as well as this:
```
gnome-panel-clock.svg
```

and this

```
gnome-panel-clock
```

The seems to be the case with all the different icon settings. Is there some place special the files to need to before USP will load them?

Thanks in advance,
Angel

---

### Post by Malac on 2009-11-13
The setting in Preferences is for the icon for the minimized plugin to use in the left hand pane not the one on the Button within Date/Time plugin.
To alter that one you would have to edit the usptime.glade file. Depending where you have installed from the file will be in usp-extras folder in the SVN or in /usr/lib/python2.4/site-packages/usp/plugins.
If you do it in a text editor(gedit?) and search for "config-date" replace this with your icon name you shouldn't need a path or extension.

Sorry for the confusion and hope this helps.

---

