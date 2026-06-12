---
title: "Remove Bittorrent Application"
date: 2007-07-16
forum: Repositories &amp; Backports
---

### Post by CityofAsh on 2007-07-16
Anyone know how i can remove bittorrent without removing ubuntu-desktop??


 
```
root@CityofAsh-Linux:/home/cityofash# apt-get remove bittorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bittorrent gnome-btdownload ubuntu-desktop
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.

```

---

### Post by jimrz on 2007-07-16
> **CityofAsh said:**
> Anyone know how i can remove bittorrent without removing ubuntu-desktop??


 
```
root@CityofAsh-Linux:/home/cityofash# apt-get remove bittorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bittorrent gnome-btdownload ubuntu-desktop
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.

```

don't think you can, but it's not as bad as it sounds. ubuntu-desktop is just a meta package used on install and removing it will not hurt your setup. i have heard that it's absence can cause problems if you plan to dist upgrade to the next version rather than a fresh install (always my choice), though.

---

### Post by bapoumba on 2007-07-17
> **jimrz said:**
> don't think you can, but it's not as bad as it sounds. ubuntu-desktop is just a meta package used on install and removing it will not hurt your setup. i have heard that it's absence can cause problems if you plan to dist upgrade to the next version rather than a fresh install (always my choice), though.
Yes, ubuntu-desktop can be removed, but it is recommended to have in installed for a dist-upgrade:
[https://help.ubuntu.com/community/CommonQuestions?#head-957d1f0d9534d9e9a43a1ade8e3622bc04a8d812]("https://help.ubuntu.com/community/CommonQuestions?#head-957d1f0d9534d9e9a43a1ade8e3622bc04a8d812")

---

### Post by CityofAsh on 2007-07-17
Ah ok thanks. I wasn't sure if ubuntu-desktop was a part of GDM.

---

### Post by bapoumba on 2007-07-17
> **CityofAsh said:**
> Ah ok thanks. I wasn't sure if ubuntu-desktop was a part of GDM.
Actually ubuntu-desktop depends on gdm ;)
Please run:
```
aptitude show ubuntu-desktop
```
and you will see all of its dependencies.

---

