---
title: "Does anyone know if..."
date: 2007-02-13
forum: The Cafe
---

### Post by Adamant1988 on 2007-02-13
.9999 (repeating) actually **DOES** equal 1?

---

### Post by Sqwishy on 2007-02-13
um ... no it doesn't. why are you asking the ubuntu forums? lol

---

### Post by muguwmp67 on 2007-02-13
> **Adamant1988 said:**
> .9999 (repeating) actually **DOES** equal 1?

Not in any number system that I'm aware of.  After an infinite number of repeats, its going to be so close to 1 that it may be insignificant for statistical or engineering purposes, but its still going to be 'approaching' 1.

---

### Post by GeneralZod on 2007-02-13
*sigh*

Yes it does:

[http://en.wikipedia.org/wiki/0.999](http://en.wikipedia.org/wiki/0.999)

This usually erupts into a flamewar that puts GNOME vs KDE and vi vs Emacs to shame.  On a forum I frequent, merely broaching the topic is grounds for a ban :)

---

### Post by Pelekophori on 2007-02-13
How about this  ?

[http://polymathematics.typepad.com/polymath/2006/06/no_im_sorry_it_.html]("http://polymathematics.typepad.com/polymath/2006/06/no_im_sorry_it_.html")

---

### Post by highneko on 2007-02-13
> **Adamant1988 said:**
> .9999 (repeating) actually **DOES** equal 1?
If by 1 you mean true: then my answer is yes.
for ((i=0;i<5;i++)); do if echo ".9999"; then echo "true"; fi; done

---

### Post by doobit on 2007-02-13
Statistically, .9999 also equals 1.

---

### Post by Hendrixski on 2007-02-13
I've seen that around before, and it sounds disquetingly wrong.  If you keep adding 9's after a decimal you are getting closer to 1, but never actually touch it.. there is still an infinitsmally small amount of space between it and the actual number one?  no?

I've heard there's a proof for the .999..... = 1 thing, but haven't seen it.  I've seen tricks where you convert formats, do an operation, switch formats and then it LOOKs like it works (like the link posted above).   I haven't seen an actual "proof"

Although really, it's not important.

---

### Post by mips on 2007-02-13
> **Adamant1988 said:**
> .9999 (repeating) actually **DOES** equal 1?

Nope. Close but no cigar.

---

### Post by muguwmp67 on 2007-02-13
> **highneko said:**
> If by 1 you mean true: then my answer is yes.
for ((i=0;i<5;i++)); do if echo ".9999"; then echo "true"; fi; done
It sounds like this thread should die, but isn't the above statement true for *any* non-zero value because its a boolean operation?

I tried to read the proofs, but they made my head hurt.  Apparently its because I think of .999... as a process and not a value. It sounds like a religious issue to me.

---

### Post by koenn on 2007-02-13
> **highneko said:**
> If by 1 you mean true: then my answer is yes.
for ((i=0;i<5;i++)); do if echo ".9999"; then echo "true"; fi; done


```
 for ((i=0;i<5;i++)); do if echo "this is nonsense"; then echo "true"; fi; done
```

---

### Post by highneko on 2007-02-13
> **muguwmp67 said:**
> It sounds like this thread should die, but isn't the above statement true for *any* non-zero value because its a boolean operation?

I tried to read the proofs, but they made my head hurt.  Apparently its because I think of .999... as a process and not a value. It sounds like a religious issue to me.
I agree. Was thinking it was a legit questions for a second. But it was a trap!!!

I'm not sure, all I know if that it returns true because echo was successful. 1 is true if I remember correctly.

> **koenn said:**
> ```
 for ((i=0;i<5;i++)); do if echo "this is nonsense"; then echo "true"; fi; done
```
 I meant it as a joke, but what I said is true. If by 1 he meant true then...

---

### Post by %hMa@?b&lt;C on 2007-02-13
it is simple, in any algebra book, it has a simple proof for how to turn repeating decimals into fractions

n=.9(repeating)
therefore
10n=9.9 (repeating)
subtract "n" from both sides
9n = 9
divide both sides by 9
n=1

it is irrefutable, becaues the 9's go on forever, the subtraction in the subtraction step cancells out the 9's for ever

---

### Post by Choad on 2007-02-13
quick proof

1/3 = 0.333...

0.333... * 3 = 0.999....
1/3 * 3 = 1

0.999... = 1

---

### Post by era86 on 2007-02-13
Holy crap... I've never viewed the world in such a way... hahaha

---

### Post by jdong on 2007-02-13
**A Mathematical Proof**

0.999 repeating is 1. "close but not quite" is not correct. 0.9999repeating is a limit -- a limit of the number as you add more and more 9's -- so 0.9999repeating is not a number itself -- it's the limit of an expression.

Let's rewrite it in more mathematical terms:

0.999repeating = 0.9 + 0.09 + 0.009 + 0.0009.... = 9/10 + 9/100 + 9/1000 + ....

So, rewriting in summation notation:

Sum of 9*(1/10)^n for n from 1 to A

We are interested in what happens as A approaches infinity (you can not plug infinity into an expression -- you must take the limit of the expression as a value APPROACHES infinity)


If we recall the sum of a geometric sequence (See a proof at [http://www.everything2.com/index.pl?node_id=383038](http://www.everything2.com/index.pl?node_id=383038)):
> 
For any geometic sequence a*r^n, the sum of the sequence to A terms is equal to 

a*((1-r^A)/(1-r))

for all nonzero r between -1 and 1 (noninclusive)


So, applying that to our equation:

a = 9
r = 1/10

So the sum of the sequence to A terms is:

=9*((1-(1/10)^A)/(1-1/10))
=1-(1/10)^A

Ok, cool! We have a generic formula now for the sum up to A terms. We need to take the limit of this as A approaches infinity:

**By the way**: Note this expression is now **what's 1 - 0.0000...1**? Cool! Two birds, one stone.

As A -> infinity, (1/10)^A -> 0,  we get that the limit = 1-0, or 1


So, we have proven mathematically that 0.999......repeating =1

---

### Post by Omnios on 2007-02-13
It is there yet it does not exist does this solve a lot of what we do not understand. It exists but where?

---

### Post by Choad on 2007-02-13
> **jdong said:**
> **A Mathematical Proof**

0.999 repeating is 1. "close but not quite" is not correct. 0.9999repeating is a limit -- a limit of the number as you add more and more 9's -- so 0.9999repeating is not a number itself -- it's the limit of an expression.

Let's rewrite it in more mathematical terms:

0.999repeating = 0.9 + 0.09 + 0.009 + 0.0009.... = 9/10 + 9/100 + 9/1000 + ....

So, rewriting in summation notation:

Sum of 9*(1/10)^n for n from 1 to A

We are interested in what happens as A approaches infinity (you can not plug infinity into an expression -- you must take the limit of the expression as a value APPROACHES infinity)


If we recall the sum of a geometric sequence (See a proof at [http://www.everything2.com/index.pl?node_id=383038):](http://www.everything2.com/index.pl?node_id=383038):)


So, applying that to our equation:

a = 9
r = 1/10

So the sum of the sequence to A terms is:

=9*((1-(1/10)^A)/(1-1/10))
=1-(1/10)^A

Ok, cool! We have a generic formula now for the sum up to A terms. We need to take the limit of this as A approaches infinity:

**By the way**: Note this expression is now **what's 1 - 0.0000...1**? Cool! Two birds, one stone.

As A -> infinity, (1/10)^A -> 0,  we get that the limit = 1-0, or 1


So, we have proven mathematically that 0.999......repeating =1
i think my proof was easier to understand lol

---

### Post by muguwmp67 on 2007-02-13
Whats the difference between .9999.... and the value of the number that is closest to one without being one?

When I was in grade school, we were always told that .3333... was a repeating number and an approximation.  Apparently something has changed over the last 20 years, as I've seen people say that its in every algebra book.  I never thought I'd ever have problems with 'the new math' in my lifetime.  Has there been some sort of redefinition of real numbers, integers, etc in the last 20 years?

---

### Post by Omnios on 2007-02-13
.3333... is something wierd in that it just keeps going.  When they make something to represent the  endless .3333  things might be different say something like 1 to the power of ten. As long as it is .33333....endless it may not be handled properly

---

### Post by rai4shu2 on 2007-02-13
> **Choad said:**
> quick proof

1/3 = 0.333...

0.333... * 3 = 0.999....
1/3 * 3 = 1

0.999... = 1

The flaw I would mark a big red circle around is the "0.333... * 3 = 0.999...." part which obviously can't be true.

---

### Post by jdong on 2007-02-13
ok:

.333 is an approximation of 1/3
.333333333 is an approximation closer to 1/3
.33333333333333333333333333333333333333333333333333333333333333333333333333333333333333 is an approximation EVEN CLOSER to 1/3
.333.... is a way of writing 1/3
.3 repeating is a way of writing 1/3


Apply the above concepts to .999... and 1

---

### Post by jdong on 2007-02-13
> **rai4shu2 said:**
> The flaw I would mark a big red circle around is the "0.333... * 3 = 0.999...." part which obviously can't be true.

It is true. Rewrite it in terms of limits and recall that C*lim(expr) = lim(C*expr)

---

### Post by jdong on 2007-02-13
> **Choad said:**
> i think my proof was easier to understand lol

Your proof was not a mathematical proof. It was a rough outline, informal proof, informal demonstration, etc....

But what I wrote was a mathematically valid proof. Every statement is proven or an application of a proven statement.

For your proof to be valid you also need to expand all your ...'s into a  infinite summation expression. In which case you will prove your statement is algebraically identical to mine.

---

### Post by Choad on 2007-02-13
> **rai4shu2 said:**
> The flaw I would mark a big red circle around is the "0.333... * 3 = 0.999...." part which obviously can't be true.
say what now?

@djong

ok, fair point. my one *does* get the point accross tho :p

---

### Post by jdong on 2007-02-13
> **Choad said:**
> say what now?

@djong

ok, fair point. my one *does* get the point accross tho :p

My theory is a lot of people see those ordinary demonstrations and will refuse to believe them.

Shove pure math in their face and there is no point where they can refute.

If anyone can counter-argue my proof please do so!

---

### Post by saulgoode on 2007-02-13
The question to ask is:

Is 0.9999(repeating) equal  to 1 - (1 / infinity) ?

Because infinity is not a number and equations such x/x = 1, x - x = 0, and x - 0  = x are not valid unless 'x' is a finite number.

---

### Post by Choad on 2007-02-13
> **saulgoode said:**
> The question to ask is:

Is 0.9999(repeating) equal  1 - (1 / infinity) ?

Because infinity is not a number and equations such x/x = 1, x - x = 0, and 0 - x = x are not valid if 'x' is not a finite number.
yep

1 - 0.000...1 = 1

wierd no?

---

### Post by jdong on 2007-02-13
> **saulgoode said:**
> The question to ask is:

Is 0.9999(repeating) equal  1 - (1 / infinity) ?

Because infinity is not a number and equations such x/x = 1, x - x = 0, and 0 - x = x are not valid unless 'x' is a finite number.

**NO**. That is not what I stated.

I stated is 0.9999repeating equal limit(1-(1/A)) as A approaches infinity. And limit  of 1/A as A approaches infinity is proven to be zero.

You can see how to prove limits at [http://www.math.ucdavis.edu/~kouba/CalcOneDIRECTORY/preciselimdirectory/PreciseLimit.html](http://www.math.ucdavis.edu/~kouba/CalcOneDIRECTORY/preciselimdirectory/PreciseLimit.html)

But it'll be easier on your head just to accept limit of 1/A a->infinity to be zero.

---

### Post by Choad on 2007-02-13
> **jdong said:**
> **NO**. That is not what I stated.

I stated is 0.9999repeating equal limit(1-(1/A)) as A approaches infinity. And limit  of 1/A as A approaches infinity is proven to be zero.

You can see how to prove limits at [http://www.math.ucdavis.edu/~kouba/CalcOneDIRECTORY/preciselimdirectory/PreciseLimit.html](http://www.math.ucdavis.edu/~kouba/CalcOneDIRECTORY/preciselimdirectory/PreciseLimit.html)

But it'll be easier on your head just to accept limit of 1/A a->infinity to be zero.
then surely what you have just said means he was right in saying 0.999... = 1 - (1/infinity)

if 1/infinity = 0, then 1 - 1/infinity = 1, and the 0.999.... thing is 1, so it works...

---

### Post by muguwmp67 on 2007-02-13
> 
.333 is an approximation of 1/3
.333333333 is an approximation closer to 1/3
.3333333333333333333333333333333333333333333333333 3333333333333333333333333333333333333 is an approximation EVEN CLOSER to 1/3
.333.... is a way of writing 1/3
.3 repeating is a way of writing 1/3

I understand this logic, even though I doubt that its anything even close to valid as a formal proof.  

It does explain it to me though.  There is a difference between what I call a 'value' and what I call a 'numeral'

a value is an amount and in these terms, there is a difference between 1 and .999... as long as we believe that it expresses the closest value to 1 without being 1.

A 'numeral' is a representation used in a system that has a series of rules it uses to keep the system consistent and useful.

I can concieve of a value between 0 and 1, closest to 1 without being one and I would express it as .9999.... .  There might be a differrent way of writing this down in a formal fashion though.  I can also guess that there are rules governing the use of infinity that I obviously don't understand.

It does seem to me that this is a semantic argument.  It may be between laymen and math nerds, but it seems to me that the argument is actually an argument of definitions, and not correct and incorrect.

Mathematical proofs don't resolve this argument until everyone agrees to use the same system and understands the rules of the system.

---

### Post by Choad on 2007-02-13
> **muguwmp67 said:**
> I understand this logic, even though I doubt that its anything even close to valid as a formal proof.  

It does explain it to me though.  There is a difference between what I call a 'value' and what I call a 'numeral'

a value is an amount and in these terms, there is a difference between 1 and .999... as long as we believe that it expresses the closest value to 1 without being 1.

A 'numeral' is a representation used in a system that has a series of rules it uses to keep the system consistent and useful.

I can concieve of a value between 0 and 1, closest to 1 without being one and I would express it as .9999.... .  There might be a differrent way of writing this down in a formal fashion though.  I can also guess that there are rules governing the use of infinity that I obviously don't understand.

It does seem to me that this is a semantic argument.  It may be between laymen and math nerds, but it seems to me that the argument is actually an argument of definitions, and not correct and incorrect.

Mathematical proofs don't resolve this argument until everyone agrees to use the same system and understands the rules of the system.
im pretty sure they do proove it. just coz the way we write numbers cant actually write 1/3, we have to say it repeats forever as 0.333... that doesnt mean its not a real number tho

but im no mathematician... fun debate tho lol

---

### Post by muguwmp67 on 2007-02-13
I was just playing with a calculator and now thought of something strange about ,99999999.....

If I multiply ,99999999999.... by 2 I recieve a number that is going to end in an 8.  Does this mean that .999999(infinity)8 is the same as 2?  Or does it mean that we'll never see the 8 because the infinite number of 9's prevents it from coming up, so I'm basically trying to break an essential rule of the universe?

<edit>
I think I found the root my problem.  Calculators are more sophisticated today.  In my days (LED calculators) if you did a 1 / 3 * 3 you would recieve .9999999E.  Today you recieve 1.
<edit>

---

### Post by rai4shu2 on 2007-02-13
> **jdong said:**
> It is true. Rewrite it in terms of limits and recall that C*lim(expr) = lim(C*expr)

Oh, I see. Now it totally makes sense. ;)

* whoosh * #-o

---

### Post by jdong on 2007-02-13
> **Choad said:**
> then surely what you have just said means he was right in saying 0.999... = 1 - (1/infinity)

if 1/infinity = 0, then 1 - 1/infinity = 1, and the 0.999.... thing is 1, so it works...
No, you are mixing limits with values.

0.9999.... is a **LIMIT**. Same with writing any nonterminating value with "..." or "repeating". (One must use an alternative method to express these values without the implication of a limit)

Strictly speaking, 1/infinity is not defined. Arithmetic operations are not defined on infinity -- as it is not a numeric expression. You should've said lim(1/A ) as A approaches infinity, etc.

But yes, lim(1-1/A) as A approaches infinity = 1, so 1-0.000.....1 = 1.

---

### Post by jdong on 2007-02-13
> **Choad said:**
> im pretty sure they do proove it. just coz the way we write numbers cant actually write 1/3, we have to say it repeats forever as 0.333... that doesnt mean its not a real number tho

but im no mathematician... fun debate tho lol
Nobody said that .3333... is not a real number and/or 1/3 is not a real number.

You must agree that .3333.... is an expression that means the limit of the expression that was started, by adding more and more 3's, or 3/10+3/100......

Another way of writing that value is 1/3. 


Same with 0.9999



And a calculator or any machine will be useless for this kind of problem... Calculators and machines calculate based on simplified models of real life.

For most calculators when you type in 1/3 and it shows .33333333333, it is representing an approximation of 1/3 as an N digit decimal approximation, where N is a finite number (if you have a TI-89 or other CAS calc with exact mode, shut up :D)

They are not idealistic real world models. Don't use them to prove anything mathematically :)

---

### Post by jpkotta on 2007-02-13
> **muguwmp67 said:**
> 
It does seem to me that this is a semantic argument.  It may be between laymen and math nerds, but it seems to me that the argument is actually an argument of definitions, and not correct and incorrect.


I think this is the crux of the matter.  Mathematically, 0.999... is DEFINED to be an infinite sum, as jdong has written before.  It is literally another way of writing \sum_{i=1}^\infty \frac{9}{10^i}, which is in turn defined as a limit.  If you want to define it in some other way such that 0.999... != 1, go ahead.  You just have to make sure your definition leads to no contradictions.  Otherwise, learn about limits.

So here's a question: it is possible to make a definition such that 0.999... != 1?

---

### Post by jdong on 2007-02-13
> **jpkotta said:**
> 
So here's a question: it is possible to make a definition such that 0.999... != 1?
Not unless you go around re-inventing number theory. :)

---

### Post by Tuna-Fish on 2007-02-13
> **Choad said:**
> 
1 - 0.000...1 = 1


Actually, no. Because 0.000...1 does not and cannot exist. You cannot shoestring a value at the end of a representation of an infinite series. the 1 at the end would simply never come. no matter what, the last dot in ... is the last symbol in a correct repeating number. now, try 1/infinity, or as someone pointed out, 1/A, A-> infinity. That, you might find, equals zero.

One thing to look at this is to consider how things work out at the actual number line, and realize at the positional number systems we use are just imperfect representations of it. They work quite fine until you bring up the infinite repeating decimals, after that you have exactly two representations for all whole numbers. Zero is a special case, with -0 and +0, the rest are all 1 = 0.999.../2 = 1.999.../3 = 2.999.../...

---

### Post by saulgoode on 2007-02-13
> **Tuna-Fish said:**
> Actually, no. Because 0.000...1 does not and cannot exist. You cannot shoestring a value at the end of a representation of an infinite series. the 1 at the end would simply never come. no matter what, the last dot in ... is the last symbol in a correct repeating number. now, try 1/infinity, or as someone pointed out, 1/A, A-> infinity. That, you might find, equals zero.

But you are only speaking of notational definition. The value of the infinite convergent series, "9/10+9/100+9/1000 ad infinitum" does not exist anymore than 1/infinity exists. The series is not equal to "1", only its limit is -- the ratio is not equal to "0", only its limit.

---

### Post by aktiwers on 2007-02-13
What about this then..  hope its not too offtopic :P
[U][B]
Proff that 1 = 2[/B][/U]

X = Y      (we take X from one site to another)
0 = Y-X    (Now we multiply by 2 on both sites)

0 = 2Y-2X   (This can be rewritten)
0 = 2(Y-X)   (Now when 0 = Y-X as shown on line two, we replace 0 with Y-X)

Y-X = 2(Y-X)  ( Divide with Y-X on both sites)

1 = 2

Now thats something!    (can anyone spot the error?) :P

---

### Post by jdong on 2007-02-13
Oldest trick in the book... division by zero

I loved to embed these in geometry or calc proof homework to sneak in some extra homework points when I'm lazy :)

---

### Post by FuturePilot on 2007-02-13
> **aktiwers said:**
> What about this then..  hope its not too offtopic :P
[U][B]
Proff that 1 = 2[/B][/U]

X = Y      (we take X from one site to another)
0 = Y-X    (Now we multiply by 2 on both sites)

0 = 2Y-2X   (This can be rewritten)
0 = 2(Y-X)   (Now when 0 = Y-X as shown on line two, we replace 0 with Y-X)

Y-X = 2(Y-X)  ( Divide with Y-X on both sites)

1 = 2

Now thats something!    (can anyone spot the error?) :P
Something to do with dividing by 0

---

### Post by jdong on 2007-02-13
> **FuturePilot said:**
> Something to do with dividing by 0

More precisely (Y-X) = 0 and you cannot divide by Y-X.

---

### Post by FuturePilot on 2007-02-13
> **jdong said:**
> More precisely (Y-X) = 0 and you cannot divide by Y-X.
Hehe, I remembered that from Precalc:-)

---

### Post by Motoxrdude on 2007-02-13
Well, as so long we are on the subject of math, here are some of my favorites.
[IMG]http://farm1.static.flickr.com/98/371723041_9f5eb359d4_o.gif[/IMG]
[IMG]http://farm1.static.flickr.com/172/371722924_4828281113_o.jpg[/IMG]

---

### Post by Crashmaxx on 2007-02-13
> **aktiwers said:**
> (Now when 0 = Y-X as shown on line two, we replace 0 with Y-X)


Doesn't work that way. You can only replace Y-X with 0, not the other way around.

So instead:

0=2(Y-X)
0=2(0)
0=0

No problem. Or you can do this:

0=2(Y-X)
0=2Y-2X
2X=2Y
X=Y

And then you are back to square one.

The problem is, that 0 can not explicitly equal (Y-X), its a value representing nothing. So if you at best have:

(Y-X)=2(Y-X) only when (Y-X) equals 0
0=2(0)
0=0

Anyway, more incorrect proofs, and you can't use algebra alone to solve a calculus problem. Trust me, I've tried, but calculus has its own properties that can't be manipulated  or tricked.

So the original problem of .999...=1 is not an arithmetic or algebra problem at all. But an intro calculus one. Its really the limit of an assentope. The graph, nor the function, will never actually be exactly one. But when you approach it, you see it goes to one.

That is really the whole point of calculus, to calculate the equations that algebra can't because they are infinite. Only with its crazy set of tools can you figure out things like the area under a curve.

Basically, if you have no idea what I am talking about, you haven't done, didn't understand, or forgot, calculus.

If you'd like to understand this problem and much more. Teach yourself or take a class in calculus.

If you have realized that since you are not an engineer or in some other career that requires the analyzation of these kinds of problems. Then I recommend not wasting your time. Its a real PITA learning this stuff and the real theory behind it all, is so insane, that I just can even care. Its not practical for daily life, unless you need it or really enjoy pondering such things, just forget it. It VERY tedious.

---

### Post by FuturePilot on 2007-02-13
[IMG]http://media3.guzer.com/pictures/findx.jpg[/IMG]
:lolflag:

---

### Post by euler_fan on 2007-02-14
EDIT: This is basically one of the proofs given in the wikipedia article GeneralZod cites on page one of this thread, but in case you don't want to read their better typeset proofs, here goes my version:

As a math major, please indulge my urge to prove .99 repeating = 1.

Sorry if this sounds a bit stuffy or anything. I have no intention to offend.

Show .999 repeating = 1.

( 0 ) We are working in the real numbers.
( 1 ) Note any real number can be approximated by two other numbers, one of which is above and the other below it.
( 2 ) Define two sequences, a_n and b_n such that a_n <= a number, b_n >= the same number, and each successive interval between a_n and b_n gets smaller as n increases.
( 3 ) Let the infimum of b_n - a_n =0.
( 4 ) By theorem (based on the above hypotheses), the number between a_n and b_n for all n is unique. I provide a citation below.
( 5 ) let a_n be {.9, .99, .999, . . . , .99 repeating} and b_n be {1.1, 1.01, . . . , 1.001 repeating}.
( 6 ) Observe as the limits of both sequences are 1, the difference of their limits is 0, and thus (3) is satisfied.
( 7 ) The only number between them, which is the number they converge to, is 1.
( 8 ) By the theorem cited above, 0.999 . . . =1=1.0 . . . 01

Ergo, 0.99 repeating = 1.

This is all basically strait of of Bartle's Intro. to Real Analysis section 2.5. The theorem I cite is numbered as 2.5.4, and uses 2.5.3 as a starting point (Bartle's numbering).

Sorry, but while there are many people out there who do not like this fact, it is in fact proven as above. I could also make b_n = {1.0, 1.00, 1.000,  . . . } , but I thought I would use a slightly less controversial sequence for the proof. It wouldn't matter either way.

---

### Post by -Phi- on 2007-02-14
I always liked proofs that don't involve series and subscripts and calculations. Especially if they are short and make pictures in my head. So for those of you that still aren't convinced, here goes:

Real numbers are complete, meaning that between any two distinct real numbers there is a third real number. (Sidenote: Integers are not complete. There is no whole number between 1 and 2)

So for 0.9999... and 1 to be distinct real numbers, you need to find a real number larger than 0.9999... and smaller than 1.

And there isn't one :)

- Phi

---

### Post by muguwmp67 on 2007-02-14
> **-Phi- said:**
> 
So for 0.9999... and 1 to be distinct real numbers, you need to find a real number larger than 0.9999... and smaller than 1.

And there isn't one 


<lightbulb goes on>
wow...trippy.

I think I'm gonna go listen to the grateful dead and stare at my [electricsheep]("http://www.electricsheep.org/") for a while now.

---

### Post by steven8 on 2007-02-14
> **muguwmp67 said:**
> <lightbulb goes on>
wow...trippy.

I think I'm gonna go listen to the grateful dead and stare at my [electricsheep]("http://www.electricsheep.org/") for a while now.

I wonder.  Do mathematicians dream of electric sheep?

---

### Post by rai4shu2 on 2007-02-14
This is what happens when you muck about with infinities.

---

### Post by v8YKxgHe on 2007-02-14
Like it says in the Wikipedia article:

0.333 = 1/3
so, 0.666 = 2/3
therefore, 0.999 = 3/3 = 1

---

### Post by jdong on 2007-02-14
> **Crashmaxx said:**
> 
The problem is, that 0 can not explicitly equal (Y-X), its a value representing nothing. So if you at best have:


The problem is that you cannot divide by zero, and whenever you have to:

(1) Divide by a variable, you must set a domain limit on your answer that the value isn't zero
(2) Multiply by a variable and it HAPPENS to be zero, you have just lost a bunch of potential solutions.

So, the correct answer to a * x = b,  is not b/a, but b/a if a != 0

---

### Post by saulgoode on 2007-02-14
> **-Phi- said:**
> So for 0.9999... and 1 to be distinct real numbers, you need to find a real number larger than 0.9999... and smaller than 1.
there isn't one :)

My contention is that 0.999(repeating) is not a real number. Infinity is not a real number and once you have introduced "infinity" into an equation, standard algebra no longer applies. Proofs involving equations incorporating infinity are just as invalid as proofs incorporating division by zero.

Would you say that 1.00(repeating)1 is equal to 1? I am not talking about mathematical notation but the concept of a number greater then 1 by an infinitely small amount -- just as 0.999(repeating) is about a number less than 1 by an infinitely small amount.

Because if 0.999(repeating) is a real number and 1.00(repeating)1  is real number then between them you can find the real number 1 and they would, using your test, be distinct numbers. But then how could 0.999(repeating) be identical to 1 and 1.00(repeating)1 be identical to 1 -- it is the same concept, just the other side of the point -- and yet they be distinct from each other?

---

### Post by jdong on 2007-02-14
0.999repeating is a number because 0.999repeating is a limit expression, the result of which is **ONE**. The 'infinity' has been resolved by the implicit limit function and is no longer a problem.

---

### Post by ljpm on 2007-02-14
OK so I get that 1 = 0.99999 repeating.

Now can someone explane what the squareroot of -1 is. That one has always baffled me.

---

### Post by euler_fan on 2007-02-14
> **saulgoode said:**
> My contention is that 0.999(repeating) is not a real number. Infinity is not a real number and once you have introduced "infinity" into an equation, standard algebra no longer applies. Proofs involving equations incorporating infinity are just as invalid as proofs incorporating division by zero.

First, you can throw out 0.999 repeating being real if you throw out the completeness axiom. But then you can never be sure if a function, as defined in the real numbers presently, is continuous (in the epsilon-delta sense).

The proof I provided is not algebraic, but a proof from calculus. If you go to the link GeneralZod provided, there is in it a proof from algebra, whereas the others are all from analysis (calculus). If proofs not in violation of another existent rule (and thus invalid by default) involving infinity are invalid, provide one which incorporates infinity and is invalid for the standard real numbers.

If you reject the usage of limits (or completeness, as you want to do), especially as certain quantities go to zero in denominators (zero) or other quantities become infinite (integrals, e, taylor series approximation, the proof for the existence and uniqueness of solutions to differential equations), you throw out many things.

Incidentally, the limit going to zero in the denominator of the limit quotient is there explicitly because we cannot divide by zero and are getting around it using continuity and completeness in the limit. You're entitled to do so, but please note that the computer you used to type your post relies on much of that mathematics.

> **saulgoode said:**
> Would you say that 1.00(repeating)1 is equal to 1? I am not talking about mathematical notation but the concept of a number greater then 1 by an infinitely small amount -- just as 0.999(repeating) is about a number less than 1 by an infinitely small amount.

As has been proven for the real numbers, for two decimals to be infinitely close together really means they are representing the same number. One of three thing would have to change for your argument to make sense: either we change one of the axioms of the real numbers or we change our system of formal logic or we have to find rigorous fault with the existing proofs. You are more than welcome to, but as a working mathematical system, you would be more or less on your own with a very small group of professional mathematicians.

> **saulgoode said:**
> Because if 0.999(repeating) is a real number and 1.00(repeating)1  is real number then between them you can find the real number 1 and they would, using your test, be distinct numbers. But then how could 0.999(repeating) be identical to 1 and 1.00(repeating)1 be identical to 1 -- it is the same concept, just the other side of the point -- and yet they be distinct from each other?

That's the point: THEY ARE NOT DISTINCT. I suggest reading the proof of the theorem. It proceeds be showing that under the conditions which are satisfied by .99 repeating and 1.0 . . . 1, the two numbers "become the same" in the limit, indicating they are both, in the limit, 1.

All I really want if for people to understand they can throw out this results, but only if they throw out everything else that builds on it or that was built on something that had to be changed in order to prevent the result from being valid for the number system in question.

---

### Post by jdong on 2007-02-14
It simply is defined as i, and a branch of mathematics has evolved from that fundamental definition.

There's nothing to get. Just as why 1+1 is defined as 2, or why 1 is defined as 1 and not as 2....

---

### Post by saulgoode on 2007-02-14
> **jdong said:**
> 0.999repeating is a number because 0.999repeating is a limit expression, the result of which is **ONE**. The 'infinity' has been resolved by the implicit limit function and is no longer a problem.

But you are merely supplying a notational definition and your proof only validates the notation. I suspect that the original poster intended 0.999(repeating) to indicate a number which was "defined" by an infinite number of "9"s after the decimal point.

A limit of an infinite convergent series is not equal to the series itself; any edict which pronounces such an equality is merely assuming a premise for the sake of convenience and proofs which assert the equality of a limit with a real value are likewise a convenience and do not represent an actual statement about the series itself.

---

### Post by Nonno Bassotto on 2007-02-14
> **-Phi- said:**
> Real numbers are complete, meaning that between any two distinct real numbers there is a third real number. (Sidenote: Integers are not complete. There is no whole number between 1 and 2)


Just to be precise. Completeness of the real is not the property you stated, which is also true for example in the rationals. Completeness means (it is one of the possible definitions) that every bounded subset of the reals has a least upper bound.

---

### Post by jdong on 2007-02-14
> **saulgoode said:**
> But you are merely supplying a notational definition and your proof only validates the notation. I suspect that the original poster intended 0.999(repeating) to indicate a number which was "defined" by an infinite number of "9"s after the decimal point.

A limit of an infinite convergent series is not equal to the series itself; any edict which pronounces such an equality is merely assuming a premise for the sake of convenience and proofs which assert the equality of a limit with a real value are likewise a convenience and do not represent an actual statement about the series itself.

Ok, now we are just arguing semantics of what equality means....

Are you saying that if I define A as 3+1 that I cannot later say A =4 because A is defined as the expression 3+1 and not the number 4?

---

### Post by aktiwers on 2007-02-14
> **ljpm said:**
> OK so I get that 1 = 0.99999 repeating.

Now can someone explane what the squareroot of -1 is. That one has always baffled me.

The Squareroot of -1 = i 
i = Imaginary number. 

More I cant explain, but im sure other can :)

---

### Post by saulgoode on 2007-02-14
> **jdong said:**
> Ok, now we are just arguing semantics of what equality means....

Are you saying that if I define A as 3+1 that I cannot later say A =4 because A is defined as the expression 3+1 and not the number 4?

No, I am talking about infinite convergent series; not finite real values. 

I am saying that proving that the limit of 1/x as x approaches infinity equals zero does not prove that 1/infinity is equal to zero. 1/infinity is not equal to zero and it never will be equal to zero. Would "mathematicians" argue otherwise? 

By the same token, "1" is not equal to the infinite series 9/10+9/100+9/1000+~~~, where the tildes represent extending the terms to infinity (soas to avoid any confusion about mathematical interpretations of ellipses). The *limit* may equal "1", but not the series.

---

### Post by Sqwishy on 2007-02-14
> **jdong said:**
> Are you saying that if I define A as 3+1 that I cannot later say A =4 because A is defined as the expression 3+1 and not the number 4? But A = 3+1 and 3+1 we all know is 4 thus A = 4

---

### Post by TravisNewman on 2007-02-14
You just had to post this didn't you? ;)
I had mentioned to Adamant in #ubuntuforums that I wasn't about to post this to the cafe because of the flamewar that would ensue.

Luckily no flamewar yet.
For the record.... I share saulgoode's feelings on the subject.

---

### Post by jdong on 2007-02-14
> **Sqwishy said:**
> But A = 3+1 and 3+1 we all know is 4 thus A = 4

A=.999repeating which we all obviously know = 1 and thus A = 1.

---

### Post by jpkotta on 2007-02-14
> **saulgoode said:**
> No, I am talking about infinite convergent series; not finite real values. 

I am saying that proving that the limit of 1/x as x approaches infinity equals zero does not prove that 1/infinity is equal to zero. 1/infinity is not equal to zero and it never will be equal to zero. Would "mathematicians" argue otherwise? 

By the same token, "1" is not equal to the infinite series 9/10+9/100+9/1000+~~~, where the tildes represent extending the terms to infinity (soas to avoid any confusion about mathematical interpretations of ellipses). The *limit* may equal "1", but not the series.

As I said before, 0.999... is defined to be the limit.  It is literally another way of writing the infinite series, which is a limit.  The infinite series is different from each of the series that make up the limiting sequence of the infinite series.  The infinite series and the limit are the same thing; infinite series are defined in terms of limits.

---

### Post by jdong on 2007-02-14
An infinite series is defined to be the limit of the series as the # of terms to sum approaches infinity.

---

### Post by CheshireMac on 2007-02-14
> **Adamant1988 said:**
> .9999 (repeating) actually **DOES** equal 1?
No.  0.999999999999 will never equal 1 . . .no matter how many places past the decimal you take it. 1 is equivalent to 1.000, and therefore is not 0.999 in any sense. But it's close (just a decimal place away. ~LOL~)

---

### Post by v8YKxgHe on 2007-02-14
> **CheshireMac said:**
> No.  0.999999999999 will never equal 1 . . .no matter how many places past the decimal you take it. 1 is equivalent to 1.000, and therefore is not 0.999 in any sense. But it's close (just a decimal place away. ~LOL~)

0.333 = 1/3
0.666 = 2/3
0.999 = 3/3
3/3 = 1

That's all I understand, none of this techno-wango-jango these last pages have been!

---

### Post by jdong on 2007-02-14
Can we call this closed with a resolution of like:

> 
Despite numerous algebraic, calculus, and geometric proofs of the statement, some still adamantly insist that 0.9repeating !=1


I think all the ways of proving and denying this have been discussed. Let's all go back to something more productive.

---

### Post by Adamant1988 on 2007-02-14
> **jdong said:**
> Can we call this closed with a resolution of like:



I think all the ways of proving and denying this have been discussed. Let's all go back to something more productive.


I don't know.. I'm still not convinced...

---

### Post by saulgoode on 2007-02-14
> **jpkotta said:**
>  The infinite series and the limit are the same thing;** infinite series are defined in terms of limits**.
(emphasis mine)

All you are doing is *stipulating* that they are the same thing. You haven't *proved* that the limit and the series are same thing; you have *defined* them to be the same thing. 

If you can prove that infinity is a real number, I could see where your proofs might be valid. But your proof is only valid if I accept your presupposition that 0.33(repeating) equals 1/3. It does not, for the same reason that 0.99(repeating) does not equal 1. 

You have not proved that an infinite series is a real number, you have stipulated that it is one. Unless you prove this, you are engaging in a logical fallacy known as the argument presupposing its conclusion.

NOTE: I am voicing my comments with great respect towards those of the opposing view. The language of polemics can often come across harsher than the original intent.

---

### Post by qalimas on 2007-02-14
I'm taking AP Calculus this year, and we've discussed this.  Limits are something that is never reached, so while the limit is 1, .9 repeating will never become one, it will only get closer and closer, never quite making it, because if it made it on a graph, an asymptote would loose definition.

That's my understanding of it, .9 repeating != 1

---

### Post by jdong on 2007-02-14
No, no, no -- you can **never reach 0.9 repeating** -- you can only get infinitely close to representing 0.9 repeating. That's where the limit part plays in.

---

### Post by qalimas on 2007-02-14
So if .9 repeating is never reached, then neither is 1, right :confused:

*cluelessly wanting to learn*

---

### Post by unbuntu on 2007-02-14
**YES, 0.9999..... == 1**

The definition of equality is this:

```

A==B if and only if |A-B|<epsilon for every small positive number epsilon, 

```

Since 0.999... is infinitly repeating, it's always true that |1-0.999...|<epsilon for every possible epsilon, therefore they are equal.  For those who are still incredulous, read some books on the theory of calculus.

---

### Post by shining on 2007-02-14
> **saulgoode said:**
> (emphasis mine)

All you are doing is *stipulating* that they are the same thing. You haven't *proved* that the limit and the series are same thing; you have *defined* them to be the same thing.



The serie and the limit aren't the same thing. The sum of a serie is a limit.

> 
If you can prove that infinity is a real number, I could see where your proofs might be valid. But your proof is only valid if I accept your presupposition that 0.33(repeating) equals 1/3. It does not, for the same reason that 0.99(repeating) does not equal 1. 


I remember using the notation (R U inf), so infinity isn't generally considered as a real number, but that doesn't matter.
The presupposition isn't that 0.33(repeating) equals 1/3.
It's that 0.33(repeating) is interpreted as the sum of the following serie :
3/10 + 3/100 + .... + 3/(10^N)
Is this your only problem, the interpretation of 0.33(repeating) ?

Maybe it would be best to just avoid this kind of notation, to avoid any confusion.

---

### Post by jdong on 2007-02-14
> **shining said:**
> The serie and the limit aren't the same thing. The sum of a serie is a limit.

Uhh, yes they are. A series is a sum of a sequence. An infinite series is defined as the limit of the series as the number of summation terms approaches infinity.

---

### Post by euler_fan on 2007-02-14
> **jdong said:**
> Can we call this closed with a resolution of like:



I think all the ways of proving and denying this have been discussed. Let's all go back to something more productive.

I second this. It has been hashed over enough by now.

---

### Post by shining on 2007-02-15
> **jdong said:**
> Uhh, yes they are. A series is a sum of a sequence. An infinite series is defined as the limit of the series as the number of summation terms approaches infinity.

I'm not sure you are denying, what I said, are you?
Isn't a series a sum of a finite sequence? And so, it isn't a limit ?

---

### Post by jdong on 2007-02-15
[http://en.wikipedia.org/wiki/Series_%28mathematics%29](http://en.wikipedia.org/wiki/Series_%28mathematics%29)

No, a series is the sum of a sequence -- finite or infinite terms. An infinite series is a special instance of a series, where the number of terms to sum to is infinite.

The value of an infinite series is:

(A) : Undefined if the limit of the partial sum S(n) as n -> infinity is nudefined
(B) : Equal to the limit of the partial sum S(n) as n-> infinity otherwise

---

### Post by Adamant1988 on 2007-03-18
I'm sorry Jdong I'm just still not convinced...

---

