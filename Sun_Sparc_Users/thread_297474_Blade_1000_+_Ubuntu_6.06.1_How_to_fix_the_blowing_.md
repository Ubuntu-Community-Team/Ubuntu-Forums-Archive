---
title: "Blade 1000 + Ubuntu 6.06.1: How to fix the blowing fans (bbc driver)"
date: 2006-11-11
forum: Sun Sparc Users
---

### Post by ubumatic on 2006-11-11
Hello,

With Ubuntu 6.06.1 SPARC on Sun Blade 1000 the fans will blow at full speed.
Loading the bbc module will reduce the fan speed temporarily, but you get high
CPU load and the fans still end up spinning fast. With Edgy Eft you will get
the Qlogic disk driver problem. Quite a puzzle, eh?

Well, I just got fed up with the fan noise and decided to make this fschking
bbc_i2c to work with Ubuntu 6.06.1. Here are the results:

**Removing the CPU load:**
See <kernel>/drivers/sbus/char/bbc_i2c.c, in function wait_for_pin (line 181)
there is a call to function msleep_interruptible(250). The purpose of this
function, as far as I can tell, is to wait for some memory mapped control
register to be ready. The msleep_interruptible is responsible for the CPU load
(blocks the kernel thread or something?). Waiting for 250ms cumulates quickly
as wait_for_pin is called many times in a row.

In addition, 250ms is simply excessive wait time for some register value. I
removed the msleep_interruptible completely and modified the while loop to poll
the register value without any wait. It seems to take 100-200 while cycles for
the value to be ready (definitely faster than 250ms).

The result is that there is no visible CPU load related to bbc_i2c. In
addition, when the bbc module is installed/removed there is no waiting.

**Getting slower spinning fans:**
I got rid of CPU load, but the fans kept slowly accelerating. After a bit of
tracing I ended up modifying the CPU temperature values.

My box is a 750MHz duallie, in normal use the temperature of cpu0 is in range
[69,71] and cpu1 in range [65,69] (degrees C).  See
<kernel>/drivers/sbus/char/bbc_envctrl.c, the function analyze_cpu_temp
determines which action to take (accelerate/same/decelerate). There are
variables cpu_goal_hi and cpu_goal_lo, these will define a goal range of
[67,70] with default values. To get the fans slowing down the average
temperature must be equal or lower to 67.  

Obviously, because my cpu0 likes to operate in the range [69,71], the fans have
to blow really hard to hit 67 and it will slip out of the goal range all the
time. I changed the values so that the goal range is [69,72]. Now the fans seem
to settle. I would quess that this optimal range is for this particular machine
only.
[B]
The good:[/B]
- bbc_i2c doesn't increase CPU load.
- Fans are not blowing at full speed.
- Normal use cpu temperature about 70 for cpu0 and 66 for cpu1.

**The bad:**
- It is still a noisy box.
- Judging from the newer Linux sources, Edgy Eft probably won't fix this
  problem.

Cheers,

Ubumatic

---

### Post by lister on 2006-11-19
Look on the bright side - it's better than having fans that suck.... :)

---

### Post by Basurero on 2007-07-24
Hi,
I'm having the same problem with a Blade 2000 and Ubuntu 7.04 (Feisty Fawn). The fans are continuously working and that makes it impossible to use the workstation for daily work.
Has there been any update on this issue?

Thanks

---

