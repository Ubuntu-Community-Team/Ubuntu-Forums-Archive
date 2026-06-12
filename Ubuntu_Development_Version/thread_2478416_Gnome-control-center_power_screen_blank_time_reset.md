---
title: "Gnome-control-center power screen blank time reset to 5 minutes"
date: 2022-08-26
forum: Ubuntu Development Version
---

### Post by corradoventu on 2022-08-26
Gnome-control-center Settings - Power - I set Screen Blank to any value different from 5 minutes. My value is ignored, Screen Blank is reset to 5 minutes.
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1987388](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1987388)

---

### Post by KingHanco on 2022-09-05
You beat me sending this bug. I using this command to turn it off.

gsettings set org.gnome.desktop.session idle-delay 0

---

### Post by jbicha on 2022-09-06
This was fixed in today's updates.

---

### Post by KingHanco on 2022-09-07
Nice I just now checked. Fully working, :)

---

### Post by corradoventu on 2022-09-07
On my Ubuntu Kinetic gnome-control-center is not upgraded:
```
The following packages have been kept back:
  burner-common gnome-control-center libburner-media3-1 libnautilus-extension4 nautilus
  nautilus-data ubuntu-desktop ubuntu-desktop-minimal
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
```

---

### Post by jbicha on 2022-09-07
Do a dist-upgrade?

If that still doesn't work, check what happens when you try to update the package directly:

```

sudo apt install gnome-control-center

```

etc

---

### Post by KingHanco on 2022-09-09
I just do this. Grab all the updates.

sudo apt-get update --fix-missing -y && sudo apt-get full-upgrade --auto-remove -y && sudo apt-get install unattended-upgrades --auto-remove -y && sudo snap refresh

---

