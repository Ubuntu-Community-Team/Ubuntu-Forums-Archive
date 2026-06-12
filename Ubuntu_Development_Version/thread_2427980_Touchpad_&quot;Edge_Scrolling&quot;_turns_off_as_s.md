---
title: "Touchpad &quot;Edge Scrolling&quot; turns off as soon as System Settings is closed"
date: 2019-09-28
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2019-09-28
Just testing Eoan on an old Dell Latitude E6400 and notice when I switch Edge Scrolling on it works as I'd expect as long as I leave System Settings open but as soon as I close System Settings the setting reverts to off (the default setting). What package do you think I should file a bug report against?

---

### Post by kansasnoob on 2019-09-28
That laptop has nVidia graphics so I switched back to nouveau just to be sure it wasn't a driver issue. BTW both the nouveau and nVidia drivers have minor issues, nouveau being the lesser of two evils right now.

---

### Post by P-I H on 2019-09-28
It's working on my old Asus X202E with Intel graphics, but I have to place the cursor in the window I want to scroll.

---

### Post by kansasnoob on 2019-09-28
> **P-I H said:**
> It's working on my old Asus X202E with Intel graphics, but I have to place the cursor in the window I want to scroll.

The rather default out-of-box settings for any OS I've ever tried is two-finger scrolling which works fine. I just don't like it, preferring edge scrolling which I know works fine in both Xenial and Bionic on those E6400's. It's always been necessary to focus the pointer properly - more and more web pages now place content-in-content just to complicate things. It looks like GNOME has totally redesigned mouse and touchpad settings. I don't recall what Disco looked like in that regard because I didn't test it on a laptop.

---

### Post by kansasnoob on 2019-09-28
This was easy to solve after a bit of searching. I installed the package 'xserver-xorg-input-synaptics' and now things behave properly. BTW it actually effects the entire appearance of the  mouse/touchpad settings UI. Two-finger scrolling has a separate "place" in the UI now, so when one is changed the other is changed. Anyway it works with the addition of that package.

---

### Post by kansasnoob on 2019-09-29
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1845898](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1845898)

Just in case anyone else notices this.

---

