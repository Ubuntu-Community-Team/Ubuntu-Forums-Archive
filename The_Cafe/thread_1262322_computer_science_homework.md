---
title: "computer science homework"
date: 2009-09-09
forum: The Cafe
---

### Post by nathang1392 on 2009-09-09
im taking ap computer science at school over distance learning, i am usually pretty sure what to do, but this confuses me. i am given a code, of numbers, and i have to write an algorithm to decode these numbers: 220 241 255 245 052 313
311 052 312 303 052 312
252 245 052 205 241 251
253 243 052 203 253 302
251 244 303 301 053. the problem is that i cant figure out what the numbers decode to in the first place, anyone have any idea?

---

### Post by Bachstelze on 2009-09-09
Maybe octal numbers that you need to convert to decimal? It's a bit weird that you're just given those numbers and "plz decode that kthx".

---

### Post by nathang1392 on 2009-09-09
its weird to me also. i dont necessarily have to decode it, but i have to write an algorithm. i also assumed they could translate into words somehow, but it doesnt make any sense.

---

### Post by #11u-max on 2009-09-09
is it a hex code?

---

### Post by t0p on 2009-09-09
If you don't understand your assignment, you should have a chat with your teachers.  It's clear you have missed something somewhere along the line as the assignment doesn't make any sense the way you've presented it here.  Decode numbers... into what?  To *decode* something implies that there is a *code*.  And a series of numbers is only a code if it is supposed to mean something.

Go talk to your teachers.

---

### Post by MaxIBoy on 2009-09-09
I'm going to assume here that it's okay to give you suggestions on the code, since the real assignment is to "write an algorithm," but you're on shaky ground here, asking for homework help. Just putting that out there. I'm only helping because I find it to be an interesting problem myself.



If it was hex there would be As, Bs, Cs, Ds, Es, and Fs.  In fact there doesn't seem to be anything over five. 

I would say that each group of three digits is a byte but there are some  which are more than 256.

Try treating each group of three as a three-digit octal number (9 bits.) Looking at these numbers, the most-significant bit is always zero. The highest number is 313 which from octal to binary is 11001011. This is only 8 bits. So try discarding the most-significant bit, then you have a round byte which could be ACII.

---

### Post by PurposeOfReason on 2009-09-09
The instructor left something out, it is a CS class not a class to decode things. He should have said what they were coded with so that you could then decode it. That's like me giving you a slew of letters that were shift coded, not telling you, and letting you pick at it. It is a waste of time when the real goal is the algorithm.

---

### Post by MaxIBoy on 2009-09-09
Maybe you're supposed to write a program to try different decoding methods, then automagically throw out any results which look like garbage?

---

### Post by PurposeOfReason on 2009-09-09
I don't think so because that is assuming they know many different code methods and they don't assume things when you're a student. So unless you've been lectured on that, I don't think that's the goal.

OP, it would help to know how advanced this class is.

---

### Post by clonne4crw on 2009-09-09
Maybe its Base64

---

### Post by lhowaf on 2009-09-09
The only numbers present are 0 through 5. Therefor it is base 6.
Wouldn't that mean the first number (220) in base 10 would be (2 X 36) + (2 X 6) + (0 X 1)?

Hint: first word is "Take"

---

### Post by lhowaf on 2009-09-10
You're welcome.

---

### Post by nathang1392 on 2009-09-10
just a question, once you convert the number to base 10, where are you getting the text from? how do you convert between decimal and text?

---

### Post by PurposeOfReason on 2009-09-10
> **nathang1392 said:**
> just a question, once you convert the number to base 10, where are you getting the text from? how do you convert between decimal and text?
Memorize this because if you plan to code a lot, you'll want to know all the letters:
[http://www.asciitable.com/](http://www.asciitable.com/)

---

### Post by LookTJ on 2009-09-10
A little googling took me to a ascii table full of codes, however I will not link it. :) Base 10 to ascii

Nevermind, purposeofreason :)

---

### Post by lhowaf on 2009-09-10
If you find an ASCII table in base 10 you can look up codes directly but most often they're in hex so you need to convert.
Look in your accessories for both a calculator and a character (ASCII) chart.

---

### Post by ve4cib on 2009-09-10
> **PurposeOfReason said:**
> Memorize this because if you plan to code a lot, you'll want to know all the letters:
[http://www.asciitable.com/](http://www.asciitable.com/)

There's also the ASCII man page:

```
$ man ascii
```

---

