---
title: "Disable screenshots from maiking sound &amp; Flash"
date: 2021-12-27
forum: Ubuntu/Debian BASED
---

### Post by dangleben2 on 2021-12-27
zerion@Lenovo:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Zorin
Description:    Zorin OS 16
Release:    16
Codename:    focal


New to linux
I am currently on zorion. And everytime i make a screenshots it makes a sound of a photo clikcing and flashes my screen like in cs:go.
So i wanna turn it off buy a cannot find where

---

### Post by jeremy31 on 2021-12-27
Moved to Ubuntu/Debian based

---

### Post by schragge on 2021-12-27
The proper way to disable the sound is [via a custom sound theme]("https://unix.stackexchange.com/questions/93368"). A quick&dirty way is described in answers to [this AskUbuntu question]("https://askubuntu.com/questions/140200").

Another approach mentioned in the first link is to create a wrapper script for **gnome-screenshot**:
```
#!bin/sh
amixer -D pulse sset Master mute
gnome-screenshot
amixer -D pulse sset Master unmute
```

---

