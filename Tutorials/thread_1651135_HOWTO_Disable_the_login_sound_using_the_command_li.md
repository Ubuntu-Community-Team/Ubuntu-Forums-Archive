---
title: "HOWTO: Disable the login sound using the command line"
date: 2010-12-22
forum: Tutorials
---

### Post by tom56 on 2010-12-22
I wanted to disable the Ubuntu login sound over the command line because my only access to the machine in question was over ssh. Here's how to do it, in the same way the GUI does it, so that it can be re-enabled using the GUI if necessary. Simply enter the following single command.

These instructions were tested on Ubuntu 10.10.

To disable login sound:
```
echo -e '\n[Desktop Entry]\nType=Application\nName=GNOME Login Sound\nComment=Plays a sound whenever you log in\nExec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"\nOnlyShowIn=GNOME;\nAutostartCondition=GNOME /desktop/gnome/sound/event_sounds\nX-GNOME-Autostart-Phase=Application\nX-GNOME-Provides=login-sound\nX-GNOME-Autostart-enabled=false' > ~/.config/autostart/libcanberra-login-sound.desktop
```
To renable:
```
rm ~/.config/autostart/libcanberra-login-sound.desktop
```

---

### Post by Rytron on 2011-01-09
Thanks for this.

---

### Post by WarrenSH on 2011-01-09
Thanks for this easy to do removal A++ write up

---

### Post by samthethe on 2012-05-08
I <3 1 liners.

Many thanks for this.

---

