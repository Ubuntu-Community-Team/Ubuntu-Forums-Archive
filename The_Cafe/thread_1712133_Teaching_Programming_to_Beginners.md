---
title: "Teaching Programming to Beginners"
date: 2011-03-22
forum: The Cafe
---

### Post by P1C0 on 2011-03-22
I'll be teaching a course in Introduction to Computer Science to a **Seminary** for the next few weeks, and I am trying to find out what programming paradigm and language should I use in order to introduce them a bit to very simple facts of programming.

"Seminary" is bold because I want to emphasize the fact that the course is planned to be kept really really simple. Most of them probably don't even know how to use a computer. We will teach them that too.

At first I thought about python, but the professor was like "wtf" and he prompted me to look for sth like pascal or basic, BUT he will accept anything I come up with, provided the correct arguments.
So basically I also wasn't to sure about python, to make a strong argument on that one.
I've even read that OOP is good to start with, but I'm thinking of sth straightforward, procedural.

Windows will be the platform of choice (possibly XP). 

Thank you for any suggestion!

---

### Post by RiceMonster on 2011-03-22
I think python would be a good starter language, but if they won't go for it, maybe c would be a good idea, since it's syntax has a had a strong influence on modern languages.

Definitely do not start with OO. I think it's better they have a good understanding of functional programing before they get into OO, because it adds a lot more complexity to the game. Keep it simple. Start with basic logic like if statements and loops.

---

### Post by Johnsie on 2011-03-22
Java is probably the most relevent one. There are alot of good tools for Java development and it's quite widely used. Java apps will run on most platforms and Linux. All Android apps are written in Java too, so there's quite alot of scope for development.

VB.NET is really easy and will have them developing Windows apps the quickest, but the structure of the code isnt really compatible with many other languages or operating systems. Still, a good place to start if you want to keep things simple.

---

### Post by ikt on 2011-03-22
Why are you teaching programming to people who don't even know how to use a computer?

Seems a bit backwards to me, learn to use computer first, then program.

---

### Post by slackthumbz on 2011-03-22
Perl.

---

### Post by fisaacs on 2011-03-22
*context* I've tried teaching myself to program numerous times, eventually with enough success that in college I waived taking your basic cs course and talked the prof into letting me take AI, Robotics and Organization/Hardware courses.  Now trying to get myself schooled on data structures / real programming vice the above subjects */context*

I'd also think about what, if anything they're going to be programming.  c (as a beginner) is great if you're learning to write command line unix/dos applications, but gets hairier to add graphical functionality.

Java's everything-is-a-class mentality is going to help or hurt you on how you're teaching them, but the upswing is you have a windows friendly IDE you can teach out of and you can get them into writing gui programs quickly.  WHen I was learning, I got a lot farther with VB (in my pre-linux days) than I ever did with c because I saw a final polished product faster.

Narrowing it down though, I'd say Java/Perl/Python.  Don't leave their experience at the command line.

---

### Post by sisco311 on 2011-03-22
IMO, c, java and python are equally good choices.

But, you could use pseudocode and flowcharts to teach them the basic concepts.

---

### Post by P1C0 on 2011-03-22
> **ikt said:**
> Why are you teaching programming to people who don't even know how to use a computer?

Seems a bit backwards to me, learn to use computer first, then program.Well despite the fact it is a Seminary, they have this computer science related course and they want someone from the Informatics Department to teach it.

The plan is to talk to them a little about computers and computer science, open up a computer to show them the parts it consists of, teach them some basics of using a computer, introduce them a bit to programming and what it's good for and just at that point do some examples in a programming language and give them a small task as homework.

Probably none of them will ever program again.

I like python because it is also interactive. They can try things on the fly, like mathematical calculations, small assignments, an if-else structure, a for loop.

---

### Post by mips on 2011-03-22
> **P1C0 said:**
> 
Probably none of them will ever program again.


[Logo]("http://en.wikipedia.org/wiki/Logo_(programming_language)")

---

### Post by P1C0 on 2011-03-22
> **mips said:**
> [Logo]("http://en.wikipedia.org/wiki/Logo_(programming_language)")I programmed in logo in elementary school :D We had a little turtle we could move around.

It crossed my mind, but I believe it is sth I could use to teach small children.

ANYWAY, after about 5 secs of persuasive talking, python it is.
> ...
-me: I don't like pascal
-prof: what are you suggesting instead
-me: python, it's interactive, it's cool
-prof: ok, we'll do python
...

---

### Post by sydbat on 2011-03-22
> **P1C0 said:**
> Well despite the fact it is a Seminary, they have this computer science related course and they want someone from the Informatics Department to teach it.

The plan is to **talk to them a little about computers and computer science**Good.
 
> **open up a computer to show them the parts it consists of**Good.
 
> **teach them some basics of using a computer**Good.
 
> [B]introduce them a bit to programming and what it's good for and just at that point do some examples in a programming language and give them a small task as homework.
[/B]
Probably none of them will ever program again.Bad.

When getting my IT Management degree, we had a class for programming. Every single person hated it. Why? Because it had nothing to do with the rest of the course. It actually took away from everything else we were learning.

Had we been taking a different IT degree, that included programming, then it would have been inline with what we were learning. However, it actually caused a few people to drop that class and make up the credits elsewhere.

My suggestion - do all the things you mention **except for** the programming. All that will do is alienate the ***Seminary*** students who will never be programmers. Make the ***introductory computer class*** enjoyable, instead of believing that just because you like to program, everyone needs to know how programming works.

---

### Post by P1C0 on 2011-03-22
> **sydbat said:**
> Good.
 
Good.
 
Good.
 
Bad.

When getting my IT Management degree, we had a class for programming. Every single person hated it. Why? Because it had nothing to do with the rest of the course. It actually took away from everything else we were learning.

Had we been taking a different IT degree, that included programming, then it would have been inline with what we were learning. However, it actually caused a few people to drop that class and make up the credits elsewhere.

My suggestion - do all the things you mention **except for** the programming. All that will do is alienate the ***Seminary*** students who will never be programmers. Make the ***introductory computer class*** enjoyable, instead of believing that just because you like to program, everyone needs to know how programming works.You are probably right, but python is so enjoyable:
```
>>> l = ['a','b','c']
>>> for i, j in enumerate(l):
    print i, j

    
0 a
1 b
2 c
```

*Divine* programming, in a *Seminary* :D

---

### Post by cloyd on 2011-03-22
I don't know what language, but todays church is getting to be technologically demanding. From worship t o administration, to communication, technology is important. A little bit of programing can teach folks like me who are more used to thinking in metaphors and analogies how rigidly a computer operates.  

A little tech familiarity could save a church lots of money . . . the church secretary wants a new computer because the one she is using is using is getting slower and slower. Looking at the system, it is windows, has never been defragged, and she has all kinds of toolbars and weather reports and other gadgets and the system tray is always full . . .  and when we asked when was the last time the antivirus was updated, they say "what is that?"  And, lest of all, all day long, she never closed an application. Email, word processors, spreadsheets, payroll programs, membership tracking programs web browsers all stayed open and minimized. Yes, the machine was indeed slow. No wonder

A little tech familiarity might prevent the situation I saw where the church secretary was using the computer, and IE suddenly started going to pron sites.  

And, maybe a little knowledge might teach people that there is a reason to use  something like Ubuntu and Linux.

---

### Post by cookiecloud on 2011-03-22
If you want a firm base upon which they can build, then teach them C. It may take a little more effort, but isn't C what everything *else* stems from? (unless you want to confuse them, and teach ASM :lol:)

---

### Post by Dustin2128 on 2011-03-22
I would teach them  esoteric programming languages, it'd be hilarious if they actually went on to develop real software in, say, LOLCODE.
```

//Hello world
HAI
CAN HAS STDIO? 
VISIBLE "HAI WORLD!" 
KTHXBYE

```

---

### Post by cookiecloud on 2011-03-22
> **Dustin2128 said:**
> I would teach them  esoteric programming languages, it'd be hilarious if they actually went on to develop real software in, say, LOLCODE.
```

//Hello world
HAI
CAN HAS STDIO? 
VISIBLE "HAI WORLD!" 
KTHXBYE

```

I LOL'd, literally!

Ohai, btw! ^_^

---

### Post by GabrielYYZ on 2011-03-22
how about BASH? 

it's simple, it's useful and there's a whole lot you can do with it. plus, it can teach them structure.

i know it's scripting, not programming, but maybe walking before running isn't a bad idea, after all.

---

### Post by ikt on 2011-03-23
> **GabrielYYZ said:**
> how about BASH? 

it's simple, it's useful and there's a whole lot you can do with it.

Bash is none of the above to a new computer user.

---

### Post by ashmew2 on 2011-03-23
> **ikt said:**
> Bash is none of the above to a new computer user.

+1

Well , i was taught GW-BASIC in school as the first language , then C++...

I think the std::cout etc are very easy to learn...Just keep it simple..Dont do functions or anything...

IMHO though, teaching people who dont know what a cdrom is how to program is going to be tough (more for them)...U can throw them into a phobia..because they have to be geeks to jam all that in their heads in a single class..

---

### Post by StephanG on 2011-03-23
Actually, I think your intuition to teach them Python is spot on.  You don't have to worry about whether user input is a string, float, or int.

Python allows you to get straight into the logic behind programming.  I would say its perfect to give users a small glimpse into what code looks like, without what my Lecturer calls the "piping" of other languages.

---

### Post by Shining Arcanine on 2011-03-23
> **P1C0 said:**
> I'll be teaching a course in Introduction to Computer Science to a **Seminary** for the next few weeks, and I am trying to find out what programming paradigm and language should I use in order to introduce them a bit to very simple facts of programming.

"Seminary" is bold because I want to emphasize the fact that the course is planned to be kept really really simple. Most of them probably don't even know how to use a computer. We will teach them that too.

At first I thought about python, but the professor was like "wtf" and he prompted me to look for sth like pascal or basic, BUT he will accept anything I come up with, provided the correct arguments.
So basically I also wasn't to sure about python, to make a strong argument on that one.
I've even read that OOP is good to start with, but I'm thinking of sth straightforward, procedural.

Windows will be the platform of choice (possibly XP). 

Thank you for any suggestion!

Since this is a seminary and very few of your students are expected to do anything with this, I suggest that you teach them a functional programming language. Haskell is probably a good choice because its interpreter is very useful as a calculator and a decent understanding of it can enable people to very rapidly obtain results from a computer without having to understand how the computer actually works. Haskell also uses the GMP library for its calculations, so things such as word size are a non-issue for it.


> **fisaacs said:**
> *context* I've tried teaching myself to program numerous times, eventually with enough success that in college I waived taking your basic cs course and talked the prof into letting me take AI, Robotics and Organization/Hardware courses.  Now trying to get myself schooled on data structures / real programming vice the above subjects */context*

I'd also think about what, if anything they're going to be programming.  c (as a beginner) is great if you're learning to write command line unix/dos applications, but gets hairier to add graphical functionality.

Java's everything-is-a-class mentality is going to help or hurt you on how you're teaching them, but the upswing is you have a windows friendly IDE you can teach out of and you can get them into writing gui programs quickly.  WHen I was learning, I got a lot farther with VB (in my pre-linux days) than I ever did with c because I saw a final polished product faster.

Narrowing it down though, I'd say Java/Perl/Python.  Don't leave their experience at the command line.

While I believe that all people should be educated in C, I do not think a few weeks is enough to teach people who have no concept of how to use computers how to write useful programs in C. I also do not think that it will have much relevance in their later lives.

By the way, graphics functionality is too complex for a beginner programming class. Teaching it that early would likely be very discouraging and produce a strong hatred for programming.

---

### Post by GabrielYYZ on 2011-03-23
> **ikt said:**
> Bash is none of the above to a new computer user.

but... compared to Python, C, Perl? and that's just the ones people are throwing around here... 

i can just imagine the starting lesson with C:

ok guys, let's do a really, really simple program with C
```

#include <stdio.h>
main(){
     prinf("Hello World!");
}

```compared to BASH:

```

#/bin/bash
echo "Hello Wold!"

```but, anyways, it was just a suggestion...

---

### Post by StephanG on 2011-03-23
> **GabrielYYZ said:**
> but... compared to Python, C, Perl? and that's just the ones people are throwing around here... 

i can just imagine the starting lesson with C:

ok guys, let's do a really, really simple program with C
```

#include <stdio.h>
main(){
     prinf("Hello World!");
}

```compared to BASH:

```

#/bin/bash
echo "Hello Wold!"

```but, anyways, it was just a suggestion...

Compared to Python:
```

print('Hello World!')

```

---

### Post by Shining Arcanine on 2011-03-23
> **GabrielYYZ said:**
> but... compared to Python, C, Perl? and that's just the ones people are throwing around here... 

i can just imagine the starting lesson with C:

ok guys, let's do a really, really simple program with C
```

#include <stdio.h>
main(){
     prinf("Hello World!");
}

```compared to BASH:

```

#/bin/bash
echo "Hello Wold!"

```but, anyways, it was just a suggestion...

Your example is K&R C, which is no longer in use. To do this in ANSI C, you should do:

```
#include <stdio.h>
#include <stdlib.h>

int main(){
printf("Hello World\");
return EXIT_SUCCESS;
}
```

If I were teaching a C class, I would not do this in the first lecture. Instead, I would talk about how computer hardware works in the first lecture. Then this could follow, although I would probably want to talk a bit about variables and I/O alongside it.

---

### Post by ikt on 2011-03-23
> **GabrielYYZ said:**
> but... compared to Python, C, Perl? and that's just the ones people are throwing around here... 

Which is why I and many others are saying don't do it at all, there's absolutely nothing to be gained by doing so.

edit: and I'm 99% sure the people suggesting C were joking.

---

### Post by Shining Arcanine on 2011-03-23
> **ikt said:**
> Which is why I and many others are saying don't do it at all, there's absolutely nothing to be gained by doing so.

edit: and I'm 99% sure the people suggesting C were joking.

I was not joking in my spiritual support for C, although my vote is for a functional programming language. It is more practical for priests to know functional programming than it is for them to know imperative programming.

If this were a K-12 or college class for beginners, I would say to teach them C and let them learn other languages afterward. Alternatively, they could be taught FORTRAN, which is the only acceptable substitute for C.

---

### Post by ikt on 2011-03-23
> **Shining Arcanine said:**
> It is more practical for priests to know functional programming than it is for them to know imperative programming.

What about priests who don't want to learn programming?

---

### Post by GabrielYYZ on 2011-03-23
> **ikt said:**
> Which is why I and many others are saying don't do it at all, there's absolutely nothing to be gained by doing so.

edit: and I'm 99% sure the people suggesting C were joking.

now that i had a 2nd look, i see you were the third poster and you were, in fact, against starting there at all. my bad :rolleyes: i would say the same thing, don't teach any language to a non-computer person but, since the OP is, apparently, set in his way, BASH is not a bad candidate, in my humble opinion.

@Shining Arcanine: yeah, python is both a scripting language and a programming language, but my reasoning for BASH instead of python is that you get more familiar with keywords you'll see both in linux and in windows powershell (i.e. cat, echo, ls, cp, mv) , so you get some extra mileage from that.

---

### Post by pi3.1415926535... on 2011-03-23
What ever you do, do not teach HTML or Scratch etc. and call them programming languages (HTML (Hyper Text Markup Language)). I believe that these classes are found to be too slow by most every one, and do not provide a good foundation in what programming is about. Teaching the programming mindset is one of the key essentials.

---

### Post by P1C0 on 2011-03-23
> **Shining Arcanine said:**
> Since this is a seminary and very few of your students are expected to do anything with this, I suggest that you teach them a functional programming language. **Haskell** is probably a good choice because its interpreter is very useful as a calculator and a decent understanding of it can enable people to very rapidly obtain results from a computer without having to understand how the computer actually works. Haskell also uses the GMP library for its calculations, so things such as word size are a non-issue for it.

I like haskell. I'm just quoting you to post this article I read yesterday and made me Lol!
[Haskell Researchers Announce Discovery of Industry Programmer Who Gives a S**t]("http://steve-yegge.blogspot.com/2010/12/haskell-researchers-announce-discovery.html")

---

### Post by leg on 2011-03-23
Well I think the guy who said don't bother had a very good point. If however you insist on teaching something about how programming works why not take a look at something like [scratch]("http://scratch.mit.edu/"). You can show them the constructs visually and also how they fit together.

---

### Post by danbuter on 2011-03-23
Honestly, from your parameters, I think your students would be far better off learning the ins and outs of excel and word, than wasting time learning programming. They will almost definitely need to use spreadsheets and a word processor in their job.

---

### Post by P1C0 on 2011-03-24
> **danbuter said:**
> Honestly, from your parameters, I think your students would be far better off learning the ins and outs of excel and word, than wasting time learning programming. They will almost definitely need to use spreadsheets and a word processor in their job.```
>>> a = 1
>>> b = 2
>>> a, b = b, a
>>> print a, b
2 1

```
So much better!

Actually ok, besides being a python fan boy I must admit you have a point, and possibly 1-2 lectures will be about creating documents, spreadsheets and so on.

---

### Post by pbpersson on 2011-03-26
Show them a really simple application, explain how it works, then offer a software development exercise as extra credit for those who are interested.

---

### Post by P1C0 on 2011-05-10
I'm bumping this thread to provide some info, as we are almost finished with the lab courses (there may be one more).

It seems python was a big success!

We had 7 students in total from the beginning to the end. We covered the basic control flow stuff, functions, standard input and output, and did a lot of easy coding.
Today we even played with the pow function of the math module.

We asked them if they would have preferred theory (we did 2 theory lectures in the beginning) instead of coding on the computer and their answer was: "NOOO!"
Most of the times they were excited about the results of their programs, because they really enjoyed the interactive environment in python.

:)

---

