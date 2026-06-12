---
title: "linux-lowlatency development details"
date: 2016-04-24
forum: Ubuntu Studio
---

### Post by CrocoDuck on 2016-04-24
Hi there cool people!

Hopefully some dev is reading. I would like to learn more about what makes a good lowlatency kernel. What I did so far was to compare linux-lowlatency config file with the config file of the standard kernel of Ubuntu and other distros. It is kinda hard to figure out which are the fields that relate specifically to audio optimization though. Also, it lefts me wondering whether you have applied any particular patch.

As such, I would like to ask if there is a source where I can find details about the kernel development.

---

### Post by QDR06VV9 on 2016-04-25
I doubt if the Devs have the time to visit these forums.
here is a couple of links that I refer to.
[https://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/](https://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/)

[http://www.versalogic.com/mediacenter/whitepapers/wp_linux_rt.asp](http://www.versalogic.com/mediacenter/whitepapers/wp_linux_rt.asp)

---

### Post by CrocoDuck on 2016-04-25
Cool, thank you very much.

I bumped into the first one, but the second is new to me. I will maybe try to reach some dev through the IRQ channel. Hopefully I will not annoy them too much :D.

---

### Post by yoshii on 2016-04-25
Really cool questions, CrocoDuck.  
If you find good answers, please post them here.  
People like me will be reading.  I will add anything I find too.

---

### Post by CrocoDuck on 2016-04-27
A guy just built a [lowlatency kernel for OpenSuse]("https://linuxmusicians.com/viewtopic.php?f=4&t=15655"). He supplied also some good info. I will try this myself in the next week and I think I will document the procedure somewhere (if successful).

---

### Post by yoshii on 2016-04-28
> **CrocoDuck said:**
> A guy just built a [lowlatency kernel for OpenSuse]("https://linuxmusicians.com/viewtopic.php?f=4&t=15655"). He supplied also some good info. I will try this myself in the next week and I think I will document the procedure somewhere (if successful).

That's really cool.  

I haven't done much stuff.  I'm too afraid to try compiling.  
But I did install the Ubuntu low-latency kernel to a laptop which runs Xubuntu and it does show up in the grub boot menu and it boots.  

The only thing disappointing is that the low-latency kernel seems to be an older kernel than the Xubuntu kernel.  
I think it's like 3.13 or something instead of 3.19 or 4.x

---

