---
title: "No bluetooth audio thru pulseaudio on gdm3"
date: 2017-06-18
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-06-18
Apparently a longstanding issue, with the dumping of lightdm it should be made right.
Basically what happens is you can connect & pair to for instance a bluetooth speaker but that device will never show up in sound settings,  so no sound thru it.

Temp workaround - 
connect & pair (may take multiple stabs at button in bluetooth settings
run this, 
```
sudo setfacl -m u:gdm:r /usr/bin/pulseaudio
```
Now open sound settings & pick bluetooth device.

Old bug, reopened, [https://bugs.launchpad.net/ubuntu-gnome/+bug/1489651](https://bugs.launchpad.net/ubuntu-gnome/+bug/1489651)

---

### Post by jbicha on 2017-06-18
It's probably not an Ubuntu-specific issue. Do you want to try to talk to Debian or GNOME about it?

---

### Post by mc4man on 2017-06-19
> **jbicha said:**
> It's probably not an Ubuntu-specific issue. Do you want to try to talk to Debian or GNOME about it?
that would appear premature as I only see this on Ubuntu-Gnome daily (- gnome-shell;gdm3;xorg or wayland), installed & somewhat in a live session.
In fedora-25 bluetooth > speaker works fine - (gnome-shell;gdm3;wayland
In Ubuntu-17.10 daily it also works fine (- gnome-shell;lightdm;xorg or wayland

On the current UG image > live session it actually works correctly for a bit. If one was to disconnect > reconnect then the device will never show again. 
Or if logging out/in then the device is again gone for good.
Once installed it doesn't work at all right from first login on.

May be worth waiting until Ubuntu gets on whatever path it's going, currently Ubuntu & Ubuntu-Gnome aren't on same...(lightdm vs. gdm.

---

### Post by mc4man on 2017-07-13
Solved in upcoming gdm3 update
(- also with recent change to pulseaudio it, (pulseaudio), should automatically switch to the bluetooth device upon connecting

There still remains some intermittent issues with actually connecting, sometimes takes multiple clicks in the connection window (6-10 clicks here..
Additionally dual booting Ubuntu & using a bluetooth speaker on those installs remains a complete mess. (could be the cause of ^ 
Edit: No, dual booting & using the speaker results in the other install no possibility of connecting. The only way is to remove & 're-install' the device which then makes the other install face the same issue, i.e. a circular fubar..

---

