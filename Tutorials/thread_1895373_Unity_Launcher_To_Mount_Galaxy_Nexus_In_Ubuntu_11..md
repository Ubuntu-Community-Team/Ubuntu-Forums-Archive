---
title: "Unity Launcher To Mount Galaxy Nexus In Ubuntu 11.10"
date: 2011-12-14
forum: Tutorials
---

### Post by nyteryder79 on 2011-12-14
[IMG]http://i.imgur.com/aEOgJ.png[/IMG]

I wrote some scripts to set up an easy right-click mount/unmount of the Galaxy Nexus in Ubuntu 11.10's launcher.  I also wrote a script which sets everything up automatically, which installs MTPFS package, moves an icon to the pixmaps folder, installs 2 scripts for mounting/unmounting the device, and installs a launcher file to the .local folder.

All you have to do is download [[COLOR="Blue"]**THIS FILE**[/COLOR]]("http://dl.dropbox.com/u/25218780/mount_gnex.tar.bz2"), extract it, then open a terminal and navigate to where you extracted the contents and run the following:

```
./install_me.sh
```

You'll be prompted for your password, then when it's finished, it will open Nautilus and present you with the launcher icon to move to the Unity launcher.

To undo what this does, remove the icon from the Unity launcher, then run the following in the same directory:

```
./remove_me.sh
```

Let me know if it works for you.  I haven't tested yet because Verizon hasn't released the phone yet, but as soon as they do, I'll get one and test.  I'm assuming this will work after reading multiple posts about mounting the Galaxy Nexus as well as the ASUS Transformer in Ubuntu .

---

### Post by Dayofswords on 2011-12-14
There might be an issue here, but I can't test it anyway but I noticed in galaxy-nexus.desktop you have

```
[Desktop Entry]
Version=1
Type=Application
Categories=System;
Name=Mount Galaxy Nexus Filesystem
GenericName=Mount Galaxy Nexus
Comment=Mount and navigate the Galaxy Nexus.
Icon=/usr/share/pixmaps/galaxy-nexus.png

X-Ayatana-Desktop-Shortcuts=Mount;Unmount

[Mount Shortcut Group]
Name=Mount Galaxy Nexus
Exec=**/home/towens/**.scripts/mount_galaxy_nexus.sh
TargetEnvironment=Unity

[Unmount Shortcut Group]
Name=Unmount Galaxy Nexus
Exec=**/home/towens/**.scripts/unmount_galaxy_nexus.sh
TargetEnvironment=Unity

```

Now I'm no expert but you may want that to say `~` rather than your home of `/home/towens` for it to go to the correct .scripts/ folder that you created in install_me.sh

---

### Post by nyteryder79 on 2011-12-14
> **Dayofswords said:**
> There might be an issue here, but I can't test it anyway but I noticed in galaxy-nexus.desktop you have

```
[Desktop Entry]
Version=1
Type=Application
Categories=System;
Name=Mount Galaxy Nexus Filesystem
GenericName=Mount Galaxy Nexus
Comment=Mount and navigate the Galaxy Nexus.
Icon=/usr/share/pixmaps/galaxy-nexus.png

X-Ayatana-Desktop-Shortcuts=Mount;Unmount

[Mount Shortcut Group]
Name=Mount Galaxy Nexus
Exec=**/home/towens/**.scripts/mount_galaxy_nexus.sh
TargetEnvironment=Unity

[Unmount Shortcut Group]
Name=Unmount Galaxy Nexus
Exec=**/home/towens/**.scripts/unmount_galaxy_nexus.sh
TargetEnvironment=Unity

```

Now I'm no expert but you may want that to say `~` rather than your home of `/home/towens` for it to go to the correct .scripts/ folder that you created in install_me.sh

You are right.  Thank you for pointing that out.  I updated the download file with this correction.

---

### Post by taxi333 on 2012-01-12
it doesn't work for the verizon version
I'm using UBUNTU 11.10 x64

---

