---
title: "Monkey's Audio"
date: 2006-09-19
forum: The Cafe
---

### Post by The Keeper on 2006-09-19
I don't know for how long, but apparently Monkey's Audio has been open-source for some time now.
[http://www.monkeysaudio.com/developers.html](http://www.monkeysaudio.com/developers.html)

Currently I've been able to play .ape files only in xmms thanks to an unofficial repository which contained Monkey's Audio codec and xmms plugin for Dapper. I wonder if gstreamer or ffmpeg will have Monkey's Audio support in the near future?

---

### Post by bruce89 on 2006-09-19
Monkey's Audio support has been in gstreamer since 0.8.2 - [http://gstreamer.freedesktop.org/releases/gst-monkeysaudio/0.8.2.html](http://gstreamer.freedesktop.org/releases/gst-monkeysaudio/0.8.2.html)

---

### Post by The Keeper on 2006-09-19
The plugin doesn't work with gstreamer 0.10 and that's just a plugin. The plugin requires you to also install unofficial linux mac-port, which might have been made when Monkey's Audio was still closed source.

Since the source code is now available, I wish codec support to be included in gst-plugins-ugly or gst-plugins-bad instead of a seperate plugin. But that's something I have no control of even if I am longing for a proper Monkey's Audio support in linux...

---

### Post by bruce89 on 2006-09-19
The plugn seems to have been abandoned, it is 9 months since the last CVS checkin.

---

