---
title: "Linux on a 8-bit processor!"
date: 2012-08-31
forum: The Cafe
---

### Post by mips on 2012-08-31
[http://dmitry.co/index.php?p=./04.Thoughts/07.%20Linux%20on%208bit](http://dmitry.co/index.php?p=./04.Thoughts/07.%20Linux%20on%208bit)

> **Intro**

It is common to see newbies asking in microcontroller forums if they can run Linux on their puny little 8-bit micro. The results are usually laughter. It is also common to see, in Linux forums, asked what the minimum specs for Linux are. The common answer is that it requires a 32-bit architecture and an MMU and at least a megabyte of ram to fit the kernel. This project aims to (and succeeds in) shatter(ing) these notions. 

<snip>

**How fast is it?**

uARM is certainly no speed demon. It takes about 2 hours to boot to bash prompt ("init=/bin/bash" kernel command line). Then 4 more hours to boot up the entire Ubuntu ("exec init" and then login). Starting X takes a lot longer. The effective emulated CPU speed is about 6.5KHz, which is on par with what you'd expect emulating a 32-bit CPU & MMU on a measly 8-bit micro. Curiously enough, once booted, the system is somewhat usable. You can type a command and get a reply within a minute. That is to say that you can, in fact, use it. I used it to day to format an SD card, for example. This is definitely not the fastest, but I think it may be the cheapest, slowest, simplest to hand assemble, lowest part count, and lowest-end Linux PC. The board is hand-soldered using wires, there is not even a requirement for a printed circuit board.


There's also a video on his page.

---

### Post by |{urse on 2012-09-06
Awesome! Just for the sake of awesome.

---

### Post by forrestcupp on 2012-09-06
That's pretty amazing. Anyone who can make an 8-bit processor emulate a 32-bit processor & MMU is a superhero. I'd like to see someone try this on a Commodore 64 with a RAM Expansion Unit.

---

### Post by Lightstar on 2012-09-06
That sounds brutal.

---

### Post by mips on 2012-09-06
> **forrestcupp said:**
> I'd like to see someone try this on a Commodore 64 with a RAM Expansion Unit.

Load"linux",8,1

---

