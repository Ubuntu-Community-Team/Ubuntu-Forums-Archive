---
title: "System Specifications for Audio Recording"
date: 2008-10-06
forum: Ubuntu Studio
---

### Post by Sam the Wizer on 2008-10-06
I was wondering how various system specifications, such as bus speed, L1 and L2 cache, etc affect system performance for audio recording.  I'm working on building a new system for this purpose, but don't want to buy a processor/mobo combination with sufficient processor speed and RAM but have it bottleneck somewhere else.  I have been told that a 7200 RPM hard disk is pretty much a necessity.  I'm looking at ~2.4GHz dual core and 2Gb RAM, any suggestions about minimum L1 + L2 cache size and bus speed/hyper-transports speeds to optimize this build?  Anyone able to find a thread along similar lines?

Thanks

---

### Post by Sam the Wizer on 2008-10-20
I talked to an audio engineer friend of mine and he agreed that throughput was important.  He is running a 2.6GHz dual core processor with 1066MHz FSB which he said was probably a minimum.  He works with Mac and Windows but said the Realtime kernel (Linux in general, really) would probably compensate well for a slower system.  I have always used Intel processors in the past, but I have been looking at AMDs recently.  I was always taught to match bus speeds but see that most AMD processors have a higher FSB (MTs) than the boards that are built for them.

---

### Post by Stochastic on 2008-10-20
What level of audio recording are you talking about?  2-channel? 389-channel? How long are you recording at once?

Your processor specs seem to be far above my single core laptop, and I can record a number of channels at once.  The limit you'll probably bump into first is hard-drive write speed.  I don't know if those new solid-state harddrives are any faster (they should be) but the faster the better on those.

---

### Post by Sam the Wizer on 2008-10-20
I have a Presonus Firepod, and will be using 9 channels when recording drums (8 mics +1 scratch track).  I have noticed that when I run Ardour with my current system (2.4GHz single core processor with 512Mb Ram, 7200RPM IDE hard disk) I get serious latency when running projects with more than a few tracks.  I'm sure that this issue is due to my RAM, but I don't think it's worthwhile to spend the money to upgrade RAM with my current Mobo/CPU.  Eventually I will probably add another Firepod, so I would like to have power to record up to 16 channels simultaneously if I can build such a system within my price range (around $300US).  I also plan on upgrading to SATA drive interfaces with these upgrades, so I'm not too concerned about bus/write speed for the hard drive.

I think in a single project the longest recording will probably be around 7 minutes.  In the future I might try to record whole shows, but that will likely be fewer tracks for an hour or so.

Thanks,
Sam

---

