---
title: "lost my volume control in taskbar"
date: 2016-10-03
forum: Ubuntu Studio
---

### Post by fbfrankb5 on 2016-10-03
somehow pulseaudio was installed. i removed that and i lost the nice volume knob with settings that comes with U Studio.
Card works as if I select is from a program in settings. but i have no global way of settting it. In short, I want that volume tray program back.. help

thanks

---

### Post by fbfrankb5 on 2016-10-04
indicator-sound-service switcher seems to require pulseaudi. Was Ubuntu Studio using an earlier version? ......wind blows....tumbleweed...

---

### Post by CantankRus on 2016-10-05
Isn't pulseaudio part of the default install?
[http://cdimage.ubuntu.com/ubuntustudio/releases/trusty/release/ubuntustudio-14.04.5-dvd-amd64.manifest](http://cdimage.ubuntu.com/ubuntustudio/releases/trusty/release/ubuntustudio-14.04.5-dvd-amd64.manifest)
[http://cdimage.ubuntu.com/ubuntustudio/releases/xenial/release/ubuntustudio-16.04.1-dvd-amd64.manifest](http://cdimage.ubuntu.com/ubuntustudio/releases/xenial/release/ubuntustudio-16.04.1-dvd-amd64.manifest)

---

### Post by fbfrankb5 on 2016-10-06
i thought ubuntu studio avoided pulseaudio. im clearly uninformed.

---

### Post by CrocoDuck on 2016-10-07
> **fbfrankb5 said:**
> i thought ubuntu studio avoided pulseaudio. im clearly uninformed.

How can you think that UStudio avoids pulseaudio when you find it installed on your system? Actually, Ubuntu always used pulsaudio as far as I can remember.

You probably read a lot of stuff that stated that pulseaudio si very bad for proper audio configuration, as it tends to mess up jack. This was true 5 years ago and in few cases still today, but not so much anymore. Fact is that pulseaudio is way better integrated with jack nowadays. I run pulsaudio along with jack with no issues and my audio configuration is fine.

[This]("http://askubuntu.com/questions/397748/volume-control-applet-disappeared#397751") might help you. Perhaps, the xfc4-mixer application depends on pulseaudio in it will be pulled back into your system. If pulseaudio is not causing you any problem you have no reason to remove it. You could try to see if you can find some volume applet application that does not need pulseaudio as a dependency. I am not on Ubuntu, so I have not many suggestions for you. These are the Arch Linux packages I am aware of that implement some volume applet functionality compatible with XFCE:

volumeicon
xfce4-mixer
xfce4-volumed
xfce4-indicator-plugin

Try to see what you find in Ubuntu repos along the same lines.

Hope it helps, good luck.

---

### Post by fbfrankb5 on 2016-10-07
thanks

---

