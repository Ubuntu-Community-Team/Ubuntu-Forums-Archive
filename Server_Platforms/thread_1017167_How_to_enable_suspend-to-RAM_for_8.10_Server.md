---
title: "How to enable suspend-to-RAM for 8.10 Server?"
date: 2008-12-20
forum: Server Platforms
---

### Post by daniel_v on 2008-12-20
Hi all,

I have an 8.10 Server install. Which packages do I need to enable power management? How can I trigger suspend-to-RAM?

I found some older posts with similar questions, but no answers that would seem to work...


Some more info:

Why: I have a little home server, that will probably idle >90% of the time. The idea is to suspend-to-RAM when idle to drop power consumption from 30-something Watts into the single digit Watt range, and then wake it up again using wake-on-LAN.

The problem, as far as I can tell: I take it suspend/hibernate is extremely undesirable for a 'real' server, so naturally the Ubuntu server edition doesn't come with any power management support. I'd hope I only need to find whichever packages do the magic for the desktop edition, and then apt-get them into my installation.

Hardware: Mainboard is an Intel D945GCLF2. It's supposed to have reasonable power management support.


Thanks!

Daniel

---

### Post by Vegan on 2008-12-20
No need, there is good power management that can slow the CPU significantly to save energy.

---

### Post by daniel_v on 2008-12-21
Hi Vegan,

Thanks for the quick reply!

> **Vegan said:**
> No need, there is good power management that can slow the CPU significantly to save energy.

Well... judging from what I've read, idle power for my system should be ca. 24W and S3 power is more like 1W. That looks like significant additional savings to me, so I still want to try...


Looks like the following does what I want:

$ apt-get install pm-utils
$ pm-suspend

That was easy... :-)


Daniel

---

### Post by windependence on 2008-12-21
This board is already energy efficient to the Nth degree. I really don't see the point. These mini-ITX boards draw next to nothing in power, they're fantastic. The CPU alone only draws 4 watts loaded.

-Tim

---

