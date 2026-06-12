---
title: "I find it ironic that people complain about Pulseaudio when..."
date: 2009-11-19
forum: The Cafe
---

### Post by hoppipolla on 2009-11-19
I am sitting here downloading Cedega to play FEAR because I can't get a peep out of the sound on Windows 7! lol

I only have a Sound Blaster Audigy and I've tried everything!

Oh well, I'll see if I have better luck through Cedega :)

Hoppi :)

---

### Post by dragos240 on 2009-11-19
It's not EVEN pulseaudio. It's actually ubuntu's implementation of PA.

---

### Post by Skripka on 2009-11-19
Weird.  Win7 automatically detected my on-board sound and supplied generic enough drivers for everything to run fine enuff for basic use--until I loaded manufacturer drivers.

I hate Creative BTW.

---

### Post by Skripka on 2009-11-19
> **dragos240 said:**
> It's not EVEN pulseaudio. It's actually ubuntu's implementation of PA.

Ding ding ding.

---

### Post by Icehuck on 2009-11-19
So you're complaining that hardware that was made over 5 years ago doesn't work on an OS the manufacturer doesn't support?

---

### Post by hoppipolla on 2009-11-19
It works (on Windows)! yay! Of course, it's too late to actually PLAY games now as people are sleeping, but when Win 7 breaks the sound again tomorrow I will have fond memories of when it worked at 20 to 1 in the morning! lol

Sorry I think I'm just fed up as I was really looking forward to playing fear ._.

---

### Post by hoppipolla on 2009-11-19
> **Icehuck said:**
> So you're complaining that hardware that was made over 5 years ago doesn't work on an OS the manufacturer doesn't support?

Actually, they do. It's the official drivers that were failing, it's just a bug or something in Win 7 itself I believe. but it works now so I'm going to at least TRY to play FEAR! :)

---

### Post by FuturePilot on 2009-11-19
> **dragos240 said:**
> It's not EVEN pulseaudio. It's actually ubuntu's implementation of PA.

> **Skripka said:**
> Ding ding ding.

I've never had a problem with Ubuntu's implementation of Pulse Audio

---

### Post by gnomeuser on 2009-11-19
> **dragos240 said:**
> It's not EVEN pulseaudio. It's actually ubuntu's implementation of PA.

And driver bugs.. 99% of all PA complaints stem from driver bugs but since nobody has managed to hook this up to apport or a similar service to catch and inform the user the fact that PA crashes leads users to blame PA rather than the actual cause.

The PA log will show potential driver bugs when in very verbose output mode.

As these bugs get killed the PA experience will be much more pleasant.

The reason why these bugs do not show up when you run in "pure" alsa mode is that PA stresses the drivers much more, it actually expects them to work, in all aspects, and they don't for the most part.

I would say that the biggest mistake made when implementing PA was to not make the driver bugs automatic, it would have saved the developers from a lot of misdirected flames.

---

### Post by Icehuck on 2009-11-19
> **hoppipolla said:**
> Actually, they do. It's the official drivers that were failing, it's just a bug or something in Win 7 itself I believe. but it works now so I'm going to at least TRY to play FEAR! :)

I'm sorry, I misread their support page. However, the 6.1 speaker mode and gamerport will not function.

---

### Post by FuturePilot on 2009-11-19
> **gnomeuser said:**
> And driver bugs.. 99% of all PA complaints stem from driver bugs but since nobody has managed to hook this up to apport or a similar service to catch and inform the user the fact that PA crashes leads users to blame PA rather than the actual cause.

The PA log will show potential driver bugs when in very verbose output mode.

As these bugs get killed the PA experience will be much more pleasant.

The reason why these bugs do not show up when you run in "pure" alsa mode is that PA stresses the drivers much more, it actually expects them to work, in all aspects, and they don't for the most part.

I would say that the biggest mistake made when implementing PA was to not make the driver bugs automatic, it would have saved the developers from a lot of misdirected flames.

This x9001

---

### Post by hoppipolla on 2009-11-19
> **gnomeuser said:**
> And driver bugs.. 99% of all PA complaints stem from driver bugs but since nobody has managed to hook this up to apport or a similar service to catch and inform the user the fact that PA crashes leads users to blame PA rather than the actual cause.

The PA log will show potential driver bugs when in very verbose output mode.

As these bugs get killed the PA experience will be much more pleasant.

The reason why these bugs do not show up when you run in "pure" alsa mode is that PA stresses the drivers much more, it actually expects them to work, in all aspects, and they don't for the most part.

I would say that the biggest mistake made when implementing PA was to not make the driver bugs automatic, it would have saved the developers from a lot of misdirected flames.

wow, well there we go :)

So why can't Pulse just be a bit easier on drivers, or have some way of knowing when they're not totally reliable?

I've had no issues with it like I say, but I have heard a lot of complaints and also the reason I actually GOT my SB Audigy was because I considered it about the most generic (and therefore supported) soundcard I could find that was ok quality and cheap!

It didn't actually occur to me that Windows might not support something as it is too OLD, as usually in Linux it's due to something being a bit too new.

Win is just a bit foreign to me now, so concepts like that slip me by! :)


Oh, and yeah Icehuck I was using the proper Win 7 drivers, and still am. For now, it seems ok :)

---

### Post by Skripka on 2009-11-19
> **hoppipolla said:**
> wow, well there we go :)

So why can't Pulse just be a bit easier on drivers, or have some way of knowing when they're not totally reliable?

I've had no issues with it like I say, but I have heard a lot of complaints and also the reason I actually GOT my SB Audigy was because I considered it about the most generic (and therefore supported) soundcard I could find that was ok quality and cheap!

It didn't actually occur to me that Windows might not support something as it is too OLD, as usually in Linux it's due to something being a bit too new.

Win is just a bit foreign to me now, so concepts like that slip me by! :)


Oh, and yeah Icehuck I was using the proper Win 7 drivers, and still am. For now, it seems ok :)

In all honesty.  You'll live a much happier life using on-motherboard audio.  It by-and large works on any OS out of the box.  And good luck noticing much difference.

Sound cards...especially Creative/SoundBlaster cards have never done anything for me...unless you count wanting to make me blow my brains out.

---

### Post by gnomeuser on 2009-11-19
> **hoppipolla said:**
> 
So why can't Pulse just be a bit easier on drivers, or have some way of knowing when they're not totally reliable?


It _does_ have ways of knowing when the driver is not working as it is expected to, try running pulseaudio -vvvv and notice that if there is a problem these will be highlighted.

The problem is that nobody thought to hook up a service like Apport to catch them and report them. This is why PA gets blamed.

Regardless, how do you expect to uncover bugs unless you actually use the software. A lot of the functionality PA uses was expected to work, it does in an increasingly amount of drivers now as a result of PAs wide deployment.

We had the same situation with Network Manager, instead of working around driver bugs the aim was to fix drivers. As a direct result of this the Linux wifi stack and drivers now work for nearly all people. Unfortunately all technological advances has birthing pains, all we can do is attempt to make it easy to report the problems with enough information to locate the exact problem.

I think the bigger problem is getting wide adoption for something like apport and getting it hooked up as part of the design when we spot such mistakes to catch them early and to keep a prioritized list of drivers (in combination with something like smolt this is fairly easy to do - if 50% of users are on a broken driver that is an easy target for fixing).  Knowing those two things, in case we can't fix a bug in time for a release (say the bug requires a massive rework of the driver), we can optionally include a workaround if one is present till the real fix is present. We can't just guess blindly, we don't know where the bugs are and we don't know how many people are affected.

---

### Post by kevCast on 2009-11-19
Irony e.g.

```
A prostitue moves to the Virgin Islands.
```

Coincidence e.g.

```
A prostitue moves to the Whore Islands.
```

Trying to downplay a problem by comparing two operating systems, where one contains an implemented sound system and the other a wrapper for a wrapper for a sound system.

```
Well, in Windows 7 you can't [verb] [noun].
```

---

