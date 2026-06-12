---
title: "alesis io|26 with Jack?"
date: 2008-05-07
forum: Ubuntu Studio
---

### Post by mpgarate on 2008-05-07
I have an alesis io|26 that I can use with windows

[http://www.alesis.com/io26](http://www.alesis.com/io26)

but would MUCH rather use with ardour in ubuntustudio. any known way to achieve this?

---

### Post by Stochastic on 2008-05-07
Unfortunately the firewire audio drivers for Linux (freebob, which is now ffado) do not support Alesis devices (see [http://www.ffado.org/?q=devicesupport/list](http://www.ffado.org/?q=devicesupport/list)).  This is probably because they have refused to provide the developers any info for writing the drivers.  I'd suggest attempting two possible routes to get it working on Ubuntu.

1) Phone Alesis and ask them for a driver. (this will help more in the long run, as Alesis will begin to realize the growing linux audio field shouldn't be ignored, but is not likely to produce any immediate results)
2) Try ASIO through Wine.

The third option would be to return the device and buy from a company that supports the linux audio developers.  I like this option the best as it directly punishes Alesis for their bad behavior.

If you're able to make any progress, post back for others to see.

---

### Post by mpgarate on 2008-05-07
ok. could you recommend another piece of hardware? All I need is at least a handful of inputs into ardour. preferably cheap

---

### Post by Stochastic on 2008-05-07
Well I really like my Firepod but that cost me $450, so that may be considered cheap to some (particularly for an 8-in 8-out card).  Your best bet would be to take a read through the list of supported devices at [http://freebob.sourceforge.net](http://freebob.sourceforge.net) and [http://www.ffado.org](http://www.ffado.org) and see which ones would work for your needs and budget.  Firewire is one of the better technologies for professional sound, and that driver is the main (maybe even the only) one for linux.

---

