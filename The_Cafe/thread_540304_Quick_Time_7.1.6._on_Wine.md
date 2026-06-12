---
title: "Quick Time 7.1.6. on Wine"
date: 2007-09-01
forum: The Cafe
---

### Post by Malta paul on 2007-09-01
I spotted this link,  [http://wine-review.blogspot.com/2007/08/quicktime-716-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/08/quicktime-716-on-linux-with-wine.html)
Thought some of you guys might be interested

---

### Post by starcraft.man on 2007-09-01
Maybe I'm missing something but why would you want to go through all that for Quicktime? We have one step solutions like VLC and the codec pack... they certainly don't take that much effort to play back video.

---

### Post by FuturePilot on 2007-09-01
> **starcraft.man said:**
> Maybe I'm missing something but why would you want to go through all that for Quicktime? We have one step solutions like VLC and the codec pack... they certainly don't take that much effort to play back video.

Yes, I was thinking the same thing. Mplayer+Gstreamer plugins has been able to playback anything I've thrown at it.

---

### Post by Malta paul on 2007-09-01
Well I don.t use window myself I also use VLC  but perhaps be someone may like to use Quick Time.
 Choice is one of the strengths of Linux.:).

---

### Post by Acglaphotis on 2007-09-01
You guys think it could work with QT pro?

---

### Post by Andrewie on 2007-09-01
> **Acglaphotis said:**
> You guys think it could work with QT pro?

QT pro is the same thing so I don't see why not

---

### Post by orko3001 on 2007-09-01
But how do I add it? I tried:

[http://packages.ubuntu.com/dapper/utils/quicktime-x11utils](http://packages.ubuntu.com/dapper/utils/quicktime-x11utils)

and this:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
#
For i386, the package is called w32codecs:
sudo apt-get install w32codecs

#
For i386, the package is called w32codecs:
wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1+build1_i386.deb)
sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb

But still no luck :(

---

### Post by Acglaphotis on 2007-09-01
It doesnt work with qt pro : (.

EDIT: IT WORKS! HAPPINESS!

---

### Post by MacBookBuntu on 2008-01-02
> **starcraft.man said:**
> Maybe I'm missing something but why would you want to go through all that for Quicktime? We have one step solutions like VLC and the codec pack... they certainly don't take that much effort to play back video.
While VLC and Mplayer can play Quicktime files with the codecs installed, I have found NO working program for Linux that lets me edit movies (trim, cut, paste, merge).  Quicktime Pro under Wine is a godsend for Linux for simple video editing.

---

