---
title: "semi-bug haunts years"
date: 2015-12-28
forum: Ubuntu Development Version
---

### Post by forcecore on 2015-12-28
is there plans to fix this so called feature that causes loading cursors on Unity and most of Gnome based desktops and it has haunted long years. 16.04 LTS developers should consider turning this StartupNotify=true to StartupNotify=false in .desktop files and this loading cursor anomaly will stop.

---

### Post by ian-weisser on 2015-12-28
Is there a Launchpad bug open for the issue?
If so, link?

---

### Post by mc4man on 2015-12-29
The semi-issues concerning this aren't present in an ubuntu session, likely just for lightly supported gnome-panel env's so wouldn't expect any changes 
It does provide a useful visual cue for - 
many apps open slower the first time per session
there are still many users with slower hardware so cue is useful

list of those using here, I guess if presenting an issue it would be up to user to edit problem .desktop's

```
/usr/share/applications$ grep -R StartupNotify=true
unity-screen-panel.desktop:StartupNotify=true
nact.desktop:StartupNotify=true
seahorse.desktop:StartupNotify=true
brasero-nautilus.desktop:StartupNotify=true
unity-datetime-panel.desktop:StartupNotify=true
gedit.desktop:StartupNotify=true
rhythmbox.desktop:StartupNotify=true
libreoffice-startcenter.desktop:StartupNotify=true
ghex.desktop:StartupNotify=true
nautilus-autorun-software.desktop:StartupNotify=true
ccsm.desktop:StartupNotify=true
org.gnome.Totem.desktop:StartupNotify=true
unity-power-panel.desktop:StartupNotify=true
simple-scan.desktop:StartupNotify=true
vino-preferences.desktop:StartupNotify=true
apport-gtk.desktop:StartupNotify=true
unity-credentials-panel.desktop:StartupNotify=true
eog.desktop:StartupNotify=true
totem.desktop:StartupNotify=true
nautilus-connect-server.desktop:StartupNotify=true
python3.5.desktop:StartupNotify=true
libreoffice-impress.desktop:StartupNotify=true
thunderbird.desktop:StartupNotify=true
org.gnome.font-viewer.desktop:StartupNotify=true
gnome-session-properties.desktop:StartupNotify=true
unity-sound-panel.desktop:StartupNotify=true
ibus-setup.desktop:StartupNotify=true
gkbd-keyboard-display.desktop:StartupNotify=true
gnome-sudoku.desktop:StartupNotify=true
system-config-printer.desktop:StartupNotify=true
unity-appearance-panel.desktop:StartupNotify=true
org.gnome.Nautilus.desktop:StartupNotify=true
gnome-mines.desktop:StartupNotify=true
nm-connection-editor.desktop:StartupNotify=true
brasero.desktop:StartupNotify=true
empathy.desktop:StartupNotify=true
unity-bluetooth-panel.desktop:StartupNotify=true
org.gnome.Cheese.desktop:StartupNotify=true
gnome-mpv.desktop:StartupNotify=true
gnome-user-share-properties.desktop:StartupNotify=true
gnome-system-monitor.desktop:StartupNotify=true
transmission-gtk.desktop:StartupNotify=true
unity-network-panel.desktop:StartupNotify=true
gnome-power-statistics.desktop:StartupNotify=true
landscape-client-settings.desktop:StartupNotify=true
libreoffice-xsltfilter.desktop:StartupNotify=true
credentials-preferences.desktop:StartupNotify=true
unity-universal-access-panel.desktop:StartupNotify=true
libreoffice-calc.desktop:StartupNotify=true
gnome-system-monitor-kde.desktop:StartupNotify=true
org.gnome.DiskUtility.desktop:StartupNotify=true
unity-region-panel.desktop:StartupNotify=true
nautilus.desktop:StartupNotify=true
python3.4.desktop:StartupNotify=true
evince.desktop:StartupNotify=true
unity-display-panel.desktop:StartupNotify=true
gnome-mahjongg.desktop:StartupNotify=true
ubuntu-software-center.desktop:StartupNotify=true
evince-previewer.desktop:StartupNotify=true
python2.7.desktop:StartupNotify=true
org.gnome.Screenshot.desktop:StartupNotify=true
bluetooth-sendto.desktop:StartupNotify=true
gimp.desktop:StartupNotify=true
sound-juicer.desktop:StartupNotify=true
libreoffice-writer.desktop:StartupNotify=true
unity-keyboard-panel.desktop:StartupNotify=true
gucharmap.desktop:StartupNotify=true
file-roller.desktop:StartupNotify=true
unity-activity-log-manager-panel.desktop:StartupNotify=true
unity-wacom-panel.desktop:StartupNotify=true
unity-mouse-panel.desktop:StartupNotify=true
gnome-terminal.desktop:StartupNotify=true
hplj1020.desktop:StartupNotify=true
libreoffice-draw.desktop:StartupNotify=true
org.gnome.FileRoller.desktop:StartupNotify=true
org.gnome.baobab.desktop:StartupNotify=true
sol.desktop:StartupNotify=true
org.gnome.Contacts.desktop:StartupNotify=true
ibus-setup-table.desktop:StartupNotify=true
org.gnome.gedit.desktop:StartupNotify=true
yelp.desktop:StartupNotify=true
cheese.desktop:StartupNotify=true
ca.desrt.dconf-editor.desktop:StartupNotify=true
unity-info-panel.desktop:StartupNotify=true
medit.desktop:StartupNotify=true
nautilus-home.desktop:StartupNotify=true
inkscape.desktop:StartupNotify=true
firefox.desktop:StartupNotify=true
gnome-calculator.desktop:StartupNotify=true
unity-user-accounts-panel.desktop:StartupNotify=true
libreoffice-math.desktop:StartupNotify=true
nautilus-folder-handler.desktop:StartupNotify=true
unity-control-center.desktop:StartupNotify=true
unity-color-panel.desktop:StartupNotify=true
```

---

### Post by kansasnoob on 2015-12-29
> **mc4man said:**
> The semi-issues concerning this aren't present in an ubuntu session, likely just for lightly supported gnome-panel env's so wouldn't expect any changes 
It does provide a useful visual cue for - 
many apps open slower the first time per session
there are still many users with slower hardware so cue is useful

list of those using here, I guess if presenting an issue it would be up to user to edit problem .desktop's

```
/usr/share/applications$ grep -R StartupNotify=true
unity-screen-panel.desktop:StartupNotify=true
nact.desktop:StartupNotify=true
seahorse.desktop:StartupNotify=true
brasero-nautilus.desktop:StartupNotify=true
unity-datetime-panel.desktop:StartupNotify=true
gedit.desktop:StartupNotify=true
rhythmbox.desktop:StartupNotify=true
libreoffice-startcenter.desktop:StartupNotify=true
ghex.desktop:StartupNotify=true
nautilus-autorun-software.desktop:StartupNotify=true
ccsm.desktop:StartupNotify=true
org.gnome.Totem.desktop:StartupNotify=true
unity-power-panel.desktop:StartupNotify=true
simple-scan.desktop:StartupNotify=true
vino-preferences.desktop:StartupNotify=true
apport-gtk.desktop:StartupNotify=true
unity-credentials-panel.desktop:StartupNotify=true
eog.desktop:StartupNotify=true
totem.desktop:StartupNotify=true
nautilus-connect-server.desktop:StartupNotify=true
python3.5.desktop:StartupNotify=true
libreoffice-impress.desktop:StartupNotify=true
thunderbird.desktop:StartupNotify=true
org.gnome.font-viewer.desktop:StartupNotify=true
gnome-session-properties.desktop:StartupNotify=true
unity-sound-panel.desktop:StartupNotify=true
ibus-setup.desktop:StartupNotify=true
gkbd-keyboard-display.desktop:StartupNotify=true
gnome-sudoku.desktop:StartupNotify=true
system-config-printer.desktop:StartupNotify=true
unity-appearance-panel.desktop:StartupNotify=true
org.gnome.Nautilus.desktop:StartupNotify=true
gnome-mines.desktop:StartupNotify=true
nm-connection-editor.desktop:StartupNotify=true
brasero.desktop:StartupNotify=true
empathy.desktop:StartupNotify=true
unity-bluetooth-panel.desktop:StartupNotify=true
org.gnome.Cheese.desktop:StartupNotify=true
gnome-mpv.desktop:StartupNotify=true
gnome-user-share-properties.desktop:StartupNotify=true
gnome-system-monitor.desktop:StartupNotify=true
transmission-gtk.desktop:StartupNotify=true
unity-network-panel.desktop:StartupNotify=true
gnome-power-statistics.desktop:StartupNotify=true
landscape-client-settings.desktop:StartupNotify=true
libreoffice-xsltfilter.desktop:StartupNotify=true
credentials-preferences.desktop:StartupNotify=true
unity-universal-access-panel.desktop:StartupNotify=true
libreoffice-calc.desktop:StartupNotify=true
gnome-system-monitor-kde.desktop:StartupNotify=true
org.gnome.DiskUtility.desktop:StartupNotify=true
unity-region-panel.desktop:StartupNotify=true
nautilus.desktop:StartupNotify=true
python3.4.desktop:StartupNotify=true
evince.desktop:StartupNotify=true
unity-display-panel.desktop:StartupNotify=true
gnome-mahjongg.desktop:StartupNotify=true
ubuntu-software-center.desktop:StartupNotify=true
evince-previewer.desktop:StartupNotify=true
python2.7.desktop:StartupNotify=true
org.gnome.Screenshot.desktop:StartupNotify=true
bluetooth-sendto.desktop:StartupNotify=true
gimp.desktop:StartupNotify=true
sound-juicer.desktop:StartupNotify=true
libreoffice-writer.desktop:StartupNotify=true
unity-keyboard-panel.desktop:StartupNotify=true
gucharmap.desktop:StartupNotify=true
file-roller.desktop:StartupNotify=true
unity-activity-log-manager-panel.desktop:StartupNotify=true
unity-wacom-panel.desktop:StartupNotify=true
unity-mouse-panel.desktop:StartupNotify=true
gnome-terminal.desktop:StartupNotify=true
hplj1020.desktop:StartupNotify=true
libreoffice-draw.desktop:StartupNotify=true
org.gnome.FileRoller.desktop:StartupNotify=true
org.gnome.baobab.desktop:StartupNotify=true
sol.desktop:StartupNotify=true
org.gnome.Contacts.desktop:StartupNotify=true
ibus-setup-table.desktop:StartupNotify=true
org.gnome.gedit.desktop:StartupNotify=true
yelp.desktop:StartupNotify=true
cheese.desktop:StartupNotify=true
ca.desrt.dconf-editor.desktop:StartupNotify=true
unity-info-panel.desktop:StartupNotify=true
medit.desktop:StartupNotify=true
nautilus-home.desktop:StartupNotify=true
inkscape.desktop:StartupNotify=true
firefox.desktop:StartupNotify=true
gnome-calculator.desktop:StartupNotify=true
unity-user-accounts-panel.desktop:StartupNotify=true
libreoffice-math.desktop:StartupNotify=true
nautilus-folder-handler.desktop:StartupNotify=true
unity-control-center.desktop:StartupNotify=true
unity-color-panel.desktop:StartupNotify=true
```

+1! I like it just the way it is :D

Really just a feature request rather than a bug but could be mentioned here:

[https://mail.gnome.org/mailman/listinfo/gnome-flashback-list](https://mail.gnome.org/mailman/listinfo/gnome-flashback-list)

I'd vote against the change though.

---

### Post by forcecore on 2015-12-29
in unity it causes loading circle when application is already open, in gnome it shows "opening appname" even after app is opened. Nothing special but just annoying and it has lasted as far i can remember 12.04

---

