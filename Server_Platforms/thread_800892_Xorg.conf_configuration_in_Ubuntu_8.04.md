---
title: "Xorg.conf configuration in Ubuntu 8.04"
date: 2008-05-20
forum: Server Platforms
---

### Post by paladin_knight on 2008-05-20
I just installed Ubuntu server 8.04 and managed to install ubuntu-desktop inside. But, the Xwindow still got some problems.

#I cannot login to my username as the X will always crash after that. 

I already installed ATI driver but I cannot configure the xorg.conf. 

My xorg.conf file is like this.> Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "intl"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection 

My ATI card is ATI Radeon Express 200. My monitor is HP 1280x1024 ,60 Hz. 

anyone can help me with this?. I am so hopeless.:):(

---

### Post by solcott on 2008-05-20
You coulld try using the EnvyNG tool to autoconfigure the ATi driver and xorg.  It's a pretty useful tool that I've used to troubleshoot xorg for some of my relatives.

Either CRTL+ALT+1 or just let the x server crash so you can get into text mode and try...
```

sudo apt-get install envyng-core
sudo envyng -t

```
You can then choose to uninstall the driver you have now and then choose install ATi driver and it will reconfigure for you.

---

### Post by paladin_knight on 2008-05-20
Thanks a lot. This is my first time that I can enable my 3D screensaver although I have used ubuntu for a long time. 

There is still one little problem I have here. For login window after booting, it always prompt me that the resolution is too high and it automatically changes into 1280x1024 ( my monitor max resolution ). How can configure the login window resolution?

Thanks a lot again.:):popcorn::guitar:

---

