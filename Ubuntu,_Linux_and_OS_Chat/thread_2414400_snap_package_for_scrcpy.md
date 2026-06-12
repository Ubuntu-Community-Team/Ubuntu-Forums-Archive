---
title: "snap package for scrcpy"
date: 2019-03-09
forum: Ubuntu, Linux and OS Chat
---

### Post by sisco311 on 2019-03-09
My very first snap !!! :guitar:

scrcpy is a great tool for controlling your Android device from your computer but unfortunately there is no simple way to install it on Ubuntu so I created a snap package for it.

[s]It's in the snap store's edge channel. If you are interested in you can install it (amd64 only for now) with:
```
sudo snap install --edge scrcpy
```

In order to use the app you need adb-support:
```
sudo snap connect scrcpy:adb-support :adb-support
```
[/s]

It's in the [snap store]("https://snapcraft.io/scrcpy").

If you need to use the built in adb server, run:
```
scrcpy.adb [options]
```

The current status of the project is: it works for me. So any feedback is welcomed.  

git page for scrcpy: [https://github.com/Genymobile/scrcpy](https://github.com/Genymobile/scrcpy)
snap git page: [https://github.com/sisco311/scrcpy-snap](https://github.com/sisco311/scrcpy-snap) (Don't expect much; for now is just the .yaml file)

---

### Post by sisco311 on 2019-05-07
A little update.

I made some progress.

v1.8 of the package is available from the stable channel of the snap store for amd64 and i386. The git version built from the master branch is in the edge channel.

Added some rudimentary installation instructions.

---

### Post by sisco311 on 2019-06-14
v1.9 is out with some cool new features and bug fixes: [https://github.com/Genymobile/scrcpy/releases](https://github.com/Genymobile/scrcpy/releases)

The snap now auto connects to the adb-support and home slots.

snaps are updated automatically in the background every day so most snap users should already enjoy the latest version of scrcpy.

---

### Post by sisco311 on 2019-11-19
v1.11 is out: [https://github.com/Genymobile/scrcpy/releases](https://github.com/Genymobile/scrcpy/releases)

---

### Post by sisco311 on 2019-12-09
Version 1.12 is out.

---

### Post by sisco311 on 2020-05-02
BUMP for v1.13

[https://github.com/Genymobile/scrcpy/releases](https://github.com/Genymobile/scrcpy/releases)

---

### Post by sisco311 on 2020-05-30
v1.14 is out and it rocks!

---

