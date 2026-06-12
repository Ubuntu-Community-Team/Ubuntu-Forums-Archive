---
title: "Transitions"
date: 2012-11-28
forum: Ubuntu Development Version
---

### Post by anca-emanuel on 2012-11-28
info: Here are details about transitions.

For now,
> Dear Ubuntu developers,

I intend to upload libav 9 to raring rather sooner than later. I'm writing you because:

 - the package is not in debian/unstable yet, but currently sitting in NEW, targeted at experimental (but syncing is not possible anyway)
 - I don't think that there will be a similar fallout like the last big libav package, but given that some more internal API got dropped and there are a number of packages in the archive that use deprecated APIs, there will be some problems.
 - I remember that Collin requested such big updates to be announced before on this mailing list. I'm doing it with this email.
 - gstreamer (via gst-libav) requires this version.

All relevant SONAMEs have been bumped, so existing binaries should not be broken by this upload. See [http://libav.org/news.html#9beta1](http://libav.org/news.html#9beta1) for an overview of the most important changes.
Preview packages are available in ppa:motumedia/libav-daily

I would suggest to upload the package now so that we have enough time to deal with packages that require cleaning ups, in case that would happen
[http://people.canonical.com/~ubuntu-archive/transitions/libav.html](http://people.canonical.com/~ubuntu-archive/transitions/libav.html)

Here you can find all: [http://people.canonical.com/~ubuntu-archive/transitions/](http://people.canonical.com/~ubuntu-archive/transitions/)

---

### Post by mc4man on 2012-11-28
Good, (if it ups the versioning of libavcodec, ect. which seems likely.
Then if someone bothers to rebuild audacious-plugins there will again be a ffaudio plugin
(the attention paid to audacious plugins over the last 3 or 4 Ubuntu releases is pitiful, part of the fallout of Debian/Ubuntu using Libav instead of FFmpeg

---

