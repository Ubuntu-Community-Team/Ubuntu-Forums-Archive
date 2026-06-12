---
title: "VLC 2.0 has support for MPRIS v2, meaning it can make use of the Ubuntu Sound Menu"
date: 2012-03-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2012-03-01
Thought some of you guys might be interested in this.

[http://www.webupd8.org/2012/02/how-to-add-vlc-to-ubuntu-sound-menu.html](http://www.webupd8.org/2012/02/how-to-add-vlc-to-ubuntu-sound-menu.html)

---

### Post by mc4man on 2012-03-01
The mpris support is pretty much automatic though I guess it doesn't hurt to have explicitly enabled.

As soon _as any setting is saved _then support is auto  enabled, can be seen like this, (dbus not enabled in settings - 
 > $ vlc
VLC media player 2.0.0 Twoflower (revision 2.0.0-0-g421a4fc)
[0x95d8dd8] dbus interface: listening on dbus as: org.mpris.MediaPlayer2.vlc
[0x9546908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface

If enabling directly then it gets doubled up - 
> $ vlc
VLC media player 2.0.0 Twoflower (revision 2.0.0-0-g421a4fc)
[0x8d4f728] dbus interface: listening on dbus as: org.mpris.MediaPlayer2.vlc
[0x8d4c2d8] dbus interface: listening on dbus as: org.mpris.MediaPlayer2.vlc
[0x8cb7908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.


---

