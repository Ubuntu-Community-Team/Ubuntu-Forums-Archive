---
title: "Current status of M-Audio's MobilePre"
date: 2013-06-14
forum: Ubuntu Studio
---

### Post by slippycurb on 2013-06-14
Hey People, Im just wondering what the current state of the MobilePre's modules are at, and what settings you are all recommending for jack, It seems to be working out of the box.
I read somewhere that the snd_ice1724 module also works...is that any faster(as in lower latency)?(as i record guitar and use amp/cab plugins..e.g guitarix)
currently my jack setup seems stable, although i would like to reduce from 256 to 128 frames for recording, but if i do this i get a barrage of dropouts,,,periods/buffer is set to 3...I only use 16bit recording too (i dont need 24bit fidelity) and the sample rate is 44100.....does anybody have anymore suggestions i should be thinking about?
This is the old mobilepre by the way.......
thanks for any interest anybody has....:-)

---

### Post by breakall on 2013-07-13
I hope it's ok to bump this! I just got a MobilePre and would like any advice anyone has about using it!

Cheers!

---

### Post by tgalati4 on 2013-07-13
As far as latency:

256 frames would be 256/44100 Hz which is 5.9 milliseconds.
128 frames would be 128/44100 Hz which is 2.9 milliseconds.

The speed of sound at 75F is 1133 feet/second.  So:

256 frames:  6.7 feet of delay
128 frames:  3.3 feet of delay

So, if you are jamming together in an acoustic session, then you are probably 3 to 6 feet away from the other performers.  If you are farther away, you may lose sync or you may hear reflections from walls and play to that which will throw off your timing.

From a digital recording, your personal monitoring of your guitar playing will be (effectively) 3 or 6 feet away.  3 feet is desireable, but 6 feet is workable.  It would be hard to play a guitar if it was farther away.

So if you can play your guitar at 256 frames of delay and not have a headache after an hour of playing, then it shouldn't make a difference.  If you have a headache--because your brain is constantly confused by what it is feeling and what it is hearing, then you should find ways to reduce the delay.  It's similar to watching a 3D movie.  Your brain has to jump through hoops to figure out what is going on, and that will give you a headache.

There's a youtube video of a "Stop Talking" device from Japan that takes the voice and delays it 200 to 300 ms.  That interferes with your brain's speech processing, so you stop talking.  You can think of some useful applications.

If you want to play around:

```

sudo apt-get install sox
play "|rec -d pitch -200"
play "|rec -d delay .25"
```

Use headphones to isolate the microphone from the speakers.  Control-C to quit.

---

