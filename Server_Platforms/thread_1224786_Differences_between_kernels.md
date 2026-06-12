---
title: "Differences between kernels"
date: 2009-07-27
forum: Server Platforms
---

### Post by pythonscript on 2009-07-27
What's the difference(s) between the default ubuntu desktop kernel, the linux-server kernel, and the linux-virtual kernel? The virtual kernel shows up as a server kernel in grub, so I'm wondering what the differences are between all of them. Thanks!

---

### Post by doogy2004 on 2009-07-27
> **pythonscript said:**
> What's the difference(s) between the default ubuntu desktop kernel, the linux-server kernel, and the linux-virtual kernel? The virtual kernel shows up as a server kernel in grub, so I'm wondering what the differences are between all of them. Thanks!

a quick Google search for ```
ubuntu kernel server generic difference
``` is a good start
[http://www.google.com/search?q=ubuntu+kernel+server+generic+difference](http://www.google.com/search?q=ubuntu+kernel+server+generic+difference)

the first result
[http://www.serverwatch.com/tutorials/article.php/3715071](http://www.serverwatch.com/tutorials/article.php/3715071)
will give you the answer you seek.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)
gives information about JeOS and the virtual kernel

---

### Post by brentoboy on 2009-07-27
when I looked, the only significant difference I could find was that they give a longer timeslice to processes before switching processes.

This has the effect of spending more time overall getting things done, and less time wasting cycles on the actual swapping of threads.

The "bad" side effect is that it means that a user might actually notice that their app wasn't getting "instant" feedback because it took a moment longer before it got the processor as part of the round-robin thread handling going on in the background.

I run the server kernel on my laptop, and it seems identical to me.

I've heard people say that it also has better raid support - but I'm not seeing it in the build scripts - they all have the same hardware support, there is one flag switch in the compile settings, and it has to do with thread switching, prioritization and favouritism at the kernel level.

---

### Post by doogy2004 on 2009-07-27
The links that I gave contain the specific examples of the differences between the kernels, however my rule of thumb is as follows

```
server  - optimised for background processes
desktop - optimised for foreground processes
virtual - server kernel optimised to run in a virtual machine
```

---

### Post by pythonscript on 2009-07-31
Thanks for the help everyone! I installed the server kernel, and it works great running 5 virtual machines in the background while I use my every day programs. I noticed a performance boost too. Thanks again.

---

