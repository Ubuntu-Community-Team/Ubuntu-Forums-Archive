---
title: "Step by step jack and ardour guide please ?"
date: 2010-04-19
forum: Ubuntu Studio
---

### Post by Mysticaly on 2010-04-19
Hi, I've been trying to replace windows all together with a working installation of ubuntu with ardour for music production. .
I've come across a whole bunch of problems with this, and are now on a fresh install ..

Here is my hardware:
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

CPU: Pentium 4 3.40
Hard drives 10.000 RPM's
Soundcard: SB Audigy 2
Ubuntu 9.10
RAM 2048MB

The CPU and hard drives should hold there end all fine, the sound card is a gamer card and not for producing music, I'm well aware of this.

**I will only use Ardour for mixing/editing and playback, there will be no recording at all done in ardour as I do this with a physical mixer.**

As I started out saying I've been experiencing tons of trouble getting all this to work satisfactory, I've had xruns, I've had jackd taking over as sound server even when jackd are not running at all, I've had jerky sounds, I have experienced pulseaudio being impossible to start even when uninstalling jack, ardour and allot of other stuff altogether (only thing that gets PA back is a reinstall)

I have tried pretty much every guide I've found, and there is allot of them out there, I've followed the guides hosted at the ubuntu help pages, rt-linux real time kernels and much more, still I have all of these problems. My conclusions are: ether I'm setting it up all wrong or my soundcard can not be used with Ubuntu Jack. On the other hand I've been pretty successful in AV Linux so obviously my sound card can be used.

I need help setting it all up, a guide from a to z kind of.
I hope someone can help me out as I really do want to only run Linux.

---

### Post by cchhrriiss121212 on 2010-04-19
An rt kernel with jack in real time mode will give you the best performance, and try checking the soft mode box in the qjackctl setup window. You can reduce xruns by increasing your frame rate, giving you a higher latency, which should not interrupt your work as you are just mixing and editing. Other things like compiz and wireless internet connections can apparently interfere with jack, so try disabling those.

I'm not sure about pulse problems as it has been removed on my system after not co-operating with my soundcard. Perhaps start a thread in multimedia and video, explaining what happens when pulse does not start.

---

### Post by hxcobd on 2010-04-19
Hello and welcome!

You might want to take a quick look at the video tutorials in my signature for solving your RT audio issue, as well as possibly the CPU scaling video for helping with your stuttery audio issue.

If you can further cite a specific issue you're having, I'd love to make a tutorial to solve it, also.

*edit - I sort of dislike the recommendation to enable Soft Mode in JACK, as that's not really ever going to help anyone properly set up JACK. If your JACK is properly configured for your particular hardware, you'll get VERY minimal xrun errors.

xruns are a great way to benchmark your audio performance; it's best to use them as a guideline, rather than just ignore them completely.

---

### Post by AutoStatic on 2010-04-20
hxcobd, finally, Youtube tutorials on JACK and Linux & RT!

---

### Post by hxcobd on 2010-04-20
Is that sarcasm? Why I oughta...

---

### Post by AutoStatic on 2010-04-20
No, no, seriously, there are no good Youtube tutorials available on this subject. I just watched the JACK one and it's good. You speak clearly so it's easy to follow and the info is good, not too much, not too little. Maybe a bit too much though on the history and the ReWire thing, but maybe that's personal, I prefer tutorials that get to the point right away.

---

### Post by cchhrriiss121212 on 2010-04-20
> *edit - I sort of dislike the recommendation to enable Soft Mode in JACK, as that's not really ever going to help anyone properly set up JACK. If your JACK is properly configured for your particular hardware, you'll get VERY minimal xrun errors.
I'm aware of that, and it is just a suggestion as opposed to a necessity. I enabled it on my old laptop with intel sound, and it seemed to help stability. I did however, find this after a quick search:
> Jackd's 'softmode' option allows that clients can be late in processing
data, and will not be booted from the graph for doing so. However, this
causes the whole graph to be delayed and an audible glitch is likely
to result.

So maybe it is not worth it. Nice tutorials btw.

---

### Post by Mysticaly on 2010-04-20
> **hxcobd said:**
> Hello and welcome!

You might want to take a quick look at the video tutorials in my signature for solving your RT audio issue, as well as possibly the CPU scaling video for helping with your stuttery audio issue.

If you can further cite a specific issue you're having, I'd love to make a tutorial to solve it, also.

*edit - I sort of dislike the recommendation to enable Soft Mode in JACK, as that's not really ever going to help anyone properly set up JACK. If your JACK is properly configured for your particular hardware, you'll get VERY minimal xrun errors.

xruns are a great way to benchmark your audio performance; it's best to use them as a guideline, rather than just ignore them completely.

Hi, thanks allot for pointing me out to your guide, it seems following it did the trick, I really appreciate your guides and would like to offer a huge thank you :)

I've been playing around with jack and ardour since you offered the tips and I've only had one! xrun so far (incredible)
I've loaded up 8 tracks earlier, no problems at all. I will test for a few more days, if it works well I'll finally be ridth of windows for good..

Btw, I'm not using a realtime kernel now, so as you said in your guide it's probably not necessary to do so with the newest kernels.

I'm looking forward to more of your guides, to be honest a link for your guides should have been stickied on the top of this forum.. 

Best regards
a really grateful dude.

Edit:
> **AutoStatic said:**
> No, no, seriously, there are no good Youtube tutorials available on this subject. I just watched the JACK one and it's good. You speak clearly so it's easy to follow and the info is good, not too much, not too little. Maybe a bit too much though on the history and the ReWire thing, but maybe that's personal, I prefer tutorials that get to the point right away.Yes, he's guides are very good and very clear with great explanations. Also I have not succeeded in finding any other good jack guide on youtube so this one is very welcome as you say :)

---

### Post by hxcobd on 2010-04-20
Well thanks for the feedback, guys! Glad they could be of use.

I'd really like to start compiling a list of common problems/errors people are having with JACK setups, and then make tutorials to attempt to solve each of these problems.

My main target audience is people not overly familiar with linux or linux audio, so I try to keep them relatively straightforward.

---

### Post by DerickX on 2010-04-22
Here are some other starter tutorials for Jack and Ardour
[http://www.openstudioproductions.org/tutorials](http://www.openstudioproductions.org/tutorials)

@hxcobd, nice videos, nicely captured. Only the nice value in limits.conf is an myth actually... It doesn't help the performance..

---

