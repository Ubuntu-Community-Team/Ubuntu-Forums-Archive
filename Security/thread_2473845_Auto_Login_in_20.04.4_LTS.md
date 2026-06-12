---
title: "Auto Login in 20.04.4 LTS"
date: 2022-04-15
forum: Security
---

### Post by securitydad on 2022-04-15
I was using Ubuntu version 18.04 and just upgraded to 20.04 LTS.

Unfortunately the system does a screen blank, and then requires the password to get back to the Desktop.  I am building a test device which non-geeks can use, so a Password is defeating the usability of the device.  How do I disable the password requirement for the Screen lock, and Power up sequences?

Note:  I don't want to remove the password from the account, just make the box easier to use.

Thank you.

---

### Post by #&amp;thj^% on 2022-04-15
I just use this:
```
gsettings set org.gnome.desktop.screensaver lock-enabled false
```
More also found here: [https://linuxconfig.org/disable-turn-off-lock-screen-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/disable-turn-off-lock-screen-on-ubuntu-20-04-focal-fossa-linux)
barely a security question though. ;)

---

### Post by securitydad on 2022-04-20
Thank you for the reply.  I perform the command and I am greeted with
dconf-WARNING **: {time}: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY

Any ideas?

---

### Post by Apanta on 2022-05-04
For automatic login, into Ubuntu 20.04 :
[URL="https://imgur.com/a/sbjTq8X"]
[/URL][[IMG]https://i.postimg.cc/HVTqnQ9k/Schermata-da-2022-05-04-22-49-53.png[/IMG]]("https://postimg.cc/HVTqnQ9k")

---

