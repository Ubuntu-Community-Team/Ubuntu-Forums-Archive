---
title: "Easy way to convert decimal to binary"
date: 2009-04-16
forum: The Cafe
---

### Post by swoll1980 on 2009-04-16
Start with any number, divide it by 2, if there's a remainder of .5  you drop the .5 before you divide by 2 again. If it's whole you don't have to drop before you divide again.  repeat this until you get to 0. When your done, write a 0 next to all the answers that were whole numbers, and 1 next to all the ones that ended in .5 if you read from the bottom up, that's your number in binary. See the chart in the pic. I used 213 in the example. but it will work with all numbers

---

### Post by ostrm on 2009-04-16
hey, I have an easier way :-D


```
echo 'ibase=10; obase=2; 213' | bc
```

---

### Post by swoll1980 on 2009-04-16
> **ostrm said:**
> hey, I have an easier way :-D


```
echo 'ibase=10; obase=2; 213' | bc
```

Hey! That's Cheating!

---

### Post by Kareeser on 2009-04-16
There's no such thing as "cheating" in the real world :)

---

### Post by yabbadabbadont on 2009-04-16
> **Kareeser said:**
> There's no such thing as "cheating" in the real world :)

There is when you get caught...

---

