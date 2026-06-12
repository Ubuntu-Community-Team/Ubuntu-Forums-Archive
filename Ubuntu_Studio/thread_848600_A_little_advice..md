---
title: "A little advice."
date: 2008-07-03
forum: Ubuntu Studio
---

### Post by handtomouth on 2008-07-03
[FONT="Tahoma"]Hello, 

I am brand new to Ubuntu, I’ve only seen it once on someone else's laptop.  However, from what I have seen, it looks that mutts nuts!

Whilst looking around on the subject I found Ubuntu Studio.  As a guitarist wishing to do some home recording it looks like just the thing I need....but I have a few questions.

Basically, as already mentioned, I play acoustic guitar.  I have a Rode NT1 Microphone, and that’s it.   Whenever I need to record, I have to get in a car drive 2 hours down the motorway where I have a friend with a Mac and Pro Tools, and he does a fantastic job in making me sound reasonable in a recording!

What I would like to do is record the guitar at my place, and email it to my friend for mastering/mixing.

That a little bit about me……now for my question:

Can anyone advise me on the minimum requirement for a laptop to run Ubuntu Studio, with the expectation of recording acoustic guitar to a decent quality?  That’s it.  No mastering. No layering of tracks.  Just recording; Oh, and a click track/drum loop through the headphones to keep me in time.

I’ve seen other people within the forum asking the “Minimum requirements” question, but the answer is always “It depends on what you want to do”.  Hopefully you have an understanding of what I am trying to achieve with Ubuntu Studio and someone can give me some clues.

Cheers.

[/FONT]

---

### Post by Stochastic on 2008-07-04
Welcome!  I'm glad you were impressed by linux.

Well I should first warn you that things like mic placement and room acoustics will greatly alter your recordings, so your milage may vary when creating your own recordings (though that's an ok mic, so you're halfway there).

UbutnuStudio runs fine on my AMDTurion 1.8ghz (single core) laptop, with 2gig of ram - it's getting to be an old machine by today's standards.  And that's with lots of power kicking around for processing etc...  I imagine you could easily work your way down to a Pentium600mhz with 512mb ram (maybe less), and still make a decent mono recording without XRUNS (glitches).

The one piece of hardware that will make a substantial difference is your soundcard.  Take a look either at the [ALSA driver's supported soundcards]("http://www.alsa-project.org/main/index.php/Matrix:Main"), or the [ffado supported soundcards]("http://www.ffado.org") to make sure that you get one that's linux friendly.  I'd also buy it from a music store if I were you and make sure you get one with a built-in microphone pre-amp with phantom power (or you'll need to buy an external preamp with phantom power).  Better yet, spend the money on a REALLY NICE pre-amp in your soundcard, as you're mastering friend will thank you greatly for making his job easier, and you'll get a nicer/truer product in the end.

Then all you'll need is a recording program like Ardour, Rezound, or Audacity to make your mono WAV file recording to send away.

---

### Post by handtomouth on 2008-07-07
Nice on Stochastic, your reply is much appreciated.   You've given me some things to think about whilst I save up for the laptop!! 

Cheers,

HandToMouth.

---

### Post by jem7v on 2008-07-08
You'll definitely need a preamp for your microphone, because the "Mic" port on any computer simply won't cut it.  Usually a preamp will bring your microphone up to "line level" so you can plug it into the Line In port on your computer, which is better than nothing...

If you're handy with a soldering iron (or have a friend who is), you can even build your own mic preamp! It might be harder to find one for a phantom powered mic, but if you search Google for "diy balanced microphone preamp" you'll turn up a few designs. (You can get most of the parts you need from Smallbear Electronics (online) 90% of the time for things like that, or Mouser or Digikey.)

Meanwhile, these guys [http://www.system76.com/](http://www.system76.com/) sell laptops optimized for Ubuntu with it preinstalled.  If you're looking for an Ubuntu laptop that might be an easy way to go, and possibly cheaper than buying a laptop with Vi$$$ta installed on it.  (Remember - if you buy a computer with Windows on it, you're also paying for Windows... not just the hardware!)


Don't know how helpful any of that was, but Maybe...

---

### Post by Stochastic on 2008-07-08
If you're considering a firewire card + new laptop you should also consider what firewire chipset is in the laptop (if you can find that out) as RICOH are known to be pretty bad for audio, whereas TexasInstruments have a much better reputation.  I was told by a System76 user that their personal laptop's chipset was a RICOH, but I couldn't find any offical docs on the subject.

---

### Post by Ed J on 2008-07-16
I'm not using a laptop, but I have been using Ardour on an old P4 1.5GHz with 1MB RAM. I'm also using Hydrogen for drum tracks, its cool.

---

