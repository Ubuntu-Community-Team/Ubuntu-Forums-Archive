---
title: "Xubuntu XX: Lost VLC, Sound Control Keys and XFCE4 Control"
date: 2015-12-17
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-12-17
Trials and errors are among problems that I deal with in Xubuntu that appears to be extremely stable under Kernel 4.4 RC5.  


VLC:  Was trying to set it for HTTP streaming and after it wouldn't open any more.  So I reset settings back to their previous state:

```
vlc --reset-config
```

Sound control on the keyboard were not working any more.  Try the following command lines and I recover volumeup, volume down and mute after resart:

Up: 
```
amixer set Master 10%+ -q
```
Down: 
```
amixer set Master 10%- -q
```
Mute: 
```
amixer set Master toggle -q 
```

If not working, then install aumix package

```
sudo apt-get install aumix
```
For XFCE4, I was not able to recover Indicator Plugin (Volume and Network icons) and main menu (Whisker).  So I reset XFCE 4 back to it's original settings:
```
rm -r ~/.config/xfce4
```

---

