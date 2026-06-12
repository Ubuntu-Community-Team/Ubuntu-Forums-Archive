---
title: "Not sure what program to use."
date: 2008-09-02
forum: Ubuntu Studio
---

### Post by matdombrock on 2008-09-02
I finally have a good enough computer with Linux on it to try my hand at some music production.

I am looking for some sort of alternative to ableton live. It doesn't need to be anything like live really, it just needs to have the same (or close) end results. 

I don't really want to install Ubuntu studio, but could you recommend any good apps?

---

### Post by paulmerchant on 2008-09-02
Not sure what you mean by something like Ableton Live, but if you want to buy a proprietary virtual studio application like Live, you could try Renoise or energyXT. Both are great and work on Linux. They both have functional demos for download. For an open source virtual studio, you can try LMMS. Rosegarden and Muse are also fairly complete as virtual studios (midi and audio).

One thing a lot of people do is set up something called the Jack Sound Server. Then they string together multiple applications using this sound server to create their own, customized studio. For example, you could write your music in seq24, Rosegarden, Muse, etc., have it drive synths like ZynAddSubFx, Qsampler, Hydrogen, etc., and then record everything in something like Ardour using your Jack connections. This method was a pain the first time I tried it. Now I'm starting to love it.

If you go this modular, multiple application approach, make sure you take things slowly. Instead of getting bogged down by trying to learn and isntall a dozen applications at the same time, spend time in one application before moving to another. For example, if you are going to mostly write midi and use synths, get comfortable with a midi application first. If you will mostly be playing with drums, play with Hydrogen before moving on to something else. If you will mostly be playing with audio recordings, spend a lot of time in Ardour first.

I was using energyXT. Lately I've been playing with seq24 to qSampler, ZynAddSubFx, and Hydrogen all going into Ardour.

Someone can probably come along with a more specific answer, but you may need to share some of your computer/audio experience and more details on how you plan to make music in Linux.

---

### Post by pkslot on 2008-09-03
Just remember to install the linux-kernel-rt before you go and try out the different things.

---

