---
title: "Another statistics question. Still not homework."
date: 2010-08-19
forum: The Cafe
---

### Post by mkendall on 2010-08-19
Actually, confirmation of the correctness of my calculations.

I know that the Expectation (weighted mean average, expected value, first moment) of a fair X-sided die (dX) is E(dX) = (1+2+3+...+X)/X (which collapses to (1+X)/2) and that the Expectation is additive: E(2dX) = 2E(dX). Note that dX does not mean the infinitesimal.

Now, roll a die and subtract a fixed number with a minimum of 0. For example, roll a 6-sided die, subtract 3, any negative results become 0. So all we look at are when the die roll is greater than the number.

Abusing the notation, I find:
```
E(d6>1) = (0+1+2+3+4+5)/6 = 15/6
E(d6>2) = (0+0+1+2+3+4)/6 = 10/6
E(d6>3) = (0+0+0+1+2+3)/6 = 6/6
E(d6>4) = (0+0+0+0+1+2)/6 = 3/6
E(d6>5) = (0+0+0+0+0+1)/6 = 1/6
E(d6>6) = (0+0+0+0+0+0)/6 = 0
```

Generalizing this, E(dX>Y) = Summation i=1 to X-Y of i, all over X (looks much nicer in mathematical notation)

Taking this further, roll a die dX and subtract the result of a second die dY. The table above represents d6>d6. In this scenario,

E(dX>dY) = Summation j=1 to Y of Summation i=1 to X-j of i, all over X*Y.

Lastly, dX>dY+Z, roll of dX subtracting a roll of dY and a constant Z gives

E(dX>dY+Z) = Summation j=Z to Y+Z of Summation i=1 to X-j of i, all over X*Y.

So, any Statistics people out there, did I get it correct? If not, where have I screwed up?

---

### Post by lisati on 2010-08-19
I'm not sure but unless I've missed something, I think you're on the right track. [SIZE="1"]I got momentarily sidetracked by misreading E(d6>1) as P(d6>1)[/SIZE]

---

### Post by mkendall on 2010-08-20
Sweet. Thanks.

> **lisati said:**
> [SIZE="1"]I got momentarily sidetracked by misreading E(d6>1) as P(d6>1)[/SIZE]

I was doing this while watching a game on TV. Kept having the same problem. ;)

---

