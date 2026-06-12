---
title: "snap-store segmentation fault in wayland session"
date: 2020-03-30
forum: Ubuntu Development Version
---

### Post by corradoventu on 2020-03-30
Installing Ubuntu Focal from last ISO Ubuntu 20.04 LTS "Focal Fossa" - Alpha amd64 (20200329) I have snap-store rev.308. In wayland session snap-store gives segmentation fault.
I opened a problem in snapcraft: [https://forum.snapcraft.io/t/snap-store-segmentation-fault-in-wayland-session/16153](https://forum.snapcraft.io/t/snap-store-segmentation-fault-in-wayland-session/16153)
but I don't know how to open a bug in launchpad because ubuntu-bug does not work for snap applications.

---

### Post by P-I H on 2020-03-30
I also get this crash.
These are the related info in syslog
```
Mar 30 11:20:32 pi-MS-7A34 systemd[1557]: Started Application launched by gnome-shell.
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.385295] audit: type=1400 audit(1585560032.776:57): apparmor="DENIED" operation="open" profile="snap.snap-store.snap-store" name="/var/lib/snapd/hostfs/usr/share/mime/mime.cache" pid=11215 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.385302] audit: type=1400 audit(1585560032.776:58): apparmor="DENIED" operation="open" profile="snap.snap-store.snap-store" name="/var/lib/snapd/hostfs/usr/share/mime/globs2" pid=11215 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.385306] audit: type=1400 audit(1585560032.776:59): apparmor="DENIED" operation="open" profile="snap.snap-store.snap-store" name="/var/lib/snapd/hostfs/usr/share/mime/magic" pid=11215 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.385310] audit: type=1400 audit(1585560032.776:60): apparmor="DENIED" operation="open" profile="snap.snap-store.snap-store" name="/var/lib/snapd/hostfs/usr/share/mime/aliases" pid=11215 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.385314] audit: type=1400 audit(1585560032.776:61): apparmor="DENIED" operation="open" profile="snap.snap-store.snap-store" name="/var/lib/snapd/hostfs/usr/share/mime/subclasses" pid=11215 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.385317] audit: type=1400 audit(1585560032.776:62): apparmor="DENIED" operation="open" profile="snap.snap-store.snap-store" name="/var/lib/snapd/hostfs/usr/share/mime/icons" pid=11215 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.385320] audit: type=1400 audit(1585560032.776:63): apparmor="DENIED" operation="open" profile="snap.snap-store.snap-store" name="/var/lib/snapd/hostfs/usr/share/mime/generic-icons" pid=11215 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.390865] audit: type=1400 audit(1585560032.780:64): apparmor="DENIED" operation="open" profile="snap.snap-store.snap-store" name="/var/lib/snapd/hostfs/usr/share/glib-2.0/schemas/gschemas.compiled" pid=11215 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.405272] snap-store[11215]: segfault at 0 ip 00007fa59ccf6ae4 sp 00007ffc34595e30 error 4 in libwayland-client.so.0.3.0[7fa59ccef000+d000]
Mar 30 11:20:32 pi-MS-7A34 kernel: [10292.405284] Code: 5b c3 e8 1f d3 ff ff 0f 1f 44 00 00 66 2e 0f 1f 84 00 00 00 00 00 41 55 41 54 49 89 cc 55 53 48 89 fb 48 83 ec 08 48 8b 7f 08 <44> 0f b6 07 45 84 c0 0f 84 17 01 00 00 48 89 f8 44 89 c1 31 ed 41
Mar 30 11:20:32 pi-MS-7A34 systemd[1557]: gnome-launched-snap-store_snap-store.desktop-11215.scope: Succeeded.

```
By the how do log in to the snapcraft forum? Ubuntu Single Sign-On doesn't work.

---

### Post by corradoventu on 2020-03-30
Ubuntu Single Sign-On doesn't work. this is further confirmation that snaps are a ruin
You must just open page [https://forum.snapcraft.io/](https://forum.snapcraft.io/) and create your account

Edit: if you try to use ubuntu-bug on snap-store you receive a message:

---

