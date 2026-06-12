---
title: "About programming"
date: 2007-07-27
forum: The Cafe
---

### Post by kristalsoldier on 2007-07-27
Hi...

I have a question that is related to computing/ programming and was not sure where to post it. So, if this post is out of place - Mods/ admin, will you please move it to where you think it is relevant? Thanks.

OK. Here is the question:

I have no mentionable background in programming. I have heard it being said (and have read) that programs can be and should be 'elegant'. What does this mean? What does 'elegance' mean in the context of computer programs?

Thanks and apologies for the obtuseness of this request!

---

### Post by igknighted on 2007-07-27
There is a proper, thorough method of doing things in computer programming, and then there is a "quick and dirty" way.  Think about how many web developers are standards compliant and build sites to the W3C spec, but some just "build for IE".  The W3C compliant site is elegant, while the "made for ie" site is taking the lazy shortcut route.

Another aspect of an elegant program is a lack of excess code.  While one could certainly develop very elaborate algorithms to create a simple counting program, the simplest algorithim that does the job properly is always the best, or most elegant choice.

---

### Post by LaRoza on 2007-07-27
> **kristalsoldier said:**
> 
I have no mentionable background in programming. I have heard it being said (and have read) that programs can be and should be 'elegant'. What does this mean? What does 'elegance' mean in the context of computer programs?

Thanks and apologies for the obtuseness of this request!

"Elegant" can also be undesireable, like with factorials. There are two short ways to calculate factorials, one uses loops and another uses recursion. The recursive method is very elegant, but has a higher overhead than a loop. If that doesn't make sense, don't worry. Basically "elegant" is finding a short way to do something that looks more complicated.

---

### Post by rjfioravanti on 2007-07-27
> **LaRoza said:**
> "Elegant" can also be undesireable, like with factorials. There are two short ways to calculate factorials, one uses loops and another uses recursion. The recursive method is very elegant, but has a higher overhead than a loop. If that doesn't make sense, don't worry. Basically "elegant" is finding a short way to do something that looks more complicated.

I think elegant is more something that employs good design and best practices... part of which includes readability. Somebody writing very obscure but highly efficient C code is not writing elegant code

---

### Post by LaRoza on 2007-07-27
> **rjfioravanti said:**
> I think elegant is more something that employs good design and best practices... part of which includes readability. Somebody writing very obscure but highly efficient C code is not writing elegant code

```

unsigned int factorial(unsigned int number)
{
    if(number == 1)
    {
        return 1;
    }
    else
    {
        number *= factorial(n-1);
        return number;
    }
}
```
Easy to follow, easy to read, solves the problem, is elegant, but is not the best or most desireable solution.

---

### Post by mostwanted on 2007-07-27
I feel this well-known essay is somehow appropriate:

[http://www.paulgraham.com/hp.html](http://www.paulgraham.com/hp.html)

---

### Post by kristalsoldier on 2007-07-27
> **LaRoza said:**
> "Elegant" can also be undesireable, like with factorials. There are two short ways to calculate factorials, one uses loops and another uses recursion. The recursive method is very elegant, but has a higher overhead than a loop. If that doesn't make sense, don't worry. Basically "elegant" is finding a short way to do something that looks more complicated.

Hmm...in other words, the recursive method is less efficient that the loops?

It would also seem that common standards is an important thing. But this also raises a question:

Is there a specific 'logic' of programming?

Thanks

---

### Post by rjfioravanti on 2007-07-27
> **LaRoza said:**
> [code]

Easy to follow, easy to read, solves the problem, is elegant, but is not the best or most desireable solution.
ok i think we are in agreement, i was just confused because you said before that looking more complicated is better, but now youre saying more readable is better

---

### Post by kristalsoldier on 2007-07-27
> **mostwanted said:**
> I feel this well-known essay is somehow appropriate:

[http://www.paulgraham.com/hp.html](http://www.paulgraham.com/hp.html)

Thanks! It looks very interesting! Did not know of it.

---

### Post by LaRoza on 2007-07-27
> **kristalsoldier said:**
> Hmm...in other words, the recursive method is less efficient that the loops?

It would also seem that common standards is an important thing. But this also raises a question:

Is there a specific 'logic' of programming?

Thanks
The recursive method is good, but it uses too much memory and doesn't use the CPU effectively, the logic is fine.

For programming, the only choices you can make are, in psuedo code:

IF *somethingIsTrue* THEN *doThis* OTHERWISE *doThis*

The only "real" values are TRUE and FALSE, everything is based off that.

---

### Post by Foxmike on 2007-07-27
I am no programmer.  However, I am very interested into the topic.  I used to do some bash/posix-sh/gawk scripting.  As well, I used to read some C programming books and ended up reading Python documentation.  I must say that the Python way to code seems to be very elegant: Good self-documentation mechanisms, code indentation to make reading clear, nice tweaks you can do with code.  It might be less efficient than C, but to me it looks very elegant.

As of scripting, I tend sometimes to re-open a script and end to re-write it completly for it to look more elegant with what I have learned.

I also think that an elegant code is a code that can easily grow up and evoluate, as well as being re-used: being modular, using good variables instead of hard-coded informations, for example.

That was my 2 cents...:)

---

### Post by LaRoza on 2007-07-27
> **Foxmike said:**
> 
I also think that an elegant code is a code that can easily grow up and evoluate, as well as being re-used: being modular, using good variables instead of hard-coded informations, for example.
That was my 2 cents...:)

Good 2 cents!

Python and C are different, but you can use the same style, so Python enforces readability and C doesn't but all programmers should write clean code.

---

### Post by kristalsoldier on 2007-07-27
That bit about the If/ Then statement was enlightening. This holds true of all programming work? As a side note - If/ Then is not the same as the Either/ Or binary is it?

BTW, if you are wondering why I am asking these questions, it has relevance to a piece of writing that I am currently engaged in.

Evolutionary programming sounds grand - though I am sure I am misunderstanding it...perhaps I am emphasizing too much on the 'evolutinary' part!

---

### Post by popch on 2007-07-27
> **kristalsoldier said:**
> What does 'elegance' mean in the context of computer programs?

Elegant - when about programming - means 'least awkward' or 'least clumsy'.

Elegant programs reflect in their structure (or in other means employed) the problem to be solved.  The 'recursive' example which calculates the factorial of a number is a good example.

By the way, there are programming languages where the elegant (recursive) solution is, in fact, more efficient and less wasteful of computer resources than the plainer looping one.

---

### Post by kristalsoldier on 2007-07-27
> **popch said:**
> Elegant - when about programming - means 'least awkward' or 'least clumsy'.

Elegant programs reflect in their structure (or in other means employed) the problem to be solved.  The 'recursive' example which calculates the factorial of a number is a good example.

By the way, there are programming languages where the elegant (recursive) solution is, in fact, more efficient and less wasteful of computer resources than the plainer looping one.

How so?

---

### Post by mangar on 2007-07-27
scim

---

### Post by popch on 2007-07-27
> **kristalsoldier said:**
> How so?

This takes two conditions
one: recursion is an elementary construct of the language, and the language (which means, of course, the implementation) has been optimized towards that end
two: branching back to a particular place within the program is - within the particular language - not a naturally or elegantly supported way of transferring control

Prolog comes to mind. I rather suspect that languages derived from LISP could behave in a similar way.

---

