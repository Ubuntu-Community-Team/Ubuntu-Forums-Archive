---
title: "Which programme language is good for non-programmer?"
date: 2007-04-26
forum: The Cafe
---

### Post by Masoris on 2007-04-26
As programme languages become easier, everyone can use programme language without knowing how it works in detail. For example everyone can make macro for spreadsheet programme, although he never studied computer science before.

If someone know a programme language, he can use programme language to make macro, backup programme, or to organise or to analysis his data, and so on.

Do you think which programme language can be useful tool for person who is not professional programmer?

---

### Post by EerFoolWVU on 2007-04-26
not sure about what you can use without any experience but HTML and migrating into CSS is definitely the easiest to learn


just out of curiosity why do you add an me to end end of program and use an s instead of z in organize?

is this a different english dialect or is english simply not your first language?

---

### Post by Nils Olav on 2007-04-26
the strangeness of your question makes me giggle.

---

### Post by tbroderick on 2007-04-26
Most people will say Python, but I've decided I'm going to start learning Perl as my first language, after much back and forth between the two. Ruby seems nice too.

---

### Post by BuffaloX on 2007-04-26
Check out Lazarus.

It's pascal which is very easy to learn.
It has a very nice gui designer, and works on both Linux and Windows.

[http://www.lazarus.freepascal.org/]("http://www.lazarus.freepascal.org/")

BTW why didn't you post in programming talk??

---

### Post by Nikron on 2007-04-26
> **EerFoolWVU said:**
> not sure about what you can use without any experience but HTML and migrating into CSS is definitely the easiest to learn


just out of curiosity why do you add an me to end end of program and use an s instead of z in organize?

is this a different english dialect or is english simply not your first language?

What?  HTML/CSS isn't exactly a language.  Seeing as you want an easy to learn powerful tool and you use Ubuntu, I would suggest Python.

---

### Post by fuscia on 2007-04-26
i've only made it to 'hello world' with javascript and c++, if that's any help to you.

---

### Post by Pobega on 2007-04-26
For non-programmers? If you don't mind being restricted to websites, PHP is definitely a great language to look into.

Not only is the syntax extremely simple, but within a week (From the start of knowing nothing!) you can create innovative and original pages, with user interaction. I remember when I started I went from nothing to a shoutbox with registration in under a week. It was quite a thrill to get something thrown together that fast, practically from thin air.

---

### Post by zubrug on 2007-04-26
[http://tryruby.hobix.com/](http://tryruby.hobix.com/)

Play with this ruby tutorial, its fun

---

### Post by Tundro Walker on 2007-04-26
Folks are gonna hound me for this (since Linux is a C / Python playground), but I started with VBScript, and moved on to Visual Basic.

HTML & CSS are more "formatting languages" in that they don't really do a whole lot except re-format text and such that you enclose in tags.  Real programming languages, like c, C++, C#, VB, Python, Ruby, etc, etc let you use logic and decision loops in your program.

The difference between

```
<html>
<b>This text is bold in HTML</b>
</html>
```...and...

```
sub IncrementMyRs(rs as ADODB.Recordset)

Dim i as Integer

Do until rs.EOF
  rs.field(0).value = i
  i = i + 1
Loop

end sub
```...there's a jump in power there.  But, on the plus side, when you learn one programming language, the concepts usually follow over to every other programming language you learn, making it easier to pick new ones up.  (which is good, because they change so often these days, and new ones are invented every day.)

EG: All modern languages have some kind of "Do / Loop", "If / Else / Else if / End If", etc you can use to allow decision-making programs to do their thing.  They all have some kind sub-procedure capability, letting you re-use code again and again by calling it as a sub-procedure from other code.  

EG: For instance, that "sub" code I wrote up there is a VB sub-procedure which you'd pass an ADODB recordset to, to which it'll increment through each record until end of the recordset and make the 1st field equal to the current value of "i".  I can use that sub-procedure again and again from some other code, sending it as many recordsets as I want to let it incrementally number them.  This saves you from having to type that same code tons of times, for each recordset you wanted to do that to.

Certain programming languages are "higher level" than others, and by that I mean "closer to human language", not "better than the others".  For instance, Visual Basic is pretty high-level, with it's own garbage-collecting, easy to understand / read code that uses words you can understand, etc.  But, you usually can't control low-level (IE: closer to machine-language) devices.  EG: in C & C++, you can usually directly control the printer, or directly control what programs load into what memory addresses.  But in Visual Basic, you just "dimension" variables, and the VB compiler / interpreter does a lot of the leg-work for you, and usually you can't directly control printers or other hardware.

With that said, it's hard to say which language to start with without understanding what motivates you.  If you're the type that likes to jump into the deep-end, sink-or-swim, and enjoys the challenge, then hop right into C++.  But, if you like something a little easier, you might want to try Java, Python, Ruby.  Find a decent tutorial, because a lot of what makes a programmer good is the initial "conventions" they learn when first learning to program.  By that I mean, how they structure their code.  Some self-taught folks may be genius programmers, but their code may look tangled and messy.  Learning good structure is important, because it makes your code easier to read, making it easier for you to debug and add-to later on.  (Not to mention making it easier for others to do so, if you're ever working on a large, group project).

Side note,  this topic will end up with folks arguing for both sides.   Some folks will argue that "newer" languages, like VB and Java, suck, because they don't force you to do "real programming", IE: "newer" languages usually do the memory allocation, garbage-handling, etc for you.  Others will argue that "older" programming languages, like straight C, are antiquated and obsolete, because you have to spend so much time coding to handle memory usage, etc.

To this I would say, both are right, and you'll have to simply learn some programming to understand why.  Using HTML as an example, if you open up a text editor and do a web-site by hand, you can make a very trimmed down, efficient one that loads fast, because you've left out a lot of unnecessary code that some web-page builders (Nvu, Amaya, Dreamweaver, RoboHelp, etc) add in.  But, it takes more time to build it by hand.  The programs that do it for you may add some "fluff", but make it fast and easy to build pages.  Some will say the hand-done method is best.  Others say the helper program method is best.

But, when it comes down to it, real programmers do both.  They know how to do everything by hand (IE: like old-school C programmers), but they're not afraid to use "newer" tools and languages that increase productivity.  There's nothing wrong with cranking out loads of code with the help of an IDE.  But it's always good to be able to fine-tune it once it's cranked out, and that ends up taking knowledge of everything that's going on under the hood.
 
Anyways, with all that said, I'd recommend installing an IDE from the "programming" section in Synaptic and looking for a good tutorial.  There's an IDE that uses a "Visual Basic" like language (which I was gonna try out), one for GTK (Gnome Tool Kit) applet design, etc.  Pick something you're interested in, and start with a project that's fun, preferably visual, too (EG: code a small game, which is usually what folks get their feet wet with once they pass the whole training curve.)

Ok, let the flame -session ensue...LOL!  Talking about programming languages is like comparing Linux to Windows...you'll get some heated discussion.

---

### Post by dbbolton on 2007-04-26
> **fuscia said:**
> i've only made it to 'hello world' with javascript and c++, if that's any help to you.
:lol:

---

### Post by Masoris on 2007-04-26
> **EerFoolWVU said:**
> 
just out of curiosity why do you add an me to end end of program and use an s instead of z in organize?

is this a different english dialect or is english simply not your first language?

Both right. English is not my first language. And I'm learning British English now.
When program means about computer. program and programme both right spelling in British English.
But most time only programme is right spelling - when it not means about computer.
And -ize and -ise are both right spelling in British English as I know. e.g. 'organise and organize', 'realise and realize' and so on.

---

### Post by troymcdavis on 2007-04-26
A professor in my computer science department whom I respect very much claims that [Turing]("http://en.wikipedia.org/wiki/Turing_%28programming_language%29") is a great pedagogical language, but has no vocational value (it won't mean anything on a job application). I learned on Java, and it has its benefits, but I/O is madly complicated and Java overhead is killer, among other issues. I personally vote for Python, though.

---

### Post by Tundro Walker on 2007-04-27
> **troymcdavis said:**
> A professor in my computer science department whom I respect very much claims that [Turing]("http://en.wikipedia.org/wiki/Turing_%28programming_language%29") is a great pedagogical language, but has no vocational value (it won't mean anything on a job application). I learned on Java, and it has its benefits, but I/O is madly complicated and Java overhead is killer, among other issues. I personally vote for Python, though.

LOL!  I totally agree with this.  When it comes to a resume, folks don't look for

- computer modelling
- system design
- software design
- relational database design

...the look for ...

- Java, HTML, C++, UML, SQL, Oracle, (etc)

I constantly get a kick out of this, because once you know the fundamentals, it's easy to pick up different "languages" which are simply sub-sets of a primary skill, or program/apps that make using the fundamental skill easier (like an IDE).  

Some tech recruiting companies are actually getting smart, and don't just look for the latest "languages", since they've realized programming languages are like fads that change so fast.  There's so many languages these days, and a lot of them do the same things (or at least have the potential to).  

But, there still are tech recruiting companies that don't just want someone who can code Java...you have to know "NetBeans", because that's what the job hiring out will use.  Pfft...  There's a minor learning curve when using a new IDE, but most visually look the same these days, because programmers have gotten used to a standard look about them.  Doing something drastically different then the norm is a good way to become obsolete.  

EG: like a spreadsheet program coming out to compete with Excel (the current king), and NOT looking somewhat like Excel.  If it had a totally different interface, etc, it'd be hard for folks to migrate.  However, with a fundamental knowledge of what spreadsheets do and are for, it would be easier for some to pick it up.  But, having a common interface makes it easier.

Yeah, it's sad.  So, knowing programming fundamentals and good convention isn't a "marketable" skill for recruiters to pick up on and hire you over others.  But, when you work with other folks who know what they're doing, they'll know it, and thank their lucky stars you know it.  It's just one of those "intangible" things that you can't put on a piece of paper, or that's subjective and means different things to others, like "good work ethic", or "good problem-solving skills".  Seriously, lots of people put that on their resumes, and some folks have it while others don't, so it gets ignored.  For recruiters, it comes down to the latest "buzz" words you have on your resume that are repeated over and over so you pop-up first when their software is scanning resumes for "Java programmer".  But, when you work with others, they'll realize if you have "good work ethic" or "problem solving skills", and those out-weigh just knowing Java.  Because lots of people know Java, but just knowing Java doesn't make you a team-player or good worker.  It's all the intangible skills that separate the good workers from the rest.

---

### Post by Rob Alderson on 2007-04-27
Going back a few years I learned Pascal & Cobol at college & self taught myself with Delphi. Once you know the basics of one language they're all pretty simple to migrate to.

---

### Post by Tomosaur on 2007-04-27
I'd say python for easiest to pick up. Here's a hello world program in python:

```

print "Hello World!\n"

```

Here's the same thing in Java:
```

class Hello{
  public static void main(String[] argv){
    System.out.println("Hello World!");
  }
}

```

---

### Post by use a name on 2007-04-27
Not as a serious suggestion, but if you want to know more about the internal workings of your computer, you can always do some [linux assembly](http://docs.cs.up.ac.za/programming/asm/derick_tut/#helloworld). It's real difficult, but it may put certain issues you run into (any language) in a different perspective.

---

### Post by the.dark.lord on 2007-04-27
> **zubrug said:**
> [http://tryruby.hobix.com/](http://tryruby.hobix.com/)

Play with this ruby tutorial, its fun

I would recommend Ruby myself too.

---

### Post by proalan on 2007-04-27
I first programmed in basic like this

```
10 print "hello world"
run
```

it is shorter than in java, but java is helpful as Object Orientation goes hand in hand with modern software engineering principles. It may look ugly sometimes but its a solid disciplined approach to designing and coding robust and reliable software. 

C++ is probably the most widely used, but java is easier to learn imho as the garbage collector deals with the memory management aspects, which can be difficult to spot when using C++ in the form of memory leaks. Java is also the most strictly typed language I know which in theory is supposed to make programs more secure for example java will ensure that if you create an array, you will only be able to access within the array where as in C++ this concept is not enforced and is commonly exploited to hack and break programs.

HTML CSS aren't programming languages, you can't use them to solve problems e.g. simple arithmetics 1+1 etc... They are intended to be used to present data.

PHP is another language similar to java/C++ which relaxes the type strictness and contains an extensive library of common functions, it is actually built in C++. I can't decide if PHP is a programming language or a scripting one as it feels like both. 

There are many types of programming languages classified in the following categories

Imperative (C++/Java/smalltalk)
Procedural (C, Pascal) 
functional (Haskell)
logical (Prolog)

are just some examples.

---

### Post by steven8 on 2007-04-27
> **the.dark.lord said:**
> I would recommend Ruby myself too.


I did the 'Try ruby'.  Very cool.

---

### Post by r.k.maroon on 2007-04-27
> 
There are many types of programming languages classified in the following categories

Imperative (C++/Java/smalltalk)
Procedural (C, Pascal) 
_functional (Haskell)_


Goodness! Haskell! w00t! 

But I'd mention ML, which is really the only functional language used in the industry.

I also wonder abit about this division into procedural and imperative (seems like you mean imperative and object oriented), but that's nitpicking!

I'd say Python is a good first language, but really any language will do - the fundamentals of programming remain the same whatever language you decide to use.  I've taught both Haskell and C as first languages, and really to similar effect.  Go with whatever you find useful.  Some will seem more daunting than others (like Perl's extensive use of regular expressions) but it's zeroes and ones in the end!

---

