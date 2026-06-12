---
title: "Dell PowerEdge SC1435 disks not recognized"
date: 2007-02-21
forum: Server Platforms
---

### Post by nuzzy on 2007-02-21
I'm trying to build a mail server at work for testing using a Dell PowerEdge SC1435 server but it doesn't recognize the disks due to lack of drivers.  Has anyone been able to find a workaround for this?

---

### Post by chrisfay on 2007-02-22
Have you tried recompiling the kernel with the drivers you need? I had an issue with the scsi card on my compaq server not being recognized and a newer kernel fixed it.

---

### Post by nuzzy on 2007-02-22
Hi chrisfay,

That thought crossed my mind, but I assumed I needed to create an update bootCD which I don't know how to do.  Do you know if that's true?

---

### Post by chrisfay on 2007-02-22
For recompiling the kernel? No...

If you're unfamiliar with hit, there's a good howtoforge doc located:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Which scsi drivers are you missing?

---

### Post by nuzzy on 2007-02-24
I'm missing the SAS drivers, which I "think" may be megaraid2 or something similar

Thanks for the HOWTO, but I can't even get the hard drive recognized to begin with which is why I think I need a bootCD with an updated kernel.

---

### Post by alex.lake on 2007-03-05
Did you get anywhere with this, nuzzy? We're facing the same problem. Wondering about ditching the 1435 and going back to 1425.
Alex

---

### Post by nuzzy on 2007-03-05
I did, actually, but it may not be what you want.  I actually found a Debian Sarge updated kernel release here:

[http://kmuto.jp/debian/d-i/](http://kmuto.jp/debian/d-i/)

I used that and it worked fine.  What version of Ubuntu did you try?  6.10 "may" work.  If you decide to go with Debian you'll notice it looks like it's stuck at 33% when formatting partitions.  It's not stuck - it just takes a while to format them.  I wasn't patient enough :-)

---

