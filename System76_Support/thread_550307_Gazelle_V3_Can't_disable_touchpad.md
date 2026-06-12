---
title: "Gazelle V3 Can't disable touchpad"
date: 2007-09-13
forum: System76 Support
---

### Post by AusIV4 on 2007-09-13
Latest kernel update broke the button that turns off the touchpad. I had to run the restore driver to get the sound working after the update, so I'm pretty sure that won't fix it.

---

### Post by thomasaaron on 2007-09-14
OK, you might go ahead and

---

### Post by thomasaaron on 2007-09-14
Are you running Ubuntu or Kubuntu?

If you are running Ubuntu (Gnome), go ahead and file a bug report on it. This one will probably take some digging.

---

### Post by AusIV4 on 2007-09-14
Found a fix. You have to add the line:

Option          "SHMConfig"             "true"

to the Synaptics Touchpad section of Xorg.conf.

And for whatever it's worth, I'm using Gnome on my Gazelle these days. While I like the ideas behind KDE better, I find KDE has been somewhat neglected by Ubuntu, and Gnome is quite a bit more functional, particularly for laptop uses. Hopefully KDE 4.0 will help resolve this.

---

