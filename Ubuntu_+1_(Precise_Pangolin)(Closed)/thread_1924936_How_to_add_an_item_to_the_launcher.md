---
title: "How to add an item to the launcher"
date: 2012-02-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by williammanda on 2012-02-13
I wanted to add root nautilus icon to the launcher but things have changed a little since 11.10. The current home folder icon comes with a multi-option, which is nice, but I'm confused due to the 11.10 instructions. It references using the .local/share/applications directory for creating it but in 12.4 there isn't that folder. Would someone comment on how either to added to the current home folder or create a new icon for root nautilus.
Thanks 

Here is the link:

[http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available](http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available)

---

### Post by mc4man on 2012-02-13
I don't think I'd make a separate icon, will always run thru your current.
(you could also just get an ext. for context menu
[http://ubuntuforums.org/showthread.php?p=11684982#post11684982](http://ubuntuforums.org/showthread.php?p=11684982#post11684982)

If you wish to add as a quicklist something like this, in a terminal

This is 1 complete command, C&P all 
```
mkdir -p ~/.local/share/applications && \
> cp /usr/share/applications/nautilus-home.desktop \
> ~/.local/share/applications/ && \
> gedit ~/.local/share/applications/nautilus-home.desktop

```

edit the .desktop to look like this, changes in blue, red see edit

```
[Desktop Entry]
Name=Home Folder
Comment=Open your personal folder
Exec=nautilus %U
Icon=[COLOR="Red"]user-home[/COLOR]
Terminal=false
StartupNotify=true
Type=Application
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Core;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.0.0
X-Ubuntu-Gettext-Domain=nautilus
X-Ayatana-Desktop-Shortcuts=Window;[COLOR="Blue"]Root;[/COLOR]

[Window Shortcut Group]
Name=Open a new window
Exec=nautilus
TargetEnvironment=Unity

[COLOR="Blue"][Window Shortcut Group]
Name=Open a Root Nautilus
Exec=gksu nautilus
TargetEnvironment=Unity[/COLOR]

```

The Name=Open a Root Nautilus in the quicklist entry can be changed if desired
Then just log out/in

Edit: small note
due to some par for the course user confusion whatever the Home Folder (nautilus-home-folder.desktop) now uses a blank folder icon

If wanting the old one change as I've marked in red above.
If so & you've already closed the desktop just run 

gedit ~/.local/share/applications/nautilus-home.desktop

---

### Post by williammanda on 2012-02-13
Thanks! Worked great!

---

