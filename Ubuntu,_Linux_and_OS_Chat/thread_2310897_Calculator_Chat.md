---
title: "Calculator Chat"
date: 2016-01-22
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2016-01-22
I taught English for 30 years in Los Angeles secondary schools. I am now retired and live in the Dominican Republic. I have always regretted my illiteracy in math--until now! Since August, 2015, I have progressed from second grade early math through arithmetic and now 1/2 finished with Algebra 1, geometry, and statistics--high school level.

On Ubuntu I've been using the Qalculate! calculator, which has served me well, until now, when I entered a tan function and got a weird result. Comparing, if I go to Wolfram-Alpha, I can enter something as simple as 7tan65 and the answer I get is 15.01 (rounded to hundredths). My virtual Khan Academy chokes on this simplicity and I have to enter 7 x tan(65) to get an answer. But whichever I try on Qalculate! I get a weird result: ~ -10.29

For those of you using Qalculate! do you get my weird result or am I inputting wrong?

What are your favorite virtual and hard calculators?

---

### Post by mörgæs on 2016-01-22
7 * tan (65 degrees) = 15.01
7 * tan (65 radians) = -10.29

---

### Post by rewyllys on 2016-01-22
My favorite virtual calculator is GRPN.  My favorite hard calculator is the Hewlett-Packard 12CP.

---

### Post by Kurt_Alan on 2016-01-23
Re-checked the plain vanilla calculator that comes with Ubuntu (calculator 3.10.3), and the advanced mode works properly, so good-bye Qalculate!

---

### Post by mörgæs on 2016-01-23
How does Qalculate calculate if you set it to use degrees?

---

### Post by Petro Dawg on 2016-01-23
Here is my favorite.  It never lies....
[ATTACH=CONFIG]266913[/ATTACH]

Line up 7 and Tan(65 Deg)...
[ATTACH=CONFIG]266914[/ATTACH]

And read result at the end of the "C" scale...
[ATTACH=CONFIG]266915[/ATTACH]

And 15.01 is shown.  You just need to know that the answer isn't .1501, 1.501, or 150.1 to use this method ;)

---

### Post by montag dp on 2016-01-23
The good old radians versus degrees.  Garbage in -> garbage out, as they say.  This would be a case of user error.  Sorry OP.  ;)

By the way, radians *should* be the default for trig functions, IMO.

---

### Post by SantaFe on 2016-01-24
> **montag dp said:**
> 

By the way, radians *should* be the default for trig functions, IMO.

So you're saying radians are **RAD**? ;)

---

### Post by Kurt_Alan on 2016-01-24
Both my Ubuntu calculator and my Khan Academy choked on this input (either malformed expression or wrong answer) for this input for a law of cosines problem:

```
7^2+13^2-2(7)(13)(cos28)
```

give me 31.78 on my Khan Academy and Ubuntu calculators, both the wrong answer, but give me 57.30 on Wolfram Alpha, the correct answer. It seems that multiplication is kind of slippery because there are different ways to show it. Maybe WA is more forgiving of a beginner like me, not sure.

---

### Post by Kurt_Alan on 2016-01-24
Just checked out GRPN. It calculates as I input. I like to see my input before calculation. Am I missing something?

---

### Post by Kurt_Alan on 2016-01-24
Probably they are. I think that degrees were introduced as approximations.

---

### Post by Kurt_Alan on 2016-01-24
Very nice. I need to learn to use a slide rule. Faith in a machine (or user error) is a problem. Weren't all calculations for the Apollo Mission done with a slide rule?

---

### Post by montag dp on 2016-01-24
> **Kurt_Alan said:**
> Both my Ubuntu calculator and my Khan Academy choked on this input (either malformed expression or wrong answer) for this input for a law of cosines problem:

```
7^2+13^2-2(7)(13)(cos28)
```

give me 31.78 on my Khan Academy and Ubuntu calculators, both the wrong answer, but give me 57.30 on Wolfram Alpha, the correct answer. It seems that multiplication is kind of slippery because there are different ways to show it. Maybe WA is more forgiving of a beginner like me, not sure.Some calculators will require you to use the * character for multiplication, which may be why they are saying you have a malformed expression (I don't know for sure because I haven't used either of them).  Most calculators would also require you to type cos(28) instead of cos28.  Wolfram Alpha is designed to be very flexible in how the inputs are written; it tries to "figure out what you meant," whereas most others require more rigid syntax.

57.30 is the correct answer, by the way, as long as 28 means 28 degrees.  You should also check with those other calculators whether they use radians or degrees for angles.  If it is radians, you should switch it to degrees if possible, or, if not, multiply all your angles by pi/180 to convert them to radians.

---

### Post by poorguy on 2016-01-25
> **Petro Dawg said:**
> Here is my favorite.  It never lies....
[ATTACH=CONFIG]266913[/ATTACH]

Line up 7 and Tan(65 Deg)...
[ATTACH=CONFIG]266914[/ATTACH]

And read result at the end of the "C" scale...
[ATTACH=CONFIG]266915[/ATTACH]

And 15.01 is shown.  You just need to know that the answer isn't .1501, 1.501, or 150.1 to use this method ;)
  
First one I learned to use.

---

### Post by rewyllys on 2016-01-25
> **Kurt_Alan said:**
> Both my Ubuntu calculator and my Khan Academy choked on this input (either malformed expression or wrong answer) for this input for a law of cosines problem:

```
7^2+13^2-2(7)(13)(cos28)
```

give me 31.78 on my Khan Academy and Ubuntu calculators, both the wrong answer, but give me 57.30 on Wolfram Alpha, the correct answer. It seems that multiplication is kind of slippery because there are different ways to show it. Maybe WA is more forgiving of a beginner like me, not sure.
It's easy using R:

[COLOR=blue]7^2 + 13^2 - 2*7*13*cos(28*pi/180)
[/COLOR][1] 57.30354

---

### Post by Petro Dawg on 2016-01-25
> **Kurt_Alan said:**
> Very nice. I need to learn to use a slide rule. Faith in a machine (or user error) is a problem. Weren't all calculations for the Apollo Mission done with a slide rule?

Slide-rules were used along with very expensive computers with primitive spread sheet programs.  Time using the computers was very expensive so slide-rules were used for the easier calculations.  My grandfather was an engineer who worked on some camera equipment that went on the Apollo missions, the slide-rule in the pictures I posted earlier was his.  It was given to me when I graduated with my engineering degree and may have actually been used to complete some calculations related to equipment that went on the Apollo missions.

The only problem with slide-rules are they don't provide the position of the decimal place or whether solution is positive or negative.  So an estimate of the final answer is usually required before you can determine the precise solution.  A slide-rule can be very fast, easy to use, and accurate enough for most real world problems with some practice and good understanding of trig.

However, I doubt my boss would be to happy if I threw out Excel or Mathcad in place of a slide-rule.  :D

---

