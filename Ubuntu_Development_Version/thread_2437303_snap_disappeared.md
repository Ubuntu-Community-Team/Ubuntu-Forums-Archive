---
title: "snap disappeared?"
date: 2020-02-21
forum: Ubuntu Development Version
---

### Post by corradoventu on 2020-02-21
Installed last ISO: Ubuntu 20.04 LTS "Focal Fossa" - Alpha amd64 (20200220)
After install I was going to remove snap but:  ```
corrado@corrado-p7-ff-0220:~$ snap list
No snaps are installed yet. Try 'snap install hello-world'.
corrado@corrado-p7-ff-0220:~$ 
```I'm dreaming? or is it true?

---

### Post by howefield on 2020-02-21
Maybe dreaming :)

At least, todays manifest lists.. 

```
gir1.2-snapd-1:amd64	1.55-0ubuntu2
gnome-software-plugin-snap	3.35.2-0ubuntu2
libsnapd-glib1:amd64	1.55-0ubuntu2
snapd	2.43.3+git1.8109f8
snap:core	stable	8689
snap:core18	stable	1668
snap:gnome-3-28-1804	stable/ubuntu-20.04	116
snap:gnome-calculator	stable/ubuntu-20.04	544
snap:gnome-characters	stable/ubuntu-20.04	399
snap:gnome-logs	stable/ubuntu-20.04	81
snap:gtk-common-themes	stable/ubuntu-20.04	1440
```

---

### Post by corradoventu on 2020-02-21
yes I have seen in manifest but for some reason they are not installed/activated and:
```
corrado@corrado-p7-ff-0220:~$ snap refresh
error: too early for operation, device not yet seeded or device model not acknowledged
corrado@corrado-p7-ff-0220:~$ 
```
```
corrado@corrado-p7-ff-0220:~$ systemctl status snapd.seeded.service
&#9679; snapd.seeded.service - Wait until snapd is fully seeded
     Loaded: loaded (/lib/systemd/system/snapd.seeded.service; enabled; vendor preset: enabled)
     Active: activating (start) since Fri 2020-02-21 10:58:13 CET; 7h ago
   Main PID: 1112 (snap)
      Tasks: 11 (limit: 9132)
     Memory: 12.0M
     CGroup: /system.slice/snapd.seeded.service
             &#9492;&#9472;1112 /usr/bin/snap wait system seed.loaded

feb 21 10:58:13 corrado-p7-ff-0220 systemd[1]: Starting Wait until snapd is fully seeded...
corrado@corrado-p7-ff-0220:~$
```

---

### Post by mc4man on 2020-02-21
If such cases you need to find correct commands to fix or simply start over.
Some possible commands in [bottom half here]("https://forum.snapcraft.io/t/cant-install-or-refresh-snaps-on-arch-linux/8690/26") or [1 here]("https://bugs.launchpad.net/snapd/+bug/1826662")
or start over
sudo apt purge snapd
sudo apt install snapd

Then install a snap, 1st installed snap will pull in the core/base snaps..

---

### Post by corradoventu on 2020-02-21
They are 2 bugs for this problem:
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1864113](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1864113)
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1864230](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1864230)

---

