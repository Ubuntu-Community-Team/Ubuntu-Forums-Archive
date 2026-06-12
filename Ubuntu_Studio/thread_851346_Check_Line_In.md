---
title: "Check Line In?"
date: 2008-07-06
forum: Ubuntu Studio
---

### Post by secondstage on 2008-07-06
I have tried to record the input with sound recorder, but I don't get anything. I'm not even sure if it works or not. Is there a way to check it to make sure that it even works from a command or something?

--secondstage

---

### Post by secondstage on 2008-12-15
I found an answer in fiddling around a bit, but just now got the idea to answer this for everyone else.

First install gnome-alsamixer.
```
sudo apt-get install gnome-alsamixer
```

This is a great GUI for adjusting the levels of any audio input or output on your computer. Open it up(Applications > Sound & Video > Gnome Alsa Mixer), and look to the very right side of the levels for Capture(s). Turn these up to about 3/4, and then turn any levels that have Front Mic, or Mic, or Mic Boost to about 1/2 to 2/3. Open what ever program you are trying to record with, and see if you are getting anything. If not. then turn the levels up all of the way. 

By now you should have some kind of feed. Adjust as necessary so you don't get cracks, or distortion. Next, mess around a bit, and find out which level on the mixer is the corresponding input. I had 3 different captures, and 2 microphones. This is very handy to know when you are in a rush and have an input that is weak.

If you are still not getting any input at all, then you might have blown something up in your computer. :( Sorry. You could get another sound card from Fry's Electronics or Newegg.com, or whatever else you may have locally.

---

### Post by Stochastic on 2008-12-15
it's good to also look through the levels in the pulse audio mixer by running ```
pavucontrol
``` and take a read through the [Comprehensive Sound Problems Solution Guide]("http://ubuntuforums.org/showthread.php?t=205449") before anyone gives up.

---

