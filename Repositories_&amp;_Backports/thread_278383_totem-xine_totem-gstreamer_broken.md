---
title: "totem-xine totem-gstreamer broken"
date: 2006-10-16
forum: Repositories &amp; Backports
---

### Post by dmizer on 2006-10-16
i would like to use the totem-xine firefox plugin to view streaming media, but when i try to install it, i have this problem:
```
totem: Depends: totem-gstreamer (>= 1.4.3-0ubuntu1) but it is not installable or totem-xine (>= 1.4.3-0ubuntu1) but 1.4.1-0ubuntu4 is to be installed.
```
i am offered a solution to downgrade totem, but then video quality is pitiful.

i don't recall having this problem on a separate but recent install ... what's the deal?

edit: this is a default ubuntu (gnome) dapper install.  no tweaks yet.

---

### Post by adds2one on 2006-11-28
same problem here except it doesn't give me the option to downgrade, I just can't install totem plugins for firefox.

---

### Post by beameup on 2006-12-02
Using Dapper, this command will downgrade Totem-gstreamer to 1.41 and load the plugin for you. At least it did for me.

sudo aptitude install totem-gstreamer-firefox-plugin

I'm having problems with Ogg theora movies. The player will open, then disappear. I've tried Mplayer, Vlc, Gxine, and Totem. I thought that plugin might have been part of the issue.

---

### Post by dmizer on 2006-12-20
well, as i said, i could install the older version and it played the video, but quality was unbearable.

anyway ... i have it working now.  not sure i remember how i got around that little annoyance.  i should have made a note here, sorry.

---

