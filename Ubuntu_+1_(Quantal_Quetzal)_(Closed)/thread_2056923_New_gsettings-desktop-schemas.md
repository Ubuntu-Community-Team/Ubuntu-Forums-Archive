---
title: "New gsettings-desktop-schemas"
date: 2012-09-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-09-12
The new version of gsettings-desktop-schemas (3.5.91-0ubuntu2)
changes the way gdm sets the background.
At least I can see this in gnome-shell.
It seems it uses the default theme (adwaita) timed backgrounds.

Does someone know the rules for this?
Where to change this?
What file sizes are supported?

---

### Post by dino99 on 2012-09-12
i really does not know, and have spend time to fix new missing schemas:

 org.gnome.gnome-panel.applet.fish » is relocatable (the path must be specified)
 « org.gnome.gnome-panel.applet.workspace-switcher »is relocatable (the path must be specified)
 « org.gnome.gnome-panel.applet.window-list » is relocatable (the path must be specified)
 « org.gnome.gnome-panel.launcher » is relocatable (the path must be specified)
 « org.gnome.gnome-panel.object » is relocatable (the path must be specified)
 « org.gnome.gnome-panel.toplevel » is relocatable (the path must be specified)
 « org.gnome.gnome-panel.applet.clock » is relocatable (the path must be specified)
 « org.gnome.gnome-panel.menu-button » is relocatable (the path must be specified)


Bug #1049520

---

### Post by jbicha on 2012-09-12
Harry,

Yes, if you don't have ubuntu-default-settings installed then the default background is now the upstream default which is the timed blue blinds wallpaper.

ubuntu-desktop depends on ubuntu-default-settings but maybe you don't use ubuntu-desktop.

---

### Post by Harry33 on 2012-09-13
> **jbicha said:**
> Harry,

Yes, if you don't have ubuntu-default-settings installed then the default background is now the upstream default which is the timed blue blinds wallpaper.

ubuntu-desktop depends on ubuntu-default-settings but maybe you don't use ubuntu-desktop.

Correct, I do not use the meta packages.
The reason being I want the ability for more adjustments and tweaking.

Anyway, it is logical that login screen and desktop has the same background.

I have tried to change the settings in the file /etc/gdm/greeter-settings to set gdm to use a different background.
However, that does not work.
It is easy to set a different background for the desktop though (system settings).

---

### Post by Harry33 on 2012-09-14
Hmm, I just played around with the new timed background system.
So I use Gdm as default DM and Adwaita as a default theme.

There (in Adwaita) are three separate background images (morning.jpg, bright-day.jpg and good-night.jpg) that are changed automatically based on settings in a xml file.
These files are located in /usr/share/themes/adwaita/backgrounds directory.

I named three images of my own according to the original Adwaita curtain images. Then I replaced the original ones with my own images.

After that I also edited the xml file to change the transitional and stable phase timings.
The transitional phase means you actually have a background where two images are mixed and stable phase is where you see only one of those three images at a time.
For example now the transition time is one minute instead of original several hours.

---

