---
title: "Headphones not working in Gazelle Professional /Ubuntu 13.04"
date: 2013-09-15
forum: System76 Support
---

### Post by bill_mcknight2 on 2013-09-15
I have a brand new Gazelle Professional (gazp9) running Ubuntu 13.04. When my 3 mm headphones are plugged in there is no sound. I have tried making sure that alsamixer settings allow sound to the headphones (like disabling auto-mute and ensurring that the audio volume is not zero).  Nothing seems to work.  And, yes, the headphones are plugged into the right jack, and otherwise work in my Windows machine.  Has anyone encountered this issue or know what I should do?

---

### Post by ddraper2 on 2013-09-19
I am having the same issue. New Gazelle Pro. Going to spend some time chasing it down. Will report anything I find.

---

### Post by ddraper2 on 2013-09-30
OK. After messing around with this I got my headphones to work. The solution makes no sense to me but here it is.

Use the Ubuntu Software Center and install the PulseAudio Volume Control.
Start PulseAudio Volume Control
Start some music or something and verify it is playing on the speakers
Plug in your headphones and they are not working and the speakers have shut off
Goto PulseAudio Output Devices Tab
Built In Audio Analog should be the output device
The drop list will have Headphones selected
Change the droplist value to Speakers
Now the headphones will work

As I have now verified, at least on my box, this is not a hardware issue it sure seems like some kind of software bug.

---

