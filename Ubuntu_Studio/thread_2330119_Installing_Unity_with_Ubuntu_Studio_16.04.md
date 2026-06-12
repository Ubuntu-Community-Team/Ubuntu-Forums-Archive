---
title: "Installing Unity with Ubuntu Studio 16.04"
date: 2016-07-08
forum: Ubuntu Studio
---

### Post by Stefan Björk on 2016-07-08
I know Ubuntu Studio is shipped with Xfce4, but I'm one of those strange users that actually use Unity. After a clean install of Ubuntu Studio, i tried to install unity-desktop using

```
apt-get install ubuntu-desktop^
```

according to [this answer posted on StackExchange]("http://askubuntu.com/questions/320334/how-do-i-install-the-unity-desktop-environment-on-ubuntu-studio-13-04-xfce").

Logging in with Unity session works as expected. However, I can no longer log in using the Xfce4-based Ubuntu Studio session, not even on a newly created user. No xfce4-panel ever shows up, although it is started. I can open a terminal, kill xfce4-panel and restart it, but it does not show up. I can start xfce4-settings-manager and edit the panel, but it does not show up.

What's wrong? Did ubuntu-desktop break something?

---

### Post by mook765 on 2016-08-05
If you like the unity-desktop it might be better to install Ubuntu.
You can add the studio-components  ( low latency kernel and the packages for audio,video...) using this commands 
```

sudo apt-get install linux-lowlatency
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins
sudo apt-get install ubuntustudio-video
sudo apt-get install ubuntustudio-graphics
sudo apt-get install ubuntustudio-photography
sudo apt-get install ubuntustudio-publishing
sudo apt-get install ubuntustudio-look

```
Choose what you need..

---

