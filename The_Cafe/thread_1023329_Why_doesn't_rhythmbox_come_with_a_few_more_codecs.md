---
title: "Why doesn't rhythmbox come with a few more codecs?"
date: 2008-12-27
forum: The Cafe
---

### Post by Afkpuz on 2008-12-27
Simple question.  If the ogg format is an open source standard format for media, why doesn't rhythmbox come with out of the box support for it?  I can understand why it wouldn't come with proprietary codecs, like wma, but this one just doesn't make sense.  It's not a big deal as I just install all the gstreamer packages after every install, but what is the reasoning behind this?  /rant

---

### Post by phrostbyte on 2008-12-27
RB doesn't come with any codecs at all. It uses the Gstreamer framework to playback music. Gstreamer packages implement support for specific formats, not the music (or video) players that come with Ubuntu or Gnome. You can think of RB as a GUI frontend to Gstreamer.

---

