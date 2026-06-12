---
title: "Using Linux sampler live"
date: 2008-10-17
forum: Ubuntu Studio
---

### Post by mrufino1 on 2008-10-17
Hi, I helped my friend set up his eee pc with ubuntu and it works great. He is a drummer (I am a bassist and we play together very often) and would now like to use his eee pc with his roland octapad to trigger samples live. He will need a midi interface- any suggestions on what works well with linux? Also, any guidance on how to set this up? I have set up JACK on my IBM laptop and have rudimentarily used ardour with my presonus firepod, so I have dabbled in linux music, but when I have produced albums, I am still on windows with reaper. Anyway, any things I should know specific to the eee pc?

---

### Post by rayj on 2008-10-19
I use Hydrogen for exactly this sort of thing, with a Roland T-8(?) drum pad set and brain. Just load your samples into the drumsound banks, and you can mindlessly whap the pads and drag the 'tracks' around in the pattern composition view to avoid even looking at MIDI data, if you are a slacker. Other than Hydrogen occasionally failing to load with Jack (sometimes it takes me 3 or 4 loads to get Hydrogen to 'take'), it works flawlessly. We even route individual drum samples to different JackRack effects, and tweak them (with some latency, but I haven't bothered to set it up very well) via a Behringer BCF2000 in 'realtime'. MidiMon is a small application that will give you a useful running log of your midi data. Fun.

If your MIDI interface is working with your laptop, it shouldn't be a problem. I have successfully routed MIDI through both my M-Audio Delta 1010 and through the BCF2000 (via USB), at the same time. If you can get MIDI into your computer, the routing possibilities are apparently endless...

---

