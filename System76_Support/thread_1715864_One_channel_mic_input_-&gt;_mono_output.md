---
title: "One channel mic input -&gt; mono output"
date: 2011-03-27
forum: System76 Support
---

### Post by azion1995 on 2011-03-27
OK, so I have a Ratel Ultra with a single microphone plugged into it. As the system recognizes my mic as a single channel (left, to be precise), all I get is a single channel recorded: the left one.

My question is this: is there any way, in software, to convince my Ratel Ultra + Ubuntu to treat this as a mono input, and give me mono output on both channels, rather than only on the left? It'd be better than needing to get a stereo mic to do simple recordings.

Thx,
-Z

---

### Post by Ebonwumon on 2011-03-27
If it's not live or anything you could duplicate the left channel to the right in audacity.

---

### Post by jml on 2011-03-27
I am not an expert in digital recording but try this.Click on the speaker icon in the upper right hand corner.  Click on the volume control button.  Make sure the two microphone channels are locked together.  Does that help?

Second idea, does the Ratel have two mono mic inputs in the back or one stereo mic input?  If you have two, split the signal with a simple "Y" connector.  If you have only one input, then the wiring setup is a bit trickier and I am not sure how to handle that hardware setup.  Good luck.

Joe

---

### Post by azion1995 on 2011-03-27
> **Ebonwumon said:**
> If it's not live or anything you could duplicate the left channel to the right in audacity.

Sadly, I am talking about live stuff. It seems that the mic jack is stereo. I suspect that the best result would be to set my 4 channel mixer to mono, feed two 1/4" channel from the mixer into an adapter which folds two 1/4" mono inputs into a single 1/8" stereo output, and then plug that into the Ratel's sound card. Provided, of course, that I can find such an adapter. I imagine that Radio Schlock should have it, but I'd prefer to see whether I Can do this purely in software before I need to buy more adapters.

Thx anyhoo,
-Z

---

### Post by isantop on 2011-03-28
Go to System > Preferences > Sound. Then, open the hardware tab. Click on the Internal audio item, then expand the profile list. What is available in there?

---

