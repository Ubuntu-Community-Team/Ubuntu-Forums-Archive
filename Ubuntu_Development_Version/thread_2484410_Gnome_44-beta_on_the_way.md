---
title: "Gnome 44-beta on the way"
date: 2023-02-25
forum: Ubuntu Development Version
---

### Post by zebra2 on 2023-02-25
```

$DESKTOP_SESSION
ubuntu
$XDG_SESSION_TYPE
wayland
GNOME Shell 43.2
Version: 44~beta-1ubuntu1
Version: 43.2-1ubuntu1
loginctl type
Type=wayland
zebra1@zebra1-15isk:~$

```

---

### Post by Hewjr100 on 2023-03-09
I did not see it in Lunar Lobster daily live 03-08-23.

Henry

---

### Post by zebra2 on 2023-03-09
[https://discourse.gnome.org/t/gnome-44-beta-released/14153](https://discourse.gnome.org/t/gnome-44-beta-released/14153)

I'm not going to get into how I'm running my system and hence getting 44 beta.  If I have it, you will have it shortly. But possibly not with 22.04, don't know.

---

### Post by #&amp;thj^% on 2023-03-10
Not not missing a whole lot ATM:> (Pretty rough currently)
```
gnome-shell version
libmutter-Message: 07:03:51.809: Running GNOME Shell (using mutter 44.rc) as a X11 window and compositing manager
org.gnome.Shell already exists on bus and --replace not specified

```
I've not heard a word for 22.04 as of yet.
```
gnome-shell --version
GNOME Shell 44.rc


```

---

### Post by Claus7 on 2023-03-10
Hello,

I discarded the upgraded lunar due to many problems after the latest upgrade. I guess that I have to wait a couple of days until 44rc lands on an iso.

Regards!

---

### Post by Claus7 on 2023-03-11
Hello,

today I grabbed it from here: [https://cdimage.ubuntu.com/daily-live/20230311/](https://cdimage.ubuntu.com/daily-live/20230311/)

Regards!

---

### Post by corradoventu on 2023-03-12
```
Preparing to unpack .../32-gnome-shell_44~beta-1ubuntu1_amd64.deb ...
Unpacking gnome-shell (44~beta-1ubuntu1) over (43.2-1ubuntu1) ...
```
... but with an old icon set

---

### Post by MyMurry on 2023-03-12
and no ubuntu dock extension.

---

### Post by #&amp;thj^% on 2023-03-12
I just took the gnome-nightly build, and for some reason I don't hate it, FTR this has nothing from Canonical no Apt, no security updates...felt that needed to be noted.
```
gnome-shell --version && nautilus --version
GNOME Shell 44.rc
** Message: 09:53:56.943: Connecting to org.freedesktop.Tracker3.Miner.Files
GNOME nautilus 44.0

```
This runs so much better without all the crap  that Canonical  adds>>>> ostree is used instead of apt, and No Snaps.
Every offer to install an application has been a flatpak, and that's fine by me.
```
free --lohi 
               total        used        free      shared  buff/cache   available
Mem:         8005500     1679992     2438200       33372     3887308     6164552
Low:         8005500     5567300     2438200
High:              0           0           0
Swap:              0           0           0

```

---

### Post by MyMurry on 2023-03-18
I have now the 44 rc.
But the lauchner only starts gnome apps. Firefox and Thunderbird won't start (terminal works). The ubuntu dock isn't compatible.

---

### Post by zebra2 on 2023-03-18
if you copy the desktop file from /usr/share/applications to /.local/share/applications, chances are they will open.  However this fix isn't working for the snap apps.

---

### Post by fthx on 2023-03-23
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2011806](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2011806)

---

