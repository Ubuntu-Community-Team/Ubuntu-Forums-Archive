---
title: "Convert Scientific Notation to Decimal?"
date: 2009-10-17
forum: The Cafe
---

### Post by Jekshadow on 2009-10-17
I have a number in scientific notation form (2.893581094e+507) and whenever I try to convert it to a decimal via a website, it either crashes my browser (I really need to turn off JavaScript) or returns infinity...

Any tips?

---

### Post by koleoptero on 2009-10-17
That number is too large.

---

### Post by issih on 2009-10-17
The number is 2893581094 followed by 498 zeros..

It is, as stated above, too large to represent in decimal in any sensible way.

---

### Post by Rhubarb on 2009-10-17
While the number is rather on the huge side, if you do wish to have a number with all those zero's after it, I suggest you try out qalculate.

```
sudo aptitude install qalculate
```

Then paste your big number in there in scientific notation into qalculate.

Press the button in the middle of the qalculate screen to change it from "normal" to "simple".

Now just press **Ctrl + Alt + V** to copy the result.
You are now free to paste that number into whatever application / text document that you like, complete with all those zeros at the end of it.

And by the way, the number 2.893581094e+507 =
2893581094000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000

---

### Post by cholericfun on 2009-10-17
> Smallest DOUBLE value: -1.79769E+308
Largest DOUBLE value: 1.79769E+308
Smallest positive DOUBLE value: 2.225E-307
Largest negative DOUBLE value: -2.225E-307

i wonder where you got the 10^507 from?

anyhow, as you can see, theres a good reason to use scientific notation.

---

