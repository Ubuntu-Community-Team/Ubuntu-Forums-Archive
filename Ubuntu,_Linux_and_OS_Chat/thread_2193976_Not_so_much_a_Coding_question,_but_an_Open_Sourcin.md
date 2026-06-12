---
title: "Not so much a Coding question, but an Open Sourcing question."
date: 2013-12-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Orange_Ribbon on 2013-12-15
I have been doing research on the Boolean Satifiability problem,  and I found two new and interesting (If you can nerd out on Boolean Algebra like me) way of tackling the problem.  I am currently writing an article about my new Algorithms.

What is the best way for sharing the code for my little proof of concept version.  I am very green when it comes to programming and about to graduate so I need something easy and bully free.   My proof of concept only works for functions that contain 30 or less literals, and my input/output is bonkers because I wanted it to work with Wolfram Alpha to check answers.  

The other question is,  is there a good way to capitalize on my thing without hoarding the knowledge of it for myself?  I don't have the money free existence some ideologues have.  I want to get this into the wild and see what happens but I am also 20 weeks out from graduating with my BS in Computer Science and really want to have a life with an apartment and dinner parties instead of my weird cloistered student life.

---

### Post by MG&amp;TL on 2013-12-15
> I have been doing research on the Boolean Satifiability problem,  and I found two new and interesting (If you can nerd out on Boolean Algebra like me) way of tackling the problem.

I *love* boolean algebra, and SAT is a very interesting problem. :-) Can you tell me a little about them?

> I am currently writing an article about my new Algorithms.

Good for you! Would you be able to e-mail or PM me them when you're finished?

> What is the best way for sharing the code for my little proof of concept version.

Stick the source code onto a source-code hosting site like GitHub, then if you think it's worth other people's attention, bring their attention to it like you usually would (that is, ask them politely if they'd mind taking a look).

> I am **very green when it comes to programming and about to graduate** so I need something easy and bully free.

...what? I mean, no disrespect here, but how do you manage to almost complete a degree in Computer Science and be 'green with programming'?!

> My proof of concept only works for functions that contain 30 or less literals, and my input/output is bonkers because I wanted it to work with Wolfram Alpha to check answers.  

This would be the advantage of open-sourcing your code. That way, interested parties (such as myself) can edit your code to make it better, and then everyone benefits.

> The other question is,  is there a good way to capitalize on my thing without hoarding the knowledge of it for myself?  I don't have the money free existence some ideologues have.  I want to get this into the wild and see what happens but I am also 20 weeks out from graduating with my BS in Computer Science and really want to have a life with an apartment and dinner parties instead of my weird cloistered student life.


Frankly, I don't think your idea (unless you can solve the problem in non-NP time, in which case that's a *whole* different can of worms) is going to be valuable enough to live off - it might be academically interesting, but I don't forsee any way that people would use your algorithms 'in real life'. I think your best bet to capitalise on this would be to release your ideas publically and academically, and hope that someone is impressed enough to hire you as a researcher.

---

### Post by tgalati4 on 2013-12-15
Start a blog on Wordpress or on your own web page, describe the problem and your novel approach to the problem.  For programming help, you need to write "pseudo" code.  Just write out what needs to be done and then others can chip in to put the code together.  You can post your article as a PDF for review on the blog.  If you get enough feedback (especially from peers) then publish it in an appropriate journal.

I know nothing about SAT, but the wiki page has a "talk" section that you could contribute to: [http://en.wikipedia.org/wiki/Boolean_Satisfiability](http://en.wikipedia.org/wiki/Boolean_Satisfiability)

Two Haikus for your dilemma:

True or false--Who knows?
Weird, cloistered dinner parties--
Shaping the future?

I have a Degree.
Computer Science--B.S.
Hello World--Help Me.

---

### Post by Orange_Ribbon on 2013-12-17
> **MG&TL said:**
> 
...what? I mean, no disrespect here, but how do you manage to almost complete a degree in Computer Science and be 'green with programming'?!


Well I have only had 2 internships where my main job was programming.  There is a huge difference between labs and having the professor there as a safety net vs being in an office and hoping someone on Stack Overflow has had the same problem.  

Sure I'll send you my article when I am done writing it.  What is really cool about the first one is,  it isn't Big-O 2 raised to the amount of literals.  Instead it is roughly 2 raised to either the amount of clauses or the second largest amount of missing literals.  It actually handles if all the clauses are missing 5 or less literals in Big O of (Clauses ^ 3) * Literals. 

The second one isn't as cool.  It basically uses a ternary tree and depth first search,  so at it's worse if has 3^Clauses (This is a 3 Sat algorithm)  The neat thing though is you can cheat with threading.  The only data that needs to be shared is if we found a combination. 


tgalati4  those are really great Haikus.

---

### Post by MG&amp;TL on 2013-12-17
> **Orange_Ribbon said:**
> Well I have only had 2 internships where my main job was programming.  There is a huge difference between labs and having the professor there as a safety net vs being in an office and hoping someone on Stack Overflow has had the same problem.  

Sure I'll send you my article when I am done writing it.  What is really cool about the first one is,  it isn't Big-O 2 raised to the amount of literals.  Instead it is roughly 2 raised to either the amount of clauses or the second largest amount of missing literals.  It actually handles if all the clauses are missing 5 or less literals in Big O of (Clauses ^ 3) * Literals. 

The second one isn't as cool.  It basically uses a ternary tree and depth first search,  so at it's worse if has 3^Clauses (This is a 3 Sat algorithm)  The neat thing though is you can cheat with threading.  The only data that needs to be shared is if we found a combination. 


tgalati4  those are really great Haikus.

Ah, okay. I think you're probably better at programming than you make yourself out to be then. :-)

I look forward to it! Your algorithms sound cool.

---

