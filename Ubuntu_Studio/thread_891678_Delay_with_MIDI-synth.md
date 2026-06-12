---
title: "Delay with MIDI-synth"
date: 2008-08-16
forum: Ubuntu Studio
---

### Post by olskar on 2008-08-16
Hi,
When I use my MIDI-synth with rosegarden there is a slight delay after pressing the keys. This problem does not occur when using ZynAddSubFX. The only difference that I can see in JACK is that ZynAddSubFX is not using timidity as rosegarden does. Could this be the reason? How would I fix this? Thanks!

---

### Post by Braincrawler on 2008-10-03
I have the same problem too. It would be nice if it's fixed. But until then there is a workaround:

I installed timidity++ and loaded a GM-Soundfont into it. It works without delay and sounds good but uses much CPU-Time.

Here is the HowTo:
[https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo?action=show&redirect=MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo?action=show&redirect=MidiSoftwareSynthesisHowTo)

---

### Post by angelsguitar on 2008-10-03
> **olskar said:**
> Hi,
When I use my MIDI-synth with rosegarden there is a slight delay after pressing the keys. This problem does not occur when using ZynAddSubFX. The only difference that I can see in JACK is that ZynAddSubFX is not using timidity as rosegarden does. Could this be the reason? How would I fix this? Thanks!

I believe you can get better results using your soundfonts with QSynth instead of timidity.  As far as I know, timidity is not compatible with Jack, but Qsynth is.  Maybe that's why you don't have the problem with ZynAddSubFX, as it is compatible with Jack too.  If you keep all your audio signal routed to Jack, instead of mixing Jack-compatible synths (like ZynAddSubFX) with non-compatible ones (like timidity), you may be able to get better latency (less delay on the audio signal) out of your soundcard when you play your synths realtime or record.

Another factor could be your soundcard/audio interface.  If your card is not a low-latency card, you will get higher delay (latency) on the signal.

---

### Post by Braincrawler on 2008-11-02
But with Windows it works with no delay on the same System ;-) So, this is not the problem.

---

### Post by akdmia on 2008-11-23
> **olskar said:**
> Hi,
When I use my MIDI-synth with rosegarden there is a slight delay after pressing the keys. This problem does not occur when using ZynAddSubFX. The only difference that I can see in JACK is that ZynAddSubFX is not using timidity as rosegarden does. Could this be the reason? How would I fix this? Thanks!

ZynAddSubFX is a software synthesizer, like timidity, fluidsynth, etc. so it don't uses timidity because it is who make the sounds.


> **angelsguitar said:**
> I believe you can get better results using your soundfonts with QSynth instead of timidity.  As far as I know, timidity is not compatible with Jack, but Qsynth is.  Maybe that's why you don't have the problem with ZynAddSubFX, as it is compatible with Jack too.  If you keep all your audio signal routed to Jack, instead of mixing Jack-compatible synths (like ZynAddSubFX) with non-compatible ones (like timidity), you may be able to get better latency (less delay on the audio signal) out of your soundcard when you play your synths realtime or record.

Another factor could be your soundcard/audio interface.  If your card is not a low-latency card, you will get higher delay (latency) on the signal.

Yes timidity is compatible with Jack.
you just need run timidity with jack output ( -Oj instead of -Os )
e.g:  timidity -iA -Oj
Ofcourse Jack server must be running first.

> **Braincrawler said:**
> But with Windows it works with no delay on the same System ;-) So, this is not the problem.

Don't think that it's the same system.
at low level timidity have sources for each output driver ( alsa, oss, jack, etc )..
The core sources of timidity are the same, but the output sound sources are complety different.

---

### Post by scott.enderle on 2008-11-28
> **akdmia said:**
> 

Don't think that it's the same system.
at low level timidity have sources for each output driver ( alsa, oss, jack, etc )..
The core sources of timidity are the same, but the output sound sources are complety different.

I suspect what Braincrawler meant was that it was on the same hardware. I have to confirm this; on my hardware, windows offers low-latency midi synthesis of a kind I haven't been able to achieve using any flavor of linux. I'll just have to keep trying!

---

### Post by davesollows on 2009-01-26
Perhaps this should be a seperate thread.

But I am using a KORG microKontrol through Jack via the usb port, and I can't seem to get the keys to trigger qsynth I've tried loading various soundfonts.  But i see/hear no indication that a midi trigger is being recognized in either qsynth or jack.  i have verbose messages enabled.

How do I begin troubleshooting this issue?

Please and thank you for your time, 
DCS

---

