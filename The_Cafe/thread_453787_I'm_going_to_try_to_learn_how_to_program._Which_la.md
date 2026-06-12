---
title: "I'm going to try to learn how to program. Which language do you recommend and why?"
date: 2007-05-24
forum: The Cafe
---

### Post by medicineman24 on 2007-05-24
Thanx

---

### Post by atlfalcons866 on 2007-05-24
i use eclipse it is free and open source i dont even know how to program someone recommeded to me

---

### Post by Znupi on 2007-05-24
It depends what you want to do. I'm *specialized* (well, self-taught, have been studying for over an year now, but I know almost as much as my bro knows, who is 7 years older and is a hired web developer) in web developing, so I'd recommend HTML, CSS, JavaScript, PHP, MySQL. This is what I know, and like, a lot. Right now I'm struggling with Python, and it looks reeaaaally nice, but it's syntax is a bit confusing, but it's fresh and I like it. Unfortunately, I don't have time to study because of school, so I'll have to wait for the holidays.

Anyway, if you're just starting off, and don't know the tiniest bit about programming, you should probably start with C++.

If you want to look into web technologies, [W3Schools](http://w3schools.com) is a good place to start. They really have some nice tutorials. At least that's where I first went.

---

### Post by melancholeric on 2007-05-24
Python.

Why? The syntax is simple enough. When you're beginning to learn programming, you don't want to waste time on learning obscure semicolon placement rules, you'd rather focus on the problem solving and getting things done.

Hello world in C++:
```

#include <iostream>
using namespace std;
int main()
{
    cout << "Hello world!" << endl;
    return 0;
}

```
And in python ?
```
print "Hello world"
```

And besides, once you learn one language, it's generally easy to move to new languages.

---

### Post by medicineman24 on 2007-05-24
So python or C++?  Pros Cons?

---

### Post by Znupi on 2007-05-24
Well, C++ is much more low-level. You can do basically anything in it. Even assembly coding (which, I think, can't be done in Py). So, theoretically, C++ is faster (because it's compiled, not interpreted), and lets you do more things.

On the other hand, Python is **much** simpler. Functions that in C++ you'd have to define yourself in a few pages of code, are already defined and you just have to call them. But it's slower, being interpreted, and doesn't let you do low-level stuff.

[SIZE=1]Correct me if I'm wrong[/SIZE]

---

### Post by melancholeric on 2007-05-24
> **Znupi said:**
> It depends what you want to do. I'm *specialized* (well, self-taught, have been studying for over an year now, but I know almost as much as my bro knows, who is 7 years older and is a hired web developer) in web developing, so I'd recommend HTML, CSS, JavaScript, PHP, MySQL. This is what I know, and like, a lot. Right now I'm struggling with Python, and it looks reeaaaally nice, but it's syntax is a bit confusing, but it's fresh and I like it. Unfortunately, I don't have time to study because of school, so I'll have to wait for the holidays.

Anyway, if you're just starting off, and don't know the tiniest bit about programming, you should probably start with C++.

If you want to look into web technologies, [W3Schools](http://w3schools.com) is a good place to start. They really have some nice tutorials. At least that's where I first went.
I personally wouldn't recommend C++ for a beginner, but I can see why some people do. I think that's a bit of a "tough love" approach: it forces you to learn all the low level stuff (like pointers), and that might be helpful on the long run.

But that's like recommending gentoo instead of ubuntu to a linux newbie. Well, you'll learn a lot whether you want to or not.

The only thing I find weird about python syntax is whitespace. But in the end you'll just indent code pretty much like you'd normally do without really thinking about it at all. But you don't need to use those curly braces ...

---

### Post by melancholeric on 2007-05-24
> **Znupi said:**
> Well, C++ is much more low-level. You can do basically anything in it. Even assembly coding (which, I think, can't be done in Py). So, theoretically, C++ is faster (because it's compiled, not interpreted), and lets you do more things.

On the other hand, Python is **much** simpler. Functions that in C++ you'd have to define yourself in a few pages of code, are already defined and you just have to call them. But it's slower, being interpreted, and doesn't let you do low-level stuff.

[SIZE=1]Correct me if I'm wrong[/SIZE]

The speed difference between interpreted and compiled languages is really insignificant. Unless you're coding an FPS game or something like photoshop, it really doesn't matter.

You know the one laptop per child project? The desktop environment (sugar) is written entirely in python. You'd think performance would matter given how low end the hardware is.

Remember, programmer time is more valuable than CPU time. So what if a few CPU cycles are wasted if development is faster.

And besides, python can be compiled to binary too if I recall correctly.

---

### Post by medicineman24 on 2007-05-24
> **Znupi said:**
> Well, C++ is much more low-level. You can do basically anything in it. Even assembly coding (which, I think, can't be done in Py). So, theoretically, C++ is faster (because it's compiled, not interpreted), and lets you do more things.

On the other hand, Python is **much** simpler. Functions that in C++ you'd have to define yourself in a few pages of code, are already defined and you just have to call them. But it's slower, being interpreted, and doesn't let you do low-level stuff.

[SIZE=1]Correct me if I'm wrong[/SIZE]

If someone can verify this I will shoot for C++

---

### Post by CautionaryX on 2007-05-24
I'd recommend starting off with either SQL, Java, or C++. Either one of them will give you a good introduction to programming concepts and there are a lot of free online tutorials for them. SQL is only used with databases though, so if you want to do more general purpose applications stick with C++ or Java. I haven't had any experience with C++ though, maybe I'll start learning it today.

Good luck!

[http://java.sun.com/docs/books/tutorial/]("http://java.sun.com/docs/books/tutorial/")
[http://www.sqlcourse.com]("http://www.sqlcourse.com")
[http://www.cplusplus.com/doc/tutorial/]("http://www.cplusplus.com/doc/tutorial/")

---

### Post by medicineman24 on 2007-05-24
Thanks for the luck and the links.  I'll try C++.
Edit: Actually I'm not so sure.  How much harder is C++ than python?

---

### Post by Znupi on 2007-05-24
Well, I started off with C++, and yes it did help me a lot. It will be hard at first, but once you get the hang of it, you should have no probs.

Python's white-space syntax is amazing. It forces you to write properly organized code. That's why I like it, I hate seeing programs like
```

function something(){intruction();
assign=value;
more_instruction(); another_instruction(parameter);third_instruction(paramater1, parameter2);
do_some_more(); and_again();}

```
My stomach churns when I see stuff like that. With Python, not anymore! :D

---

### Post by Znupi on 2007-05-24
It would be a good idea to get a teacher (maybe take classes?) at first. Just so you get the basics of programming. I hope you'll like your first "Hello World" program. I think I still have mine somewhere... written in Pascal... :D

---

### Post by melancholeric on 2007-05-24
> **medicineman24 said:**
> Thanks for the luck and the links.  I'll try C++.
Edit: Actually I'm not so sure.  How much harder is C++ than python?

It is **way** harder. But as some others have said, it will probably pay off. I'd still recommend python though.

Again, once you have learned one language properly, learning new languages is fairly easy.

Think of it this way: when you're first learning programming, do you want to learn semicolon or curly brace placement rules ... or do you want to learn to think like a programmer?

The former is (somewhat) language specific, the latter is universal. And far more rewarding.

edit: [How to think like a computer scientist](http://www.ibiblio.org/obp/thinkCSpy/).

---

### Post by medicineman24 on 2007-05-24
> **Znupi said:**
> It would be a good idea to get a teacher (maybe take classes?) at first. Just so you get the basics of programming. I hope you'll like your first "Hello World" program. I think I still have mine somewhere... written in Pascal... :D

Yeah I wish. I had signed up for programming classes @ school, and supposedly not enough people did so... they drop the class.  So, instead I'll hit the books and internet this summer.  9 Days left of School:D:guitar::D

---

### Post by Znupi on 2007-05-24
How old are you? I really suggest you start with C++, it will really ease up a lot when learning Py / PHP. You'll see that I'm right :).

[SIZE=1]What's so wrong with curly braces??[/SIZE]

---

### Post by CautionaryX on 2007-05-24
```

public class First {
public static void main(String[] args) {
System.out.print("Hello World!");
}
}

```

An example of the Hello World program coded in Java. In case anyone was wondering. :D

Python seems to be a little too simple. While I do like simplicity, sometimes simplicity makes it harder to customize certain attributes of a variable or function. It reminds me of the time I downloaded Visual Basic .Net 2005 Express from MS and was able to make a semi-functional web page viewer in 10-15 minutes. It was pretty cool but I felt like I hadn't really done anything and the code/programming environment did it all for me. It makes things easier to do, but not always easier to understand.

---

### Post by medicineman24 on 2007-05-24
I guess I'll begin with python since its syntax seems much simpler.  Will this keep me from any functionality available in C++ ?

> **Znupi said:**
> How old are you? I really suggest you start with C++, it will really ease up a lot when learning Py / PHP. You'll see that I'm right :).

[SIZE=1]What's so wrong with curly braces??[/SIZE]

16, Now I'm torn. Dangit I can't make up my mind

---

### Post by melancholeric on 2007-05-24
> **medicineman24 said:**
> I guess I'll begin with python since its syntax seems much simpler.  Will this keep me from any functionality available in C++ ?

Well, you won't do pointer arithmetic (for example) in python. But I can't imagine you'd want to, either ...

---

### Post by Andrewie on 2007-05-24
C/C++ they are hard, but once you understand them all the other languages will be easier for you

---

### Post by CautionaryX on 2007-05-24
I really can't say much about differences between Python and C++, but maybe you could try to learn both and learn the pros & cons of each.

I really commend you for wanting to program at that age though. I'm 17 and I started seriously learning Java and SQL at 16.

---

### Post by melancholeric on 2007-05-24
> **Znupi said:**
> [SIZE=1]What's so wrong with curly braces??[/SIZE]

Try coding with a Finnish keyboard layout for a while and you'll understand :p

There's nothing wrong with them, but I'd rather do without. Not like I love them. And well, they're really easy to get misplaced in one way or another, and that can cause some really funny bugs that are next to impossible to find. Python is just way easier with this: it's so easy to see the separate blocks when they're separated with indentation instead of braces.

---

### Post by Znupi on 2007-05-24
> **Andrewie said:**
> C/C++ they are hard, but once you understand them all the other languages will be easier for you

Exactly. That's the main reason I recommend C/C++, even though it's harder.

[QUOTE=CautionaryX]
I'm 17 and I started seriously learning Java and SQL at 16.
[/QUOTE]

I first started learning Pascal at the age of 9. C/C++ at 15. And suddenly, I discovered PHP, MySQL, JavaScript, HTML, CSS. Now I'm 16 and I've learned these quite fast, thanks to C++ which helped me **think** like a computer. So basically I know everything from socket programming in PHP in CLI to designing web pages with CSS.

Oh, but nothing is more important when trying to learn something new than loving it. I love programming. Even if I come home tired from school, depressed because I got an F, the first thing I do is start coding. I think that helped me more than anything else :popcorn:

---

### Post by %hMa@?b&lt;C on 2007-05-24
I started learing lots of shell (bourne again shell ftw!) at 13/14 when I was 15 I started learning python.  This summer, I plan to learn more python and begin C/C++. If I were you, I would begin with python and work your way up to the compiled languages.

---

### Post by Seidojohn on 2007-05-24
Does anybody think Ruby is a good place to start? 
I've got a *tiny* bit of experience (one class in college) with C++ and have been checking Ruby out for about a week. I was looking at different languages, and anything I read about Ruby couldn't say enough good things about it. It seems easy enough to learn too... Just wondering what people with actual experience thought. 
As for myself, I'm still debating, but I think I'll go back to C++. If only because I use KDE and I don't know how much help I'd be to the community if all I knew was Ruby.

---

### Post by Tundro Walker on 2007-05-24
> **melancholeric said:**
> ...besides, once you learn one language, it's generally easy to move to new languages.

Agreed.  At it's heart, most programming languages you'll use (unless specialized)  do the following...
[LIST]
[*]let you set variables to some values to store for later use
[*]use logic to branch off your program (if "this" then "that" otherwise "do this other thing")
[*]create "loops" to  cycle through something multiple times until a criteria is met (EG:  until you hit the end of the recordset, move to each row and add the words "Hello Kitty" to each column)
[*]let you re-use code sub-procedures or functions so you don't have to type the same code every time you want to use it (EG: If I have some code that goes through a recordset and adds "Hello Kitty" to each row, I can call it again and again for each recordset I send it, instead of having to type out that code each time I want to use it)[/LIST]I agree that you should start with a very easy language so you can focus on the basic structure, logic, loops, etc.  After you learn those basics, you'll find that the difference between languages is usually syntax, or object-oriented, etc.

Not to say that all programming languages are alike.  Some are more specialized for certain tasks.  But, personally, I'd start with a high-level language that does all the janitorial stuff (like memory management, etc) and get to know that.  Code a simple game with it.  Then, if you like, move on to a lower-level language, or jump to an alternate high-level language.  You'll find that once you have the basics, it's really just learning new programming syntax and nuances of the new language...the rest of the logic usually runs along the same lines, so it's easy to pick up new languages.  Unless you go from like Visual Basic (Gambas) to learning old-school C...then you'll need to learn additional things about managing your own memory and such.

---

### Post by n0dl on 2007-05-24
Personally I started off with perl. Good fun very useful language. I think what you need to read first is a good book or online doc on How To Think Like A Computer Scientist before you delve into coding. Understand the difference between static and dynamic types, what are variables, how computer memory works. Sort of get familiar with what a primitive type is. Understand what various programming paradigms are all about. I think once you understand this youll be able to pick your first language all by yourself.

---

### Post by ryanVickers on 2007-05-24
C++ is probably harder than most if your brand new to this, but it is by far the most powerful and widely useable in the field, If your considering it.  Many other things like Python, Java, and actionscript are less efficient and depending on what you are doing, the pros and cons would be different.  Flash is really easy, so is java after a bit, but check it all out.

---

### Post by maniacmusician on 2007-05-24
C++ will be a better choice in the long run.

It's a lot harder, and the chances that you'll fail at learning it are significantly higher. But if you succeed in mastering it, you'll have opened a gateway and will have the ability to do a lot more things than you believed possible.

---

### Post by techdude2007 on 2007-05-24
Visual Basic is good for beginners....many people in the world use Visual Basic.  RealBasic allows the developer to compile their program for Windows, Mac OS X or Linux.

Java is great since it allows the users to run the compiled program on any computer that have the Java Virtual Machine

C++ is the best, but hard to learn for some beginners

---

### Post by ButteBlues on 2007-05-24
> **Seidojohn said:**
> Does anybody think Ruby is a good place to start? 
I've got a *tiny* bit of experience (one class in college) with C++ and have been checking Ruby out for about a week. I was looking at different languages, and anything I read about Ruby couldn't say enough good things about it. It seems easy enough to learn too... Just wondering what people with actual experience thought. 
As for myself, I'm still debating, but I think I'll go back to C++. If only because I use KDE and I don't know how much help I'd be to the community if all I knew was Ruby.
Ruby is a *very* good and easy language to learn.

It's got the advantage of being object-oriented, but, like Python and other languages, can be ran in "script form" sans classes and such. The code is also ridiculously readable.

Ruby has strong GTK and QT bindings as well.


But the biggest edge Ruby has is Rails, which is a web development framework. It's insanely good and easy. :)

---

### Post by maniacmusician on 2007-05-24
> **ButteBlues said:**
> Ruby is a *very* good and easy language to learn.

It's got the advantage of being object-oriented, but, like Python and other languages, can be ran in "script form" sans classes and such. The code is also ridiculously readable.

Ruby has strong GTK and QT bindings as well.


But the biggest edge Ruby has is Rails, which is a web development framework. It's insanely good and easy. :)
is it really that easy? I mean, is it a good one to start out on? it sounds interesting and I'd like to give it a whilr.

---

### Post by n0dl on 2007-05-25
Ruby is a pretty spiffy language and it is fairly easy to learn. However I think you should start out with something that allows structured programming as well.

---

### Post by ButteBlues on 2007-05-25
> **n0dl said:**
> Ruby is a pretty spiffy language and it is fairly easy to learn. However I think you should start out with something that allows structured programming as well.
That's where Ruby's foundation in OO programming comes in. ;)

---

### Post by ButteBlues on 2007-05-25
> **maniacmusician said:**
> is it really that easy? I mean, is it a good one to start out on? it sounds interesting and I'd like to give it a whilr.
I like to think of it like a blend of C# and Python. :)

There's a really great tutorial [here](http://tryruby.hobix.com/) that actually simulates using a Ruby prompt and shows you how to accomplish some basic things.

Then there's always [_why's poignant guide]("http://poignantguide.net/ruby/") which is a more fun and carefree approach.

---

### Post by Znupi on 2007-05-25
I still recommend C/C++. Although hard to learn, it's low level and it helps you learn how a machine actually works. With Py, you won't be able to do that. You'll understand how memory is organized, and all sorts of interesting, low-level stuff. If you don't have the patience to learn it (it can be a pain in the *ss), you should start with a higher-level language, like Py, probably Ruby (it sounds nice, but I never used it), PHP, etc...

Anyway, the main point I want to make in this post is that I saw many people recommending that you first read a book before starting to code. **NO!** That's not a good approach! A book will only confuse you, and when you'll get your hands on the keyboard you won't know what to do and how to start. The best way to learn is using web-tutorials, and getting your hands dirty all the time, making small 'hello world' programs and such. At least that is the best way for me, I can't stand programming books.

---

### Post by regomodo on 2007-05-25
If you want to lose the will to live i couldn't recommend anything better than VHDL (not really programming tho)

---

### Post by ButteBlues on 2007-05-25
> **Znupi said:**
> I still recommend C/C++. Although hard to learn, it's low level and it helps you learn how a machine actually works. With Py, you won't be able to do that. You'll understand how memory is organized, and all sorts of interesting, low-level stuff. If you don't have the patience to learn it (it can be a pain in the *ss), you should start with a higher-level language, like Py, probably Ruby (it sounds nice, but I never used it), PHP, etc...

Anyway, the main point I want to make in this post is that I saw many people recommending that you first read a book before starting to code. **NO!** That's not a good approach! A book will only confuse you, and when you'll get your hands on the keyboard you won't know what to do and how to start. The best way to learn is using web-tutorials, and getting your hands dirty all the time, making small 'hello world' programs and such. At least that is the best way for me, I can't stand programming books.
I would never *recommend* C++ as a first language.

It's the equivalent of, "You're about to read your first book? Here's a copy of *War and Peace*!"

---

### Post by dodgePT on 2007-05-25
For starters, definitelly PHP, easy to learn (a few months study and you're all set).
Once you master PHP, try lower level language like C++.
When you understand C++, the other languages will be easier to learn, since some other languages are similar, only with mild changes in structure and syntax.

---

### Post by mips on 2007-05-25
"Hello World" comparison between languages:
[http://www2.latech.edu/~acm/HelloWorld.shtml]("http://www2.latech.edu/%7Eacm/HelloWorld.shtml")
[http://www.roesler-ac.de/wolfram/hello.htm](http://www.roesler-ac.de/wolfram/hello.htm)

---

### Post by Znupi on 2007-05-25
> **ButteBlues said:**
> I would never *recommend* C++ as a first language.

Then why do most schools first teach C/C++?

---

### Post by mips on 2007-05-25
> **Znupi said:**
> Then why do most schools first teach C/C++?

I actually think C/C++ is and excellent first language. It would teach you some pretty good programming habits which could be carried over to other languages. That might be one of the reasons it is taught so often in education establishments.

---

### Post by ButteBlues on 2007-05-25
> **Znupi said:**
> Then why do most schools first teach C/C++?

> **mips said:**
> I actually think C/C++ is and excellent first language. It would teach you some pretty good programming habits which could be carried over to other languages. That might be one of the reasons it is taught so often in education establishments.

C and C++ are very wide-spread, and once you learn them, you can easily pick up almost any language.


But, the fact of the matter is, it's still exactly like handing *War and Peace* to someone who's just beginning to read or asking someone who's just learning how to use a computer to compile their whole OS, kernel and all. In the end, sure, they stand to learn a lot. But it's gonna be stupidly hard to learn it because it's very complicated.

---

### Post by mips on 2007-05-25
> **ButteBlues said:**
> 
But, the fact of the matter is, it's still exactly like handing *War and Peace* to someone who's just beginning to read or asking someone who's just learning how to use a computer to compile their whole OS, kernel and all. In the end, sure, they stand to learn a lot. But it's gonna be stupidly hard to learn it because it's very complicated.

Agreed, but don't you think they will be better off in the long run having learnt C/C++ first ? They would take to other languages like a duck to water after that. I never learnt C but started with basic for a short while and then taught myself assembler out of books & source code I got on BBS' and I was like 15yrs old at the time. Only thing I learnt after assembler was pascal and I almost exclusively used assembler while studying electronic eng. After that I had no further interest in programming.

Is C really that hard to learn ?

---

### Post by saulgoode on 2007-05-25
> **ButteBlues said:**
> C and C++ are very wide-spread, and once you learn them, you can easily pick up almost any language.


But, the fact of the matter is, it's still exactly like handing *War and Peace* to someone who's just beginning to read or asking someone who's just learning how to use a computer to compile their whole OS, kernel and all. In the end, sure, they stand to learn a lot. But it's gonna be stupidly hard to learn it because it's very complicated.

I wouldn't disagree with reference to C++ but the C language is quite simple (many complain, too simple). Brian Kernighan's [Programming in C:  A Tutorial](http://www.lysator.liu.se/c/bwk-tutor.html) from 1974 lays out the basics in a manner that is easily apprehended and, though there have been changes over the last three decades, still gets the general concepts across (and those concepts apply to almost all other programming languages).

---

### Post by ButteBlues on 2007-05-25
> **saulgoode said:**
> I wouldn't disagree with reference to C++ but the C language is quite simple (many complain, too simple). Brian Kernighan's [Programming in C:  A Tutorial](http://www.lysator.liu.se/c/bwk-tutor.html) from 1974 lays out the basics in a manner that is easily apprehended and, though there have been changes over the last three decades, still gets the general concepts across (and those concepts apply to almost all other programming languages).
Right, but since syntax among languages is common enough to begin with, I always recommend starting with a high-level language.

Why? Because you get the same generic stuff from all languages out of the way with simple-to-learn, easy-to-read syntax. It let's people get a feel for programming in general before dealing with the complexities and oddities of low-level languages.

---

### Post by muguwmp67 on 2007-05-25
I am a big foe of C++ as an introductory  language.  It is a good tool for learning computer science and working on low level functions, but allows you to do too many things that can make your code unreadable.  

I'll probably get flamed, but I think Java is a great introduction to OOP.  It has all the capability that a new programmer needs, and an easier syntax than C++.  Yet, the syntax is close enough to C++ that transitioning to it (for a college course, for instance) is not hard.  Also, everything is an object in Java, so it forces you to learn OOP (unlike C++, where you can still code C-style)

---

### Post by medicineman24 on 2007-05-25
Thanks for all the advice.  Yes I understand the basics of computers and programming and have programmed simple things with python, batch, and my calculator :D during school.  I'm going to jump to C++ just as soon as finals are over. Thanks for all your help.

---

