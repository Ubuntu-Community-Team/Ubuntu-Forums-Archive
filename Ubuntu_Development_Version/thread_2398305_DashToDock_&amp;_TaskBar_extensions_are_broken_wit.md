---
title: "DashToDock &amp; TaskBar extensions are broken with GS 3.29.90"
date: 2018-08-10
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-08-10
These two extensions does not support yet the latest proposed Gnome-shell 3.29.90 version, and the upstream work is not also started  :(

---

### Post by PaulW2U on 2018-08-12
New version of GNOME Shell has now landed.

It looks like I need to temporarily use the repository versions of some extensions and ignore any prompts for updating them at [http://extensions.gnome.org/](http://extensions.gnome.org/).

Edit: It seems I've also lost the application top-bar right-click menu.  :mad:
Edit 2: Downgraded gnome-shell and mutter, right-click menu restored. Just need to clean up some broken packages by removing a couple that were installed as new packages.
Edit 3: Broken packages fixed. 14 updates to version 3.29.90-1 held by apt. Will review updating tomorrow.

---

### Post by P-I H on 2018-08-12
With Gnome 3.29.90, this is my extension situation
- Ubuntu dock, working
- Kstatusnotifieritem/appindicator support, working 
- Alternatetab, not working
- Freon, working. Used to present temps and fan speeds
- Openweather, working

---

### Post by PaulW2U on 2018-08-14
> **dino99 said:**
> These two extensions does not support yet the latest proposed Gnome-shell 3.29.90 version, and the upstream work is not also started  :(
Bug report: [Latest Cosmic dist-upgrade causes shell extensions (dash to dock, hide top bar) to fail to load]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1786948")

---

### Post by dino99 on 2018-08-14
> **PaulW2U said:**
> Bug report: [Latest Cosmic dist-upgrade causes shell extensions (dash to dock, hide top bar) to fail to load]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1786948")

I have opened issues on github for dastodock & taskbar
[https://github.com/zpydr/gnome-shell-extension-taskbar/issues/197](https://github.com/zpydr/gnome-shell-extension-taskbar/issues/197)
[https://github.com/micheleg/dash-to-dock/issues/786](https://github.com/micheleg/dash-to-dock/issues/786)

Actual journal output:

gnome-shell[2196]: JS WARNING: [/usr/share/gnome-shell/extensions/TaskBar@zpydr/windows.js 92]: reference to undefined property "screen"

gnome-shell[2196]: JS WARNING: [/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/openweathermap_org.js 376]: reference to undefined property "deg"
gnome-shell[2196]: JS WARNING: [/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/extension.js 1139]: reference to undefined property "NaN"

gnome-shell[2196]: Extension "dash-to-dock@micxgx.gmail.com" had error: TypeError: object is undefined

---

### Post by dino99 on 2018-09-28
Still waiting a Taskbar upgrade:
- proposed commit works  [https://github.com/zpydr/gnome-shell-extension-taskbar/pull/200](https://github.com/zpydr/gnome-shell-extension-taskbar/pull/200)
[https://github.com/zpydr/gnome-shell-extension-taskbar/pull/200/files](https://github.com/zpydr/gnome-shell-extension-taskbar/pull/200/files)

Please sync

---

