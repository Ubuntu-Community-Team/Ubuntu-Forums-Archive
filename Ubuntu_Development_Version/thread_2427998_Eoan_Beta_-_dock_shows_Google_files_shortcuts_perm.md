---
title: "Eoan Beta - dock shows Google files shortcuts permanently"
date: 2019-09-28
forum: Ubuntu Development Version
---

### Post by mobile-harvey on 2019-09-28
Hi

I have upgraded from Disco to Eoan Beta and have found that the dock permanently displays and icon for my Google Account's shared files. I can make the icon disappear from the dock via Gnome Settings -> Online Accounts -> Google -> Untick 'Files'. 

Has anyone else seen this and know how to fix it? Or should I raise a bug?

Thanks
Nick

---

### Post by mobile-harvey on 2019-09-29
This appears to be related to any mounted volume (i.e. insert an SD card an it also appears in the Dock). So I assume this is a feature rather than a bug, but I'm not sure I will find it useful and would rather switch it off to avoid clutter in my Dock. Does anyone know hoe to do this?

Thanks
Nick

---

### Post by deadflowr on 2019-09-29
There seems to be a new dconf setting for the dock in org/gnome.shell.extensions.dash-to-dock
that allows mounts to show.
It's viewable and changeable with
```
gsettings get org.gnome.shell.extensions.dash-to-dock show-mounts
```
to see current value
Default value looks to be true.
Simply set it to false.
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false
```

---

### Post by mobile-harvey on 2019-09-30
That did it! Many thanks.

---

### Post by jbicha on 2019-09-30
Maybe it's worth opening an Ubuntu gnome-control-center bug to request that the Ubuntu developers add an on/off switch for Ubuntu 20.04 LTS for showing extra mounts in the Dock.

---

### Post by mobile-harvey on 2019-10-01
Good idea. Done: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1846205](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1846205)

---

### Post by dino99 on 2019-10-01
or suggest on upstream: [https://github.com/GNOME/gnome-control-center/pulls](https://github.com/GNOME/gnome-control-center/pulls)

---

### Post by pastor-t on 2019-11-01
That got it... uberthanx

---

### Post by Frogs Hair on 2019-11-01
19.10 released thread closed.

---

