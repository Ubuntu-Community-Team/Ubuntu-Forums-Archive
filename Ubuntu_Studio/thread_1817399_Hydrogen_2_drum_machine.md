---
title: "Hydrogen 2 drum machine"
date: 2011-08-03
forum: Ubuntu Studio
---

### Post by xlandonlinux on 2011-08-03
Hello, my Hydrogen 2 drum machine isn't producing sound whenever I test an instrument or create a pattern for that matter.

I've reinstalled twice, and that doesn't seem to be helping.

I really could use some help.

---

### Post by sgx on 2011-08-03
Hi, you need a few things, a drumkit and a pattern, or a demo song,
(which contains both) or someones hydrogen saved song, and then the proper sound
connections.

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

Install qjackctl with Synaptic, if it's not in your system


menu Tools -->Preferences  then choose the audio system tab,

jack, alsa, oss, portaudio, and auto, choose auto, or jack.

Start qjackctl, then start hydrogen, choose the mode button
to the left of the tempo lcd, to switch between song and pattern mode.

menu Project --> Open demo  should take you to several default demo songs you can load.  Google the gscw drumkits, for some high quality
sounds

The Preferences Midi system lets you turn on midi input, so a qwerty,
midi keyboard or other midi devices can input beats.

Create a main beat, an intro, breaks, and finale etc, place the patterns in the song grid, looking at the demos will give you the
idea.

[http://briansbedroom.org/hydrogen/amen-break-hip-hop-drum-beat-for-hydrogen/](http://briansbedroom.org/hydrogen/amen-break-hip-hop-drum-beat-for-hydrogen/)     a good example
Cheers

---

