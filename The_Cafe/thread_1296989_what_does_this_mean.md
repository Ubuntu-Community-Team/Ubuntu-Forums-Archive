---
title: "what does this mean?"
date: 2009-10-21
forum: The Cafe
---

### Post by MelDJ on 2009-10-21
i did this with python: 
>>> print 4^2
6
>>> print 4^6
2

does the ^ mean minus?
and is python unable to show negative numbers?

---

### Post by GeneralZod on 2009-10-21
> **MelDJ said:**
> i did this with python: 
>>> print 4^2
6
>>> print 4^6
2

does the ^ mean minus?
and is python unable to show negative numbers?

According to this:

[http://docs.python.org/library/operator.html](http://docs.python.org/library/operator.html)

it is ["bitwise exclusive OR"](http://en.wikipedia.org/wiki/Xor).

---

### Post by forrestcupp on 2009-10-21
^ is a bitwise XOR operator.  That means in binary, if exactly one of the 2 statements is true, the answer is true.  Otherwise the answer is false.

4 =  0100
2 =  0010
XOR
6 =  0110


4 = 0100
6 = 0110
XOR
2 = 0010

---

### Post by MelDJ on 2009-10-21
suddenly the boolean algebra i learn at school makes sense. :) 
thanks. just taking my baby steps into programming:KS

---

### Post by Warpnow on 2009-10-21
The free book byte of python has a chart in it. I'm also learning python. Started reading the book yesterday, and the first thing I coded was a compound interest generator. That book is great.

I just think its odd that powers are ** not ^, totally feels nonintuitive. Also the distinction between intergers and floating points seems odd to me. Intergers don't seem very useful to me.

---

### Post by MelDJ on 2009-10-21
i did not understand anything you said!:). i am following the full circle magazine's tutorials. i seem to be a snail compared to you:rolleyes:

---

### Post by jespdj on 2009-10-21
> **MelDJ said:**
> does the ^ mean minus?
and is python unable to show negative numbers?
Does the ^ mean minus? Is 4 - 2 = 6, or 4 - 6 = 2? Question answered... :P

Ofcourse Python is not unable to show negative numbers, that would be totally silly.

---

### Post by forrestcupp on 2009-10-21
> **Warpnow said:**
> 
I just think its odd that powers are ** not ^, totally feels nonintuitive. Also the distinction between intergers and floating points seems odd to me. Intergers don't seem very useful to me.
I agree about the powers thing.  Coming from Commodore BASIC, I was used to ^ being for powers, too.

But I totally disagree about integers.  When you start coming up with a lot of real world algorithms, you'll stumble across thousands of reasons to use integers.

---

### Post by Tibuda on 2009-10-21
> **Warpnow said:**
> Also the distinction between intergers and floating points seems odd to me. Intergers don't seem very useful to me.

It is a matter of storage of the data. There are only two integers between 0 and 1, but there are infinite real numbers.

---

### Post by emigrant on 2009-10-21
> **Warpnow said:**
> The free book byte of python has a chart in it. I'm also learning python. Started reading the book yesterday, and the first thing I coded was a compound interest generator. That book is great.

I just think its odd that powers are ** not ^, totally feels nonintuitive. Also the distinction between intergers and floating points seems odd to me. Intergers don't seem very useful to me.

can you please give a link for the book?
thank you.

---

### Post by j.bell730 on 2009-10-21
> **emigrant said:**
> can you please give a link for the book?
thank you.

[http://tinyurl.com/ygzoduz](http://tinyurl.com/ygzoduz)

---

### Post by emigrant on 2009-10-22
[j.bell730]("http://ubuntuforums.org/member.php?u=563127"), thanks for the help.
for those who need a direct link:
[http://www.google.com/url?sa=t&source=web&ct=res&cd=4&ved=0CBoQFjAD&url=http%3A%2F%2Fwww.ibiblio.org%2Fg2swap%2Fbyteofpython%2Ffiles%2F120%2Fbyteofpython_120.pdf&ei=ohLgSsWTGNLn-QaS6_CsCw&usg=AFQjCNHp7ZTqo0_e8WqSjtbsTez_aORjeQ&sig2=XJHqq5w0zN2c0sjjPfenHg](http://www.google.com/url?sa=t&source=web&ct=res&cd=4&ved=0CBoQFjAD&url=http%3A%2F%2Fwww.ibiblio.org%2Fg2swap%2Fbyteofpython%2Ffiles%2F120%2Fbyteofpython_120.pdf&ei=ohLgSsWTGNLn-QaS6_CsCw&usg=AFQjCNHp7ZTqo0_e8WqSjtbsTez_aORjeQ&sig2=XJHqq5w0zN2c0sjjPfenHg)

---

