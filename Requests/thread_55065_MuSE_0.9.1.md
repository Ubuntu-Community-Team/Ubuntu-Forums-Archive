---
title: "MuSE 0.9.1"
date: 2005-08-07
forum: Requests
---

### Post by SFN on 2005-08-07
from [dyne.org](http://dyne.org):
> MuSE provides the free software community with a user friendly but powerful tool for network audio streaming, making life easier for indypendent free speech online radios.

MuSE is an application for the mixing, encoding, and network streaming of sound: it can mix up to 6 encoded audio bitstreams (from files or network, mp3 or ogg) plus a souncard input signal, the resulting stream can be played locally on the sound card and/or encoded at different bitrates, recorded to harddisk and/or streamed to the net. When sent to a server, the resulting audio can be listened thru the net by a vast number of players available on different operating systems.

To be operated MuSE offers graphical interfaces and a documented commandline interface in the good old unix style.

There's a .deb available that works well on Debian but does not work on Ubuntu. Part of the reason is the versions of libvorbis0a, libvorbisenc2 and libvorbisfile3 that Ubuntu uses. They are behind the current ones you get from Debian. (Debian is providing 1.1.0-1 of each, where Ubuntu gives us 1.0.1-1)  However, installing the Debian packages only fixes part of the problem. You can stream in MP3 without issue. However, OGG streams fail.

So perhaps this is a request for a MuSE package as well as updated libvorbis packages.

The .deb package is located [here](ftp://ftp.dyne.org/muse/binary/MuSE-0.9.1-i386-1.deb).

---

### Post by CrimsonKing on 2005-12-14
I desire the improved ncurses interface and would very much like to echo this request.

---

