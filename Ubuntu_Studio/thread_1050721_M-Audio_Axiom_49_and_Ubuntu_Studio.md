---
title: "M-Audio Axiom 49 and Ubuntu Studio"
date: 2009-01-25
forum: Ubuntu Studio
---

### Post by joshclaxton on 2009-01-25
I just installed Ubuntu Studio 8.10.  I have a M-Audio Axiom 49 Midi Controller I want to play through something.  On PC I use Reason and Ableton Live, so I'm wondering which programs on Ubuntu Studio would be comparable...mainly for midi controlled keyboard samples...It'd be really cool if there were something I could play my Reason samples through.

I also dont even know how to begin installing this Axiom 49.  Can anyone tell me what to do?

---

### Post by g-raf on 2009-12-14
The Axiom 49 doesn't work with Qsynth or ZynAddSubFX? Those are two synthesizers that you should be able to use with the Axiom 49. You will need to connect the Axiom 49 with one of the synthesizers using qjackctl and record audio in Ardour or Audacity.

---

### Post by kayosiii on 2009-12-14
> **joshclaxton said:**
> I just installed Ubuntu Studio 8.10.  I have a M-Audio Axiom 49 Midi Controller I want to play through something.  On PC I use Reason and Ableton Live, so I'm wondering which programs on Ubuntu Studio would be comparable...mainly for midi controlled keyboard samples...It'd be really cool if there were something I could play my Reason samples through.

I also dont even know how to begin installing this Axiom 49.  Can anyone tell me what to do?

I have an AXIOM 61 and it requires almost no setup under Ubuntu. On other versions of linux I have had to make sure that the snd-seq snd-usb-audio modules are loaded at boot time.

A lot of linux programs require an external program to route midi between applications. Patchage is my favourite application for doing this ( but requires jack to be running in the 8.04 version) Jack Control can do this and so can qmidiroute (I think)

---

### Post by sgx on 2009-12-15
> **joshclaxton said:**
> I just installed Ubuntu Studio 8.10.  I have a M-Audio Axiom 49 Midi Controller I want to play through something.  On PC I use Reason and Ableton Live, so I'm wondering which programs on Ubuntu Studio would be comparable...mainly for midi controlled keyboard samples...It'd be really cool if there were something I could play my Reason samples through.

I also dont even know how to begin installing this Axiom 49.  Can anyone tell me what to do?
google for qjackctl screenshots and tutorials, but it is just a virtual patchbay gui, in three sections, the middle section can often be ignored.
Each section has left and right sides, hardware on one side, software on the other. Cick on items to select them, then press the connect button.

Linuxsampler plays giga format files, qsynth (gui for fluid synth) plays soundfonts, Reaper can run in WINE, to host most vsts that don't require dongles or pace/ilok style copy protections, but Reason and Ableton are not working yet in wine, and probably never will work 'good enough to justify fiddling, although FLStudio 9 fans are making headway, so I hope
I get proved wrong!.

zynaddsubfx synth, and hydrogen drum machine are excellent native linux apps, you can play them along with reaper vsts, and record the lot in timemachine, an easy one-button recorder, again, using qjackctl to connect everything.

So there is excellent tunes out there just waiting to be made!

---

