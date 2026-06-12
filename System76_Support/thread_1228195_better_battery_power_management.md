---
title: "better battery power management"
date: 2009-07-31
forum: System76 Support
---

### Post by poikiloid on 2009-07-31
I have noticed that the battery is recharging even when it is almost full. This wastes the limited charge-discharge cycles that Li-ion batteries have. I see that someone is working on solutions for ubuntu ([http://brainstorm.ubuntu.com/idea/6839](http://brainstorm.ubuntu.com/idea/6839)) which is a more-specifically worded duplicate of this one, listed as 'in development': [http://brainstorm.ubuntu.com/idea/81/](http://brainstorm.ubuntu.com/idea/81/)

any possibility of a solution for system76 lappies in the meantime? at least is there a way in the bios or something to tell it not to start recharging until below a certain % charge?

when ubuntu gets around to it, they should include lots of control, that are easily toggled:
i mostly use AC power, so want it to stay at 40% battery charge most of the time. want to easily tell it i'll be needing full battery charge in a while, so go ahead and charge up to 100%. want to tell it never to start a charge cycle, even if in full-battery mode, unless it drops below a charge % (95?) i can specify.  ubuntu really needs to get good with maximizing battery life to reduce electronics waste...

---

### Post by thomasaaron on 2009-07-31
There are no configurations like that.

Those would be good suggestions, though, to suggest to the Ubuntu developers. I don't think I've even seen anything quite like that on Windows either.

---

### Post by jdb on 2009-07-31
> **poikiloid said:**
> I have noticed that the battery is recharging even when it is almost full. This wastes the limited charge-discharge cycles that Li-ion batteries have. I see that someone is working on solutions for ubuntu ([http://brainstorm.ubuntu.com/idea/6839](http://brainstorm.ubuntu.com/idea/6839)) which is a more-specifically worded duplicate of this one, listed as 'in development': [http://brainstorm.ubuntu.com/idea/81/](http://brainstorm.ubuntu.com/idea/81/)

any possibility of a solution for system76 lappies in the meantime? at least is there a way in the bios or something to tell it not to start recharging until below a certain % charge?

when ubuntu gets around to it, they should include lots of control, that are easily toggled:
i mostly use AC power, so want it to stay at 40% battery charge most of the time. want to easily tell it i'll be needing full battery charge in a while, so go ahead and charge up to 100%. want to tell it never to start a charge cycle, even if in full-battery mode, unless it drops below a charge % (95?) i can specify.  ubuntu really needs to get good with maximizing battery life to reduce electronics waste...

The charging isn't controlled by the operating system or even bios, it is contolled by a chip built into the battery case.
Li-on batteries aren't degraded much if any by topping the charge off, what affects them most is how often they have been deeply discharged.

jdb

---

