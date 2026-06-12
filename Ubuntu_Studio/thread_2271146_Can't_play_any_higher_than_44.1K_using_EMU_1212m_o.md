---
title: "Can't play any higher than 44.1K using EMU 1212m on Ubuntu Studio"
date: 2015-03-27
forum: Ubuntu Studio
---

### Post by sd_read on 2015-03-27
Hello,

I just spent about 4 hours (older machine) recompiling for my emu 1212m card and it works but will only play 44.1K files?

In other words it hangs up on higher bit rates such as 24/192.

Rhythmbox, Clementine, Deadbeef won't play them. 

Actually, if I pound on Deadbeef enough it has played the file only four times slow.

What is interesting is that I upgraded from an older Ubuntu Studio (perhaps 5 years old?) and it was working fine with the higher bit rate files.

Thank you for any ideas - Steve

---

### Post by Mike_Whell on 2015-03-30
Steve - Pulse Audio may be the culprit.  You might have a look at the thread below about how to set up playback software under Linux to playback high res audio files. Start with post #3 in the thread:

[http://www.head-fi.org/t/561961/bit-perfect-audio-from-linux](http://www.head-fi.org/t/561961/bit-perfect-audio-from-linux)

---

### Post by angus-tropical on 2015-04-02
Hi Steve - I also have that identical card - I have just installed a fresh Ubuntu Studio 14.04.2 64bit, and I don't have such problems, although I have always worked at 48kHz. I'll give it a try at 24/96 and let you know how it goes.

I have always had patchy inconsistent results with that card, though. (i.e. jack refusing to see all the inputs and outputs).

I did notice that the old pulse audio sink, which I had when running dreamstudio, is not there now, and that most 'conventional' apps are using the built in audio card, and not the 1212.

---

