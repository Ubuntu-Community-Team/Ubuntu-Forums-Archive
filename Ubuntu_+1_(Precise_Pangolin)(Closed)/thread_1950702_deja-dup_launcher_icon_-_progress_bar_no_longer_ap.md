---
title: "deja-dup launcher icon - progress bar no longer appears"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jb5 on 2012-04-01
The progress bar on the unity launcher icon for deja-dup no longer appears whilst a backup is in progress.

Anybody else experiencing this?

---

### Post by jb5 on 2012-04-03
Is the progress bar appearing for other people?

Submitted a [bug [972194]](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/972194).
Please 'me to' if affected.
Ta.

---

### Post by VMC on 2012-04-03
Ye, it's working for me

---

### Post by jb5 on 2012-04-05
@ VMC: Thanks.

After digging around it appears that there are three deja-dup  desktop files in ```
/usr/share/applications/
```The one that is pulled up by dash doesn't display the progress bar. So if this is the one that gets locked to the launcher, no progress bar is shown. 
I suppose users who ARE seeing the progress bar, locked deja-dup to the launcher during a back-up whilst the bar was displayed. 
In any case, I've edited the deja-dup desktop file to include a quicklist to allow access to the preferences, and ALSO displays the progress bar whilst running.```
mkdir ~/.local/share/applications
cp /usr/share/applications/deja-dup.desktop ~/.local/share/applications/
cd ~/.local/share/applications/
gedit deja-dup.desktop
```Add the following to the bottom of the file & save. NB save it as deja-dup.desktop, DO NOT change the name or the progress bar will not be painted onto the icon```
X-Ayatana-Desktop-Shortcuts=Preferences;

[Preferences Shortcut Group]
Name=Backup-Preferences
Comment==Change your backup settings
Exec=deja-dup-preferences
TargetEnvironment=Unity
StartupNotify=true
Type=Application
Categories=GNOME;GTK;System;Archiving;Utility;Settings;X-GNOME-SystemSettings;
NotShowIn=GNOME;Unity;
```Lock this file to the launcher, i.e. drag the file from a nautilus instance onto the launcher bar.
This seems to work, it is just a pity that the deja-dup pulled up by the dash doesn't also have the progress bar.

Does anyone know where or how the progress bar gets painted onto the icon? It seems to be specifically tied to the name of the desktop file somehow.

Ta

---

### Post by VMC on 2012-04-05
deja-dup uses duplicity as the backend, so I search for both to see if any readable python files. None. Using duplicity on the command line just backs up my files. So I would guess its deja-dup as the culprit. Maybe just re-install deja-dup again. See if that fixes things. 

The search for both files returned a ton on related files.

---

