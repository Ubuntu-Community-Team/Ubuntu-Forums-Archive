---
title: "i386 with 256k ram..."
date: 2007-04-03
forum: The Cafe
---

### Post by mardawi on 2007-04-03
Hi,

I found this really old machine in my basement, it's a 386 with 256Kb ram, not sure about the processor though..

I was wondering, is there a Linux distro that i can install on this very old machine so i can turn it to a wired mp3 player :) ?

---

### Post by insane_alien on 2007-04-03
DSL should run. alternatively, you could just use the kernel and a couple of modules.

---

### Post by Delkster on 2007-04-03
> **mardawi said:**
> I found this really old machine in my basement, it's a 386 with 256Kb ram, not sure about the processor though..

I was wondering, is there a Linux distro that i can install on this very old machine so i can turn it to a wired mp3 player :) ?

If it seriously has that little RAM, no. I'm not sure if it's very easy to get any recent distros, even Damn Small Linux, to run on anything less than a 486 either. If it really has that little RAM, I doubt it's a 386, though (and vice versa). I'd imagine that most 386 machines would have come with at least a meg of RAM.

Furthermore, I'm not sure a 386 has enough power for decoding mp3 in real-time.

So, with that hardware information, I'd say the chances of success are less than great. It might, of course, be an interesting adventure if you feel like going for one. I'd verify the hardware specs before trying, though. Like I said, the combination of a 386 and only 256k of RAM doesn't sound normal, and Linux has never run on anything less than a 386. (ELKS runs on 16-bit systems but it's also an adventure)

---

### Post by heimo on 2007-04-03
That's... admirable. Closest thing I could find that could be installed on it is freedos and still their FAQ says that "you can get by with 640k base memory". Even if you could get something installed on it... ;) (what did it run when it was new?) ... I seriously doubt you could get it to run mp3's. I think I had problems playing mp3s with my 486DX/33 with 4MB - but yes, it did run Linux.

I don't think DSL is light enough.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Zuph on 2007-04-03
It's going to be impossible to decode MP3s with anything less substantial than a 486 with a 66mhz processor, and even then you'll have skips and other problems.

---

### Post by heimo on 2007-04-03
> **Zuph said:**
> It's going to be impossible to decode MP3s with anything less substantial than a 486 with a 66mhz processor, and even then you'll have skips and other problems.
This is my memory too. I think it was only the fastest 486s, like 486DX4/100MHz, which were able to play mp3s without skipping.


Here's a small operating system which should run on x86 too... 
>  Contiki is designed for embedded systems with small amounts of memory. A typical Contiki configuration is 2 kilobytes of RAM and 40 kilobytes of ROM.
[http://www.sics.se/contiki/about-contiki.html](http://www.sics.se/contiki/about-contiki.html)
[http://en.wikipedia.org/wiki/Contiki](http://en.wikipedia.org/wiki/Contiki)

---

### Post by Mathiasdm on 2007-04-03
> **mardawi said:**
> Hi,

I found this really old machine in my basement, it's a 386 with 256Kb ram, not sure about the processor though..

I was wondering, is there a Linux distro that i can install on this very old machine so i can turn it to a wired mp3 player :) ?
µLinux might do the trick. [http://mulinux.nevalabs.org/](http://mulinux.nevalabs.org/)
It fits on a single floppy. Though it's possible the computer isn't strong enough to decode mp3's!

---

### Post by SishGupta on 2007-04-03
dont even try a gui...lol

---

### Post by ssam on 2007-04-03
[http://en.wikipedia.org/wiki/MCC_Interim_Linux](http://en.wikipedia.org/wiki/MCC_Interim_Linux)

---

