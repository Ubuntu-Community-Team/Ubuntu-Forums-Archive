---
title: "Direct recording through external sound card"
date: 2015-07-26
forum: Ubuntu Studio
---

### Post by Cludio on 2015-07-26
Hello. 

I have a question for the ubuntu musicians out there:

Can I connect a modeling amp that does not have official Linux support to a sound card that does have ( focusrite/m-audio/others), and record directly to the computer?
The amplifier in use would be a Line6 POD HD Pro X.
If its is possible, should I use the MIDI ports or de S/PDIF?

Also what DAW should I use?

P.S. I'm using ubuntu 14.04 LTS.

---

### Post by tgalati4 on 2015-07-26
Welcome to the forums.

In theory, yes, you should be able to plug into a SPIDF port of a supported card (I'm familiar with M-Audio's [Delta66]("http://www.soundonsound.com/sos/jan01/articles/maudio.asp")--it works well in Ubuntu) and simply record the sound using SPIDF as a digital input.

You can also use the SPIDF out from the Delta66 (or similar card) route it into the Line6POD, apply processing, then sent it back into the Delta66 for recording.  You can also make analog patches and get decent quality.  It really depends on what your goals are.

I would only use MIDI if you have a MIDI stream (such as a drum track) that you are trying to record or mix in your session.

As far as using a DAW (digital audio workstation) you can use a similar setup, but there are restrictions.  Those restrictions depend on what you are trying to accomplish and how you have your equipment hooked up.  [http://line6.com/support/topic/5118-question-about-using-the-pod-hd-with-a-daw/](http://line6.com/support/topic/5118-question-about-using-the-pod-hd-with-a-daw/)

I don't have any recommendations on a DAW, but select a system that is compatible with the rest of your gear.  You could use MIDI from the DAW and SPDIF from the Line6 effects POD and feed them both into a Delta66 and still have 4 analog inputs and outputs remaining.  As with any recording setup, monitoring is difficult, confusing, and there is always latency with digital processing that you need to account for.  If your latency is over 10 to 12 ms, then trying to play to your monitor becomes a challenge.

Perhaps explain what your musical goals are.

---

### Post by Cludio on 2015-07-26
Thank you for the info.

Mainly, what I'm seeking to do is to record guitar tracks using the various effects of the POD HD Pro X without using a cab/mic setup (and monitoring that), and mixing it with tracks of the other (virtual) instruments.

---

### Post by tgalati4 on 2015-07-27
Play around and let us know what works and what doesn't.  I don't have a Line6 Pod, so I can't suggest exactly how to hook it up, but share your experiences.

---

