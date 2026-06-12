---
title: "No filters in Dash"
date: 2014-02-21
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-02-21
Seemed to have disappeared with recent unity upgrades, hope it's not permanent
(last seen in unity 7.1.2+14.04.20140217-0ubuntu1

---

### Post by Mateusz Stachowski on 2014-02-21
I also have this problem in my install but I don't know when this started (which Unity update).

When I run yesterdays live image there are filters in Dash. Also when I launch Ubuntu Help in my install I still get 13.10 docs but in daily live it displays 14.10 documentation.

---

### Post by mc4man on 2014-02-21
Pretty sure it was the 18 unity upgrade, on a fresh install if I downgrade to the 17 mentioned before they come back

Does remind me of how bad the Music lens is without  filters if you have more than 1 player with a scope installed, this however started in 13.10 & hasn't been addressed.

current issue - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1283159](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1283159)

outstanding music lens issue - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1189038](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1189038)

Manpage scope no longer working - 
[https://bugs.launchpad.net/ubuntu/+source/unity-scope-manpages/+bug/1283160](https://bugs.launchpad.net/ubuntu/+source/unity-scope-manpages/+bug/1283160)

---

### Post by grahammechanical on 2014-02-21
I do not normally notice the filters option but I see that it is now very extensive. It now seems to be the place to deactivate scopes. Synaptic showed me that unity7.1.2+14.04.20131106 was ready for an upgrade. I went ahead and I now have the 20140220 version and yes the filter options are now gone.

The upgrade brought unity control centre with the option in Appearance>Behaviour to put the application menus in the window title bars and not in the global menu. But it has messed up the themes. I was using Radiance and it has now reverted to Ambiance which would not matter so much if selecting Radiance made the change from Ambiance. But it does not. It now does not matter which of the two themes we select, we get Ambiance. :)

There is also a change to the default look of Chromium. Reminds me of an old Windows look. Does not fit what was the Radiance theme. Same with Libreoffice. Is this a LightDM system theme?

And so we live.

---

### Post by Mateusz Stachowski on 2014-02-21
> **grahammechanical said:**
> The upgrade brought unity control centre with the option in Appearance>Behaviour to put the application menus in the window title bars and not in the global menu. But it has messed up the themes. I was using Radiance and it has now reverted to Ambiance which would not matter so much if selecting Radiance made the change from Ambiance. But it does not. It now does not matter which of the two themes we select, we get Ambiance. :)

There is also a change to the default look of Chromium. Reminds me of an old Windows look. Does not fit what was the Radiance theme. Same with Libreoffice. Is this a LightDM system theme?

And so we live.

You have to install unity-settings-daemon and re-login.

---

### Post by grahammechanical on 2014-02-21
> [COLOR=#000000]You have to install unity-settings-daemon and re-login.[/COLOR]

Thank you.

---

### Post by xc3RnbFO8P on 2014-02-21
Unity is gone from Lightdm  (7.1.2+14.04.20140220)
OS: Ubuntu 14.04 trusty
Kernel: x86_64 Linux 3.13.0-11-generic

---

### Post by mc4man on 2014-02-21
> **Mateusz Stachowski said:**
> You have to install unity-settings-daemon and re-login.

At this point people are free to remove if using unity - 
gnome-control-center
gnome-session
gnome-settings-daemon

There is a fix already for no filters (music lens excluded), should show in near future

---

