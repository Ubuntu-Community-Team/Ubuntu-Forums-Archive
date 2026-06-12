---
title: "Sound capture woes - tons of noise!"
date: 2008-09-22
forum: Ubuntu Studio
---

### Post by Envergure on 2008-09-22
I'm trying to record my Roland JX-3P  into Audacity and i isn't working.  First of all, when the synth isn't playing anything the signal is far above the middle, and it's very noisy.  When i do play the synth's sound is WAY too loud and very distorted.  I don't hear any of the noise through my headphones, but i *do* hear the synth perfectly.  I have th synth connected to my microphone-in, actually, but using line-in creates the same problem.  I've tried using the synth's normal output and the headphone-out.  When i use the headphone-out i hear the sound perfectly, but when i use normal-output i only get it in one ear, but the recorded sound in Audacity is in both ears.

This seems like quite an assorted pile of symptoms.  I hope someone can sort them out!

Thanks in advance, 
Chris

---

### Post by paulmerchant on 2008-09-23
It sounds like you are plugging an amplified or high impedance source (your synth) into line level inputs on your sound card. You probably need a mixer, a direct box, or an audio interface that can handle your synth's output.

If you have a mixer, a direct box, or a pre-amp type device around, you can plug your synth into that and then take the line level output from your device and connect that to your line level inputs on your sound card.

You'll get the best results from a digital audio interface that's designed to take inputs from instruments and digitize the audio for your computer. I use either my cheapo Tascam US-122 or a little pre-amp for this purpose.

Then again, I might be completely misunderstanding your problem.

---

### Post by paulmerchant on 2008-09-23
One more thing. If you are trying to get a decent recording, you'll want to avoid using headphone outputs on your instruments and/or the little microphone inputs on sound cards. Both are trouble.

---

### Post by Envergure on 2008-09-26
I've dug up a little analog preamp/mixer sort of thing.

With it in place etwwen the synth and my comp here's what i hear:
In Audacity:  Same as before.
Thru the computer's headphones:  Same as bafore, but with tons of hiss.
Thru the mixer's headphones:  The synth, with no perceptable noise or distortion, like it should be.

On Sunday i'll see if i can borrow a direct-box from my church and try that.


I think it's a driver problem, though.  Some signal somewhere is ending up where it shouldn't be.


Should i upload some quick samples of what it sounds like?

---

### Post by Envergure on 2008-09-27
Attached are some short samples of the problem.  **Read the text file first!**

---

