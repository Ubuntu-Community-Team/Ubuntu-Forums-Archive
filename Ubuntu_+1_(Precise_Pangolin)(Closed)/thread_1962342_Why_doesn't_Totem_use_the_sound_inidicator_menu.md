---
title: "Why doesn't Totem use the sound inidicator menu?"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pt123 on 2012-04-20
It is the quickest media player to play a "random" mp3 file you don't want in your library.

---

### Post by BwackNinja on 2012-04-20
It is implemented upstream since totem 3.2, but ubuntu uses 3.0 so that it doesn't depend on clutter. It would have to be backported.

---

### Post by mc4man on 2012-04-21
It's likely you'll see it one way or the other in 12.10. Precise is using an older totem version so as to not preclude some hardware from using (or something like that.

There is basic mpris2 support in totem starting in 3.2 as seen in screen

To note - vlc & audacious currently do offer mpris2 support
(if it doesn't show in vlc just open tools > preferences & save a change

---

### Post by pt123 on 2012-04-21
sweet thanks for the info

---

### Post by xyzzyman on 2012-04-21
If you want to add totem 3.4 via ppa, just

```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get upgrade
```

As usual do so are your own risk.

---

