---
title: "Kernel 3.10.10, RT patch 3.10.10, and Nvidia 319.49  How do I do this?"
date: 2013-09-08
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2013-09-08
I"m using Ubuntu 12.04.

Back in April, I compiled a custom 3.4.47 kernel with the associated RT patch and was successful in getting Nvidia to work simply by running the "experimental-310" binary from Nvidia.  I was playing Windows games, Recording Audio, with ZERO problems, with latencies of 0.7ms@88.2KHz audio, until an update from the other day.  The update, updated the Nvidia with 319-updates 304-updates...it basically thought I needed every Nvidia package installed at once.  After I removed them all, I couldn't get the original binary to work, nor could I get the nouveau to work either, so I decided to try a new kernel and a new Nvidia binary to see what happens.

So far it's been an utter failure.  After grub, I get a black screen and nothing else.  I have to restart a few times for the login window to actually appear after a few moments of the black screen. Even then, the resolution is very low.  I'm typing from the fluxbox evironment right now, because it's the only one that will work without restarting X.

What I'd really like to do, despite any legalities or bias, is include Nvidia as a module during compiling the kernel.  There are NO "complete" tutorials on how to do this, from my research.  Just vague fragments of info.  Which are usually very out of date.

If this is just a case of Kernel version and Nvidia version incompatibility, can anyone suggest a kernel newer than 3.4.X that will work with the corrisponding RT kernel patch and some version of the Nvidia driver?

And for the love of God please don't change the subject or try to get me to try something other than Nvidia and the RT kernel.  There are enough threads on the internet that change the subject so that it is of no use to anyone else looking for this information in the future.  Which is why I made this thread.  Also, the Low Latency kernel is not sufficient for my needs.  It has to be hard realtime.

Thanks.



Edit:  It seems as though I found a working driver.  Nvidia 304.88 seems to work with Kernel 3.10.10 with RT patch.  Hoowever, I still want to know how to include Nvidia in the kernel compilation.

---

