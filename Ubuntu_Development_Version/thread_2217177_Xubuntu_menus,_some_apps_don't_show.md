---
title: "Xubuntu menus, some apps don't show"
date: 2014-04-15
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-04-15
When I was recently without any Ubuntu install for a few days due to removing & then having a bad image I remembered I had an Xubuntu boot up disk so installed that last night.
I really don't know xubuntu at all but found it wierd that after installing 2 apps I needed, gparted & usb-creator-gtk, that they were nowhere to be found in the menus.
(though did show in settings menu editor 

After finally getting Ubuntu back decided to take a look, it seems that having "Settings" in the desktop's Categories= line is an issue in xubuntu.
(after removing Settings from the line both apps now show up in the menu (accessories)  & recently used.
Is this some known limitation/bug of xubuntu?

---

### Post by Toz on 2014-04-16
I believe it was [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1040902") that changed this ([patch]("ps://lists.launchpad.net/xubuntu-dev/msg01804.html")). The intent was to put all settings-type apps into the settings manager.

---

### Post by mc4man on 2014-04-16
> **Toz said:**
> I believe it was [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1040902") that changed this ([patch]("ps://lists.launchpad.net/xubuntu-dev/msg01804.html")). The intent was to put all settings-type apps into the settings manager.


That report/fix release seems pretty well grounded when in the specifics & I guess after 20 months well accepted (behavior.
Though in my limited use  I have to say it makes no sense to me, why exclude apps from the 'upfront' menu solely based of them having *Settings *in their .desktop's Categories
(not to mention 2 apparently useful subs of "all" & "recently used" in that menu.
Applications tend to use a number of types in their .desktops, some liberally like *Settings*. Gparted isn't really a 'settings' app, s-d-c not at all.

---

### Post by Elfy on 2014-04-16
I've argued this point numerous times

---

