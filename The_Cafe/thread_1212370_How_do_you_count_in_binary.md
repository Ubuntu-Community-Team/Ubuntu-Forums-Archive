---
title: "How do you count in binary?"
date: 2009-07-13
forum: The Cafe
---

### Post by dragos240 on 2009-07-13
How do you count in binary? What pattern do you follow?

---

### Post by Mehall on 2009-07-13
0, 1, 10, 11, 100, 101, 110, 111, etc.

---

### Post by Gizenshya on 2009-07-13
open up a hex editor and start typing :)  It depends on the editor, but I have mine set up to shw the character on the right, and I can switch between hexadecimal and binary code on the left side.  So I can just start typing on the right and it gives me the binary.  :)

---

### Post by dragos240 on 2009-07-13
I think I get it.
0 1 10 11 100 101 111 1000 1001 1010 1011 1100 1101 1110 1111

---

### Post by swoll1980 on 2009-07-13
from right to left(backwards) 8 bits is a word (most of the time)

if there's a 1 the value is counted in the word if not it's not counted. From right to left(backwards) the values of the bits are 1,2,4,8,16,32,64,128 
The first bit on the left is a one I forgot to put it in the drawing. This is how ASCII works too, except each value from 1-128 is assigned a character.

---

### Post by ddrichardson on 2009-07-13
> **dragos240 said:**
> I think I get it.
0 1 10 11 100 101 111 1000 1001 1010 1011 1100 1101 1110 1111
As Swoll's getting at - don't do it horizontally:```
0001
0010
0011
0100
0101
```You geet the idea.  Depending on the word size its easiest to write it starting at the beginning alternating by the size:```
0
0
1
1

```Then the second digit alternates```
00
01
10
11
```I only ever need to do this for truth tabes BTW.

---

### Post by eldragon on 2009-07-13
> **dragos240 said:**
> I think I get it.
0 1 10 11 100 101 111 1000 1001 1010 1011 1100 1101 1110 1111

no you dont...

thing of it this way, in decimal, youve got 10 symbols.. when youve run through all of them, you increment (or place a new one to the left, and start over). 

its the same but with only 2 symbols.

so:
```

0
1   <-- increments symbol
10  <-- new column
11 
100 <-- new column
101
110
111
1000  <-- new column
1001

```

hope ive been clear enough ;)

---

### Post by Bungo Pony on 2009-07-13
Okay, let's give you a definition. All counting starts at the right.

00000

Here is binary number zero. Start at the right.

00001

Here is binary number one. 

00010

Here is binary number two

00011

Here is binary number three.

00100

Here is binary number four

Each placement is a multiplier (I think that's the correct term). They work as follows:


x16 x8 x4 x2 x1

You can keep adding multipliers to the left if you need.

So for instance, the binary number 26 looks like this:

11010

The number 31 looks like this:

11111

Understand? :)

---

### Post by dragos240 on 2009-07-13
Why does it matter if I list the numbers horizontally?

---

### Post by dragos240 on 2009-07-13
0
1
10
11
100
101
110
111
1000
1001
1010
1011
1100
1101
1110
1111
10000
10001
10010
10011
10100
10101
10110
10111
11000
11001
11010
11011
11100
11101
11110
11111
100000

---

### Post by monsterstack on 2009-07-13
There is an easier way of thinking about it. Consider an eight-bit binary value. Starting from the right, the first value is worth 1, the second 2, the third 4, and so on. Think of the ones as "on" and the zeros as "off":

```

64  32  16  8  4  2  1
**0   0   0   0  0  0  0**

```

So, if we want to make 17, we must write:

```

64  32  16  8  4  2  1
**0   0   1   0  0  0  1**
16+1=17

```

If we wanted to make 57, we would write:
```

64  32  16  8  4  2  1
**0   1   1   1  0  0  1**
32+16+8+1=57

```

If we wanted to make 111, we would write:

```

64  32  16  8  4  2  1
**1   1   0   1  1  1  1**
64+32+8+4+2+1=111
```

Pretty neat, eh?

---

### Post by swoll1980 on 2009-07-13
00 = 0
01 = 1
10 = 2
11 = 3
100 =4
101 = 5
110 = 6
111 = 7
1000 = 8
1001 = 9
1010 = 10
1111 = 15

hope this makes sense.

---

### Post by Redache on 2009-07-13
>          Why does it matter if I list the numbers horizontally?      Putting them Vertically makes it easier to read and harder to make mistakes with.

---

### Post by RD1 on 2009-07-13
"one, two, three, four, five, six ..... etc."

---

### Post by swoll1980 on 2009-07-13
computers are fun.

---

### Post by monsterstack on 2009-07-13
```

  | **8  4  2  1** |
--------------------------
1 | 0  0  0  1 | 1
2 | 0  0  1  0 | 2
3 | 0  0  1  1 | 2 + 1
4 | 0  1  0  0 | 4
5 | 0  1  0  1 | 4 + 1
6 | 0  1  1  0 | 4 + 2
7 | 0  1  1  1 | 4 + 2 + 1
8 | 1  0  0  0 | 8
9 | 1  0  0  0 | 8 + 1
10| 1  0  1  0 | 8 + 2

```
Woot.

---

### Post by Cephi on 2009-07-13
> **swoll1980 said:**
> That would be counting in decimal.

No, "1, 2, 3, 4, 5, 6" would be counting in decimal.
"One, two, three, four, five, six" is neutral.  "six" is an appropriate pronunciation of the binary numeral 110... it's not a translation of that binary numeral into the decimal system.

EDIT: uh, I mean, I agree, computers are fun.

---

### Post by RD1 on 2009-07-13
> computers are fun.

Spoil Sport! :lolflag: ):P

---

### Post by ddrichardson on 2009-07-13
There are only 10 types of people, those who understand and those who don't understand binary.

I'll get my coat...

---

### Post by swoll1980 on 2009-07-13
> **Cephi said:**
> No, "1, 2, 3, 4, 5, 6" would be counting in decimal.
"One, two, three, four, five, six" is neutral.  "six" is an appropriate pronunciation of the binary numeral 110... it's not a translation of that binary numeral into the decimal system.

EDIT: uh, I mean, I agree, computers are fun.

Yeah I caught myself. It was to late though obviously.

---

### Post by koleoptero on 2009-07-13
> **dragos240 said:**
> Why does it matter if I list the numbers horizontally?

It doesn't.

Also since you understood the thing about binary then you also can understand how to count in any other system. Like hexadecimal which has 16 symbols for each digits. Every column of the number is a higher power of the number you use as a base.

e.g.

In binary: 10010110 = 1*2^7 + 0*2^6 + 0*2^5 + 1*2^4 + 0*2^3 + 1*2^2 + 1*2^1 + 0*2^0

In hexadecimal 2d1 = 2*16^2 + 13*16^1 + 1*16^0


P.S.: There's also a nice way to represent numbers using prime numbers as the base. Anyone wants to play with that? :mrgreen:

---

### Post by dragos240 on 2009-07-13
> **monsterstack said:**
> There is an easier way of thinking about it. Consider an eight-bit binary value. Starting from the right, the first value is worth 1, the second 2, the third 4, and so on. Think of the ones as "on" and the zeros as "off":

```

64  32  16  8  4  2  1
**0   0   0   0  0  0  0**

```So, if we want to make 17, we must write:

```

64  32  16  8  4  2  1
**0   0   1   0  0  0  1**
16+1=17

```If we wanted to make 57, we would write:
```

64  32  16  8  4  2  1
**0   1   1   1  0  0  1**
32+16+8+1=57

```If we wanted to make 111, we would write:

```

64  32  16  8  4  2  1
**1   1   0   1  1  1  1**
64+32+8+4+2+1=111
```Pretty neat, eh?

Good trick! Thanks!

---

### Post by twright on 2009-07-13
btw. The default calculator in ubuntu (gnome) has a programming mode which does binary pretty well :KS

---

### Post by doas777 on 2009-07-13
learning to count binary on my fingers while i was walking to school was a good exercise for me. only really helps at the low ranges, but you pick up the progression, and making it tactile helped retention.

somtimes it depends on what you want to do. I memorized bit positions both R->L and L->R when learning subnetting. 

for bytes themselves, i count backward, comparing the bit value to the remainder of the quantity I'm looking for

235 is 1 192, 0 64s, 1 32, 0 16s, 1 8, 0 4s, 1 2, and 1 1. if you look at binary regularly, you will slowly begin to read it the way we usually read words or numbers, rather than calculate it.

---

### Post by lisati on 2009-07-13
> **dragos240 said:**
> Why does it matter if I list the numbers horizontally?
Sometimes it's easier to see the pattern if the numbers are listed vertically, particularly if you left-pad with zeros.

---

### Post by JordyD on 2009-07-13
Well, look at decimal or base 10 (place values):
```

thousands hundreds  tens      ones
10^3      10^2      10^1      10^0
```

In decimal:
17 = 10^1 * **1** + 10^0 * [B]7
[/B]


They can all be represented like that. Apply the same thing to binary (base 2):
```

sixteens eights   fours    ones
2^3      2^2      2^1      2^0
```

Thus, in binary:

1001 = 2^3 * **1** + 2^2 * **0** + 2^1 * **0** + 2^0 * **1**

If you've noticed the pattern, this can be applied to other number systems as well, such as hexadecimal (base 16):

```
4096      256       16        1
16^3      16^2      16^1      16^0
```

---

### Post by MikeTheC on 2009-07-13
Very well, thank you very much.

---

### Post by lisati on 2009-07-13
> **Cephi said:**
> No, "1, 2, 3, 4, 5, 6" would be counting in decimal.
"One, two, three, four, five, six" is neutral.  "six" is an appropriate pronunciation of the binary numeral 110... it's not a translation of that binary numeral into the decimal system.

EDIT: uh, I mean, I agree, computers are fun.

Once we get to twenty (or is it thirteen?) that the extremely pedantic folks might start getting picky, but otherwise we're pretty much in agreement.

And yes, computers are fun: sometimes they make better sense than people!

---

### Post by swoll1980 on 2009-07-14
> **MikeTheC said:**
> Very well, thank you very much.

Well done. Took me a few seconds to get that one.

---

