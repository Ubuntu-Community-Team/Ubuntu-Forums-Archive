---
title: "How do I add my script to the Unity launcher bar?"
date: 2012-07-07
forum: Tutorials
---

### Post by billir on 2012-07-07
Trying to simplify [http://ubuntuforums.org/showthread.php?t=1700605](http://ubuntuforums.org/showthread.php?t=1700605)
Should be root to do this
1. Create a directory /usr/scripts (or where ever you want)
2. Put your script in the folder (test that it works)
3. Create an "untitled document" (gedit)
4. Add the following to the untitled document making the changes necesary
[Desktop Entry]
Name=<Your app name>
Comment=<Your app Description>
Exec=<path/name>
Icon=<icon path/name>
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Utility;
X-GNOME-DocPath=
X-GNOME-Bugzilla-Bugzilla=
X-GNOME-Bugzilla-Product=
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-OtherBinaries=
X-Ubuntu-Gettext-Domain=
5. "Save AS" the untitled document to <your scriptname>.desktop
6. Test by clicking on the iconed file in /usr/scripts directory
7. Drag to Launch bar

To view other application.desktop files use terminal to  ls /usr/share/applications. You can "less" anyone of those files
Put your <application.desktop> file in /usr/share/applications/ directory and you can see and find with the Dash Home (search) button.

---

