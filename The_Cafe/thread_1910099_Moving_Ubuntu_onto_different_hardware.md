---
title: "Moving Ubuntu onto different hardware?"
date: 2012-01-16
forum: The Cafe
---

### Post by mr-woof on 2012-01-16
Everning all,

what do you think would happen if I moved my 11.10 Ubuntu installation onto a new Cpu/Mobo without reinstalling?

I have a feeling it will probably be fine, but I thought I'd best ask the question before I go ahead with this :)

---

### Post by CharlesA on 2012-01-16
It would probably be fine.

Might have to mess with network settings, but other than that, it should be fine.

---

### Post by mr-woof on 2012-01-16
Thanks Charles, I was hoping someone will say that. Windows will be a different story, but I've got a plan for that.

I plan to do this when I next get a chance, so I'll post my results.

---

### Post by BrokenKingpin on 2012-01-16
I have swapped out a mobo and CPU on a Debian install and it booted back up like nothing changed... it was great. Doing something like this under Windows would most likely end up in a BSOD.

---

### Post by FuturePilot on 2012-01-16
It should be fine. I've moved installs between different hardware and it worked fine. The only thing I had to do was delete /etc/udev/rules.d/70-persistant-net.rules and then reboot because the networking didn't work. It automatically gets recreated on boot with the correct information.

---

### Post by CharlesA on 2012-01-16
> **FuturePilot said:**
> It should be fine. I've moved installs between different hardware and it worked fine. The only thing I had to do was delete /etc/udev/rules.d/70-persistant-net.rules and then reboot because the networking didn't work. It automatically gets recreated on boot with the correct information.

That would be the one I was thinking of but couldn't remember the name of. Thanks. :)

---

### Post by 741Baus on 2012-01-16
It should work , I recently had an m/b failure bad memory slot computer wouldn't boot to post , a new m/b + ram and original cpu ,booted in to 10.04 system automatically ran disk check .
With in minutes I was up and running no problems.

---

