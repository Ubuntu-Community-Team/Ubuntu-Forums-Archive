---
title: "Display Issue: xrandr Can't open display.  Ubuntu Server 18.04 on RPi 3B+"
date: 2019-01-24
forum: Server Platforms
---

### Post by B99 on 2019-01-24
Hi!
I am fairly new to Linux. I am running Ubuntu Server 18.04 on a Raspberry Pi 3B+ using the official image for Raspberry Pi 2 which I access primarily over ssh. I have encountered two display related issues.

1) When trying to set up a desktop environment and VNC, vncserver can't seem to find an active display.

$ /home/r/.vnc/ubuntu:2.log
```
 Thu Jan 24 14:01:06 2019 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on local interface(s), port 5902
 vncext:      created VNC server for screen 0
/usr/bin/startxfce4: X server already running on display :2
gpg-agent[1749]: WARNING: "--write-env-file" is an obsolete option - it has no effect
gpg-agent: a gpg-agent is already running - not starting a new one

(xfce4-session:1736): xfce4-session-WARNING **: 14:01:07.079: gpg-agent returned no PID in the variables

(xfce4-session:1736): xfce4-session-WARNING **: 14:01:07.083: xfsm_manager_load_session: Something wrong with /home/r/.cache/sessions/xfce4-session-ubuntu:2, Does it exist? Permissions issue?

(xfce4-session:1736): xfce4-session-WARNING **: 14:01:07.191: Unable to launch "light-locker" (specified by autostart/light-locker.desktop): Failed to execute child process “light-locker” (No such file or direc$
(xfce4-session:1736): xfce4-session-WARNING **: 14:01:07.200: Unable to launch "update-notifier" (specified by autostart/update-notifier.desktop): Failed to execute child process “update-notifier” (No such file$Failure: Module initialization failed

(xfdesktop:1760): Gtk-WARNING **: 14:01:07.323: Unable to locate theme engine in module_path: "pixmap",

(xfdesktop:1760): Gtk-WARNING **: 14:01:07.330: Unable to locate theme engine in module_path: "pixmap",

(xfdesktop:1760): Gtk-WARNING **: 14:01:07.332: Unable to locate theme engine in module_path: "pixmap",

(xfce4-session:1736): Gtk-WARNING **: 14:01:07.340: Unable to locate theme engine in module_path: "pixmap",

(xfdesktop:1760): Gtk-WARNING **: 14:01:07.341: Unable to locate theme engine in module_path: "pixmap",

(xfdesktop:1760): Gtk-WARNING **: 14:01:07.342: Unable to locate theme engine in module_path: "pixmap",

(xfce4-session:1736): Gtk-WARNING **: 14:01:07.343: Unable to locate theme engine in module_path: "pixmap",

(Thunar:1758): Gtk-WARNING **: 14:01:07.350: Unable to locate theme engine in module_path: "pixmap",

(xfce4-session:1736): Gtk-WARNING **: 14:01:07.353: Unable to locate theme engine in module_path: "pixmap",

(Thunar:1758): Gtk-WARNING **: 14:01:07.355: Unable to locate theme engine in module_path: "pixmap",

(Thunar:1758): Gtk-WARNING **: 14:01:07.357: Unable to locate theme engine in module_path: "pixmap",

(Thunar:1758): Gtk-WARNING **: 14:01:07.367: Unable to locate theme engine in module_path: "pixmap",

(Thunar:1758): Gtk-WARNING **: 14:01:07.367: Unable to locate theme engine in module_path: "pixmap",

(xfce4-session:1736): Gtk-WARNING **: 14:01:07.377: Unable to locate theme engine in module_path: "pixmap",
(xfce4-session:1736): Gtk-WARNING **: 14:01:07.378: Unable to locate theme engine in module_path: "pixmap",

(xfsettingsd:1762): Gtk-WARNING **: 14:01:07.467: Unable to locate theme engine in module_path: "pixmap",

(xfsettingsd:1762): Gtk-WARNING **: 14:01:07.473: Unable to locate theme engine in module_path: "pixmap",

(xfsettingsd:1762): Gtk-WARNING **: 14:01:07.474: Unable to locate theme engine in module_path: "pixmap",

(xfsettingsd:1762): Gtk-WARNING **: 14:01:07.487: Unable to locate theme engine in module_path: "pixmap",

(xfsettingsd:1762): Gtk-WARNING **: 14:01:07.488: Unable to locate theme engine in module_path: "pixmap",

(migrate:1779): Gtk-WARNING **: 14:01:07.489: Unable to locate theme engine in module_path: "pixmap",

(migrate:1779): Gtk-WARNING **: 14:01:07.495: Unable to locate theme engine in module_path: "pixmap",

(migrate:1779): Gtk-WARNING **: 14:01:07.497: Unable to locate theme engine in module_path: "pixmap",

(migrate:1779): Gtk-WARNING **: 14:01:07.507: Unable to locate theme engine in module_path: "pixmap",

(migrate:1779): Gtk-WARNING **: 14:01:07.508: Unable to locate theme engine in module_path: "pixmap",
(xfsettingsd:1762): xfsettingsd-WARNING **: 14:01:07.571: Failed to get the _NET_NUMBER_OF_DESKTOPS property.

(xfwm4:1752): xfwm4-WARNING **: 14:01:07.616: Error opening /dev/dri/card0: No such file or directory

(xfwm4:1752): Gtk-WARNING **: 14:01:07.659: Unable to locate theme engine in module_path: "pixmap",

(xfwm4:1752): Gtk-WARNING **: 14:01:07.663: Unable to locate theme engine in module_path: "pixmap",

(xfwm4:1752): Gtk-WARNING **: 14:01:07.665: Unable to locate theme engine in module_path: "pixmap",

(xfwm4:1752): Gtk-WARNING **: 14:01:07.674: Unable to locate theme engine in module_path: "pixmap",

(xfwm4:1752): Gtk-WARNING **: 14:01:07.674: Unable to locate theme engine in module_path: "pixmap",

** (xfdesktop:1760): WARNING **: 14:01:08.431: Failed to set the background '/usr/share/backgrounds/xfce/xfce-teal.jpg': GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such interface 'org.freedesktop.Di$


```

2) I bought a 3.5" LCD HDMI screen for the Pi and the default resolution (800*600 I presume) makes the command line text unreadable. Following various guides I found on Google I attempted to run 
$ xrandr -q
and got 'Can't open display'

It's probably worth mentioning that there is a linux-firmware package that is not it's most recent version because it won't upgrade as I posted about [here.]("https://ubuntuforums.org/showthread.php?t=2411015")

TIA

---

### Post by howefield on 2019-01-24
Thread moved to the "*Server Platforms*" forum.

---

