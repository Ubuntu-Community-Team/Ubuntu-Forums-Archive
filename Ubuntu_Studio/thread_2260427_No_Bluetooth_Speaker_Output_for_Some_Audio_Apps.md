---
title: "No Bluetooth Speaker Output for Some Audio Apps"
date: 2015-01-11
forum: Ubuntu Studio
---

### Post by marseille2 on 2015-01-11
I'm able to get beautiful sound output from my bluetooth speaker for LMMS and MIXXX (when they use alsa), but I don't know if it's possible to get/route bluetooth output for applications that use Jackd -- like Ardour, Rosegarden, or Muse -- with the same results. 

I found two posts related to this online, but not much else. The sentiment is pretty much against it due to the lag, but for my purposes ... it's not that kind of *pro-audio* serious, but I have my wired speakers hooked up to dedicated video for another system... so it does matter. 

In any case, I finally figured out how it can done, but the results weren't that great. I got sound via PA's loopback module by issuing the following command:

$ pactl load-module module-loopback 

I tested it with IDJC and Hydrogen, but since the command sends all sounds -- including the mic -- to bluetooth spkr output... it's was distorted, and the levels of the two apps differed. So now I want to know how to stop the pulse from rerouting the mic.

Any advice?

Sources:

[http://linuxmusicians.com/viewtopic.php?f=27&t=13287](http://linuxmusicians.com/viewtopic.php?f=27&t=13287)

[http://jack-audio.10948.n7.nabble.com/jack-and-bluetooth-td12151.html](http://jack-audio.10948.n7.nabble.com/jack-and-bluetooth-td12151.html)

---

