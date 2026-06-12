---
title: "Sm57 to computer (mic)"
date: 2008-08-11
forum: Ubuntu Studio
---

### Post by fait curieux on 2008-08-11
Hi everyone, I have been trying to use an sm57 microphone with my computer for some time and after lots of research, I still cant get it to work. 

Tried using both the line-in and mic plug.

The thing is that my cheap headset mic works just fine, so Im gessing the problem is not on the computer setting part. 

Do I need to get a pre-amp of some sort?

---

### Post by Stochastic on 2008-08-11
What's your soundcard model and what type of input are you plugging the grounded XLR cord (from the sm57) into (i.e. is it a 1/8" - 'small headphone-style' plug - and how many plastic rings are on the tip of the adapter you're using)?

The sm57 is a dynamic microphone so you don't need the phantom powered preamps that condenser mics will use, but you will still need to boost the mic level to a line level (with a preamp), however most soundcards that have a mic input will have a (poor) mic preamp built in.

My guess is that the adapters you're using could be grounding out the wrong signal.

What do you want to end up recording with your sm57?

---

### Post by fait curieux on 2008-08-13
The soundcard im using is a realtek ac97.  The XLR cord im using already have a 1/4" plug at one end, so im using an adapter that is 1/8" to plug it in the soundcard.  It has 1 black plastic ring. 

I want to record a Didgeridoo, which is why i use a dynamic microphone.

Hope you can help me with that :D

---

### Post by Stochastic on 2008-08-14
On your headset microphone that works fine, how many black plastic rings are on its plug?

If you plug in the sm57, hit record, and scream into the microphone (millimeters from your mouth), do you see anything recorded?  If you take that same recording and raise the gain on the soundfile (audacity works fine for this) are you able to hear your screams? - keep raising the gain until you can hear either your screams or the 'noise floor' of your soundcard.  If you do hear your screams, then you probably will need a microphone preamp.  If you can't hear them, then your adapters are most likely not working (could be a bad wire connection in your cord, etc...).

Also, the 1/4" end of your XLR cord, how many black plastic rings does it have?

---

### Post by fait curieux on 2008-08-14
There are 2 black rings on my headset microphone. 

The 1/4" plug of the XLR cable only has 1, like the adapter. What does it means?

Also, when I plug the SM57 in the computer with mic boost on (+20DB) and crank up the volume, I can hear a sort of hissing/white noise, is that the noise floor? I definitely cant hear my scream though.

---

### Post by snowpine on 2008-08-14
Hi there, my advice, do yourself a favor and purchase a proper mic preamp. You can get one that plugs into your USB or Firewire for under $100. You will not regret the purchase if you plan to do any serious recording. Good luck!

---

### Post by Stochastic on 2008-08-14
The two vs. one black plastic rings is me asking how many channels the adapters can carry.  Two plastic rings (a TRS connection) means that there is a Positive, Negative, and Ground (or two positives and one negative in the case of using it for a stereo signal - which you're not doing).  One plastic ring (a TS connection) means you have no ground - this should still work in theory, but can cause troubles in practice.

What it sounds like to me is that the soundcard is grounding out your negative terminal, and thus you're recording a dead signal.  To fix this, try getting a new adapter that has three metal sections on each portion of "linkage".  Or you could go buy a proper mic preamp as snowpine suggests - this solution will most likely be a touch pricier, but your recordings will show the added cost in their sound quality.

---

