---
title: "Microphone input unstable on 13.04 with GNOME."
date: 2013-06-27
forum: System76 Support
---

### Post by taylorcp on 2013-06-27
Hi --

 I have been having the issue that my microphone input on my Gazelle professional seems to come and go intermittently. Rebooting has solved the issue... nothing obvious seems to be the issue, it is not muted, et cetera.

 I'm using GNOME -- any helpful hints/pointers in the right direction would be appreciated.

Thanks.

---

### Post by KlipperKyle on 2013-06-27
Sounds similar to this thread about the mic not working when resuming from suspend:

[http://ubuntuforums.org/showthread.php?t=2140216](http://ubuntuforums.org/showthread.php?t=2140216)

Try looking at your audio devices with pavucontrol. Pavucontrol talks directly to PulseAudio.

```
sudo apt-get install pavucontrol
pavucontrol

```

Maybe your mic is somehow getting disabled.

---

