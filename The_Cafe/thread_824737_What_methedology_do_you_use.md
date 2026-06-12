---
title: "What methedology do you use?"
date: 2008-06-10
forum: The Cafe
---

### Post by tbrminsanity on 2008-06-10
I was lucky enough to go to a IT conference a few weeks ago and one of the main workshops was about agile development.  Well I've decided to try to make most of my projects agile (excluding projects were unit testing is irrelevant).  Before I did most of my programming in a sort of prototype/waterfall style of development.  This worked through University but I see why some of my projects failed.

What methodologies to you use and why?

---

### Post by _DD_ on 2008-06-10
Well I have no method or structure when I'm doing stuff :D

With the little bit of programming/scripting I do (a bit of C and quite a bit of PHP), I'll dive into a small project at completely the wrong angle, do things in completely illogical orders, then get to the end and find that my botched up logic doesn't allow for modifications at which point I start getting frustrated and everything falls apart.

Pretty much this happens...
[IMG]http://imgs.xkcd.com/comics/goto.png[/IMG]

Ah well, I'm only 16; I'll learn :p

---

### Post by tbrminsanity on 2008-06-10
> **_DD_ said:**
> Ah well, I'm only 16; I'll learn :p

Here is a good starting point:

[http://csss.cs.uregina.ca/articles/Test_Driven_Development](http://csss.cs.uregina.ca/articles/Test_Driven_Development)

---

### Post by KingTermite on 2008-06-10
I chose POC, though I'm not 100% sure that fits.

My experience has led me to the path of
1) DESIGN FIRST (good code does not happen "ad hoc")
2) Break down into small functional units so complexity is small
3) Unit test each functional unit
4) Assemble units (using the aforementioned design)
5) Test larger units until entire system is tested

And anywhere you can use some XP (Extreme Programming) in there will only help. XP is one of the best techniques I've ever used.

---

### Post by sonicb00m on 2008-06-10
I find as long as you use good classes you don't have to be over the top about methods. It's nearly impossible to write a good plan and stick to it without spending 99% of time on planning.

Things never work out as you plan. Ever :lolflag:

---

### Post by KingTermite on 2008-06-10
> **sonicb00m said:**
> I find as long as you use good classes you don't have to be over the top about methods. It's nearly impossible to write a good plan and stick to it without spending 99% of time on planning.High quality software is pretty much that way.

75% time spent doing software architecture and detailed design. By the time you get to code, it's almost translation and not much more. If you use a good UML tool you could even have it generate most of the skeleton code for you.

**Edit:

For the record...this is primarily what distinguishes a "software engineer" from a "programmer". That "design" is what engineering is all about. Anybody can pick up a C++ for Dummies book and be a "programmer".

---

### Post by JohnSearle on 2008-06-10
Sorry, just had to mention...

"Meth**o**dology" not "meth**e**dology"

And yes, I realize English isn't everyone's first language. For some reason this mistake just urged me into mentioning. :D

- John

---

### Post by tbrminsanity on 2008-06-10
@JohnSearle

I wish Firefox would spell check the title bar and poll questions.  I'm sure there is more then one spelling error in it.  But your right English isn't my first language, its Bad English ;) .


I've never tried XP myself but I'm told that Agile is very similar (just more testing in Agile).  Both methodologies have similar goals (get code to the customer quickly so you can get feed back).

@KingTermite

Just out of curiosity, how do you write your unit tests?  Do you write the test to test functionality you've written or do you write your tests first and try to get your code to pass the tests?

---

### Post by KingTermite on 2008-06-10
> **tbrminsanity said:**
> @KingTermite

Just out of curiosity, how do you write your unit tests?  Do you write the test to test functionality you've written or do you write your tests first and try to get your code to pass the tests?

Well a little of both.

When we have the man power on project, both are developed simultaneously by different team members. The whole "IV&V" (Independent Verification & Validation) concept.

If we don't have the man power, I've been both methods used (write test before or after). However, its "understood" that test written after shouldn't be catered to how you know the module works, but to how it "should" work. Theory is great, but nobody makes it perfect in practice "all the time".

I know from my experience, test code has typically taken about twice as long as the development code. I remember one of my 1st projects was to write some UART drivers using an abstract factory pattern and develop the drivers on about 4 different embedded platforms. That was great and took about 3 months. 

Then I had to write the test code. No advice was given, but it only made sense to use abstract factory for the test code was well, which I did to test all platforms. That test code took me about 5 months.

---

### Post by cardinals_fan on 2008-06-10
[IMG]http://www.dilbert.com/dyn/str_strip/000000000/00000000/0000000/000000/00000/1000/100/1791/1791.strip.print.gif[/IMG]

---

### Post by lisati on 2008-06-10
I wonder if "Ad-hoc procedural with spaghetti sauce" is a valid name for a methodology.

---

### Post by bobbocanfly on 2008-06-10
I braindump a load of dodgy, sorta functional code. Then i optimise it and make it a bit better. Then i realise its missing functionality so just hack that in, leaving me with dodgy code. Then i try and optimise that but give up.

I really should plan my code.

---

### Post by tbrminsanity on 2008-06-11
> **cardinals_fan said:**
> [IMG]http://www.dilbert.com/dyn/str_strip/000000000/00000000/0000000/000000/00000/1000/100/1791/1791.strip.print.gif[/IMG]

Wow that is sooooo wrong!  But so Dilbert.  Stupid thing is I can see some bosses saying things like that.

---

### Post by BobLand on 2008-06-11
A lot of this depends on where you are coding.  If you are coding for a project that shares code between sites then you must follow very strict guidelines otherwise you'll be out on the street.

If you're coding for yourself then it may not matter.  Personally, I've always had to use the "waterfall" because that was the methodology in every company I worked for -- all financial multinationals.

Code wise, I always stub out so I can track logically.  Next, decide on reuse then fill in the blanks.  Testing is done at every level and for every change.

Make judicious use of comments.  Notes such as "I thought this was a good idea" serve no purpose.  Just explain what the code does and any gotchas.

That's the general idea...
bobland

---

### Post by cardinals_fan on 2008-06-11
> **tbrminsanity said:**
> Wow that is sooooo wrong!  But so Dilbert.  Stupid thing is I can see some bosses saying things like that.
I **LOVE** Dilbert.  I read it every day.

---

### Post by tbrminsanity on 2008-06-12
> **BobLand said:**
> A lot of this depends on where you are coding.  If you are coding for a project that shares code between sites then you must follow very strict guidelines otherwise you'll be out on the street.

If you're coding for yourself then it may not matter.  Personally, I've always had to use the "waterfall" because that was the methodology in every company I worked for -- all financial multinationals.

Code wise, I always stub out so I can track logically.  Next, decide on reuse then fill in the blanks.  Testing is done at every level and for every change.

Make judicious use of comments.  Notes such as "I thought this was a good idea" serve no purpose.  Just explain what the code does and any gotchas.

That's the general idea...
bobland

I disagree.  My current client requests that we use a waterfall methodology and while the overall project run in that fashion but my personal code is Agile and my personal development is Agile.

---

