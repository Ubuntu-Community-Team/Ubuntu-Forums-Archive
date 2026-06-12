---
title: "Which is dead, CPU or motherboard?"
date: 2009-01-19
forum: The Cafe
---

### Post by jinx099 on 2009-01-19
I thought I'd try posting here to see if anyone had any ideas on how to diagnose my server which has recently died on me.

Background:  I built this machine about a year ago using 2GB (2x1 GB) of new RAM and 2GB (2x1GB) of older RAM that i used previously in my desktop.  Everything has been running just fine since then.  A week or 2 ago the server started rebooting randomly quite frequently (many times it would not even finish booting).  I ran memtest86+ and it immediately started throwing errors.  I tested every stick of RAM individually and found 1 stick was the problem.  It was the older stuff, so I didn't think too much of it and just carried on with the remaining 3GB.  I ran memtest86+ overnight on the remaining RAM to verify it was good, and it passed.

Today:  My server stopped booting, but it does not reboot like before.  It starts booting and then it just hangs.  (It runs Solaris, so I don't expect help diagnosing the booting specifically)  I ran memtest86+ again on it and it throws tons or errors right away.  Like before, I tested every stick of RAM individually, and this time they all throw tons of errors.  I tossed that RAM into my desktop and tested it for a while, and it did not throw any errors; it seems to be just fine.  So I'm thinking the problem has to be either with the CPU or the Motherboard.  I would love to be able to test the CPU, but I can't find anyone with an AM2 system to test it out in.

So my question, what could I try to do to determine if the motherboard, or the CPU has died?

---

### Post by jrusso2 on 2009-01-19
I would suspect software first since it starts booting.  Of course you did mention some bad memory. Another bad stick is possible.  Bad memory can often cause freezes.

Usually when the Motherboard or CPU is dead it won't even start to boot.

---

### Post by Redache on 2009-01-19
It could be the power supply thst's causing problems.

---

### Post by jinx099 on 2009-01-19
> **Redache said:**
> It could be the power supply thst's causing problems.

That's a good idea, I will try to test that out.

---

### Post by jinx099 on 2009-01-19
> **jrusso2 said:**
> I would suspect software first since it starts booting.  Of course you did mention some bad memory. Another bad stick is possible.  Bad memory can often cause freezes.

Usually when the Motherboard or CPU is dead it won't even start to boot.

Maybe you missed the part where I said that I tested the memory in my other computer.

I've seen motherboard with blown capacitors that will boot but will lock up.  I did not see any obviously bad caps on my motherboard though.  I've never experienced a CPU failure, so I dont know how that would behave.

---

### Post by jrusso2 on 2009-01-19
> **jinx099 said:**
> Maybe you missed the part where I said that I tested the memory in my other computer.

I've seen motherboard with blown capacitors that will boot but will lock up.  I did not see any obviously bad caps on my motherboard though.  I've never experienced a CPU failure, so I dont know how that would behave.

If the caps are blown out a bit that would be an indication.

---

### Post by jinx099 on 2009-01-19
> **jrusso2 said:**
> If the caps are blown out a bit that would be an indication.
Yeah I know, they all look fine.

---

### Post by MaxIBoy on 2009-01-19
[LIST=1]
[*]Try booting another OS.
[*]Check your BIOS settings.
[*]If you can, see if anything funny is happening to the computer's power draw.
[*]Run it with an open case. Sniff carefully. Can you smell ozone?
[/LIST]

---

### Post by Bright_View on 2009-01-19
I'm not a professional repair guy by any stretch, but I've been fixing computers for friends and family for a while now and from what I've read and seen first hand, the CPU is rarely the problem.  The two most common pieces of equipment that I've seen fail are the power supply and the motherboard.  I would suspect it's one of those in your case, if in fact it is a hardware problem.

That being said, does it hang at a specific point when it's booting?  Or does it just hang at random?

With regards to figuring out what has failed, the best way is to "swap 'til you drop".  If there are any used computer places around you, they may be willing to test out the motherboard (and CPU for that matter) on good equipment to isolate the problem.  I've done that before when I didn't have a spare system kicking around (which is always).

---

### Post by eragon100 on 2009-01-20
> **MaxIBoy said:**
> [LIST=1]
[*]Try booting another OS.
[*]Check your BIOS settings.
[*]If you can, see if anything funny is happening to the computer's power draw.
[*]Run it with an open case. Sniff carefully. Can you smell ozone?
[/LIST]

1,2 and 3 are fine. I wouldn't try to smell ozon tough, I believe it's quite toxic :wink

---

### Post by mips on 2009-01-20
Could I suggest you try running Micro-Scope Diagnostic Suite. I have battled my butt off before trying to find problems and this software is really great, for example it will find memory errors memtest simply does not pick up.

---

