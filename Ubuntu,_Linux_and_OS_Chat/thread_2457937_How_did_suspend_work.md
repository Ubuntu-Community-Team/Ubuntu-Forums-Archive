---
title: "How did suspend work?"
date: 2021-02-12
forum: Ubuntu, Linux and OS Chat
---

### Post by The Cog on 2021-02-12
Not a support question, just puzzled:

I have known for a long time that suspend uses swap space for saving RAM. So swap has to be bigger than RAM for suspend to work.

I have 8G RAM and 2G swap. A couple of days ago, I fat-fingered a shutdown and clicked suspend instead. It suspended, and when I woke it up, it worked perfectly, restoring all the open windows.

Does anyone have any idea how that might have worked? Because I don't.

P.S. Xubuntu 20.04.2, in case it's significant.

---

### Post by DuckHook on 2021-02-12
Doesn't suspend save only to RAM? Hibernate saves to swap, but my understanding is that suspend does not.

---

### Post by The Cog on 2021-02-12
Doh! 
Yes, I was thinking of Hibernate. Which isn't even listed as an option.
Thanks for putting me straight.

---

### Post by DuckHook on 2021-02-12
No prob!

I wouldn't want you to quote me on this because of my failing memory, but years ago, I vaguely recall that I did successfully hibernate a session with insufficient swap. It's very fuzzy by now, but various incomplete inquiries at the time led to the understanding that hibernation does not write the whole memory map to swap but only contentful portions, or something like that. This also seemed to be the reason that the hibernate option was nuked from default installs: some people would be fooled by successful hibernation on insufficient swap, which would work until it wouldn't, with resulting corruption and lost work.

I would not swear to this set of events even having happened, or whether I just read about it somewhere. The ol' noggin ain't what it used to be.

---

### Post by TheFu on 2021-02-12
[https://help.ubuntu.com/stable/ubuntu-help/power-suspend.html.en](https://help.ubuntu.com/stable/ubuntu-help/power-suspend.html.en) Not very technical, sadly.

Peripherals are disconnected, buses are powered off, CPU is stopped and RAM is put into low-power mode.
Reverse those steps when coming out of suspend mode and hope it works.  I've been lucky, on my laptops since around 2012, it has. Even with LUKS encryption.  Probably want to ensure that a screen lock is working correctly, however.

I've never suspended any of my desktops or servers, so I don't know if or how well those work.

---

### Post by CatKiller on 2021-02-13
> **The Cog said:**
> I have known for a long time that suspend uses swap space for saving RAM. So swap has to be bigger than RAM for suspend to work.

FWIW, this isn't quite correct. For *hibernate* to work, there needs to be enough space to store *what's currently in RAM* so that it can be reloaded at a later time when the computer is turned on again. File cache isn't stored, and it's possible to compress the RAM contents in the process. It's also not necessarily faster to resume from hibernation than to reboot normally. 

*Suspend* doesn't do any copying; it leaves the RAM contents in RAM and just keeps that powered when it turns everything else off. This is pretty quick. 

There are also schemes that will do the copy *and* leave the RAM powered for a while, so that if you turn it back on fairly soon afterwards you get the speed of resuming from suspend, but if you leave it off for longer you get the power saving of hibernating.

Putting things into an already-running state requires more hardware-specific magical invocations than just booting normally, so it's sometimes an iffy procedure without manufacturer support.

---

