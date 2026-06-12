---
title: "How many operations per second can a standard PC perform"
date: 2008-10-30
forum: The Cafe
---

### Post by josephellengar on 2008-10-30
I don't know- just a normal one that you'd buy today off the shelf.  I just saw a news story that said that someone came up with a computer that can perform 50 trillion operations per second.  Wow!  So, what can mine do?

---

### Post by NovaAesa on 2008-10-30
I guess it would all depend on the complexity of the particular operation you are talking about.

---

### Post by josephellengar on 2008-10-30
I think that the 50 trillion operations was in FLOPS.

---

### Post by teqsun on 2008-10-30
isnt a flop 32 bits of data?

---

### Post by ChanServ on 2008-10-30
1

---

### Post by LaRoza on 2008-10-30
> **idigchess said:**
> I don't know- just a normal one that you'd buy today off the shelf.  I just saw a news story that said that someone came up with a computer that can perform 50 trillion operations per second.  Wow!  So, what can mine do?

Vague question...

What is the hardward? I see no "standard PC" arch.

What is your CPU? Mine has a speed of 2.8 Ghz, therefore, it can do that many operations a second (1 hertz is an operation)

Keep in mind all the hardware works together, so you'd have to take into account the other hardware.

---

### Post by klange on 2008-10-30
Technically, one hertz just means "1 / second". It can be one anything.
2.8GHz means 2,800,000,000Hz or 2.8 billion operations per second.
And then there's multi-core processors...

---

### Post by ModelM on 2008-10-30
Perhaps there are some here who haven't heard of bogomips.

One way to measure the speed of a computer is in Millions of Instructions Per Second - or MIPS.

The kernel hackers put a quick routine into the kernel to measure your processor speed. It serves as only an estimate & shouldn't be measured against anything else so the numbers are Bogus and can't be compared to anything but themselves. Bogus MIPS - or BogoMIPS.

In a terminal type:```
dmesg | grep Bogo
```and you should see a result that looks like this:```
[   15.522333] Calibrating delay using timer specific routine.. 5057.49 BogoMIPS (lpj=10114998)
[   15.918108] Calibrating delay using timer specific routine.. 5053.97 BogoMIPS (lpj=10107947)
[   15.918704] Total of 2 processors activated (10111.47 BogoMIPS).

```

That should give you something to play with for a while.

---

### Post by ad_267 on 2008-10-30
A flop is a floating point operation. [http://en.wikipedia.org/wiki/FLOP](http://en.wikipedia.org/wiki/FLOP)

Most applications use double precision floats for operations (64 bits on a 32 bit PC)

---

### Post by LaRoza on 2008-10-30
> **WindowsSucks said:**
> 
2.8GHz means 2,800,000,000Hz or 2.8 billion operations per second.
And then there's multi-core processors...

Yes, mine is dual core, I wasn't thinking about that.

---

