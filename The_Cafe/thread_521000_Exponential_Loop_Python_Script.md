---
title: "Exponential Loop Python Script"
date: 2007-08-08
forum: The Cafe
---

### Post by yuvlevental on 2007-08-08
a = 1
while 1 == 1:
	a = a * 2
	print a

Pretty Sweet
Its infinite

---

### Post by Nekiruhs on 2007-08-08
This isn't exponential though. In order for it to be exponential you'd have to do ```
a = a ** 2
``` Instead of ```
a = a * 2
```

---

### Post by xtacocorex on 2007-08-08
That's an infinite loop.

---

### Post by yuvlevental on 2007-08-08
exponential as in exponential growth

---

### Post by Nekiruhs on 2007-08-08
> **yuvlevental said:**
> exponential as in exponential growth
But its not exponential. Theres no exponenets going on. 6 times 2 is not exponential. 6 squared is exponential.

---

### Post by yuvlevental on 2007-08-08
[Wikipedia's]("http://en.wikipedia.org/wiki/Exponential_growth") definition agrees with the script.

---

### Post by hod139 on 2007-08-08
At each iteration of the loop, a doubles.  The variable a has an exponential growth.  However, the loop is infinite, it will never terminate.

---

### Post by RussianVodka on 2007-08-08
> **yuvlevental said:**
> [Wikipedia's]("http://en.wikipedia.org/wiki/Exponential_growth") definition agrees with the script.

According to wikipedia, for your loop to have exponential growth it would have to do this:

```

a = #number
b = #number

while true:
     a = b ** a
     print a


```

---

### Post by Mathiasdm on 2007-08-09
Ugh, exponential is too slow! Try [this](http://en.wikipedia.org/wiki/Ackermann_function#Implementations):

(Source: wikipedia)

```
def ackermann(m, n):
     if m == 0:
         return n+1
     elif m > 0 and n == 0:
         return ackermann(m-1, 1)
     elif m > 0 and n > 0:
         return ackermann(m-1, ackermann(m, n-1))
```

Give 'ackermann(4,1)' a try ;-)

---

### Post by slimdog360 on 2007-08-09
just do the infinite taylor series

---

### Post by popch on 2007-08-09
> **yuvlevental said:**
> a = 1
while 1 == 1:
	a = a * 2
	print a

Pretty Sweet
Its infinite

It's not infinite, unless (a) Python has infinite precision (or rather infinite magnitude) arithmetic and (b) you have an infinite amount of RAM. If not, the program will simply crash after a while.

A bit closer to infinity will be:

a = 1
while a == a:
	print a

This will keep on running as long as you can keep the pc alive. That could be a very long time if you are using a VM.

---

### Post by popch on 2007-08-09
> **Nekiruhs said:**
> But its not exponential. Theres no exponenets going on. 6 times 2 is not exponential. 6 squared is exponential.

After doing the loop n times, the value of a will be 1 * (2 ** n), thats '2 to the n-th power. That's exponential.

---

### Post by proalan on 2007-08-09
err most programmers try to avoid infinite loops, especially exponential ones.

But since the original script wasn't exponential, and we don't know what exponential the op intended it could mean anything
2 to the power of n
n to the power of n
n to the power of 2
...

---

