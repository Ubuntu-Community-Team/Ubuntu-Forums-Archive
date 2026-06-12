---
title: "Sound api"
date: 2013-08-08
forum: Ubuntu Application Development
---

### Post by Bram Stolk on 2013-08-08
Hello fellow app developers,

I'm in the process of porting my game to Ubuntu.
The game currently runs on iOS, OSX, Android, RaspberryPi and OUYA.

Using GLFW3 I've been able to make a lot of progress.
The last remaining part is the sound.

I would love to use OPENSL ES on Ubuntu (like I do on Android) but it appears there is no OPENSL ES for Ubuntu, nor is there an OPEN SL.

I require an API that lets me generate sound samples on the fly, by getting buffer requests as they are required.
This is how OpenSL ES works, and this is how iOS's AudioQueue works.
I also require low latency sound, meaning no more buffering than 0.1sec or so.

What would be the recommended sound API to use for a game in Ubuntu?

Thanks,

  Bram Stolk
  [http://stolk.org/](http://stolk.org/)

---

### Post by Bram Stolk on 2013-08-09
I decided to go with PortAudio.
It supports buffer filling via callbacks, and has a simple yet powerful API.
I also tried PulseAudio, but its asynchronous API is frighteningly complex.
[http://portaudio.com/docs/v19-doxydocs/tutorial_start.html](http://portaudio.com/docs/v19-doxydocs/tutorial_start.html)

---

