---
title: "Ubuntu 18.04 LTS with Snap Apps Preinstalled"
date: 2018-03-10
forum: Ubuntu Development Version
---

### Post by corradoventu on 2018-03-10
On my Ubuntu 18.04 installed from Ubuntu 18.04 LTS "Bionic Beaver" - Alpha amd64 (20180308) I have Snap Apps Preinstalled

```
corrado@corrado-p8-bb-0308:~$ cat /var/log/installer/media-info
Ubuntu 18.04 LTS "Bionic Beaver" - Alpha amd64 (20180308)
corrado@corrado-p8-bb-0308:~$ snap list
Name                  Version    Rev   Developer     Notes
core                  16-2.31.1  4110  canonical     core
gnome-3-26-1604       3.26.0     31    canonical     -
gnome-calculator      3.26.0     75    canonical     -
gnome-characters      3.26.2     50    canonical     -
gnome-logs            3.26.2     23    canonical     -
gnome-system-monitor  3.26.0     31    canonical     -
corrado@corrado-p8-bb-0308:~$  
```

while on a different partition installed from an older ISO and updated almost daily (also today) I don't see snap apps:

```
corrado@corrado-p3-bb:~$ cat /var/log/installer/media-info
Ubuntu 18.04 LTS "Bionic Beaver" - Alpha amd64 (20180214)
corrado@corrado-p3-bb:~$ snap list
No snaps are installed yet. Try "snap install hello-world".
corrado@corrado-p3-bb:~$ 
```

Should I consider it a problem and file a bug?
or just wait for snap apps?

---

### Post by jbicha on 2018-03-10
I believe the intent is for upgrades from 16.04 LTS or 17.10 to install those snap apps, but I don't think that's been implemented yet.

If you are already running Ubuntu 18.04, there isn't an easy way for Ubuntu to automatically install those snap apps for you, but it's pretty easy to install them yourself. You'll want to uninstall the traditional .deb versions so that you don't have duplicate apps in your app list.

---

