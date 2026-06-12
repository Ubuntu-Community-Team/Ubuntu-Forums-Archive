---
title: "LTSP 12.04 xrandr monitors"
date: 2013-10-09
forum: Server Platforms
---

### Post by Adam_Chaudhary on 2013-10-09
I have set up LTSP on previous versions of ubuntu (10.04, 11.10) but I am having difficulty setting up multi-head displays with ubuntu 12.04.  

The first thin client I set up has 2x24" montors connected with one in portrait mode.  With previous LTSP installs, I have specified custom xorg.conf configurations from lts.conf to set the multi-monitor configurations per mac address and this works great.  This time I decided to go with the XRANDR options in lts.conf (also because generating appropriate xorg.conf files for intel integrated graphics for our newer thin clients in 12.04 or later seems just about impossible).  Using the XRANDR parameters seems to work great at first to put one monitor on left side and rotate it into portrait mode.  The thin client boots to a splash screen with the monitors set up appropriately.  However, the configuration in lts.conf is essentially thrown away when the login is completed and the monitors revert to their initial and automatic configuration (portrait monitor screen not rotated, looks like display manager or gnome-setting-daemon is doing this).  If I use the gnome display configuration tool, the correct configuration is then saved to ~/.config/monitors.xml and everything seems to work.  At first I thought this was great and was impressed that xrandr manager on server could do this for a thin client.  However, if I then connect another thin client with a different set of monitors and configuration, this solutions falls apart.  monitors.xml will be overwritten again and gnome-settings-daemon will overwrite it.  As the user changes seats (thin clients), the display configuration will keep reverting to automatic and uninitialized (and we are not having our users configure their displays at every login).

I really want to use lts.conf to set XRANDR configuration options per MAC address such that each device is bound to a display configuration (makes sense as monitors don't move between thin clients, users do).  However, it seems that gnome-settings-daemon is fighting me on this and forcing the users monitor.xml on me.  Is there a way to disable gnome-settings-daemon from using the xrandr manager to use monitors.xml to blow away whatever I previously set with lts.conf (without recompiling xrandr manager components of the gnome-settings-daemon)?  Has anyone else run into this kind of a problem?

---

### Post by Adam_Chaudhary on 2013-10-09
I am going to play with the gnome setting org.gnome.settings-daemon.plugins.xrandr.  I am doing to disable the settings-daemon xrandr plugin using dconf-editor and see if that helps.

---

### Post by Adam_Chaudhary on 2013-10-16
Disabling org.gnome.settings-daemon.plugins.xrandr doesn't seem to disable XRANDR in ubuntu 12.04 LTSP.  The LTSP install is doing something here that I can't disable or work around :(

---

