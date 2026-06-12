---
title: "Dash to Dock &amp; Ubuntu Dock User Profile location ?"
date: 2017-09-04
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2017-09-04
I have a corrupt profile and need to remove it/them and start fresh. It is not in usr/share/gnomeshell/extensions or .local. Removing the extensions clears the folder from usr/share/gnomeshell/extensions, but when reinstalled the same settings come back. Dash to panel is working fine for now.

---

### Post by dino99 on 2017-09-04
You named the 2 possible ghosts home ;)
then think to use dconf (org -> gnome -> shell -> extensions -> ...) to set your extension prefs.

---

### Post by Frogs Hair on 2017-09-05
> **dino99 said:**
> You named the 2 possible ghosts home ;)
then think to use dconf (org -> gnome -> shell -> extensions -> ...) to set your extension prefs.

Thanks for the tip , this led to resetting the dconf-editor, removing the schema from the file system, and clearing the key from the editor. Not solved yet , but I have functional desktop.

Edit: dash-to-dock appears to be outdated(gnome 3.24), a gnome shell update seems to have caused the problem. The extension was installed from the repo. 

```
gnome-shell (3.25.91-0ubuntu2) to 3.25.91-0ubuntu3
gnome-shell-common (3.25.91-0ubuntu2) to 3.25.91-0ubuntu3
```

From Github 


> A new version of Dash to Dock (v60) is available, introducing a  dedicated windows thumbnails popup menu and monitor isolation. This  release supports all recent of GNOME Shell releases (3.18, 3.20, 3.22  and 3.24)

    


---

