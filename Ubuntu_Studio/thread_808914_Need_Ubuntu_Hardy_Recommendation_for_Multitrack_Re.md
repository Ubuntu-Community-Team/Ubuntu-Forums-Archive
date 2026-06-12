---
title: "Need Ubuntu Hardy Recommendation for Multitrack Recording"
date: 2008-05-27
forum: Ubuntu Studio
---

### Post by willthebold on 2008-05-27
So what I'm wanting to do is just some fairly basic multi track recording. I've got Ardour, but there isn't a way to EQ things that I can find. Is there a plugin for it, or another studio type program that has a built in EQ? All I really need is multi track abilities and EQ in the same program. What's the best thing to get?

---

### Post by warbread on 2008-05-27
One of the things that I'm really wanting in Linux is a sweepable EQ.  AFAIK, there isn't one, but Jamin is pretty good if you know what you want to boost.

---

### Post by Stochastic on 2008-05-27
> **willthebold said:**
> So what I'm wanting to do is just some fairly basic multi track recording. I've got Ardour, but there isn't a way to EQ things that I can find. Is there a plugin for it, or another studio type program that has a built in EQ? All I really need is multi track abilities and EQ in the same program. What's the best thing to get?

Do ```
sudo apt-get install ubuntustudio-audio-plugins
``` then you'll have lots of eq options.  You'll need to insert the ladspa plugin(s) of your choice in the mixer window of Ardour in the black rectangles above the (for pre) and below the (post) fader.  Once that's in, you'll be able to fully automate each setting of the plugins via the main ardour window.

As for the sweepable eq, I don't really see the need if you've got the various multiband eq plugins and parametric eq options in LADSPA.

---

### Post by warbread on 2008-05-27
> **Stochastic said:**
> 

As for the sweepable eq, I don't really see the need if you've got the various multiband eq plugins and parametric eq options in LADSPA.

Well, I don't "need" it in the sense that I need to breathe or eat, but it's an extremely useful tool.  I love Jamin's EQ, but it's laborious to move those sliders finding that sweet-spot for each instrument, or which frequencies need to be killed to make room for others.  A sweepable eq is great for that, but unfortunately it's currently not available in Linux.

---

### Post by willthebold on 2008-05-27
God, thanks so much. I'm still pretty new to Linux, so I'm having to ask a lot of things, but so far everything ******* rocks. These forums are invaluable. It seems there's nothing I can't do with this OS. This worked like a charm. It's exactly what I was looking for. Thanks again.

---

### Post by Stochastic on 2008-05-27
Warbread, we're getting off topic from the OP, but I'd like to know what advantage you see a sweepable eq has over say the single-band or triple-band parametric eqs by steve harris (in the ladspa set) or the 4-band parametric filter by Fons Adriaensen?  A sweepable eq just has fewer options.  Jamin is excessive overhead for mere EQ, though it's graphic interface is nice.  Furthermore, Jamin doesn't require you to move all the faders, just adjust the parametric eq window.

---

### Post by warbread on 2008-05-27
When you have a mix that includes lots of different instruments and you need to attenuate or boost some of the frequencies in order to make sure they each ring clearly, it's helpful to use a sweeping eq.  You run the track through the eq, boost a narrow band of frequencies by 10 dB or so and then move that peak across an otherwise flat eq.  You can use this to find an instrument's "sweet spot" in the recording and boost that frequency to get the most out of it.  Doing the same thing with an attenuated frequency, you can clear up muddy recordings.  The Fruity Loops eq is one of two really impressive things in the commercial audio world to me (the other being SynthMaker, a stable and pretty Alsa Mod Synth).

Now, aside from the sweeping, such an eq has an advantage over a 3 or 4 band eq in that you can set the width of the band for more control.  This isn't something I'm missing in Linux as Jamin has a really nice eq.  While it may seem excessive to you, I do lots of instrumental recordings and this sort of exacting control is necessary to getting a good mix.  Now, don't get me wrong, I'm not missing it so much that I run to Windows to record.  But this is an industry standard technique for getting really clear mixes, and it's impossible for me to do without using VSTs, which I can't do since I'm running 64 bit.

One day I'll have it.  One day...

---

### Post by robeast on 2008-05-27
> **warbread said:**
> You run the track through the eq, boost a narrow band of frequencies by 10 dB or so and then move that peak across an otherwise flat eq.  You can use this to find an instrument's "sweet spot" in the recording and boost that frequency to get the most out of it.  Doing the same thing with an attenuated frequency, you can clear up muddy recordings.

That's a parametric equalizer, dude!

---

### Post by Stochastic on 2008-05-27
Yeah, a sweepable eq is often referred to as a semi-parametric eq as it has some but not all of the parametric eq's features.  Many don't allow you to set the bandwidth (or Q) of the band, just the centre frequency.

Take a look at the single-band parametric eq in the ladspa set if you're confused.

Here's a little comparison between the different types: [http://www.homerecordingconnection.com/news.php?action=view_story&id=144](http://www.homerecordingconnection.com/news.php?action=view_story&id=144)

---

### Post by warbread on 2008-05-27
> **robeast said:**
> That's a parametric equalizer, dude!


:oops:

My god, to think I've been calling it the wrong thing all this time.

*sigh*

---

### Post by robeast on 2008-05-27
> **Stochastic said:**
> 
Here's a little comparison between the different types: [http://www.homerecordingconnection.com/news.php?action=view_story&id=144](http://www.homerecordingconnection.com/news.php?action=view_story&id=144)

OoooO, good page! I just got a decent outboard parametric (Aphex 109) and I've been having a lot of fun doing big filter sweeps with it--very cool sounds. That single parametric EQ plugin should be just what warbread is looking for.

---

### Post by warbread on 2008-05-27
> **robeast said:**
> OoooO, good page! I just got a decent outboard parametric (Aphex 109) and I've been having a lot of fun doing big filter sweeps with it--very cool sounds. That single parametric EQ plugin should be just what warbread is looking for.

Yeah, my mixes should sound a lot better now :lolflag:

I do appreciate the patience though.  There's no shame in learning (or re-learning, as the case may be), but what a n00b mistake that turned out to be!

---

### Post by Stochastic on 2008-05-27
> **warbread said:**
> but what a n00b mistake that turned out to be!

No, no, just a terminology misunderstanding; you understood your sonic concepts so it really wasn't a true noob mistake.  Your point is still entirely valid too, I don't think there's a sweepable eq plugin anywhere to be found in the ladspa set.  Maybe I'll try to make one up someday (or can one of you two beat me to it?).

But now we're fairly far from the OP's topic.

---

