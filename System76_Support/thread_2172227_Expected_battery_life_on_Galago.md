---
title: "Expected battery life on Galago?"
date: 2013-09-03
forum: System76 Support
---

### Post by Michael_Corey on 2013-09-03
Hello:

I just received my new Galago, and I was surprised to find that I only get about 2 hours and some change in battery life from a full charge. Is this expected? I have an SSD for the OS and a bulk eSATA drive as well, if that makes a difference.

Thanks, all.

---

### Post by isantop on 2013-09-04
Does the eSATA drive have it's own power supply? If it doesn't, that could easily suck a lot of power.

How are you using the system? It should get around 3-4 hours per charge with normal usage.

---

### Post by Michael_Corey on 2013-09-04
The secondary drive is internal, so no separate power supply (Perhaps eSATA isn't quite the right term). I don't think I usually do things that should drain a lot of power -- run Python scripts, use the Internet. Not a ton of video or anything like that.

I'm also having problems getting the machine to shut down all the way when I close it, so it's also possible that's draining the battery while I assume it is suspended.

---

### Post by isantop on 2013-09-04
It's normal for it to drain slowly while in suspend. When you say you can't get it to shut down all the way when you close it, do you mean it won't suspend? What's the status of the power LED on the front of the machine after you close the lid.

---

### Post by Michael_Corey on 2013-09-04
It cycles through the shutdown sequence, looks like it's about to power off, then restarts Ubuntu. The power light stays solid green, or sometimes flashes green.

At times it seems the battery drains while it should be in suspend much more quickly than I would expect -- essentially the same rate as when running. But it's inconsistent, I think because it may not be consistently suspending all the way. Not sure if that's related to the shutdown issue or not.

---

### Post by isantop on 2013-09-04
Try suspending it using the Suspend menu item, or by pressing Fn+F4. See if it goes down all the way, then check that it resumes. You can resume it by pressing Fn+F4 again or by briefly pressing the power button.

---

