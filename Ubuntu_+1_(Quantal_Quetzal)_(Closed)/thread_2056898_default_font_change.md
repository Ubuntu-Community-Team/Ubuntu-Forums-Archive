---
title: "default font change"
date: 2012-09-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-09-12
one or more of the packages in the screen will change the default system fonts from half-decent to plain awful, reminds me of what's seen by default in that gnome3 only iso install. 
screen 1 shows new look, screen 2 as before & after downgrading
(- it's even worse in other area's then screen 1, _though maybe some like them_, I don't

If anyone knows what settings to change with the new packages to return usable fonts would be interested...

[COLOR="Blue"]Edit:[/COLOR]
This was caused here by not having ubuntu-default-settings installed, so check & install if affected
A log out/in for full effect

---

### Post by mc4man on 2012-09-12
g-s-d update removed an override - the settings are in
org.gnome.settings-daemon.plugins.xsettings

Actually found a better setting than I had before, (not quite as 'heavy'),  & much better than what the upgrade produced

---

### Post by xeizo on 2012-09-12
> **mc4man said:**
> g-s-d update removed an override - the settings are in
org.gnome.settings-daemon.plugins.xsettings

Actually found a better setting than I had before, (not quite as 'heavy'),  & much better than what the upgrade produced

Yes, it looks awful, what is this org.gnome.etc you're talking about? I really want things back the way they where ...

---

### Post by Alan F on 2012-09-12
> **xeizo said:**
> yes, it looks awful, what is this org.gnome.etc you're talking about? I really want things back the way they where ...

+1

---

### Post by wojox on 2012-09-12
> **xeizo said:**
> Yes, it looks awful, what is this org.gnome.etc you're talking about? I really want things back the way they where ...

Look in dconf and set the value to none or something besides full.

thanks mc4man.

---

### Post by mc4man on 2012-09-12
Open up dconf-editor, navigate  to 
org.gnome.settings-daemon.plugins.xsettings
The setting most likely to improve is 'hinting', I've set to 'slight' from 'medium'
Also check the antialiasing, I've set to rgba from grayscale

---

### Post by Alan F on 2012-09-12
> **mc4man said:**
> Open up dconf-editor, navigate  to 
org.gnome.settings-daemon.plugins.xsettings
The setting most likely to improve is 'hinting', I've set to 'slight' from 'medium'
Also check the antialiasing, I've set to rgba from grayscale

Thank you - much better

---

### Post by mc4man on 2012-09-12
I'm not sure the antialiasing does much, but the hinting certainly does.
Maybe the gnome default is 'medium', if so that may explain why the default gnome-shell in that new iso looks so crappy. (like grade school designed

Glad it's adjustable because if it wasn't would have dropped 12.10 rather than look at that...

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1049963](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1049963)

---

### Post by GreatDanton on 2012-09-12
I also had the same problem as you mc4man, however I installed latest updates (about hour ago), and now I have the old good looking fonts back. 

Regards.

---

### Post by jbicha on 2012-09-12
Those settings have been moved to **ubuntu-default-settings** which is a dependency of ubuntu-desktop.

Alternatively, you can use **ubuntu-gnome-default-settings** which has this setting but it doesn't override as much as ubuntu-default-settings does.

---

### Post by mc4man on 2012-09-12
> **jbicha said:**
> Those settings have been moved to **ubuntu-default-settings** which is a dependency of ubuntu-desktop.

Alternatively, you can use **ubuntu-gnome-default-settings** which has this setting but it doesn't override as much as ubuntu-default-settings does.
That is definitely the case. My install was prior to 08/21 & likely had ubuntu-desktop removed when trying out something or another (really should have checked that here.
So installing ubuntu-default-settings does fix the hinting, ect. back to where it was

---

### Post by wojox on 2012-09-12
ok gotcha, thanks Jeremy. :)

---

### Post by jbicha on 2012-09-13
Please note that the package with the Ubuntu overrides has been renamed to **ubuntu-settings** as apparently ubuntu-default-settings is used for something else.

---

### Post by mc4man on 2012-09-13
> **jbicha said:**
> Please note that the package with the Ubuntu overrides has been renamed to **ubuntu-settings** as apparently ubuntu-default-settings is used for something else.
It's showing up here on a new install yesterday where ubuntu-desktop **IS** installed

---

