---
title: "wily gedit preferences option is missing in flashback"
date: 2015-05-07
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-05-07
I noticed in gedit there is no preferences option. So no way to not wrap lines, show line numbers, etc.

I was going to open my own bug but I found this that was the same thing opened against Trusty.

I have never had a problem with Trusty but am with Wily Werewolf 15.10 so I added wiley to it along with my name.

If it's an issue with you feel free to add your name. I have been using leafpad until they fix gedit.

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1298666](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1298666)

Solved by albertsmuktupavels' information in post #7.

---

### Post by cariboo on 2015-05-07
I have the preferences here, see screenshots

---

### Post by mc4man on 2015-05-07
Not sure who "they" would be. Canonical & Gnome don't care about flashback so I guess you'd have to catch the attention of the 1 or maybe 1.5 dev's who do..
Till then dconf-editor is good.

---

### Post by Cavsfan on 2015-05-07
My bad. I didn't realize there was a difference with what session you were logged in with.
I logged into a unity session and could then see the preferences. I changed it to show line numbers and not wrap lines.

Then logged back in to a FB session and there is no preferences.

[ATTACH=CONFIG]261819[/ATTACH]

@mc4man I didn't know you could edit text files with dconf-editor. Please explain how you do that.

---

### Post by mc4man on 2015-05-07
See screen - 
Too bad ~/.config/gedit/accels doesn't have an action for preferences then *possibly* a key binding could be set like one can do for nautilus's preferences which is similarly missing.
(though gedit accels seem to be not subject to editing anyway so somewhat moot...

---

### Post by Cavsfan on 2015-05-07
> **mc4man said:**
> See screen - 
Too bad ~/.config/gedit/accels doesn't have an action for preferences then *possibly* a key binding could be set like one can do for nautilus's preferences which is similarly missing.
(though gedit accels seem to be not subject to editing anyway so somewhat moot...

Oh I thought you were saying use dconf-editor to edit text files with.  Now I understand what you mean.
I thought I was going to have to force myself to start liking Unity. I was just in the process of doing that.

I guess I can do whatever. I also noticed that if you set wrap-mode to 'none' it will not wrap around.

[ATTACH=CONFIG]261823[/ATTACH]

---

### Post by muktupavels on 2015-05-08
This is known problem in GNOME Flashback. From terminal:
  ```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides
'{"Gtk/ShellShowsAppMenu":<0>}'
```

This will override existing value, by default it is empty. If it has been changed I would suggest to edit it from dconf-editor.

Main problem here is that we are forced to use org.gnome.Shell dbus name. gnome-settings-daemon / unity-settings-daemon when org.gnome.Shell is available sets Gtk/ShellShowsAppMenu to 1 and applications thinks that appmenu will be shown by shell - this is wrong for GNOME Flashback.

---

### Post by Cavsfan on 2015-05-08
> **albertsmuktupavels said:**
> This is known problem in GNOME Flashback. From terminal:
  ```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides
'{"Gtk/ShellShowsAppMenu":<0>}'
```

This will override existing value, by default it is empty. If it has been changed I would suggest to edit it from dconf-editor.

Main problem here is that we are forced to use org.gnome.Shell dbus name. gnome-settings-daemon / unity-settings-daemon when org.gnome.Shell is available sets Gtk/ShellShowsAppMenu to 1 and applications thinks that appmenu will be shown by shell - this is wrong for GNOME Flashback.

Thank you Alberts! 
I put that where you mentioned and now preferences shows up in gedit in Flashback. I had to leave the single quotes out.
```
{"Gtk/ShellShowsAppMenu":<0>} 
```

[ATTACH=CONFIG]261831[/ATTACH]

---

