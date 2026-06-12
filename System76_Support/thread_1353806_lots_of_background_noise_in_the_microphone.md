---
title: "lots of background noise in the microphone"
date: 2009-12-13
forum: System76 Support
---

### Post by malachias on 2009-12-13
Hi

Any sound recorded or inputted through the internal microphone has a -lot- of background noise. Please see attached for an mp3 of what I mean. I have a Pangolin Performance, which is brand new. Anyone else had this issue and figured out how to fix it?

Thanks,
Mala

---

### Post by cb951303 on 2009-12-13
it looks okay to me :confused:

---

### Post by malachias on 2009-12-13
You don't hear the constant "shhhhhhh" in the background?

---

### Post by cb951303 on 2009-12-13
> **malachias said:**
> You don't hear the constant "shhhhhhh" in the background?

yes but it happens to me with all the crappy mics whether I'm on linux or windows.

---

### Post by NathanZal on 2009-12-14
I have a PanP6 similar to yours, so I set out to duplicate your results. I made recordings with the internal pinhole-mic as well as with a fairly decent external mic (if you know what SmartMusic is, it's the kind of clip-on that they bundle with their systems) at a variety of levels. I used "quiet mode" to minimize the fan noise - something the pinhole electret condenser mic is sure to pick up big time. The noise I got was pretty much the same as you're getting with both of them. I expected the external mic to be much cleaner. The fact that both of these mics produce this level of noise suggests to me that the noise is coming from the sound card, not (entirely) from the microphones, though the fan noise could be a factor in this, too. Most of the noise would likely be EM interference from the mother board, which I've been told is a basic problem with on-board sound cards.  When I turned down the gain on the mic (using System -> Preferences -> Sound -> Input), stood at a distance from the machine,  and held the mic very close, I got the best result.

If you need to make better recordings, I'd recommend a good external sound card. I use a  Lexicon Lambda system. It's USB powered and Ubuntu 9.10 recognizes it with no problems.  It also supports powered mics, Midi, line input, and so on.  It makes very clean, quiet recordings with good mics.

If you have to use the internal mic, I'd recommend playing with the gain as described above.

Hope this helps!

Nathan

---

### Post by HotShotDJ on 2009-12-14
I, too, have made voice recordings on several laptops, including my PanP5 using the internal microphone, and I always end up with that annoying "hissing" noise.  Lets face it, most lap tops don't come with "top-of-the-line" audio equipment.  NathanZal's suggestion is technically the best solution.  However, there is a software solution that might work for you -- it certainly did for me!

After you make your recording, open it using Audacity (installed from regular Ubuntu repositories).  You can then use "Effects -> Noise Removal" to rid yourself of the hissing.  You may want to mess with the noise removal settings, but I've found that the defaults give satisfactory results.

EDIT:  I just ran your sample through Audacity's noise removal tool.  I didn't mess with the settings, so the result isn't perfect, but it should give you an idea of what is possible.  See attached.

---

### Post by tjwilli on 2010-07-03
I'm having this same problem. I thought that maybe it was because of a cheap laptop mic, but I booted into Vista, and recording is much cleaner.

---

