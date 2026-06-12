---
title: "Is it possible to switch to gdm anymore?"
date: 2015-09-24
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-09-24
Have tried unsuccessfully to switch to gdm in an Ubuntu install, will try Xubuntu but not hopeful.
All attempts here end with an unbootable install.
If anyone knows how would be quite useful, don't care if it's Ubuntu, Xubuntu or Lubuntu

---

### Post by kansasnoob on 2015-09-24
Ubuntu GNOME still uses gdm instead of lightdm. It's working from a fresh install yesterday.

---

### Post by mc4man on 2015-09-24
> **kansasnoob said:**
> Ubuntu GNOME still uses gdm instead of lightdm. It's working from a fresh install yesterday.
That I know - I'm looking to see if any *buntu that uses lightdm can be switched over to gdm. In the past it was just a matter of changing display managers, doesn't seem to be the case anymore.

---

### Post by zika on 2015-09-25
All the ways that worked before work (here) now.
```
sudo dpkg-reconfigure gdm
```
```
sudo dpkg-reconfigure lightdm
```
```
sudo systemctl stop lightdm.service
sudo systemctl start gdm.service
```
also with using target etc...

---

### Post by Bucky Ball on 2015-09-25
Yea, I had to stop, or remove, one before starting or installing the other last I did this (lightdm to gdm that is, not using but mini install with xfce4).

---

### Post by mc4man on 2015-09-25
Ok - thanks all, that was simple on xubuntu, at least part 2 which was to remove lightdm itself (a bit more involved on a Ubuntu install
(-didn't really further quest to see why nvidia/nvidia-prime only works (has a display) with gdm & a gnome session, not with any other *buntu  other than a gdm/gnome session is doing something right that the other buntu's aren't.

xubuntu - default= no display on greeter or login with nvidia, same as Ubuntu
xubuntu - gdm= display on greeter but not on login with nvidia
xubuntu - gdm/gnome session login= nvidia works fine just like in Ubuntu-Gnome

---

### Post by grahammechanical on 2015-09-25
I do not know if this is relevant to your prime quest as to why nvidia/nvidia-prime works with gdm but not lightdm, but

months and months ago when we were messing around with xmir I was able to get all the flavours loading xmir except Ubuntu Gnome. At the time I suspected that lightdm had been modified to detect xmir and use it if it was there and to fall back to X if it was not there, and that gdm was not modified.

Expect some fun when Ubuntu Gnome starts using xwayland and gdm-wayland.

---

### Post by valereguerin on 2015-12-16
you can try gdm3 with ubuntu-gnome-desktop , it's fine for me i was probleme with lightdm/unity-destop

---

