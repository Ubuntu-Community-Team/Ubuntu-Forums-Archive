---
title: "Why does everyone hate VB?"
date: 2007-08-23
forum: The Cafe
---

### Post by edd07 on 2007-08-23
How come everyone here seems to hate Visual Basic? I actually think it's a great language. Sure, its implementation sucks, but again, as a language I find it pretty good. Any reasons for this? (Besides being made my Microsoft :P)

---

### Post by ynnhoj on 2007-08-23
i used vb.net a fair amount in college, and i liked it just fine.  vb 6 was a different story though!  :/

---

### Post by Tundro Walker on 2007-08-23
Linux is more of a C-based group.  And since Microsoft created VB, it doesn't exactly support VB's side of the argument when Linux folks talk about it.

Dear God, please don't let this turn into another programming language argument thread.

---

### Post by Spr0k3t on 2007-08-23
When you can build your own algorythm to replace a built in method and have the algorythm you write run much faster, then you know the language is not good.  As an object oriented basic approach, it's not implemented very well.  We use VB as nothing more than a proof-of-concept tool.  Any application developed in VB is tossed to the way-side until it's written in a non-MS language.  Where I work may be a microsoft shop, but the internal tools are cross platform at least.  The .NET framework is on the list of unsupported as well.  VB is good at one thing though, and that's macros inside of office.

---

### Post by jfinkels on 2007-08-23
Visual Basic has obscure, confusing, and clunky syntax.```

Dim foo as String = "bar"
```
Take a look at Python for an example of good syntax:
```
foo = 'bar'
``` Of course there are better examples of that discrepancy out there.

Visual Basic has no error handling mechanism. The best it does is use a Goto statement to continue running through code.

No multi-line comments.

It's nearly impossible to find documentation for Microsoft programming languages.

> **Spr0k3t said:**
>   VB is good at one thing though, and that's macros inside of office.

I disagree.

Not only do all the problems of Visual Basic apply to Visual Basic for Applications, but there are new problems, because different, weird syntax rules apply. They're only "good" because using VBA is the only way to make Office extensible!

---

### Post by jfinkels on 2007-08-23
> **edd07 said:**
> How come everyone here seems to hate Visual Basic? I actually think it's a great language. Sure, its implementation sucks, but again, as a language I find it pretty good. Any reasons for this? (Besides being made my Microsoft :P)

Try Python or Ruby and you will understand :D

---

### Post by Sp4cedOut on 2007-08-23
Linus Torvalds doesn't hate VB.

> For example, I personally believe that Visual Basic did more for programming than Object-Oriented Languages did. Yet people laugh at VB and say it’s a bad language, and they’ve been talking about OO languages for decades.

And no, Visual Basic wasn’t a great language, but I think the easy database interfaces in VB were fundamentally more important than object orientation is, for example.

[http://www.codinghorror.com/blog/archives/000648.html](http://www.codinghorror.com/blog/archives/000648.html)

---

### Post by thisllub on 2007-08-23
> **jfinkels said:**
> 
Visual Basic has no error handling mechanism. The best it does is use a Goto statement to continue running through code.


It's nearly impossible to find documentation for Microsoft programming languages.



You are very wrong there.  There is extensive documentation on Visual Basic and excellent books on how to connect it to the Windows API.
The error handling is logical and consistent with a number of options available to the Resume statement.

I think the biggest problem with VB is the bloatware that makes it run. The forms interface is terrible as it is with all MS products.

---

### Post by edd07 on 2007-08-23
> **jfinkels said:**
> Try Python or Ruby and you will understand :D

Well, I haven't actually started to learn Python, but just by looking at code, I find it harder to read than VB. Maybe is something you get used to, i don't know, I admit my knowledge of Python is very limited (Actually, closer to none) I can read C++, though...and I hate it. (please don't flame me :P)

---

### Post by jfinkels on 2007-08-23
> **thisllub said:**
> You are very wrong there.  There is extensive documentation on Visual Basic and excellent books on how to connect it to the Windows API.

I shouldn't have to pay for 1. a programming language and 2. the documentation for it. There are obviously websites that offer VB documentation, but there is no central, lucid, reference website. Take a look at the reference for Python, for example: [http://docs.python.org/](http://docs.python.org/) or PHP: [http://www.php.net/manual/en/funcref.php](http://www.php.net/manual/en/funcref.php)

Microsoft's documentation on the MSDN library is confusing, unhelpful, and the examples are scarce and don't work every time.

I shouldn't have to use a retail book or Google to search for information on how to interact with the operating system, a crucial function of any non-trivial program.
> 
The error handling is logical and consistent with a number of options available to the Resume statement.

```
On Error Resume Next
``` is neither as functional nor as easy to use as, for example, in python:```
try:
    foo = "bar"
except('Error'):
    baz

```
Goto statements are frowned upon in part for this reason: [http://xkcd.com/292/](http://xkcd.com/292/)
> 
I think the biggest problem with VB is the bloatware that makes it run. The forms interface is terrible as it is with all MS products.

Yes.

---

### Post by juxtaposed on 2007-08-23
The only thing about programming I know of is a little in VB6. I liked it a lot, it was easy to do. I know nothing of the technical aspects of it or any other language, I don't know what an object oriented language is or any of that stuff, all I know is that VB6 worked fine for anything I used it for.

---

### Post by ry4n on 2007-08-23
> **edd07 said:**
> Well, I haven't actually started to learn Python, but just by looking at code, I find it harder to read than VB. Maybe is something you get used to, i don't know, I admit my knowledge of Python is very limited (Actually, closer to none) I can read C++, though...and I hate it. (please don't flame me :P)

[http://www.oreilly.com/catalog/lpython2/toc.html](http://www.oreilly.com/catalog/lpython2/toc.html)

This is a great book, It is really easy to learn with this tool for O'Reilly :)

---

### Post by steven8 on 2007-08-23
I have programmed in VB3, VB4, VB5, VB6 and VB.NET 2003 and 2005.  For me, the language of VB reads easy as pie.  It may not be the best language, but it has done everything I asked of it.  To me, that's what matters most.

---

### Post by Spr0k3t on 2007-08-24
> **jfinkels said:**
> Not only do all the problems of Visual Basic apply to Visual Basic for Applications, but there are new problems, because different, weird syntax rules apply. They're only "good" because using VBA is the only way to make Office extensible!

You said it much better than I could.  I just wish there was a better language that could be used to extend the MS Office stuff.

---

### Post by vexorian on 2007-08-24
I used it for long when I was starting.

I am now happy I found other languages.

I wouldn't use vb again even if I was threatened by gun.

It is simply... not right.

And + .net it should be the worst invention ever! (unless you count IronPython)

---

### Post by the_darkside_986 on 2007-08-24
I am taking VB .NET as an elective this semester, but I don't see it as a serious programming language. Wtf does "Dim" have to do with a simple variable declaration? Is there a "Bright" keyword somewhere? The 70's are long gone and we don't need silly archaic words in a programming language. I like C# a lot better--I've used it last semester in software engineering--but I don't care for .NET, mainly because it is just the result of MS whining about not being able to steal Java. 

Speaking of Java, I've learned that all Computer Science majors in all concentrations at my univ. will be learning Java as the introductory CS course instead of C++ and VB. They said there is more of a demand for Java programmers now.

---

### Post by IYY on 2007-08-24
Everyone doesn't hate VB. Actually, Linus himself once said that it was a great language for certain types of applications.

I would also say that it's great for coding prototype applications and simple apps for business. It's a good language for people who are not coders but need to quickly make an app. However, and this is the reason that some people dislike it, VB is a horrible language for learning programming, and gives you all the wrong habits. And of course, you can't write any serious programs in VB (and by serious I mean things like iTunes, Office, any backend stuff, anything that talks to hardware).

---

### Post by swoll1980 on 2007-08-24
I don't hate. I don't even now what it is.

---

### Post by aquavitae on 2007-08-24
> I have programmed in VB3, VB4, VB5, VB6 and VB.NET 2003 and 2005. For me, the language of VB reads easy as pie.So you've spent your life looking at VB code and now its easy to read?  I used VB a lot when I was young and ignorant, but despite that, I still find it far more difficult to read than e.g python - and I've only been using python for about a month!
> Linus Torvalds doesn't hate VB.

Quote:
For example, I personally believe that Visual Basic did more for programming than Object-Oriented Languages did. Yet people laugh at VB and say it’s a bad language, and they’ve been talking about OO languages for decades.

And no, Visual Basic wasn’t a great language, but I think the easy database interfaces in VB were fundamentally more important than object orientation is, for example.
Yes, I agree it was good in its day, but now its over.  I think I'd rather program in fortran than vb now, at least its consistant!
> 
Quote:
Visual Basic has no error handling mechanism. The best it does is use a Goto statement to continue running through code.
It's nearly impossible to find documentation for Microsoft programming languages.

You are very wrong there. There is extensive documentation on Visual Basic and excellent books on how to connect it to the Windows API.
The error handling is logical and consistent with a number of options available to the Resume statement.
Digging into the OS API and kernel functions is not good error handling, its just a bad way of reporting errors.

---

### Post by steven8 on 2007-08-24
> **aquavitae said:**
> So you've spent your life looking at VB code and now its easy to read?  

No.  I found it easy to read from day one, so I continued to use it through all those versions.  Why, exactly, did you find the need to criticize me for it?

---

### Post by aquavitae on 2007-08-24
Sorry, didn't mean to criticise you (or anyone else).  Your post was just a handy example of what appeared to be a number of people saying they like VB, its great, its the easiest to read, er, no, I don't know any other languages... 

To those to whom this applies: try using something like python and you'll see why vb is unpopular.  If you still think vb is great after giving languages like python, ruby, etc a fair trial then that's your opinion and I don't criticise you for it.

---

### Post by saulgoode on 2007-08-24
For those who might be interested, there is a nice, GPLed VB-ish BASIC called [GAMBAS](http://gambas.sourceforge.net/).

---

### Post by thisllub on 2007-08-24
> **jfinkels said:**
> 
```
On Error Resume Next
``` is neither as functional nor as easy to use as, for example, in python:```
try:
    foo = "bar"
except('Error'):
    baz

```


```

On error goto ErrorHandler

...

Errorhandler:

select case error
           case a
                fix error type a
                resume 0
          case b
               can't fix
               exit function

end select


```

is every bit as useful
Easy is a matter of semantics.

In VB goto is really only used for error handling.

Anyway if goto was bad assembler would be useless.


I don't want to be seen as advocating Microsoft, just putting another point of view.

---

### Post by jethro10 on 2007-08-24
I'm perfectly happy with VB.NET

I make a good living from it and am very happy.

My company has far better bespoke software for factory tracking than any company this size has the right to expect because of it and it gives us a great competitive edge.
And with MONO i'm now close to having it cross platform, it was easy.
what can be wrong with that?

J

---

### Post by steven8 on 2007-08-24
> **jethro10 said:**
> I'm perfectly happy with VB.NET

I make a good living from it and am very happy.

My company has far better bespoke software for factory tracking than any company this size has the right to expect because of it and it gives us a great competitive edge.
And with MONO i'm now close to having it cross platform, it was easy.
what can be wrong with that?

J

You are absolutely right.  What can be wrong with that.  My first taste of computing snobbery was when I mentioned that I programed in VB to a guy I worked with.  He off-handedly mentioned that he knew a guy who did programming too, ". . .you know", he said, "real programming.  In C."  Real programming.  He actually said that.  I just stood there.  People never cease to amaze me.

---

### Post by sparks0548 on 2007-08-24
This thread has been really interesting to read.  I haven't had any experience with VB.  Any coding I've done has been in ASP.NET, and C#.NET due to the nature of the applications I was working with and the database platforms in the back end.  I actually enjoyed coding that way and enabled me to increase my skill set with database architecture and business application modeling.  

I've downloaded and picked up some books, because I want to expand my coding knowledge and work in C++ and Python and get into Perl.  I'm opting for a better job with more flexibility. 

I still believe that MS development tools and applications are going to have their place in the market, and are going to be around for a long time.  While other solutions can be built, alot is going to be determined on the comfort level of the organization like interoperability with SharePoint Server, SQL Server, Windows Server and many other products.

Hate is a pretty strong word.  While we can recommend solutions and build solutions to replace MS products either in the work place or at home it is going to take time, quality solutions and at most time limited interoperability.  We can play "dumb as a fox".  

I've worked in organizations where home grown VB apps did the trick for searching millions of documents and pulling duplicates and ensuring parent & child relationships, the database platform on the back was horrible.  After a while I saw a similar solutions to that very same application running on a circuit board with only a network connection, Linux Kernel, and home grown C app to do the same job faster, and more consistently and at lower cost.

In the end I feel that .NET and the Visual Studio suite of tools are going to be around for a while, so why not temporarily embrace them and use them for what they were designed; if the need so arised.

---

### Post by LaRoza on 2007-08-24
"Dim" means dimension, a reference to BASIC (I think)

---

### Post by popch on 2007-08-24
While band aids and strings have their uses, you should rather consider pre-stressed concrete or steel-girders and such for heavy construction work.

For 'real' programming (i.e. building applications anyone cares for) you should use the best tools there are available and - first of all - you should have learned how to program applications. 

VB can be very nice for rough draughts and prototyping, but please do not use any kind of BASIC for applications.

Also be aware that if you include VB scripts in your office documents, you will probably not be able to use those documents in another version of Office or in another country where they speak other languages than in your own.

Otherwise, I am sure that VB has its uses. 

So has the mosquito.

---

### Post by LaRoza on 2007-08-24
> **popch said:**
> 
So has the mosquito.

Feeds Dragon Flies!

---

### Post by AZzKikR on 2007-08-24
[http://bash.org/?777323](http://bash.org/?777323)

<redwyre> kez said you you are a whiney bitch
<TraumaPony> Haha
<redwyre> and that you smell
<TraumaPony> Heh
<redwyre> and that you're gay
<TraumaPony> Lol
<redwyre> and that you like visual basic
<TraumaPony> THAT C**T

:)

---

### Post by justleen on 2007-08-24
I dont think VB is evil... 

I only use it for excel, so maybe may field of view is a bit narrow, but i think its quite a nifty language. 
There are downsides, offcourse.. actually, there are quite a few downsides. The regional settings for exampleis a real pain in the *** ... but then again, with my field of view: in a corp. env. with identical images on every machine and no way for the users to change those setting: it works! 


Just wish i didnt have to learn a new langauge to use OoO's macro's..

---

### Post by popch on 2007-08-24
> **LaRoza said:**
> Feeds Dragon Flies!

So beautiful. It's a pity that evolution has done the big ones in.

Oh - I mentioned evolution. Will this thread now be moved to the GURT?

:lolflag:

---

### Post by LaRoza on 2007-08-24
> **popch said:**
> So beautiful. It's a pity that evolution has done the big ones in.

Oh - I mentioned evolution. Will this thread now be moved to the GURT?

:lolflag:

I wish I could have seen those big ones :(

I think mentioning "VB" is worse than Evolution.

---

### Post by happysmileman on 2007-08-24
I hate VB, never learned it, but I can read most languages very easily, I can't read VB at all...

I can kinda read python though the syntax seems very different from C/C++, I don't see why such a big deal is made of python when people talk about good code, even if it is easy, it's very different syntax from any othe rlanguages I've seen/iused

---

### Post by LaRoza on 2007-08-24
> **happysmileman said:**
> 
 I don't see why such a big deal is made of python when people talk about good code, even if it is easy, it's very different syntax from any othe rlanguages I've seen/iused

It may seem odd to say, but it isn't different from C the way you think it will be.

Think about it, you probably already indent consistantly, and follow a style. You can almost certainly use that same style in Python, with out trouble, just elimate the {} and add a : after certain statments (if, while, def, for...)

The syntax isn't different. What is the differenc between:

[php]
while (age < 18)
{
    printf("You can't have a drink");
}
[/php]

and 

```

while age < 18:
    print "You can't have a drink"

```

---

### Post by toupeiro on 2007-08-24
I'm not really much of a programmer, but in my windows and active directory support days (which was not so long ago)  I used VBScript quite a bit.  I write a lot of scripts, but I'm not really bold enough to call that programming.  I could do almost everything I wanted to do in batch shell scripts, right down to reghacks, killing services and directory enumerated file syncs, but there was that occasional task that I could only do using VBScript -- like actually disabling a non-standard windows service, not just starting or stopping it, or restricting certain parts of the windows GUI that weren't already group policy objects.

I'm not going to say its any easier than anything else, but it is effective.

---

### Post by nhydra on 2007-08-24
I like Basic but not Visual Basic. There is free basic implementation for linux and it is very good. If you like VB then you definitely have to take a look about Gambas IDE. This is IDE for VB developers based on Free BASIC.Free Basic is like a VB but is  free/open source.
Here you are the link [http://gambas.sourceforge.net/]("http://gambas.sourceforge.net/")

---

### Post by vexorian on 2007-08-24
> **the_darkside_986 said:**
> I am taking VB .NET as an elective this semester, but I don't see it as a serious programming language. Wtf does "Dim" have to do with a simple variable declaration? Is there a "Bright" keyword somewhere? The 70's are long gone and we don't need silly archaic words in a programming language. I like C# a lot better--I've used it last semester in software engineering--but I don't care for .NET, mainly because it is just the result of MS whining about not being able to steal Java. 

Speaking of Java, I've learned that all Computer Science majors in all concentrations at my univ. will be learning Java as the introductory CS course instead of C++ and VB. They said there is more of a demand for Java programmers now.
all the time I spent learning vB I was never able to understand what actually Dim was, when I learned other language it was so intuitive when they said "declare variables" I just don't understand who thought "dim" was a good idea..

---

### Post by popch on 2007-08-24
> **vexorian said:**
> all the time I spent learning vB I was never able to understand what actually Dim was, when I learned other language it was so intuitive when they said "declare variables" I just don't understand who thought "dim" was a good idea..

Now that's an easy one. You used to use DIM to declare arrays. Short for DIMension. It appears that you declare strings as if they were arrays of characters.

---

### Post by Daishiman on 2007-08-24
To all those who have had first-hand experience in VB:

I actually think it's singular purpose is to introduce people to programming. It does that well. 

However, as soon as you start learning more and more, you'll see where the problems lie. Mostly, it's not that you can't build stuff with it (you sure can), but that it soon becomes unmaintainable. You don't have proper object support. You have really crappy memory management (and a sigle thread, to boot), the implementation of references is not at all clear and there aren't good functions to deal with them. String handling is, IMO convulted. And the docs are plain bad; MSDN might be good for a couple of things but it doesn't have anything against perldoc or PHP documentation.

Mind you, I don't think PHP is a good language either, it's just that VB is worse. :)

---

### Post by jfinkels on 2007-08-24
> **thisllub said:**
> 
Anyway if goto was bad assembler would be useless.
 Well we try to get rid of Goto statements with higher level languages because it allows us to more easily reason about our programs, in a mathematical sense. Also, it makes code somewhat difficult to maintain.
> 
I don't want to be seen as advocating Microsoft, just putting another point of view.
I appreciate it :D
> **sparks0548 said:**
> 
In the end I feel that .NET and the Visual Studio suite of tools are going to be around for a while, so why not temporarily embrace them and use them for what they were designed; if the need so arised.
Just because it exists doesn't mean we should use it :P. In fact, if there are better tools, why would we NOT use those?
> **happysmileman said:**
> 
I can kinda read python though the syntax seems very different from C/C++, I don't see why such a big deal is made of python when people talk about good code, even if it is easy, it's very different syntax from any othe rlanguages I've seen/iused
Program with Python and you will understand. People don't just say stuff for no reason :)
> **LaRoza said:**
> 
The syntax isn't different. What is the differenc between:

[php]
while (age < 18)
{
    printf("You can't have a drink");
}
[/php]

and 

```

while age < 18:
    print "You can't have a drink"

```

The difference is two parentheses, two curly braces, the letter f, two more parentheses, and a semicolon. Python's attention to subtle detail like this is what makes its syntax superior.

---

### Post by RafG on 2007-08-24
I don't particularly care one way or the other, but [http://c2.com/cgi/wiki?ThingsWeHateAboutVb](http://c2.com/cgi/wiki?ThingsWeHateAboutVb) has a good overview of the main gripes people have with VB6...

---

### Post by guitarmaniac on 2007-08-25
Ha I read VB and I thought you were talking about Victoria Bitter the beer!
I would have told you to try a VB straight after a Carlton Draught and then you'd understand :p

---

### Post by SeanBlader on 2007-08-25
Beginners All-purpose Symbolic Instruction Code

What makes it consistently popular still is the fact that it is for beginners. Which makes it the lowest common denominator, which in a way has it's parallels with Ubuntu ironically enough. Basic is a decent language for getting into the logic of programming, and if it's the first programming you ever see, you may not be intimidated by it and think it'd be cool to continue programming.

Don't mistake that I'm defending Visual Basic. The target market for VB is system admins and part time programmers who didn't really get the opportunity to get through all the heavy concepts of C++. The problem with VB is, You Know Who has pulled, pushed, squished, stretched and just about done everything it can to extend the capabilities of a simple and great learning tool into a "qualified" object oriented business architecture, and merged it with every application they release. It really has very little left that compares to the original BASIC.

There will be very few people in this thread who don't look back fondly on their first experience with BASIC as an enjoyable discovery into making computers do things that you thought was interesting and potentially entertaining.

And on the other hand you have Java. Which is like taking basic coffee and turning it into a nonfat half-caf no-whip caramel machiatto. Java adds as much complexity to the programming process as it possibly can, and on top of that doesn't even compile into code that's native to the hardware it runs on which makes it dramatically slower than that old interpreted BASIC program that you wrote on your old PC XT or in my case an Apple II. The fact that there are actual Java applications that I need to use on a daily basis (Eclipse) to do my job is astounding to me, and the speed of that software and it's memory requirements are equally astounding.

As a comparison, Photoshop CS3 uses up less processor time and less memory than does Eclipse, and Eclipse is a text editor. The latest version of Photoshop ships on DVD, and you can fit 3 copies of Eclipse and your prefered JVM on a CD-ROM. If I had my way I'd ditch Eclipse and write my code with trees and dye if it meant I didn't have to co-exist with Java. I'd rather code in Pascal.

---

### Post by jfinkels on 2007-08-25
> **SeanBlader said:**
> 
As a comparison, Photoshop CS3 uses up less processor time and less memory than does Eclipse, and Eclipse is a text editor. Eclipse is definitely NOT a text editor, it is an IDE; vi is a text editor :D

---

