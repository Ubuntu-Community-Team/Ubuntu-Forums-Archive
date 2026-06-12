---
title: "Audacity GUI delay"
date: 2012-04-28
forum: Ubuntu Studio
---

### Post by earthshakergb on 2012-04-28
I may have asked this before, I don't remember. I don't know how to view my posts on this forum.

There are a couple of problems I am having, using Audacity and UStudio 11.10.
I have a huge gui delay, that is to say the waveform is created a long ways behind the cursor, like 5 seconds or so. I thought there was a way to turn off the waveform display, during recording, hence reducing CPU use. I can't find how to do that right now.

Any ideas?

---

### Post by sgx on 2012-04-28
menu Edit-Preferences-Tracks --in the panel, untick 
'Update tracks while playing'

If other issues crop up, you might want an older version of audacity. Maybe uninstall it using synaptic, then manually reinstall a .deb version

1.3.12-6 is in the list here:

[http://packages.debian.org/stable/sound/](http://packages.debian.org/stable/sound/)

install with

sudo dpkg -i nammxxx.deb

In the meantime, timemachine is great for basic recording
using jackd/qjackctl:

[http://packages.debian.org/unstable/sound/timemachine](http://packages.debian.org/unstable/sound/timemachine)

Cheers

---

