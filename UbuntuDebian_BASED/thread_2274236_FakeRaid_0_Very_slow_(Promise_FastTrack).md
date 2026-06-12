---
title: "FakeRaid 0 Very slow (Promise FastTrack)"
date: 2015-04-18
forum: Ubuntu/Debian BASED
---

### Post by piratelv on 2015-04-18
Hello all, It's been quite a while since I've posted anything on this forums but I feel like my current conundrum is something you will know something about.

For the past few months I've been running from a fakeRaid Raid 0 setup for the first time. This is mainly for keeping everything smooth while running VMs. All was well and cool until recently.
When running more then 2 VMs at the same time the pc started to hang and freeze for short periods. I know that when running VMs freezes usually mean your hitting a IO limit somewhere. 
There was at the time about 9GB ram free and cpu power to spare so that only leaves disk IO.

When I first setup the raid I got a respectable 310mb/s <-> 400mb/s.
[IMG]http://leviv.nu/screenshots/Screenshot-at-2014-11-15_13-17-33-cut.png[/IMG]

However when I do the same tests a few months later, I am left with only 170 mb/s <-> 180 mb/s.  That's the same speed as one of these disk standalone! 

[IMG]http://leviv.nu/screenshots/screenshot_19-04-15_01%3a38%3a23.png[/IMG]

Is there something I have forgotten to do, or is there a log file for the DMraid?  I really would like to get the performance of the raid back to around 300mb/s if at all possible.

The setup is using 2 Seagate ST1000DM003-1ER162 in Raid 0. Apparently using the Promise FastTrack firmware. I had set the raid up using the bios raid feature.
The motherboard is a Asrock 970 Pro 3 R2.0
And this is a dualboot with windows, so mdam won't work I believe.


Thanks for any help.

---

### Post by piratelv on 2015-05-03
It's been a while but still no close to an answer.
I've updated the bios to the latest version. I got a small improvement, but nothing to write home about.

If this isn't something that is solvable in software, a hardware alternative (e.g. an sub 100€ raid card) would also be something I'm open for.

---

