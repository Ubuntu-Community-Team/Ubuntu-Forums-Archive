---
title: "Midi-Keyboard in Ardour 3 (beta)"
date: 2012-03-26
forum: Ubuntu Studio
---

### Post by sirriffsalot on 2012-03-26
Hello all!

I've gotten my head around most of Ardour, JACK and everything that comes with that and how to record guitar tracks et cetera, and I'll have to do it sooner or later, so I thought I'd spent my week off getting my head around how to play and record piano, synth, drums, bass et cetera in Ardour? I am having difficulty, even with the Ardour beta having a brand new feature handling just this, finding out how I would go about getting sound out of my Midi-Keyboard (from M-Audio, if that matters).

Would the dear reader save me some time by directing me to the appropriate links that help me take off with Midi-Keyboard functionality?:) Thanks a lot!

--> Leo

---

### Post by jejeman on 2012-03-26
Does your midi keyboard shows as a device?
```
amidi -l
```

---

### Post by sirriffsalot on 2012-03-27
Yes...:)

---

### Post by jejeman on 2012-03-27
Great.
Not realy clear what you want to achive, but here are the basics:

1. Midi keyboards don't output sound, just midi messages. If it has some kind of sound module then it can output sound.

2. Ardour 3 uses jack midi, so If you are using qjackctl the connections are in "midi" tab.

3. In order to show alsa midi in jack midi tab, you need some kind of "bridge". For that use a2jmidid.

4. When you got Maudio midi port in jack midi tab, then just connect it to Ardour's port for midi track.

---

### Post by sirriffsalot on 2012-03-27
Well I've learned that much from using ardour 2, the problem is I can't find any comprehensible guides on how to make it work, lol:) The ardour guide itself is very much depending on me to know lots of stuff already, which I don't... So would you mind explaining the basics of how to get a midi-keyboard working in ardour 3?

Also, I'm getting no sound from Qtractor when playing, recording and replaying what I've recorded... There is definitely something being recorded, but there simply is no sound..:( Any ideas on that? This JACK business is confusing the hell out of me..

Thanks for taking time!:)

--> Leo

---

### Post by jejeman on 2012-03-27
> So would you mind explaining the basics of how to get a midi-keyboard working in ardour 3?Actually I already did. But here is again. 
As I said midi it's just mesages, not sound. So, you will need some sound module, e.g. soft synth. In this example I will use Yoshimi.

1. open Ardour 3
2. make midi track
3. start Yoshimi
4. In MIDI tab connect: midi keyboard with ardour midi track, and ardour midi track with Yoshimi.
5. make stereo audio track
6. connect in Audio tab Yoshimi and ardour audio track

that's it.

---

### Post by sgx on 2012-03-27
a2jmidid -j default

that launches the jackd midi port in the middle tab.

If there are midi-through ports in the alsa tab, these
may need to be connected to the midi ports on the opposite side.
Thats how it is for me. Hydrogen may autoconnect in the
audio tab, but require connection in the alsa or midi tab,
to play hydrogen drum sounds from the m-audio.

scroll down to section 12.1 for synth recording

[http://arnout.engelen.eu/files/dev/linuxmusicians/ardourtutorial.html](http://arnout.engelen.eu/files/dev/linuxmusicians/ardourtutorial.html)

this is a fine how2 page

[http://www.penguinproducer.com/2011/09/recording-with-ardour/](http://www.penguinproducer.com/2011/09/recording-with-ardour/)

put ardour zynaddsubfx youtube 
in google, lots of videos to help.

---

### Post by BcRich on 2012-03-30
> **LeoTB said:**
> Hello all!

I've gotten my head around most of Ardour, JACK and everything that comes with that and how to record guitar tracks et cetera, and I'll have to do it sooner or later, so I thought I'd spent my week off getting my head around how to play and record piano, synth, drums, bass et cetera in Ardour? I am having difficulty, even with the Ardour beta having a brand new feature handling just this, finding out how I would go about getting sound out of my Midi-Keyboard (from M-Audio, if that matters).

Would the dear reader save me some time by directing me to the appropriate links that help me take off with Midi-Keyboard functionality?:) Thanks a lot!

--> Leo
Hi Leo 
Just curious to know if you got it working. I was also wondering when you say "midi-keyboard" is that a midi-keyboard controller that interfaces with your computer via midi cables as more recent models use usb (but I'm not sure about whether those will work with ubuntu without some effort) however the former will be a lot easier to setup as a device for recording midi data, and subsequently getting that data to trigger a synth's sounds (such as zynaddsubfx) through JACK, assuming you have the proper connections. I do this with Rosegarden, if you are interested?

---

### Post by sgx on 2012-03-30
also, connecting a midi keyboard by a usb cable while also having 5 pin midi cables connected, can cause conflicts on some systems.
Test each way by itself, if problems persist.

a usb hub should not be used

make sure the keyboards power supply is the correct rating.

use a qjackctl setting of 3 for periods/buffer
fora usb device. :popcorn:

---

