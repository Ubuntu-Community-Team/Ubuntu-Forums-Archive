---
title: "[UbuntuGnome] 14.04 Upgrade Error"
date: 2013-11-05
forum: Ubuntu Development Version
---

### Post by SurfaceUnits on 2013-11-05
Receive the following errors on two 13.10 installs

W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by cariboo on 2013-11-05
The exra repositories haven't been updated to Trusty yet, go to System Settings->Software & Updates->Other Software, and disable the Independent repositories.

---

### Post by SurfaceUnits on 2013-11-05
Did this

Open a terminal (ctrl-alt-t) and issue the command
gksudo gedit /etc/apt/sources.list
This will ask for your password and then open an editor with your sources.list loaded.
Scroll down until you find lines that start with
deb [http://extras.ubuntu.com](http://extras.ubuntu.com) or deb-src [http://extras.ubuntu.com](http://extras.ubuntu.com)
Insert a # character at the beginning of each of these lines

from [https://answers.launchpad.net/ubuntu/+source/apt/+question/214327](https://answers.launchpad.net/ubuntu/+source/apt/+question/214327)

---

### Post by SurfaceUnits on 2013-11-05
> **cariboo907 said:**
> The exra repositories haven't been updated to Trusty yet, go to System Settings->Software & Updates->Other Software, and disable the Independent repositories.

Thanks

---

