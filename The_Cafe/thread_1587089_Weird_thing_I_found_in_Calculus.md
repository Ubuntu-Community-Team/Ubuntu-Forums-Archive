---
title: "Weird thing I found in Calculus"
date: 2010-10-02
forum: The Cafe
---

### Post by slooksterpsv on 2010-10-02
Ok so this is weird, but for an equation where:
f(x) = ax^2+bx+c

|(f(x+1)-f'(x+1))|-|(f(x)-f'(x))|=f''(x)

I'm guessing this is already known? I just thought it was cool cause here's how I figured it out:
```

f(x) = x^2 + 2x
f'(x) = 2x + 2

f(1) = 1 + 2 = 3
f'(1) = 2 + 2 = 4
f(1)-f'(1)= -1
                 
f(2) = 4 + 4 = 8
f'(2) = 4 + 2 = 6
f(2)-f'(2) = 2

f(3) = 9 + 6 = 15
f'(3) = 6 + 2 = 8
f(3)-f'(3) = 7

|-1 - 2| = 3
| 2 - 7| = 5

| 3 - 5| = 2
f''(x) = 2

So overall, this proves that:
|(f(x+1)-f'(x+1))|-|(f(x)-f'(x))|=f''(x)=2a

```

Sorry just thought it was cool lol

---

### Post by nmaster on 2010-10-03
that's not a proof of anything. you chose a single polynomial and then showed that your statement was true at a single point.

you need to take some classes or study some good books on analysis if you want to be able to make (and prove) claims like this.

---

### Post by Troublegum on 2010-10-03
First thing: that's not a proof. 
And second: I don't know how you got the idea, but your theory is wrong. That equation is simply false. 
It justs works for that specific function you've chosen.

---

### Post by Lightstar on 2010-10-03
"if a gorilla were to step on a flower then the goat in the forest would prove that reading what was said is just not the same as a book in the refrigerator."  - Skim Bowie

---

### Post by Frank_Schley on 2010-10-03
if f[x] = ax^2 + bx + c, then 
Abs[f[x+1] - f'[x+1]] -Abs[f[x]-f'[x]]=
-Abs[-b + c - 2 a x + b x + a x^2] + 
 Abs[-b + c - 2 a (1 + x) + b (1 + x) + a (1 + x)^2], which might equal 2 but doesn't have to.

Still a cool example though.

---

### Post by ubunterooster on 2010-10-03
I still like 

If (X) x (X) = (Y),
then (X+1) x (X-1) = (Y-1),
therefore (X-2) x (X+2) = (Y-4)...

---

### Post by Tibuda on 2010-10-03
induction is not proof...

---

### Post by GeneralZod on 2010-10-03
> **Tibuda said:**
> induction is not proof...

Before anyone pounces: I'm sure he means [http://en.wikipedia.org/wiki/Inductive_reasoning](http://en.wikipedia.org/wiki/Inductive_reasoning), not [http://en.wikipedia.org/wiki/Mathematical_induction](http://en.wikipedia.org/wiki/Mathematical_induction) :)

---

### Post by cap10Ibraim on 2010-10-03
> **GeneralZod said:**
> Before anyone pounces: I'm sure he means [http://en.wikipedia.org/wiki/Inductive_reasoning](http://en.wikipedia.org/wiki/Inductive_reasoning), not [http://en.wikipedia.org/wiki/Mathematical_induction](http://en.wikipedia.org/wiki/Mathematical_induction) :)

okay , now that makes sense becuz we do use induction to prove some propositions

---

### Post by Windows Nerd on 2010-10-03
> **ubunterooster said:**
> I still like 

If (X) x (X) = (Y),
then (X+1) x (X-1) = (Y-1),
therefore (X-2) x (X+2) = (Y-4)...
I still like the mathematical proof that girls are indeed, evil:

First we state that girls require time and money:

**girls = time x money**

[COLOR="Red"]Edit: yes, the logic of the written statement should translate to "girls = time + money, but for the sake of the joke, let it be.[/COLOR]

As we all know, "time is money"

**time = money**

Therefore,

**girls = money x money = (money)^2**

And because "money is the root of all evil"

**money = sqrt(evil)**

Therefore:

**girls = (sqrt(evil))^2**

Then we are forced to conclude that:

**girls = evil**

Edit: I also found that someone one the site where I stumbled across this joke that someone added to the humor:

> "Jim Garrigues" says:

I have a suggestion for the proof that girls = evil.
I believe that when you say:
x = (sqrt(y))^2
that you can only say that
x = |y| (absolute value of y)
therefore,
if girls=(sqrt(evil))^2
then girls=|evil|
or girls are "absolute" evil!
-Jim

---

### Post by Windows Nerd on 2010-10-03
> **cap10Ibraim said:**
> okay , now that makes sense becuz we do use induction to prove some propositions

Science is all technically inductive reasoning. According to my physics teacher.

---

### Post by Linye on 2010-10-03
Stupid calculus.

---

### Post by JDShu on 2010-10-03
> **Windows Nerd said:**
> Science is all technically inductive reasoning. According to my physics teacher.

Yep, that's why Science is technically not proven.

---

### Post by JDShu on 2010-10-03
> **Windows Nerd said:**
> 
And because "money is the root of all evil"


Another flaw is that its the "love of money" which is the root of all evil.

---

### Post by forrestcupp on 2010-10-03
This thread is proof that no matter how smart you think you are, there are always at least 10 people at hand that are going to put you down and make you look completely stupid.  And it doesn't matter what the subject is or even how much of an expert you are on that subject.

---

### Post by JDShu on 2010-10-03
> **forrestcupp said:**
> This thread is proof that no matter how smart you think you are, there are always at least 10 people at hand that are going to put you down and make you look completely stupid.  And it doesn't matter what the subject is or even how much of an expert you are on that subject.

Indeed, but that's how we learn :D

---

### Post by Linye on 2010-10-03
> **forrestcupp said:**
> This thread is proof that no matter how smart you think you are, there are always at least 10 people at hand that are going to put you down and make you look completely stupid.  And it doesn't matter what the subject is or even how much of an expert you are on that subject.

Yep; there's always someone better than you.

---

### Post by standingwave on 2010-10-03
16/64 = 1/4 (cancel the sixes)
 19/95 = 1/5 (cancel the nines)
 26/65 = 2/5 (cancel the sixes)
 49/98 = 4/8 (cancel the nines)

Whenever you have nines or sixes in both the numerator and denominator, just cancel those suckers out!

QED

---

### Post by renkinjutsu on 2010-10-03
Personally, I believe there is no other genius quite like Randall Munroe.. > [http://xkcd.com/759/]("http://xkcd.com/759/")

---

### Post by standingwave on 2010-10-04
[http://www.youtube.com/watch?v=rLprXHbn19I](http://www.youtube.com/watch?v=rLprXHbn19I)

---

