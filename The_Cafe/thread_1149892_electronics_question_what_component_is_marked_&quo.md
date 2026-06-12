---
title: "electronics question: what component is marked &quot;L1&quot; on a pcb?"
date: 2009-05-05
forum: The Cafe
---

### Post by stairwayoflight on 2009-05-05
Hey all,

I have googled around for this one, but no love. If I have a board with an obviously broken surface mount component, with an adjacent label "L4" on the pcb, what is it? (I know eg. "R1" is a resistor, etc.)

Also, I read a document about "pull-up resistors." Is the pull-up resistor the whole circuit?

eg.
```

vcc
  |
  \
  / R = 47k
  \
  /
  |
  |
 /      |\
/ .-----| }o----
  |     |/
  |
gnd

```
Or is it a special kind of resistor? Or is it just a normal resistor, but in the context of such a circuit? Ie. if I bought one, I would just buy a normal 47k resistor, right?

Thanks,
Timothy

---

### Post by mips on 2009-05-05
L usually designates an Inductor, [http://en.wikipedia.org/wiki/Inductor](http://en.wikipedia.org/wiki/Inductor)

Has it got a value written on it?

---

### Post by thisllub on 2009-05-05
I agree on the inductor.

Good luck.

---

### Post by RandomJoe on 2009-05-05
As the others said, the L4 should (normally) be an inductor.

And a pull-up resistor is just an ordinary resistor - it's the application that makes it a "pull-up".  Without it, the logic input or whatever-it-is could float at whatever random voltage between logic-low and logic-high when not grounded.  It's possible it wouldn't float high enough to be seen as a "high".  The resistor makes sure it goes high by "pulling up" the voltage on the pin when not grounded.

---

