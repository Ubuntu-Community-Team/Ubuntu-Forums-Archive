---
title: "Extending desktop actions in apps that use DBusActivatable"
date: 2017-07-13
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-07-13
Most Gnome apps are moving to DBusActivatable=true in their .desktops which renders the Exec=  and any listed desktop Actions inoperable.
So if anyone stumbles across any decent documentation as how to extend/modify actions thru this Dbus deal it would be useful.

Otherwise as it stands the option must be changes to false though in some cases the org.gnome.whatever.desktop must still be used or issues will arise
(case in point nautilus. Myself would want what was there in unity plus some, ex. screen

---

### Post by jbicha on 2017-07-13
gedit is DbusActivatable but it has Desktop Actions&#8230;

---

### Post by mc4man on 2017-07-14
> **jbicha said:**
> gedit is DbusActivatable but it has Desktop Actions&#8230;
Most gnome apps have actions but..
What's in the org.gnome.whatever.desktop regarding actions is only used to Define (Actions=) and Name (Name= in the [Desktop Action] group

the Exec= in those groups isn't used nor would any new group be usable (other than to define & name

Probably can be seen for ex.  by removing the Action groups in org.gnome.gedit.desktop, logging out/in. The launcher actions would still work but be  unnamed actions
Or by editing an Exec= in a Desktop Action group. The new command would never be executed, just the old (built-in?) one

There is this info but only seems partially in, i.e. any gapplication launch command would work via run or terminal command but nothing if used in a org.gnome. desktop file.
(-actually using gapplication commands in a .desktop may have poor consequences in gnome-shell..

[https://developer.gnome.org/gio/stable/gapplication-tool.html](https://developer.gnome.org/gio/stable/gapplication-tool.html)

---

### Post by jbicha on 2017-07-14
I don't understand what you're talking about&#8230; :confused:

---

### Post by mc4man on 2017-07-14
> **jbicha said:**
> I don't understand what you're talking about&#8230; :confused:
Simple, if i want to add an action to any Gnome app thru the org.gnome.appname.desktop file I can't (as long as DBusActivatable=true is in the .desktop
So was asking how these actions are now created as what's in these current org.gnome.appname.desktop files regarding actions is only part of the story.
It feels like something users will no longer be able to do unless they also go DBusActivatable=false

---

### Post by jbicha on 2017-07-14
I suggest you ask GNOME.

Maybe in #newcomers on irc.gnome.org ?

---

### Post by ventrical on 2017-07-15
> **mc4man said:**
> Most Gnome apps are moving to DBusActivatable=true in their .desktops which renders the Exec=  and any listed desktop Actions inoperable.
So if anyone stumbles across any decent documentation as how to extend/modify actions thru this Dbus deal it would be useful.

Otherwise as it stands the option must be changes to false though in some cases the org.gnome.whatever.desktop must still be used or issues will arise
(case in point nautilus. Myself would want what was there in unity plus some, ex. screen

I'm not getting all the options you have. How do I set it?

---

### Post by mc4man on 2017-07-15
> **ventrical said:**
> I'm not getting all the options you have. How do I set it?
```

gedit .local/share/applications/org.gnome.Nautilus.desktop
```

Insert, save, log out/in or reboot
```
[Desktop Entry]
Name=File Manager
Comment=Access and organize files
# Translators: Search terms to find this application. Do NOT translate or localize the semicolons! The list MUST also end with a semicolon!
Keywords=folder;manager;explore;disk;filesystem;
Exec=nautilus --new-window %U
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon[ar]=org.gnome.Nautilus
Icon[be]=org.gnome.Nautilus
Icon[bg]=org.gnome.Nautilus
Icon[ca]=org.gnome.Nautilus
Icon[cs]=org.gnome.Nautilus
Icon[da]=org.gnome.Nautilus
Icon[de]=org.gnome.Nautilus
Icon[el]=org.gnome.Nautilus
Icon[en_GB]=org.gnome.Nautilus
Icon[es]=org.gnome.Nautilus
Icon[eu]=org.gnome.Nautilus
Icon[fa]=org.gnome.Nautilus
Icon[fi]=org.gnome.Nautilus
Icon[fr]=org.gnome.Nautilus
Icon[fur]=org.gnome.Nautilus
Icon[gd]=org.gnome.Nautilus
Icon[he]=org.gnome.Nautilus
Icon[hu]=org.gnome.Nautilus
Icon[id]=org.gnome.Nautilus
Icon[is]=org.gnome.Nautilus
Icon[it]=org.gnome.Nautilus
Icon[ja]=org.gnome.Nautilus
Icon[kk]=org.gnome.Nautilus
Icon[ko]=org.gnome.Nautilus
Icon[lt]=org.gnome.Nautilus
Icon[lv]=org.gnome.Nautilus
Icon[nb]=org.gnome.Nautilus
Icon[nl]=org.gnome.Nautilus
Icon[oc]=org.gnome.Nautilus
Icon[pa]=org.gnome.Nautilus
Icon[pl]=org.gnome.Nautilus
Icon[pt]=org.gnome.Nautilus
Icon[pt_BR]=org.gnome.Nautilus
Icon[ru]=org.gnome.Nautilus
Icon[sk]=org.gnome.Nautilus
Icon[sr]=org.gnome.Nautilus
Icon[sr@latin]=org.gnome.Nautilus
Icon[sv]=org.gnome.Nautilus
Icon[th]=org.gnome.Nautilus
Icon[tr]=org.gnome.Nautilus
Icon[uk]=org.gnome.Nautilus
Icon[vi]=org.gnome.Nautilus
Icon[zh_CN]=org.gnome.Nautilus
Icon[zh_TW]=org.gnome.Nautilus
Icon=org.gnome.Nautilus
Terminal=false
Type=Application
DBusActivatable=false
StartupNotify=false
Categories=GNOME;GTK;Utility;Core;FileManager;
MimeType=inode/directory;application/x-gnome-saved-search;
X-GNOME-UsesNotifications=true
Actions=new-window;doc;down;music;pic;vid;divider1;comp;other
X-Unity-IconBackgroundColor=#af4853
X-Ubuntu-Gettext-Domain=nautilus

OnlyShowIn=Unity;Gnome;

[Desktop Action new-window]
Name=New Window
Exec=nautilus --new-window

[Desktop Action doc]
Name=Documents
Exec=nautilus Documents

[Desktop Action down]
Name=Downloads
Exec=nautilus Downloads

[Desktop Action music]
Name=Music
Exec=nautilus Music

[Desktop Action pic]
Name=Pictures
Exec=nautilus Pictures

[Desktop Action vid]
Name=Videos
Exec=nautilus Videos

[Desktop Action comp]
Name=Computer
Exec=nautilus /

[Desktop Action other]
Name=Other Locations
Exec=nautilus other-locations:///

[Desktop Action divider1]
Name=**********System**********
Exec=zenity --info --text 'Nothing Here'
```

---

