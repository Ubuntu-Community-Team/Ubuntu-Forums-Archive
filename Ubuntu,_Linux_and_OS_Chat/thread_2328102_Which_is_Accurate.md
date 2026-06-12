---
title: "Which is Accurate?"
date: 2016-06-17
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2016-06-17
Ubuntu Mate 16.04 is high on memory usage. 

I use the Mate System Monitor and Htop to track my resource usage. 

I notice that Mate System Monitor displays a higher amount of memory being used than the amount of memory that Htop displays being used.

The difference between the two monitors can be 150MB to 250MB.

My question is which monitor is displaying the true memory usage.


Thanks

---

### Post by ajgreeny on 2016-06-17
Compare the results you get in GUI with command ```
free -m
``` which will always be correct.

---

### Post by poorguy on 2016-06-17
> **ajgreeny said:**
> Compare the results you get in GUI with command ```
free -m
``` which will always be correct.

That being the case the Mate System Monitor is inaccurate.

By running the code (free -m) proved the same results as Htop is displaying.

I found this.

[http://askubuntu.com/questions/787642/system-monitor-doesnt-accurately-show-memory-usage/787657](http://askubuntu.com/questions/787642/system-monitor-doesnt-accurately-show-memory-usage/787657)


Thanks

---

### Post by vasa1 on 2016-06-17
I used to monitor RAM "usage" at one time via conky. But I stopped. If everything is running smoothly, I see no point. I do however keep a look out for %CPU usage and my laptop's temperature just in case ...

---

### Post by poorguy on 2016-06-17
I do it out of curiosity and the software is included so might as well use it. 

I agree if all is running and not locking up or rebooting I don't usually worry about it.

I use XSensors to monitor fans speeds / processor temps / motherboard temps and voltages etc.

Just kept noticing all of the memory usage and started checking into it and now that I know which monitors are accurate I don't see that Ubuntu Mate 16.04 uses that much more memory than Ubuntu Mate 14.04 uses.

My old 2007 desktop runs great and no problems with 16.04 other than me learning all of the new that comes with it.

---

