---
title: "Summer Holidays means CODING."
date: 2010-07-09
forum: The Cafe
---

### Post by spoons on 2010-07-09
Righto, so summer holidays. Now I have some books, but I'd not had much time to work through them. What I have is:

C For Dummies All In One Desk Reference Edition (2004)
Beginning OpenGL Game Programming (2004)
80x86 Assembly Language and Computer Architecture (2001)

Now... some of these books are getting on a little. But still, 'm hoping to use my summer to explore them. I'm learning C right now, followed by the OpenGL book. (which is only OpenGL 1.5)

Only thing that worries me is the age of the Assembly language book. 2001, and it's designed for MASM. Fortunately I have a Windows 7 environment, but it's 64-bit, and I don't know if the MASM compiler is 16-bit or anything. If anyone could suggest a compatible alternative, I'd be happy. :) I'll try this one last.

I'm hoping to become quite competent in all of these! I'd like to develop a game of some kind. The Assembly book will be useful for other things.

So, is anyone else doing the same as me? How's it going so far?

---

### Post by Penguin Guy on 2010-07-09
C? 3D game? Open GL? Assembly?? I started out like that, and trust me - you'd be better starting with a 2D game in Python instead.

As for what I'm doing this summer, I'll be continuing development on some 2D Python games I'm working on: Pythons (a snake game in the very early stages of development), and [Blobber]("https://launchpad.net/blobber").

Out of interest, why did you choose those languages?

---

### Post by theraje on 2010-07-09
Er, yeah. Start smaller. C is a chore to learn, C++ more so (be clear - C and C++ are not the same language... you will have to do a lot of "unlearning" to make a switch). Neither of those is a spectacular starting language.

As for OpenGL, you need to know a LOT of math to do anything special. Try doing something simple first, and work your way up.

I say learn to draw an image to the screen first, and then build on that, to learn new things as you go along. Your code will be horrendous if you're completely new, so just keep refactoring, and do your best to use good practices (indentation, descriptive variable names, useful comments, etc.). Keep going, and you'll (eventually!) make a game.

Just don't try to take over the world (or learn how to program games) overnight. :)

---

### Post by theraje on 2010-07-09
Oh, sorry for the postcount++, but I have another tidbit of information:

Don't bother learning assembly anytime soon. Game development has all but forgotten assembly, as machines have gotten more robust, and cross-compatibility is becoming (a little) more mainstream. Worry about getting your game done, and THEN go back and optimize.

---

### Post by spoons on 2010-07-09
Hello everyone, thanks for the input. I tried Python, Ruby, C, and I found I liked C the most. I preferred the more structured and strict nature of C - it feels more comfortable.

Also, I don't intend to use Assembly for games. I am very interested in the development kits shown off on hackaday and the like and assembly seems to play an important part. Plus I just find it very interesting in general.

I picked things I would be interested in, because I figured if I'm interested in it I'll get further with it. I just don't have any interest in Python, really. I guess I like things more hands on.

Again, thanks for the replies. I'll let you know how things go. This C book however is quite fun thus far - lots of small, simple steps and gags built into the programs. (such as one example, listing the seven dwarves)

---

### Post by theraje on 2010-07-09
Ah, that changes things. If you like C, then learn C. C is a good language, as a buntload of libraries use C-style interfaces. But, you do lose out on some stuff like OO and STL.

But then again, if you choose to stick with one thing, you can't have it all, know what I mean? :)

Good luck! (especially learning assembly!) :D

---

### Post by spoons on 2010-07-09
Thank you very much! So far I've learned things like scanf, printf, if/else, integers, floats, things like that. The next section is on loops. I'm using NetBeans as my IDE - more comfortable than Visual Studio, and multiplatform. Once I've worked through all the exercises in this book I've got some command-line programs I want to make before moving onto OpenGL.

One thing I've found so far about programming languages - they're easier than I expected!

---

### Post by theraje on 2010-07-09
You sound like an apt pupil then. :) Always a good thing. Still, it takes a lot of effort (and likely hair-pulling) to learn a language and learn it well. Then there's the fun of learning other people's coding schemes... :P

I remember when I started programming, I had a lot of trouble with C++ (I never tried C). It took a long time of mucking with other languages before I finally got decent at it, although my ability to get things that worked quickly was a strong suit of mine. I was writing my own games within a few weeks after the start of my first programming class in college. Still, it took a while before I could tolerate C++.

I think the most important thing is to have a structure you are comfortable with. Language is not important, as everyone will have their preference - so don't let anyone discourage you from learning what you want to learn... as long as you know what you're getting yourself into. ;)

---

### Post by LeifAndersen on 2010-07-09
@spoons.  It's great to see another person getting into coding.  Get ready for a world of fun (and at times, pain).  Although I'm not the best person to judge, I think C is a fine programming language, just as long as you don't expect anything cool looking very soon (at least if you're just learning).  You could probably build something with python much quicker, but if you like C, go for it. ;)

@theraje:  You can do OOP in C, structs work very similar to classes (afaik anyway, and yes, I know there are differences).  You can store parents as a pointer.  Although I do admit, it's very 'hands on', which while it's a good thing for learning, IMO anyway, for rapid development, it's not so good.  Also for the record, I prefer the syntax of generic C structs, as apposed to Java generics or STL.  (Although I do conform to the language and use them).

---

### Post by LeifAndersen on 2010-07-09
@sppons, oh, I also forgot to mention, even though it's much easier to make programs in languages such as python (seeing as (imo) python is effectively runnable pseudocode), python does have it's place.  In places where speed isn't crucial (unless you're using python libraries made in C, those count as C, even though you're using a python interface. ;) ), python is very good, especially in today's world where rapid development is very important.

---

### Post by spoons on 2010-07-09
> **LeifAndersen said:**
> @sppons, oh, I also forgot to mention, even though it's much easier to make programs in languages such as python (seeing as (imo) python is effectively runnable pseudocode), python does have it's place.  In places where speed isn't crucial (unless you're using python libraries made in C, those count as C, even though you're using a python interface. ;) ), python is very good, especially in today's world where rapid development is very important.

Well I understand Blender uses Python for it's scripts and things, and 3D modelling is quite interesting.

I'd like to make a command line program that can compress files with zlib. but with an unpacker built in. But that's advanced for now - I need to learn my pointers and mallocs first! :P

---

### Post by chessnerd on 2010-07-09
I, too, am programming this summer (doing some right now). And I'm also trying to learn more languages.

I am also trying to make a game, however, I'm using Java to do it. I've studied Java for 2 years, and I know it pretty well. Plus, I like to code using Eclipse in Ubuntu, but I'll be giving the game to people who use Windows, so it should be cross-platform anyway.

I'm also trying to learn Python. I bought a book on Python at a discount book store that looks at example projects and breaks them down. I'm also using a website called CodingBat to practice the basics. So far, so good.

I agree with you about stricter languages. Java is quite strict and I prefer that to Python's "freeness". Heck, you don't even have to declare what type your variables are going to be. That's just messed up. ;)

I want to learn C, but haven't found any good books for learning it. There are tons of C++ and C# books, but few on C. My cousin took a C class at college last year while I was taking my Java class. He's professed some interest in Java, so I'm hoping that he and I an get together and teach each other what we know.

By the end of college, I want to be fluent in Java, Python, and C and then I want to learn some Perl and Ruby. Not so crazy about Assembly, but if I really like C, I might try to learn some of that as well.

Basically: Coding is fun. End of story. :D

---

### Post by spoons on 2010-07-09
> **chessnerd said:**
> I, too, am programming this summer (doing some right now). And I'm also trying to learn more languages.

I am also trying to make a game, however, I'm using Java to do it. I've studied Java for 2 years, and I know it pretty well. Plus, I like to code using Eclipse in Ubuntu, but I'll be giving the game to people who use Windows, so it should be cross-platform anyway.

I'm also trying to learn Python. I bought a book on Python at a discount book store that looks at example projects and breaks them down. I'm also using a website called CodingBat to practice the basics. So far, so good.

I agree with you about stricter languages. Java is quite strict and I prefer that to Python's "freeness". Heck, you don't even have to declare what type your variables are going to be. That's just messed up. ;)

I want to learn C, but haven't found any good books for learning it. There are tons of C++ and C# books, but few on C. My cousin took a C class at college last year while I was taking my Java class. He's professed some interest in Java, so I'm hoping that he and I an get together and teach each other what we know.

By the end of college, I want to be fluent in Java, Python, and C and then I want to learn some Perl and Ruby. Not so crazy about Assembly, but if I really like C, I might try to learn some of that as well.

Basically: Coding is fun. End of story. :D

If you want to learn C, there's this book called C For Dummies: All In One Desk Reference by Dan Gookin. I've got it and it's a great book. About 700 pages of lessons. It eases you in really well. Made slightly more to the American market than the British with pounds and feet (for some of the examples) so I guess it's right up your street! I've not got that far through it, but I'm enjoying it so far.

Who knows you guys, you might see contributions of mine in Ubuntu one day. ;)

---

### Post by chessnerd on 2010-07-09
> **spoons said:**
> If you want to learn C, there's this book called C For Dummies: All In One Desk Reference by Dan Gookin. I've got it and it's a great book. About 700 pages of lessons. It eases you in really well. Made slightly more to the American market than the British with pounds and feet (for some of the examples) so I guess it's right up your street! I've not got that far through it, but I'm enjoying it so far.
The online reviews seem to agree with you. I've generally found the Dummies books to be useful, and if the book is good enough for you, it's good enough for me. :)

I had seen this book at Barnes and Noble a few times, but the $35 price tag deterred me. However, I was able to find it cheaper online. I'll probably order it.

> **spoons said:**
> Who knows you guys, you might see contributions of mine in Ubuntu one day. ;)
Stick with it and I'm sure we will.

As a famous starship captain once said to a Mintakan who dreamed of her people becoming space-fairing:
[QUOTE=Captain Picard]Of that I have absolutely no doubt.[/QUOTE]

---

### Post by LeifAndersen on 2010-07-09
@chessnerd (love the nick by the way):  If you want a book to learn C...you've got to get K&R (also called "The C Programming Language"), unless you're trying to build a C compiler, it's by far the best C book out there.  (The only reason I didn't recomend it to spoons is because it's not meant as a first language book.  It works as a second language book, even if it's a language in a completely different area, but it's a bit steep for your very first language.  As for Java vs. python...there are advantages and disadvantages.  The advantages of java's strict, strongly typed system is that it's secure (secure in the sense that you're much less likely to make a mistake), but on the other hand, pythons strong duck typed system is fast to make.  Which suites me well for what I'm doing at the moment.

@spoons.  Yup, blender's API is python, although 'most' of the API was written in C.  (At least the 2.5x library is, I haven't delved much into the 2.4x library).  I'm actually building regression tests for blender at the moment... ;)

---

### Post by theraje on 2010-07-09
> **LeifAndersen said:**
> If you want a book to learn C...you've got to get K&R (also called "The C Programming Language")

Ah! I was trying to remember the name of that book... Mostly the K&R part... thanks, Leif! :)

---

### Post by lisati on 2010-07-09
I've been tinkering with a little bit of coding too, mainly PHP for my website, and discovered that PHP's strstr() function works a bit differently to what I was expecting. 

Speaking of assembler, I'd suggest mastering the basics of a higher-level language first. And yes, I have seen a 32-bit version of MASM.

---

### Post by phrostbyte on 2010-07-09
Why only summer holidays? Living means coding. :)

What kind of game do you plan on making?

---

### Post by JDShu on 2010-07-09
Allegro is a nice library for writing games in C. Either that, or SDL.

Eventually you'll need to learn C anyway, so I think its a good choice. Plus, it will make you appreciate python and other higher level languages more in the future.

---

### Post by Penguin Guy on 2010-07-10
> **chessnerd said:**
> Heck, you don't even have to declare what type your variables are going to be. That's just messed up. ;)
I can see a flame-war coming on.

> **spoons said:**
> Who knows you guys, you might see contributions of mine in Ubuntu one day. ;)
I'd like to point out that, for most Ubuntu contributions, Python is recommended.

---

### Post by V for Vincent on 2010-07-10
I'm currently brushing up on PHP. I've got a web-based app in mind I'd like to deploy sometime this summer, but I'm not a very experienced programmer, so it's going to require a bit of studying.

---

### Post by spoons on 2010-07-15
> **phrostbyte said:**
> Why only summer holidays? Living means coding. :)

What kind of game do you plan on making?

I'd like to make an RTS, but with more flexibility than say, Command & Conquer. A game where you research parts and construct your tanks out of those - and have a research budget. This way two sides can go for totally different designs, if they want to. It also means economy is important - something I think lacks in a lot of RTS games.

---

### Post by Mr. Picklesworth on 2010-07-15
> **spoons said:**
> Only thing that worries me is the age of the Assembly language book. 2001, and it's designed for MASM. Fortunately I have a Windows 7 environment, but it's 64-bit, and I don't know if the MASM compiler is 16-bit or anything. If anyone could suggest a compatible alternative, I'd be happy. :) I'll try this one last.

For learning Assembly stuff, I really recommend starting from the bottom up.

I'm always babbling about [this book here]("http://www1.idc.ac.il/tecs/"). It's an excellent book about the underlying fundamentals of computers starting from low-level chip design (making OR and AND from transistors, ultimately making a logic / arithmetic processor), moving through assembly code and upwards to high level languages. It's all beautifully interconnected and incredibly enlightening.

The architecture there is pretty simple, but it has to be; you're building it from the bottom up, with your own hands! (Well, in a simulated way). Still, it'll also give you a nice feel for how code can be optimized in interesting ways. For example, some comparison operators are faster than others ;)
(I only say "feel," though, because Intel's architecture is rather different).


Learning OpenGL's fundamental stuff is probably a really good idea. It's a decently made API, so while a book on 1.5 may make some things harder than they should be, I'll bet it still has the same net benefit it had six years ago: getting you acclimatized.
I haven't figured out OpenGL myself, so I'm just guessing of course.
For real world stuff, you'll probably enjoy a higher level engine like [Ogre]("http://www.ogre3d.org/"), though being able to dive into the low level stuff at will is undoubtedly a useful skill.

---

### Post by theraje on 2010-07-15
Yeah, an OpenGL 1.5 book is pretty outdated. I'm not sure how far along GLSL was along at the time, but I imagine 95% of the material in the old book is deprecated... at least.

And by the way... "acclimatized" - Best word evar!

---

