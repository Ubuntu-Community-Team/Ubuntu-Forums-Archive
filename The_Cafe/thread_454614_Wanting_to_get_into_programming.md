---
title: "Wanting to get into programming"
date: 2007-05-25
forum: The Cafe
---

### Post by esaym on 2007-05-25
Ok I know I have been seeing alot of posts like this lately.  The answer is always "python"

Python seems great, but I feel like with my current (lack of) knowledge that I will be jumping the gun by learning a scripting language.  I would really like to start out with some kind of hardware programming.  Not sure what language would be best, maybe assembly or something.  I just really want to start at the the cpu/hardware level to be able to get a better grasp of how a computer works before I move into software stuff.

I had plans to reprogram the ECU in my car for the heck of it but the products available just make it too easy (nice gui) or are way over my head (crappy gui, missing addresses/parameters.  Don't think I have the talent to be able to look at hex data and be able to tell if it is a fuel timing table or an ignition timing table:-& )

So since that plan has kinda fell through I started looking into programmable robot kits and stuff.  Something like this maybe: [http://www.kitsusa.net/phpstore/html/PARALLAX-PLX-27807-BASIC-Stamp-Discovery-Kit-USB.html](http://www.kitsusa.net/phpstore/html/PARALLAX-PLX-27807-BASIC-Stamp-Discovery-Kit-USB.html) or [http://www.kitsusa.net/phpstore/html/PLX28132-Parallax-BOE-BOT-Robot-Serial-Version-non-soldering-programmable-kit.html](http://www.kitsusa.net/phpstore/html/PLX28132-Parallax-BOE-BOT-Robot-Serial-Version-non-soldering-programmable-kit.html)

The problem is that I have no idea what language those kits are using.  Looks like some modded form of BASIC or something?  (not even sure what BASIC is) I was really wanting to learn assembly since car ECU's are programmed in it.

So umm.. I am so lost I don't even know what question to ask.  I guess can anyone see the direction that I am trying to take and maybe give me some advice on whether or not this would be a good use of my time?

Basically I am in college and thinking about taking the software engineering route.  I really don't think I would like building windows apps though.  I like the sound of much more complicated stuff like operating system building/optimization, network engineering, and as mentioned already, vehicle engine control units.

---

### Post by Tundro Walker on 2007-05-26
Ok, several things here...

1) I wouldn't dive right into Assembly, even though it is kinda considered a low-level "root" language (basically a step above 1's and 0's).  The purpose of starting out with an "easy" high-level language like Python is so that you can learn the fundamentals of programming (creating variables, using objects, using logic paths, loops, program flow, calling functions/sub-procedures so you can re-use one snippet of code instead of writing it every time you want to use it, etc) without getting so frustrated by the archaic syntax of the language.  Start with Python, get your feet wet.  Or, start with some BASH scripting...make a script to do some stuff on your computer.  I think you can d/l a book from the repo's called "abs-guide" (Advanced Bash-Scripting Guide).  Check it out and do some Bash scripting, whcih uses some C-like programming syntax.  Once you have the fundamentals down, then switching to another programming language is pretty easy...it's just a matter of learning the nuances of its syntax then.

I understand your logic here, though.  Like quitting something cold turky, you want to dive right into the deep end of something to get right into.  But you're looking at the "foundation" wrong.  Don't start with a "foundation" language...start with learning the "foundation" concepts.  Once armed with concepts, you'll be able to tackle most any language.


2) In recent years, more and more universities are starting to branch out their Computer Science degrees into other things, like systems engineering, database architect, hardware engineering, etc.  

To me, it sounds like you like optimizing things, so you might want to look into a degree in Human Interface Design.  It's sometimes called different things, but it basically focuses on optimizing the user interface so it's intuitive and gets things done.  You can read [this]("http://www.asktog.com/basics/firstPrinciples.html") to get an idea of what it's about.  While a hardware engineer degree kinda crosses electrical engineering with computer sci, an HID degree kind cross computer sci with psychology, because you have to be able to study users and see how they'd use the device to make the interface better.

Like medicine, more and more computer sci work is specializing, so you might want to get a Bach. in Computer Sci, then branch off into an area that piques your interest.  I'll warn you now, though, that some colleges are kinda teaching "fluffy" computer sci...IE: they focus all on Java programming and stuff, which is ok, but Java tends to do a lot of the garbage cleanup for you...IE: it does all the memory management for the variables you set, etc.  It's not like learning C programming which involves tracking pointers and memory allocation and such on the hardware interaction level.  If you're gonna go into any kind of comp sci college, I'd definitely check out their classwork and ask to speak with some dept rep's first before signing on to the degree program.  You don't want to spend $40k to get a comp sci degree just to be able to write "I know JAVA" on your resume.

---

### Post by esaym on 2007-05-27
> **Tundro Walker said:**
> Ok, several things here...

1) I wouldn't dive right into Assembly, even though it is kinda considered a low-level "root" language (basically a step above 1's and 0's).  The purpose of starting out with an "easy" high-level language like Python is so that you can learn the fundamentals of programming (creating variables, using objects, using logic paths, loops, program flow, calling functions/sub-procedures so you can re-use one snippet of code instead of writing it every time you want to use it, etc) without getting so frustrated by the archaic syntax of the language.  Start with Python, get your feet wet.  Or, start with some BASH scripting...make a script to do some stuff on your computer.  I think you can d/l a book from the repo's called "abs-guide" (Advanced Bash-Scripting Guide).  Check it out and do some Bash scripting, whcih uses some C-like programming syntax.  Once you have the fundamentals down, then switching to another programming language is pretty easy...it's just a matter of learning the nuances of its syntax then.

I understand your logic here, though.  Like quitting something cold turky, you want to dive right into the deep end of something to get right into.  But you're looking at the "foundation" wrong.  Don't start with a "foundation" language...start with learning the "foundation" concepts.  Once armed with concepts, you'll be able to tackle most any language.


2) In recent years, more and more universities are starting to branch out their Computer Science degrees into other things, like systems engineering, database architect, hardware engineering, etc.  

To me, it sounds like you like optimizing things, so you might want to look into a degree in Human Interface Design.  It's sometimes called different things, but it basically focuses on optimizing the user interface so it's intuitive and gets things done.  You can read [this]("http://www.asktog.com/basics/firstPrinciples.html") to get an idea of what it's about.  While a hardware engineer degree kinda crosses electrical engineering with computer sci, an HID degree kind cross computer sci with psychology, because you have to be able to study users and see how they'd use the device to make the interface better.

Like medicine, more and more computer sci work is specializing, so you might want to get a Bach. in Computer Sci, then branch off into an area that piques your interest.  I'll warn you now, though, that some colleges are kinda teaching "fluffy" computer sci...IE: they focus all on Java programming and stuff, which is ok, but Java tends to do a lot of the garbage cleanup for you...IE: it does all the memory management for the variables you set, etc.  It's not like learning C programming which involves tracking pointers and memory allocation and such on the hardware interaction level.  If you're gonna go into any kind of comp sci college, I'd definitely check out their classwork and ask to speak with some dept rep's first before signing on to the degree program.  You don't want to spend $40k to get a comp sci degree just to be able to write "I know JAVA" on your resume.

Thanks for the advice.  Yea I don't know about this robot thing.  It sounds great in theory and you will always have something to tweak/play with.  The problem I see with learning a  computer application language is that I don't know what I would do with it.  As of right now, there is not any programs I need that aren't already available.  So after I learn python I wouldn't know what to do with it.  I can't think off hand of any programs to make/enhance.

The problem I see with going the robot route is that the language I learn will not really be usable in the real world computer environment.  It will certainly get my feet wet and I will be able to see if I got what it takes though.  The other problem is that I don't know how legitimate it is.  I was looking at this one: [http://www.superdroidrobots.com/shop/item.asp?itemid=56&catid=20](http://www.superdroidrobots.com/shop/item.asp?itemid=56&catid=20) and it can be programmed in objective C  with the oopic: [http://www.oopic.com/](http://www.oopic.com/)  Plus the robot has "eyes" so the programming possibilities are endless.  BUT searching on google gives no extra info to building robots from that company so I don't know how good they are plus the documentation for programming them is only available online after you purchase the robot.  So documentation might be very poor but they would already have your money.

I guess I will just start with python.  I am having some computer problems right now so the money that I would spend on the robot might be better spent on new computer hardware.  

Anyone know any good beginner python books?  This one I see has been recommended but in the review section everyone says that is has to many references to C to be noob friendly: [http://www.amazon.com/Learning-Python-Second-Mark-Lutz/dp/0596002815/ref=sr_1_20/002-9193872-3331259?ie=UTF8&s=books&qid=1180306454&sr=1-20](http://www.amazon.com/Learning-Python-Second-Mark-Lutz/dp/0596002815/ref=sr_1_20/002-9193872-3331259?ie=UTF8&s=books&qid=1180306454&sr=1-20)

I agree with carefully choosing a degree program though.  I have the time and money to get a bachelor's and a master's.  I just got to find a school that is close enough and has the path that I want.  I have 4 cousins that all took compsci at a university.  One stayed after getting the bachelor's and he also got some kind of master's.  He went off to work for an airline company designing flight scheduling software and he quickly moved into a management position.  The other 3 just got the standard bachelor's degree in compsci.  2 are both website developers, doing alot of java I bet.  The other one works at a middle school entering in test result numbers into a database for state examination.  The ironic thing is that none of them even like computers or were even familiar with computers in general when they first started going to school.

---

### Post by Andrewie on 2007-05-27
there was a thread about this already, forgot the link.

I think you should start with C/C++. its harder then other languages but it will make learning other languages a lot easier. Its kind of like learning piano before you learn to play saxophone.

---

### Post by H264 on 2007-05-27
Mind if I throw in a little something?

To address some of your comments and concerns...

"...website developers, doing alot of java..."
PHP, Java, Perl, Ruby, and Python are the most popular for server side programming. That does not mean you can't use other languages like Objective-C, C, and C++.
I personally started in BASIC, which booted me into Java and now (just starting) Ruby and Objective-C. If you can avoid BASIC, then do so. The GOTO statement is really bad for your programming form/style.

Robots, Microcontrollers, and electronics
I have a parallax basic stamp 2 robot kit. It is basically a microcontroller that is programmable in BASIC (I know, BASIC in general is bad) with some small electronics to plug into it. The only reason I have it is because I got a really good deal for it. If you want to get really down to earth with programming and computers, then small electronics is about as low as you can go. 
For a robot "kit" I would recommend looking into one or two PIC microcontrollers, a solderless breadboard ( [http://en.wikipedia.org/wiki/Breadboard](http://en.wikipedia.org/wiki/Breadboard) ), and the supporting electronics to get the microcontroller to do what you want it to do (transistors of both NPN and PNP, flip flops, 555 timer...). I would recommend getting a couple different small electronics books, I have a couple of Forrest M. Mims's books, they are wonderful ( [http://www.amazon.com/s/ref=/105-4338270-5012467?rs=1000&page=1&rh=n%3A1000%2Cp_27%3AForrest+M+Mims&sort=daterank](http://www.amazon.com/s/ref=/105-4338270-5012467?rs=1000&page=1&rh=n%3A1000%2Cp_27%3AForrest+M+Mims&sort=daterank))
Go to a radio shack or other book store that has any of Forrest's books and flip through it to see what you are getting into.

I have not really looked into PIC microcontrollers much (at all), but I know there are free C compilers out there to make your programming easier than using assembly. I personally would not get a robot kit unless there was a sweet deal somewhere.

Now for actual programming...
I would recommend  Java and/or Objective-C. Objective-C is a superset of the C language, which means you can use any amount of C in your Objecive-C programs. Objective-C is OOP layered on top of the C language, kinda like C++, only the OOP part is implemented in a better way. Like I said, I know Java, and going from Java to Objective-C is very easy because both implement OOP about the same way. In the most basic sense, Java and Objective-C are the same except Objective-C uses pointers and Java does not. Pointers are a little bit scary to somebody that has not used them before (like me).

If you have any other questions for me then a PM is the way to go :)
I need to go, my battery is at 6% and I have lots of homework.

---

### Post by Mateo on 2007-05-27
Basic, then pascal.  I wouldn't do python just because it doesn't compile.

Assembly?  Geez, you're hardcore if you do that.

---

### Post by gradedcheese on 2007-05-27
Sounds like you need to pick up an Atmel AVR microcontroller (tools available via apt-get) and write some embedded C :)  Well, on a serious note it sounds like you want to learn some computer architecture and low-level 'hardware' programming, so that's about as close as you will get.  In school, I designed and implemented [a fuel injection ECU]("http://picasaweb.google.com/yurovsky/FuelInjectionECUProject") using an Atmel ATmega128 microcontroller, for what it's worth.   Read through the introductory chapters of an Atmel AVR datasheet (for the ATmega88, for example) and see if this is something that interests you.  I have some [example code]("http://andrey.thedotcommune.com/articles.html") that you can look at, and there's a ton more on the 'net in general.

Mateo -- no one really uses Basic or Pascal anymore for anything serious.  They're not worth bothering with.  And assembly languages, in my opinion, are worth it.  Pretty much anyone who wants to be a programmer should learn at least one and use it.  You gain a certain understanding that you otherwise won't have.  Finally python 'not compiling' is one of the nice things for beginners: you can interactively debug, you can run from a shell, etc.  Python is an excellent way to learn the basics (and an excellent tool regadless).

---

### Post by KLineD on 2007-05-27
It seems to me that you could try out PIC programming or any other kind of microcontrollers for that matter. It's really fun stuff and depending on the microcontroller you can do lots of neat stuff. The 16F84 PIC is a very popular one, you could also try with the M68HC11 (an old motorola/freescale microcontroller) that's very basic and easy to grasp (I made a HC11 simulator in Java for my thesis).

Normally you can buy a starters kit that contains the micro and some tools to upload your program to the micro. For the HC11 there's the GNU embedded Libraries available at [http://gel.sourceforge.net/](http://gel.sourceforge.net/) and that let's you develop in C with the GNU toolchain, but I still recommend you try starting out with ASM so you get all the important concepts and really get to know the hardware, and then move on to C.

My 0.02.

Forgot to add: all the tools you need for the HC11 are available for linux. There's the assembler, and I remember using some kind of IDE for syntax coloring and uploading. Be sure to get the hc11 pink book, it's the definitive guide to that micro.

---

### Post by gradedcheese on 2007-05-28
KLineD -- the HC11 is nice but they're not available in DIP anymore and Freescale is generally getting rid of them.  I recommended the AVR because it's the closest thing, but with full support and a user base, DIP packages, and a good architecture with a GCC toolchain (unlike the terrible disaster that is the PIC, but that's my opinion I guess).  

The AVR is neat in that it is a simple/clean RISC processor and I think people can easily move to ARM from that to do bigger projects.  The PIC is a terrible architecture (no software stock, for exmaple) originally intended to provide I/O for a badly designed CPU, and it's a shame that the damn thing is still around.

---

### Post by Cows on 2007-05-28
Wow I was never thinking of actually reading a programming topic about programming robots lol. But in general I think it's pretty cool. It's good to program for hardware. I programmed a little before for the PSP system in C and LUA. So I might think of getting into robotics programming and taking on the Software Engineering course since that Software Engineering im already sure that I want to take that when I get to college. I know a little on ASM and Hex since I needed it to Debug and Edit some Diablo 2 DLLs for my Diablo Mod Also since I use to be a game hacker I needed it. Editing with Cheat Engine ( CE ) , TSearch. and after I found out the addresses I used Game Trainer Maker and made a program with the found addresses to actually patch those addresses for me so I don't have to search for them everytime I want to cheat :) lol.

---

### Post by KLineD on 2007-05-28
I never used the AVR really, and it's true about the HC11 but it's generally easy to get (at least here in mexico). Anyway I know the hc11 it's old, but it's really a great micro and easy to program. As a teaching tool I find the HC11 invaluable, but then again I have no experience with the AVR. About the PIC, I have never used it, it's just that the thing is popular but thanks for pointing that out.

---

### Post by H264 on 2007-05-28
> **gradedcheese said:**
> 
Mateo -- no one really uses Basic or Pascal anymore for anything serious.  They're not worth bothering with.  And assembly languages, in my opinion, are worth it.  Pretty much anyone who wants to be a programmer should learn at least one and use it.  You gain a certain understanding that you otherwise won't have.  Finally python 'not compiling' is one of the nice things for beginners: you can interactively debug, you can run from a shell, etc.  Python is an excellent way to learn the basics (and an excellent tool regadless).

Sadly I started in BASIC then dabbled a bit in Pascal, talk about a waste of time and programming form. I have found Java to be a nice language to start in. Scripting languages like Ruby, Perl and Python tend to look scary because people using them like to compress code into as few lines as possible, which I think is harder to follow, especially in the just starting stage of programming. However just because people *like* to make scary one-liners, does not mean that scripting languages *have* to be like that.
I strongly suggest starting in an OOP language like Java and Objective-C.

If you want to do more microcontroller programming, then C/Objective-C is a good place to start on your computer. For almost all of the popular microcontrollers there is a way to compile C for that microcontroller.

---

### Post by gradedcheese on 2007-05-28
> 
tend to look scary because people using them like to compress code into as few lines as possible


Python was specifically designed to not allow programmers to do that.  It has other designed-in 'features' to improve readability and reduce your ability to obfuscate things.

Those interested in low-level and microcontroller programming should definitely thoroughly learn C, as that's all that you will use there.  Object oriented languages are nice on bigger systems, but with these I also feel that it's better to first learn what programming is all about before diving into abstractions like OO.  That's my (biased) take on it anyway...  I use C and Python for just about everything.

---

### Post by esaym on 2007-05-30
Well I got me a couple of books:

[IMG]http://la.gg/upl/cprogram.png[/IMG]

I liked the idea of starting with C first.  I will see how this goes.  So far, from using online stuff, it's not going too good  :-s

---

### Post by kevinlyfellow on 2007-05-30
Many robotics use a [[COLOR="Navy"]_visual programming language_[/COLOR]]("http://en.wikipedia.org/wiki/Visual_programming_language").  From what I hear, thats what they use for the Mars rovers.  Its a smart idea, because they wouldn't want to misspell something and have one of them fall in a crater ;-)

I personally suggest Bash scripting.  Lots of cool and useful things you can do with it.  Python is great language to learn.  If you are into numerical computations, give octave a try.

---

### Post by thisllub on 2007-05-30
> **H264 said:**
>  The GOTO statement is really bad for your programming form/style.
.

That is why assembler will never take off.;)

Although I use PHP/CSS/DHTML/JSCRIPT for 90% of my coding now (db stored procedures being the rest) BASIC is a great place to get started and there is plenty of work out there for good thinkers who write basic code. Most small businesses use MS office and want small scale projects. You can make $1000 a day on one off jobs like integrating mailing lists.

Despite this it is good to understand how logic works. C/C++ is a good language but developing meaningful programs requires more time spent on learning the API and compiler than the language itself - especially for Windows. 
It is important to understand how to organise data. It is amazing how many badly designed databases are out there.

Don't be limited by what people tell you you can't do.

---

