---
title: "Using Qsynth"
date: 2012-10-13
forum: Ubuntu Studio
---

### Post by kriot on 2012-10-13
Hi All,

I have a simple setup:

qjacktl
QSynth (fluidsynth) 

I can load up a soundfont just fine and play notes,...etc. However, my problem is I cannot switch to a sound which is on a different channel. All I can play is which ever instrument is on Channel 1.

How can I play the sounds/intstruments on Channels 2-16?

I have this problem while using SEQ24 as well, For things like hydrogen, I can easily switch the the channel via hydrogen, however I cant for the life of me figure out how to do that using qsynth.

Sorry for such a dumb question, I'm sure there's an easy solution to this and I appreciate the help.

KC

---

### Post by sgx on 2012-10-14
Hi, to use multiple soundfonts, click the +  sign on the lower left
of the gui, which opens a new tab for a second/third/fourth instance,
and choose a soundfont for each.

If the sounfont is a bank with many sounds, once the soundfont
for the new tab is in place, click the 'Channels' button on the main gui,
and click or double click the instrument that is on channel 1.

This should open that tabs chosen sounfont requestor,
so if qsynth2 tabs soundfont has 128 instuments, or 32 etc,
any of them can be chosen by double clicking them, or single click and
press OK on the requestor.

So each tab still plays back the sounds on channel 1, and needs
its own connections in qjackctl.
Call it multi-timbral, or midi omni mode, Sampletank and other
pro samplers can do this. So does zynaddsubfx/yoshimi.

To play back a different soundfont on each of the default
midi channels, you may have to install fluidsynth-dssi, and
open it in qtractor, or rosegarden, with a track for each
midi channel. The version I have here does not allow it in
the standalone qsynth, or fluidsynth, not sure why.
You could type command

fluidsynth --help

and experiment with the options:

fluidsynth -j -L 16 -o audio.jack.multi=yes -a jack name.sf2

Its a very sensible question. Maybe if the default qsynth had
3 tabs open it would be more obvious.

Cheers

---

### Post by sgx on 2012-10-14
while on the sf2 topic, E-mu soundfonts are on sale for awhile,
at

[www.digitalsoundfactory.com](www.digitalsoundfactory.com)

coupon code OCTOBER at checkout during October saves 30%
on all sounds.

These are very affordable, excellent quality, many sound styles,
and sfz format is also available, that may work in linuxsampler.

sf2 is working fine in qsynth.
Cheers

---

