---
title: "Ubuntu server kiosk mode PDF settings"
date: 2014-12-10
forum: Server Platforms
---

### Post by gnomo84 on 2014-12-10
Hello.

I created a "kiosk station" using Ubuntu Server 14.04.1 LTS,  from this guide: [http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/](http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/)
I want to know if there's a way to say to chrome  "open pdf with acrobat" permanently, and not with the chrome integrated viewer?
Thanks.

---

### Post by volkswagner on 2014-12-10
This is a Chrome issue not Linux.

You can disable the built-in pdf plugin, but it seems to download the pdf.

To disable the plugin, from Chrome go to chrome://plugins/

---

### Post by gnomo84 on 2014-12-10
The problem is that after reboot it will lose all settings.
 is there a way to edit the chrome default settings?
or a way to start firefox at fullscreen mode permanently?

---

### Post by gnomo84 on 2014-12-12
Is there a way to start a session to make permanent modifications (like a firefox plugin installation)?

---

### Post by volkswagner on 2014-12-14
Take a look at Firefox command line options.
Perhaps you can edit the launcher/shortcut and add the fullscreen option.

---

