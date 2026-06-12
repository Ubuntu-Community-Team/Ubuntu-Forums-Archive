---
title: "beginning programming/scripting"
date: 2011-10-03
forum: The Cafe
---

### Post by RememberWhenItRained on 2011-10-03
I'm an information systems major, so i figure i should start learning programming/scripting (what's the difference anyway?)

Should i start with something like PHP, or a more classic programming language like Java?

little to no prior programming experience; i tend to do better with a physical book in my hand...
what language would you recommend for starting to learn this stuff, and can you think of a title you'd recommend reading to help learn that language?

how hard is Python? is that harder than java? I've noticed a lot of Ubuntu apps use python...

(yes, i know, i'm a newb, but better late than never, right?)

---

### Post by nipunshakya on 2011-10-03
Well, if you wanna get started with the programming stuff, i would suggest you go with C programming language first . . . . most of the object oriented stuffs originated now are from the basics of C programming language... in fact, C++ language is the extension of C programming itself...and so is Java. So i suggest you to start with C. I've just started to learn Python(25 hrs. till now) . . . and having the basic idea of it...dont know much about it...but after learning C programming, i found that C++ is easy to learn( my personal experience). 
Anyways, I learned C from this book "C Programming,A Modern Approach by K.N King" goodluck.

---

### Post by ikt on 2011-10-03
> **WinuxUser said:**
> I've just started to learn Python

Python ftw!

---

### Post by F.G. on 2011-10-03
i would say c, c++ or python are all fine (i love them all), you do need to pick one and focus on it (once you have the concepts other programming languages are easy).

I started with C, which is easy to learn, though generally seems to only be used for difficult, low-level, super-tech programming. also c is not object oriented.

if you're not mainly focused on programming in your degree, but broader system design, then i would suggest learning a 'higher-level' language, like python or c++. also these are object-oriented, and will give you an idea about object-oriented things.
c++ and python are both quite fun to learn. i think python is probably easier, there are some really good google developer talks on python which you could learn from. 
i think you probably learn more from c++ (which is a really good basis for higher-level languages). for that i would suggest looking at the 'Schaum's ouline of programming in c++' book, it's pretty cheap, and has challenges and solutions.

regarding 'programming' and 'scripting', you get scripting languages, which are 'interpreted' (basically compiled and run line by line) and 'compiled' languages (where you compile the whole program, then run it). also generally the term 'script' refers to a single file, which you can run to do one specific thing, often quickly hacked together without the more complex design elements of a full 'program'. python is a scripting, interpreted language, c++ is compiled.

also surely this thread should be in 'programming talk'. did you look there?

---

### Post by RememberWhenItRained on 2011-10-03
> **WinuxUser said:**
> Well, if you wanna get started with the programming stuff, i would suggest you go with C programming language first . . . . most of the object oriented stuffs originated now are from the basics of C programming language... in fact, C++ language is the extension of C programming itself...and so is Java. So i suggest you to start with C. I've just started to learn Python(25 hrs. till now) . . . and having the basic idea of it...dont know much about it...but after learning C programming, i found that C++ is easy to learn( my personal experience). 
Anyways, I learned C from this book "C Programming,A Modern Approach by K.N King" goodluck.

interesting. Is C a lot easier than C++? I've heard ++ is a very difficult and demanding.

---

### Post by mörgæs on 2011-10-03
Moved to the cafe, as it is not a support question.

If you know HTML, getting into PHP would be a logical next step. If you want to learn object oriented, you can slowly introduce this to you PHP scripts when you are familiar with the basics.

---

### Post by RememberWhenItRained on 2011-10-03
> **ikt said:**
> Python ftw!
care to expound?

> **F.G. said:**
> i would say c, c++ or python are all fine (i love them all), you do need to pick one and focus on it (once you have the concepts other programming languages are easy).

I started with C, which is easy to learn, though generally seems to only be used for difficult, low-level, super-tech programming. also c is not object oriented.

if you're not mainly focused on programming in your degree, but broader system design, then i would suggest learning a 'higher-level' language, like python or c++. also these are object-oriented, and will give you an idea about object-oriented things.
c++ and python are both quite fun to learn. i think python is probably easier, there are some really good google developer talks on python which you could learn from. 
i think you probably learn more from c++ (which is a really good basis for higher-level languages). for that i would suggest looking at the 'Schaum's ouline of programming in c++' book, it's pretty cheap, and has challenges and solutions.

regarding 'programming' and 'scripting', you get scripting languages, which are 'interpreted' (basically compiled and run line by line) and 'compiled' languages (where you compile the whole program, then run it). also generally the term 'script' refers to a single file, which you can run to do one specific thing, often quickly hacked together without the more complex design elements of a full 'program'. python is a scripting, interpreted language, c++ is compiled.

also surely this thread should be in 'programming talk'. did you look there?

so between c++ & python, you'd say c++? i know i have to take Java as a major related class next semester (wouldn't hurt to get an early start or more advanced, but i don't think C++ is in the docket. I also have to take COBOL (which, apparently, is more current than i thought.)

good thought about the forum section. I figured it was a newbie question so i posted it here. I'll check over there. Perhaps a mod can move this thread if appropriate?

---

### Post by DangerOnTheRanger on 2011-10-03
> **RememberWhenItRained said:**
> care to expound?


Allow me.

Python is simpler, easier to learn, and overall more intuitive than C++; for example, here are 2 programs - one written in Python, the other, C++ - that both perform the same task: printing Hello World! on the screen:

Python:
```

print "Hello World!"

```

C++:
```

#include <iostream>
using namespace std;

int main()
{
  cout << "Hello World!";
  return 0;
}

```

Which looks simpler? Both are complete programs, and both accomplish the same task, but Python lets you do more with a smaller amount of screen space used. As you start to program more and more, you'll learn that the smaller a program is, the less chances there are of bugs hiding somewhere in the code. This is why Python code often (this is just my experience) has less bugs in it than C++, especially before the first test.

---

### Post by F.G. on 2011-10-03
> **RememberWhenItRained said:**
> care to expound?



so between c++ & python, you'd say c++? i know i have to take Java as a major related class next semester (wouldn't hurt to get an early start or more advanced, but i don't think C++ is in the docket. I also have to take COBOL (which, apparently, is more current than i thought.)

good thought about the forum section. I figured it was a newbie question so i posted it here. I'll check over there. Perhaps a mod can move this thread if appropriate?

ok,  so i would really suggest c++ (though i'm always learnering too). with c++ pointers you will get a feel for memory locations and passing values etc. also if you follow a good book you will cover some data structures too.

python is excellent. but if you carefully go through c++, i think everything will be alot lot easier,  with python and Java. so my personal recommendation would be c++.

---

### Post by RememberWhenItRained on 2011-10-03
Just talked to my Comp. Sci. professor today... he said that any of those three would work, but he would recommend Java or C++...

I'm thinking java for ease & simplicity's sake...

---

### Post by RememberWhenItRained on 2011-10-04
> **RememberWhenItRained said:**
> Just talked to my Comp. Sci. professor today... he said that any of those three would work, but he would recommend Java or C++...

I'm thinking java for ease & simplicity's sake...

any book recommendations for java? thanks.

---

### Post by vehemoth on 2011-10-04
I would recommend c++ if you want to get into making complex programs, or python, perl, lisp and some others are probably good. If you just want to get simple tasks done and want have a basic idea of writing programs, then I'd recommend bash or another powerful shell language.

If you are planning on making a career out of it or using it to learn something else then I'd choose a more mainstream language such as c++ or python.
Some people like c# and java but I wouldn't recommend either if you are planning on supporting linux though some will probably say the exact opposite.

If I didn't answer your question then sorry :)

---

### Post by Drenriza on 2011-10-04
> **RememberWhenItRained said:**
> I'm an information systems major, so i figure i should start learning programming/scripting (what's the difference anyway?)

Should i start with something like PHP, or a more classic programming language like Java?

little to no prior programming experience; i tend to do better with a physical book in my hand...
what language would you recommend for starting to learn this stuff, and can you think of a title you'd recommend reading to help learn that language?

how hard is Python? is that harder than java? I've noticed a lot of Ubuntu apps use python...

(yes, i know, i'm a newb, but better late than never, right?)

Well to answer your question i think i need to ask what you want to gain by the scripting / programming.

---

### Post by RememberWhenItRained on 2011-10-04
> **Drenriza said:**
> Well to answer your question i think i need to ask what you want to gain by the scripting / programming.

i suppose that's the problem - i don't have a specific endgoal in mind other than to enhance my computer knowledge and eventually be able to write programs (not sure what those would be though.)

I know i will have to take Java eventually, and PHP/MySQL but i kind of wanted to get a head start, though not sure *where* to start.

does that help at all?

---

### Post by keithpeter on 2011-10-04
> **RememberWhenItRained said:**
> I know i will have to take Java eventually, and PHP/MySQL but i kind of wanted to get a head start, though not sure *where* to start.

Hello RememberWhenItRained

Random suggestion here: have a look at processing

[http://processing.org/](http://processing.org/)

Processing encourages bottom up programming style (which is why I'm posting, most of the other suggestions have mentioned the formal top down type languages). See

[http://en.wikipedia.org/wiki/Top%E2%80%93down_and_bottom%E2%80%93up_design](http://en.wikipedia.org/wiki/Top%E2%80%93down_and_bottom%E2%80%93up_design)

and

[http://www.paulgraham.com/progbot.html](http://www.paulgraham.com/progbot.html)

A processing program or 'sketch' is a short thing that generates an output of some kind. Applications include art projects, data visualisation, audio demos &c. so each 'project' can be small and expploratory.

Processing produces Java which is then compiled by the java you have installed, you can show your work as an applet on a web page easily. Processingjs is in early development and produces javascript for inclusion on Web pages.

I'm suggesting that by getting 'stuck in' and producing small sketches and demos you will learn the basic control structures, encounter some bugs, learn how to solve problems, and how to use external libraries. All this knowledge is reusable in more formal study of Java or C++ later when you will also be learning larger scale design processes.

---

### Post by Drenriza on 2011-10-04
> **RememberWhenItRained said:**
> i suppose that's the problem - i don't have a specific endgoal in mind other than to enhance my computer knowledge and eventually be able to write programs (not sure what those would be though.)

I know i will have to take Java eventually, and PHP/MySQL but i kind of wanted to get a head start, though not sure *where* to start.

does that help at all?

To say you want to enhance your computer skills...... uhmm. It.s kind of hard since each language is better suited for specific tasks.

If you work in a Linux environment / server. I have found the following extremely useful.

Bash / Sed / AWK scripting for solving tasks that require to make small tools, for observation and e-mail tasks. Such as observing log files / incoming files / packages and alert me if anything fishy seams to be going on. And custom scripts to the firm, at where i work.

I have started to use C# a great deal.
Where one of my bigger projects is to make a ASP.NET site where we have a list of over customers. Logon credentials, ip addresses, system static information which specific users can edit. Along with dynamic info being gathered from over servers, where the goal is to display, server resource utilization. And have Bash / Sed /AWK scripts viewing logs and alert the site if anything critical is going on.

C# and Java is also close to one and other since C# is builded taking stuff from java and tweaking it a little bit. So if u can Java u can C#, if u can C# u can Java. Tometo / Tomato

Also the firm at where i work, they are creating a lot of great things in C. This is also navite to Linux as i remember. PHP is a server side language so if your into creating websites, thats very handy.

---

### Post by Pynalysis on 2011-10-04
Python :)

---

### Post by F.G. on 2011-10-04
so i'm going to reiterate what i said before. you just need to pick one, and focus on it, learding it well. then picking up other programming languages is fairly easy.

also, just so you know python, c and c++ are all native to Ubuntu.

processing sounds really interesting i might start looking into that. as a first language i would recommend that do something mainstream, as it will be more widely documented, and have a larger support community. also C programming is generally bottom up designwise.

---

### Post by kaspar_silas on 2011-10-04
> **keithpeter said:**
> 
Random suggestion here: have a look at processing
[http://processing.org/](http://processing.org/)
Processing encourages bottom up programming style (which is why I'm posting, most of the other suggestions have mentioned the formal top down type languages). See
...
I'm suggesting that by getting 'stuck in' and producing small sketches and demos you will learn the basic control structures, encounter some bugs, learn how to solve problems, and how to use external libraries. All this knowledge is reusable in more formal study of Java or C++ later when you will also be learning larger scale design processes.

Yip I'd go with that. Processing is a lovely and very rapid introduction to Java. (It's basically Java with loads of macros to make it easier for non-coders to, well, code) 

Plus with processing your code's output gives obvious "graphical" progress which is reassuring. O and like java you get excellent cross computability (including Android and browsers) for free. 

There is also a python core version. ([http://code.google.com/p/pyprocessing/](http://code.google.com/p/pyprocessing/)) 
But I haven't tested that.

---

### Post by RememberWhenItRained on 2011-10-04
Winux - I like your sig. - it makes me feel a lot better...

all this discussion is just making me more torn between what to choose. Ultimately, like some have said, I'll just have to pick one and run with it. (im always looking for the *best* one, which there really is no such thing.)

How compatible is Processing? just as compatible as java?
I guess my biggest problem is that i don't know what i want to program. If i knew that, narrowing a suitable language would be a lot easier.

I did some very basic vB back in middle school (7 ish years ago. yes, i know im young) but it never clicked (though i enjoyed it.)

I'm foremost looking for a book on HOW to program. I hate the books or lessons that are like: let's make a Hello World program! (yes, i know it's a classic.) Maybe that's why i disliked math so much - seems like much of that is teaching by example, without much explanation of why or how outside of the specific examples. Perhaps i just haven't encountered the right book yet... I want something that teach you the philosophy and how to program, so you can make your own stuff.   maybe i just learn differently from a lot of books out there...

comp. sci. stuff, though i enjoy it, does come quite as naturally (quickly) to me as it does to most who major in that kind of field, although i would consider myself fairly-ish smart. I don't know- teaching by example and example only never seemed to do it for me...

any suggestions/comments or am i just hopeless?

---

### Post by koenn on 2011-10-04
> **RememberWhenItRained said:**
>  teaching by example and example only never seemed to do it for me...

any suggestions/comments or am i just hopeless?

Programming is quite foreign to people, so learning by doing is often an effective way to introduce the concepts a programmer needs to understand. 
(imagine someone who's never seen a car in his life, and you need to teach them howto drive one ... wouldn't yuou start with showing them an actual car ?)

But if you like a more conceptual approach, there's books such as
[http://mitpress.mit.edu/sicp/full-text/book/book.html](http://mitpress.mit.edu/sicp/full-text/book/book.html)  (with video lectures: [http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/](http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/)  )
or
[http://catb.org/~esr/writings/taoup/html/](http://catb.org/~esr/writings/taoup/html/)

I'm not promising these will teach you how to write a program.

---

### Post by keithpeter on 2011-10-04
> **RememberWhenItRained said:**
> How compatible is Processing? just as compatible as java?
I guess my biggest problem is that i don't know what i want to program. If i knew that, narrowing a suitable language would be a lot easier.

Hello RememberWhenItRained

Processing is not a mainstream programming language. I'm guessing that is what you mean by 'compatible'. 

It is a system for data visualisation and producing small graphical programs, 2d, 3d and animated. Mainly used by media artists, and as was said above, it makes Java easier to work with. 

The 'target' of a processing program is a Java .jar file and Processing will generate the .jar file and the html page you need to display your work as an applet. 

I suggested Processing because it would enable you to gain experience of producing code that works, solving small problems, while all the time you have visual products to show for your efforts. I imagined that this 'small scale' experience of the details would compliment any future 'formal' programming training in C++ or Java. Those courses tend to focus on the larger structural issues. 

An excellent example of what I'm going on about is the tutorial on the processingjs site at

[http://processingjs.org/reference/articles/PomaxGuide](http://processingjs.org/reference/articles/PomaxGuide)

This tutorial develops several major concepts in programming in a step by step way with a simple 'toy' example. That seems to be the processing way of doing things. I suggested it simply as an alternative to the other suggestions!

Not knowing what to program implies that you perhaps try some small projects - I teach maths and data visualizations are always popular with students (hence my own faltering steps with processing and R) and provide well defined tasks that do not take ages to get working.

Good luck!

---

### Post by juancarlospaco on 2011-10-04
FYI Oracle permanently forbidden distribution of Java VM with Linux,
also start charging $$$ for Closed Plugins on programs.

I say try Python.[ You got 30 Seconds...?]("http://www.youtube.com/watch?v=vfzz36Hbetg")

---

### Post by RememberWhenItRained on 2011-10-06
> **juancarlospaco said:**
> FYI Oracle permanently forbidden distribution of Java VM with Linux,
also start charging $$$ for Closed Plugins on programs.

I say try Python.[ You got 30 Seconds...?]("http://www.youtube.com/watch?v=vfzz36Hbetg")

private video... shame. 

i got a Java book since i know i will have to take that next semester (got the textbook for next semester.)

I will also have to take COBOL (ugh)

though I am curious about Python...it looks easier, and very functional. How do python and java compare as far as functionality? can they both do the same amount of stuff roughly?  I know that Java is good for graphics & webs...

what about more scripting stuff? automated searches that return results in a file, programs that can search for and pull data off the web into the program (such as a forecast)... would Python work  well for this or is Java better?

---

### Post by ninjaaron on 2011-10-06
I'm not a programmer, so you shouldn't listen to me, but in my ignorant opinion, if you are a Linux user (or OSX, naturally), and you are interested in working with any kind of code, you should learn bash scripting in addition to a more powerful language.  Bash is an invaluable tool in setting up a working environment for the power user on on any *nix machine, and it can still be extremely powerful because of it's ability to pipe all of your other programs together.  Many programmers will mock-up programs or functions in bash before they code them in a more sophisticated language.  Bash can also use functions of other scripting languages like Perl, Python, AWK, SED, etc.  Bash basically has all of the resources of any program installed on your system at it's disposal.  If you use it for a while, you'll really begin to understand this part of the 'Unix Philosophy': "Write programs to handle text streams, because that is a universal interface"

If you want to become a serious programmer, you will eventually outgrow bash for more flexible and portable languages, but the skills you learn with it will still apply, and I don't know of any other language that gives the user so much power after learning only a few short commands.  Even when you do start doing large projects in other languages, you will continue to use bash scripts for all kinds of stuff around your home system.

Bash is also great for really digging into the guts of your system.  Many of the core system utilities in Linux, from the boot process to persistent daemons, to desktop environment variables... they are all just simple plain text bash files giving the orders (often to other bash scripts).

It's totally indispensable for the Linux geek.

[edit]
And whatever you do, when you start working with compiled languages, be a good chap and make sure they take text input and produce text output that is usable for bash scripts.  Linux users will love you forever if you just do that.

---

### Post by simpleblue on 2011-10-06
Another vote for C++.

Most of Linux is written in C and C++. GTK is mostly written in C. KDE and QT are written in C++. The Kernel is written in C, with a tiny bit of assembly to enable drivers. Just to give you an idea about their position in Linux and Linux based OS's.

Sorry for the lowball to Python, but I have to throw this in here. I made a mistake learning Python first and wondering why my game was so slow even after asking on forums for information. Python is not nearly as efficient as C, C++ or Java. In fact, C and C++ are about 40x faster than Python according to this benchmark of several benchmarks:

[http://shootout.alioth.debian.org/u64q/which-programming-languages-are-fastest.php](http://shootout.alioth.debian.org/u64q/which-programming-languages-are-fastest.php)

That's equilivant to running a program on a 60Mhz computer vs a 2.2Ghz computer. Now, it would not be prudent to let speed be a deciding factor. I think Python is the most fun and beautiful language out there, but when you really really need it most...

So, that being said, If you were to learn either C or C++ I would recommend C++ as it teaches you far better programming habits as it is an Object Oriented Programming language and C is not... My next suggestion would be to learn C or Java.

Btw, if you are feeling overwhelmed, just start with Java as you'll need to learn it anyways. Might as well get a headstart. Anyways, Java is fast and powerful. Awesome for games too!

Don't dwell on it though, get out there and try something - Open Source needs you! ;)

---

### Post by pr3zident on 2011-10-07
Python +1 learning python now nice language

---

### Post by magsnus on 2011-10-07
Python is simpler, easier to learn, and overall more intuitive than C++; for example, here are 2 programs - one written in Python, the other, C++ - that both perform the same task: printing Hello World! on the screen:

Python:
```

print "Hello World!"

```Pure Basic vibes!

---

### Post by F.G. on 2011-10-07
magsnus you appear to have left out the c++ program.

here:

```

#include <iostream>
using namespace std;
int main(void){
cout << "hello world" << endl;
return(0);
}
```

this can actually be a bit more concise, but should show the kind of difference between a lower level/higher level language.

---

### Post by RememberWhenItRained on 2011-10-07
poll added

---

### Post by BrokenKingpin on 2011-10-07
I am not sure why you would start with C at this point. OOP is pretty much the standard programming paradigm, so why not start with a language that better supports it. After learning C++, if you ever needed to go back and do C programming, it really wouldn't be hard to pick up.

I personally recommend starting with C++ or C#. Being a Linux user C++ may be the better way to go, but C# is great with the Mono framework, even though it gets a lot of hate just because it was a Microsoft technology. With the MonoDevelop IDE you can easy create GTK applications in C#.

---

### Post by rg4w on 2011-10-07
FWIW, In Kyle Rankin's book on Ubuntu Server he wrote that one of the considerations in Ubuntu's design was that Python could be its lingua franca.

I don't use Python myself yet, but I've seen some nice stuff made with it and it seems reasonably easy to learn.

---

### Post by mikaelcrocker on 2011-10-07
I would go with C++ since it's a compiled language and will teach you some really basic fundamentals.

Python, PHP, Ruby etc are interpreted languages, and easy to pick up, so start with C++ learn the syntax and you can learn any language!!

---

### Post by kvvv on 2011-10-07
C -> Java/C# -> Python are for different purposes and are all good languages.

AFAIK, PHP/MySQL is used only for web server scripting albeit it's the most popular solution in that domain.

---

### Post by RememberWhenItRained on 2011-10-07
i honestly don't understand why people are recommending to start with C++. From what I understand, it's very demanding syntactically and overall not an easy language to learn. Am i wrong? maybe it just comes more naturally to some.

I ordered a Java book so will start that soon, but from what I hear from you all and have read, it looks like Python might be worth looking into. It can do a pretty broad range of stuff right? Right now i'm mostly interested in automation & web data retrieval. Overall though, i want to learn a language that's versatile and comprehensive. Java seems to fit that bill well (as does C++ but im not going to start with that.)

I imagine it would be detrimental to try and learn two languages at the same time, so i'm going to have to choose between Python or Java I imagine. Java makes more sense as I will have to use that come January. But i do  like how Python looks very clean and simple; it seems it would be conducive to rapid development (reminds me a lot of Visual Basic, but i hate how VB seemed not very versatile and limited as far as platform - MS and stuck with those forms. click this button and check this box. i don't want a box :()

Thoughts?

Thank you all very much for your input thus far.

P.S. - @SimpleBlue - as flattering as your comment about open source needing me was, i don't think i'm that good. On the off chance that i do make something usable/half decent (don't hold your breath folks,) yes, people will be seeing the code. And then making it ten times better. Because that's how open source works:P.

---

### Post by sarton85 on 2011-10-07
I am no programmer. I used to write HTML/CSS for webdesign, but these are of course no serious programming languages...

Just started with learning some basic Python in Vim last week. I have never used Python nor Vim, so I am having a double learning experience, but I like it. I like Python's simplicity over other languages like C++. I tried C++ before, but even the basics seemed to blow my mind.

---

### Post by F.G. on 2011-10-07
on a non programming related point, if you're going to learn java anyway, it will benefit your skill set more in the long run to have another programming language.

sounds like you're intimidated by c++, which you really shouldn't be. to learn any language you'll need some time and patience to methodically learn it and most c++ tutorials / books are pretty spoon-fed.  

I would certainly focus on one at a time, but you can learn loads of python in just a couple of weeks if you want to. also (sorry if this sounds patronising), but time procrastinating could be time learning, and it doesn't really matter what you start with (just so long as you start).

---

### Post by koenn on 2011-10-07
> **RememberWhenItRained said:**
> 
I imagine it would be detrimental to try and learn two languages at the same time, so i'm going to have to choose between Python or Java I imagine. .
Learning 2 languages at the same time is not such a bad idea. A school I went to tought VB and C++ simultanously in their beginner courses. (It's been a while, last thing I heard they switched to VB.net and Java).

The good thing about such a combination is that it helps you focus less on learning the language and think deeper about programming. That is, if you take the opportunity tp compare the languages, see how they handle the same issues in different ways, or ask yourself why one does things the other doesn't 
(why doesn't VB have linked lists ? Or what are they good for, what's the reason for C++ having them ? ? and if a "string' is actually an array in C++, what is it in VB ? and how affects that knowledge the way you work with strings in that language ? ... and so on)

The other advantage was that VB offers quick satisfaction, you learn to drag and drop a small application together fairly quickly with minimal hand-written code, and you can use all sorts of built-in facilities to easily access files and querydatabases - it's easy to build an application that way. 
It's a lot harder in C++ where everything is more low-level and you have to do a lot more "by hand". But at least this shows you the lower levels, which helps you think about them. 
Learning both gives you both advantages: motivation by quick progress in one, by deeper understandiung in the other. 


So I suppose Python and C++ wouldn't be a bad choice. You might replace C++ with Java, but Java already hides away (or simply doesn't have) some of the things that make C++ interesting.

---

### Post by simpleblue on 2011-10-07
[FONT=Arial]> **RememberWhenItRained said:**
> i honestly don't understand why people are recommending to start with C++. From what I understand, it's very demanding syntactically and overall not an easy language to learn. Am i wrong? maybe it just comes more naturally to some
C++ is not hard to learn. If you want an example of a challanging language then try Assembly.

One thing to consider is that C++ has much more support then Python. This may not sound that important until you want to find a good book to buy on a particular programming subject and there is not that much out there. Another thing about Python is that right now there are two versions of it. Do you use the older 2.x version that currently has much much more support, or do you learn the new 3.x version? At the very least you'll need to learn the differences between them to know if you can run the code. This is because Python is not standardized. Seems like a small annoyance until you want to try cool looking programs on the net and are denied or have to switch between two versions of Python. C++ does not have that problem as it's been standardized for the last 14 years. Even the new 2011 C++0x is compatible with C++. They made it easy.[/FONT][FONT=monospace][FONT=Arial][FONT=Arial]
[/FONT][/FONT][/FONT]

---

### Post by RememberWhenItRained on 2011-10-08
> **simpleblue said:**
> [FONT=Arial]
C++ is not hard to learn. If you want an example of a challanging language then try Assembly.

One thing to consider is that C++ has much more support then Python. This may not sound that important until you want to find a good book to buy on a particular programming subject and there is not that much out there. Another thing about Python is that right now there are two versions of it. Do you use the older 2.x version that currently has much much more support, or do you learn the new 3.x version? At the very least you'll need to learn the differences between them to know if you can run the code. This is because Python is not standardized. Seems like a small annoyance until you want to try cool looking programs on the net and are denied or have to switch between two versions of Python. C++ does not have that problem as it's been standardized for the last 14 years. Even the new 2011 C++0x is compatible with C++. They made it easy.[/FONT][FONT=monospace][FONT=Arial][FONT=Arial]
[/FONT][/FONT][/FONT]

makes sense. i downloaded the the 2.x version sense it seems more compatible and has more support.

---

### Post by Lars Noodén on 2011-10-08
perl needs to be on the list.  It's part of every system and is used heavily for web services.  It's the glue that holds the net together.  There are over [20,000 perl modules in CPAN](http://www.cpan.org/modules/01modules.index.html), each doing something different.  If you're doing something, odds are that there is a perl module for it.

---

### Post by RememberWhenItRained on 2011-10-08
> **Lars Noodén said:**
> perl needs to be on the list.  It's part of every system and is used heavily for web services.  It's the glue that holds the net together.  There are over [20,000 perl modules in CPAN](http://www.cpan.org/modules/01modules.index.html), each doing something different.  If you're doing something, odds are that there is a perl module for it.

unfortunately i can't edit poll options after it has been published can i?

---

### Post by Lars Noodén on 2011-10-08
> **RememberWhenItRained said:**
> unfortunately i can't edit poll options after it has been published can i?

Can you try?

---

### Post by RememberWhenItRained on 2011-10-09
> **Lars Noodén said:**
> Can you try?

i did. no luck.

---

### Post by scitron on 2011-10-09
I'm not sure why you are struggling with your decision much. 

 If you have to learn Java for your class in January well it seems you should start now and you'll be that much farther ahead when classes begin.

---

### Post by jonkiribati on 2011-10-09
Python is the best first language to learn. It's really easy and if you want to switch to C++ or PHP or Java or whatever you want it'll be easy.

---

### Post by RememberWhenItRained on 2011-10-09
> **scitron said:**
> I'm not sure why you are struggling with your decision much. 

 If you have to learn Java for your class in January well it seems you should start now and you'll be that much farther ahead when classes begin.

yes, that's what i'm going to do. I was thinking that it might be easier to do python first since programming doesn't come all that naturally, but it's kind of stupid to start with that & have to switch come January. Java it is.

Python might be for picking up later. Or i wonder if, once learning some java, i won't feel the need to  learn Python.

---

### Post by RememberWhenItRained on 2011-11-01
well apparently it's going to be C now, then Java. I had to make schedule changes and now, i am taking "Introduction to Programming and Algorithms"  which uses C. I will be taking Java in the fall, then COBOL in the Spring. (then PHP/MySQL and ASP.net later)

it's gonna be a long year...

---

### Post by danbuter on 2011-11-01
If you're going into IT and are focused on Linux, I'd recommend learning BASH, Perl, and C.

---

### Post by F.G. on 2011-11-01
> **RememberWhenItRained said:**
> well apparently it's going to be C now, then Java. I had to make schedule changes and now, i am taking "Introduction to Programming and Algorithms"  which uses C. I will be taking Java in the fall, then COBOL in the Spring. (then PHP/MySQL and ASP.net later)

it's gonna be a long year...
glad you finally picked one. sounds like you've got a busy year ahead.

the thing about C is that it's easy to learn, but difficult to use well, which actually makes it an ideal place to start. also you can focus on the basics of control structures and memory, and not worry about the whole object-oriented thing and privacy.

i'd recommend "schuam's outline of programming with C" but i'm sure and book will do.  
good luck, and have fun.

ps. also you don't have to do anything to start programming (ubuntu already has a C compiler, gcc).

---

### Post by RememberWhenItRained on 2011-11-02
> **F.G. said:**
> glad you finally picked one. sounds like you've got a busy year ahead.

the thing about C is that it's easy to learn, but difficult to use well, which actually makes it an ideal place to start. also you can focus on the basics of control structures and memory, and not worry about the whole object-oriented thing and privacy.

i'd recommend "schuam's outline of programming with C" but i'm sure and book will do.  
good luck, and have fun.

ps. also you don't have to do anything to start programming (ubuntu already has a C compiler, gcc).

thank you good sir, you are most helpful.

out of curiosity, why exactly do you say it's an ideal place to start if it's difficult to use well?

---

### Post by F.G. on 2011-11-02
so, i guess i meant 'any book will do'

but, regarding C you have to learn to be a bit careful with things like memory, also you don't get given a bunch of methods to do all the work for you. you learn a lot more about programming.
I think its a good place to start, probably because i started with C. but also it will cover things all programming languages use , without confusing the issue by talking about things like 'closures', 'maps', 'hashes', 'classes' and 'objects'.

I didn't mean that C is difficult to use, it's just hard to do as much as quickly as you can with a high level language, but you might as well use Word if that the aim.

then again, don't listen to me. just get stuck in, it's the only way.

---

### Post by F.G. on 2011-11-02
so i thought about you starting with C, and here's something trivial i wrote, when i was supposed to be doing something else, it's a program which includes headers, principal code structure and if statements (as well as cheeky system calls, which will also work on windows incidentally, i included the windows and linux ones in the code):
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(){
 
char ent;
while (ent != 27){
if (system("cls")) system("clear");
printf("\n\t <('.'<)\n");
usleep (500000);
if (system("cls")) system("clear");
printf("\n\t<( '.' )>\n\n");
usleep (500000);
if (system("cls")) system("clear");
printf("\n\t (>'.')>\n");
usleep (500000);
if (system("cls")) system("clear");
printf("\n\t<( '.' )>\n\n");
usleep (500000);
if (system("cls")) system("clear");
printf("\n\t <('.'<)\n");
usleep (500000);
if (system("cls")) system("clear");
printf("\n\t<( '.' )>\n\n");
usleep (500000);
if (system("cls")) system("clear");
printf("\n\t (>'.')>\n");
usleep (500000);
if (system("cls")) system("clear");
printf("\n\t<( '.' )>\n\n");
usleep(500000);
if (system("cls")) system("clear");
printf("\n\t (>'.'<)\n\n");
usleep(500000);
if (system("cls")) system("clear");
printf("\n\t<( '.' )>\n\n");
usleep(500000);
if (system("cls")) system("clear");
printf("\n\t (>'.'<)\n\n");
usleep(500000);
if (system("cls")) system("clear");
printf("\n\t<( '.' )>\n\n");
usleep(500000);
} 
return(0);
}

```
if you copy it into gedit, save it under program.c then type:
```
gcc -o prog program.c

```
then run:
```

./prog

```
you should have just compiled and run a C program (and you should see a dancing penguin).

---

