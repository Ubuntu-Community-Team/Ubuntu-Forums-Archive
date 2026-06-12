---
title: "PI to 10000 places..."
date: 2008-04-06
forum: The Cafe
---

### Post by ibuclaw on 2008-04-06
Someone's got to of done this before...:lolflag:

I've been discovering the wonders of "bc" in linux.

And I've just found that it can do sums to an infinite number of decimal places.

So the idea came to me to write an equation to figure out the number of pi.
As most half decent math students will know, the best way to calculate the number pi is "4 time the arc tangent of 1".

So I came up with this.
```

#!/bin/bash
pi()
{
    export x=`echo "scale=$scale; 4 * a (1)" | bc -l`
    echo "$x"
}
if [ "$#" = "1" ]
then
    scale="$1"
    echo `time pi`
else
    echo "Usage: $0 #"
fi

```
And now I can compute pi to 10000 places. And serve it as a benchmark for how speedy I can do it in!

> 
:~$ ./pi 10000

real    5m4.902s
user    4m58.327s
sys     0m1.052s
3.141592653589793238462643383279502884197169399375105820974944592307\
etc (147 lines later, I am not copying the whole answer here. It's too big!)....
375676


I am rather impressed with myself :KS

Regards

---

### Post by tdrusk on 2008-04-06
good job

super pi (or whatever it's called) can do the same. 

nice script.

---

### Post by Paul Miller on 2008-11-03
I think you'll have better luck (i.e. it will be much faster!) with the following formula:

```

pi = 16 arctan (1/5) - 4 arctan (1/239)

```

This is called Machin's formula.  See [http://en.wikipedia.org/wiki/Machin-like_formula](http://en.wikipedia.org/wiki/Machin-like_formula) for more info.

Edit: whoops, sorry for raising a somewhat old thread to the top. :P

---

