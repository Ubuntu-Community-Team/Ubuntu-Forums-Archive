---
title: "Programming in Linux"
date: 2009-06-06
forum: The Cafe
---

### Post by P1umb3r on 2009-06-06
I see many people in this forum saying that programming in Linux is far superior to programming in Windows.  Why is this exactly?

*about to enter college for Comp Sci major* ;)

---

### Post by kvarley on 2009-06-06
I'm not a hardcore coder but from my experience it's much easier to use the tools to create applications as well as compiling as you don't need to mess around with VisualBasic studio.

The apps are free aswell!

For coding:
> sudo apt-get install quata

For graphical interface coding:
> sudo apt-get install glade


---

### Post by Viva on 2009-06-06
Most linux distros come with python pre installed, it only takes a few hundred lines of code to create working applications using python.

---

### Post by PurposeOfReason on 2009-06-06
They're lying. End of story. If you can program in one environment, you can for any. Now programming **for** Windows vs. Linux brings out differences, but still not enough that any competent programmer would care. Really, the only difference for me in I use notepad++ in Windows and vim in linux.

Congrats on getting into wherever you did. I will tell you now though, a CS major is not programming major, there is no such thing. At most, you will take 5 programming classes. Probably less. You'll learn something basic and just be expected to do it.

> **vitium said:**
> I'm not a hardcore coder but from my experience it's much easier to use the tools to create applications as well as compiling as you don't need to mess around with VisualBasic studio.
You don't need to use VB studio . . .

---

### Post by DeadSuperHero on 2009-06-06
Well, as stated above, many tools are available for free. Linux is flexible in the sense that it has more Free libraries, toolkits, plugins, frameworks, and languages. There are a ridiculous amount of IDEs, and the compiler in the system is basically universal across IDEs and toolkits, as long as you have the language bindings.

   That said, it could also be difficult. There are less newbie-friendly editors out there. Even with a simple language such as Python, most IDEs are nothing more than debuggers, a compiler, and a text editor. If you're making a game, importing and animating sprites for characters can be tedious if you don't read the documentation first.

   I would really like to see some game-making tools simplified for newcomers.

---

### Post by .Maleficus. on 2009-06-06
> **PurposeOfReason said:**
> They're lying. End of story. If you can program in one environment, you can for any. Now programming **for** Windows vs. Linux brings out differences, but still not enough that any competent programmer would care. Really, the only difference for me in I use notepad++ in Windows and vim in linux.
Very well said, +1.

---

### Post by Delever on 2009-06-06
It depends what tools you are comfortable with. And it is possible to learn tools on different platforms. Even if not, with some care you can still can make programs which are easy to port to different systems. How easy - depends on language and your program.

---

### Post by red_Marvin on 2009-06-06
Since I prefer simpler editors + a command line environment, instead of full blown IDEs, I would say that the main benefit is sh/bash/other shells and the tools that come with those compared to cmd.exe that is, in my opinion, quite unusable. I haven't used the new powershell that is supposed to be better though.

---

### Post by BuffaloX on 2009-06-06
> **vitium said:**
> 

For coding:

Quote:
sudo apt-get install quata 

For graphical interface coding:

sudo apt-get install quata 
Hmm and what's that supposed to do?

Search in Synaptix for "quata" turns a blank, and on google too...

---

### Post by Viva on 2009-06-06
I think he meant quanta

---

### Post by BuffaloX on 2009-06-06
But that's an HTML editor ???

Weird suggestion for a good programming editor.

---

### Post by majamba on 2009-06-06
JAVA
aptitude install netbeans 
aptitude install eclipse

C#
aptitude install monodevelop

C++
aptitude install codeblocks

for kde:
QDevelop

---

### Post by Wiebelhaus on 2009-06-06
> **P1umb3r said:**
> I see many people in this forum saying that programming in Linux is far superior to programming in Windows.  Why is this exactly?

*about to enter college for Comp Sci major* ;)

It's the modular design , if one thing breaks it doesn't bring down the entire system , I suppose I could easily explain with a simple term that's wildly over used in the computer industry. *_**Stability**_* , true blue stability.

---

### Post by samjh on 2009-06-07
The short answer is that there are more freely-available tools for Linux (and other Unix-like operating systems) than Windows.  Also, the operating system's infrastructure makes it easier for developers to write and test code than on Windows.

But at the end of the day, it doesn't really matter.  If you're programming for Windows, use Windows; for Mac, use Mac; for Linux, use Linux.

---

### Post by Delever on 2009-06-07
I like geany for C/C++. [Autotools]("http://www.lrde.epita.fr/~adl/autotools.html") are bearable once you learn them.

For Java, eclipse, netbeans - both work on different platforms, so you don't need to re-learn much.

Visual Studio is best when used with .NET framework. For C/C++ (native), it is more complicated to set up than autotools on linux, but it is powerful editor and main choice for Windows.

And so on... look in programming forum, there are lots of discussions about this.

---

### Post by .Maleficus. on 2009-06-07
> **samjh said:**
> The short answer is that there are more freely-available tools for Linux (and other Unix-like operating systems) than Windows.  Also, the operating system's infrastructure makes it easier for developers to write and test code than on Windows.
Could you give an example?  Because I fail to see how that's true (the infrastructure part, I have no arguments with the free tools).  In Windows, I can open Visual Studio, write my code, click the "Run" button and test it out.  After that, I can easily package it with an installer or as a standalone .exe, in a matter of clicks.  On Linux, I can open up Vim, write my code, do a " :!% " and test it out.  After that, I can release the source, or make an number of installers (.deb, Arch PKGBUILD, .rpm, etc).  I see almost no difference.

---

### Post by amingv on 2009-06-07
> **.Maleficus. said:**
> Could you give an example?  Because I fail to see how that's true (the infrastructure part, I have no arguments with the free tools).  In Windows, I can open Visual Studio, write my code, click the "Run" button and test it out.  After that, I can easily package it with an installer or as a standalone .exe, in a matter of clicks.  On Linux, I can open up Vim, write my code, do a " :!% " and test it out.  After that, I can release the source, or make an number of installers (.deb, Arch PKGBUILD, .rpm, etc).  I see almost no difference.

I may be wrong, but I think he's talking about the headers/bindings to "bind" (so to say) your program to pretty much everything from the desktop manager to the kernel (seriously, there's so many headers/bindings it's not even funny).

Then again, he may be talking about zero dependency to dr watson, which is known to cause trauma and mild to severe seizures. [j/k :)]

---

### Post by Mateo on 2009-06-07
It's easier to program linux languages in linux.  It's not easier to program in general.  Actually Visual Studio is probably the "easiest" programming tool made.  But trying to get ruby set up on a windows box is a pain in the ***. Same for php.

---

### Post by yoda2031 on 2009-06-07
It depends on what you mean by "easier".

Programming itself is no easier, but this should be obvious.  If you can write your applications in notepad then you should see no difference between the two platforms in terms of actual code generation.

Compilation and debugging in linux is (arguably) easier if you're writing in C, as there are tools like vim, make, gdb and touch which prove invaluable.

Most importantly, though, is a feature that is available on Linux, Unix, Mac, BSD, basically all UNIX derivatives, called "man".  This is the main thing I'd miss if I switched to Windows.  So much so, that I would probably find and install a Windows port of the command.  

Other advantages include the ability to drop back to the command line and still have:
Syntax-highlighting (vim :syntax on)
Manual pages (man)
Compiler (gcc)
Debugger (gdb)
IRC (ircii)
Email (mutt)
Web (lynx)

Which, if you're building large, complex programs on slow hardware, can be an enormous advantage because you don't have to be running all the resource-intensive stuff that is associated with a full GUI.  Note that some of the above CLI utilities aren't included in ubuntu out of the box, but are all available through apt.

All that being said, I have never programmed anything significantly beyond "Hello, World" on a Windows box, so I'm probably fairly biased.

---

### Post by phrostbyte on 2009-06-07
I would say it's easier because of apt-get. If you want some library it's always an apt-get away, and sometimes it's difficult in Windows because libraries have to be found on the Internet and manually installed in your LIBPATH. Python development can be pretty annoying because of this, because there is so many python libraries out there that you may want to use. It's also true for C++/Perl/Python/Ruby/PHP, not as true for .NET, which is more "monolithic" (massive standard library, not as many 3rd party libraries used).

Basically if you want a easy experience with development on Windows, you got one option (.NET). That's why so many Windows programmers are .NET developers, there is far more programmer "diversity" in the *nix world, IMO. This is because on Linux/*nix you tend to have more 1st class options available (.NET actually being one of them, heh). Overall I just find it a bit more pleasant because of this.

---

### Post by amingv on 2009-06-07
> **Mateo said:**
> Actually Visual Studio is probably the "easiest" programming tool made.

Pretty much like their OS then, huh?

But speaking seriously, now. There's no such thing as a "Linux language", there is something called "portable language", though, which anything that has "Visual" on it's name isn't (at least not by default). Same difference with Ruby, which is of the portable kind.
The only thing I could think closer to a Linux language would be shell scripting, and you can do that in Windows through Cygwin.

Though I'll agree it's not necessarily easier to program in general, for reasons related more to the user than the environment.

---

### Post by Mateo on 2009-06-07
> **amingv said:**
> Pretty much like their OS then, huh?

But speaking seriously, now. There's no such thing as a "Linux language", there is something called "portable language", though, which anything that has "Visual" on it's name isn't (at least not by default). Same difference with Ruby, which is of the portable kind.
The only thing I could think closer to a Linux language would be shell scripting, and you can do that in Windows through Cygwin.

Though I'll agree it's not necessarily easier to program in general, for reasons related more to the user than the environment.

Ruby is not a linux language, that's true, but it's most easily run and programmed in for linux.  Well, maybe on Mac it is the same, I've never tried it.  But programming in windows it is a pain to just get set up.  Same for php.

The whole concept is silly, in my opinion, because whatever environment you are programming *for*, that's the environment you should be programming *in*.  If you're programming for a linux server, you should program it in linux, if for a windows server, program in windows.

The only language where it is equally easy in all OSes is Java, and that's because of Eclipse.

---

### Post by fr4nko on 2009-06-07
> **PurposeOfReason said:**
> They're lying. End of story. If you can program in one environment, you can for any. Now programming **for** Windows vs. Linux brings out differences, but still not enough that any competent programmer would care. Really, the only difference for me in I use notepad++ in Windows and vim in linux.


In my experience linux is a better programming environment because the programming tools are freely available just like the documentation. For example emacs is an excellent editor freely available. The same is true also for a debugger, like gdb. Also most of the library are freely available under the GNU GPL license and most of them are of excellent quality. You have also some developers utilities easily available like a good shell (command prompt), a make program, bison/yacc for parser generators and flex for lexer generators.

In windows you not even have a decent shell to type your command, everything has to be done with a visual IDE that is supposed to do everything you need. Of course the IDE is not compatible with anything except itself and once you have learnt how to use it... well you just know how to use a particular commercial product. May be is some years this product will be discontinued or may be your collegue is using a different commercial product. If you learn how to use "make" you will be able to use your knowledge on almost every system.

The drawbacks of programming on linux is that some tools are not so polished and full featured like in windows so sometimes you have to cope with a not well designed user interface or you just have to accept that you lack the feature X if you use free software tools. Anyway, my experience is that is a feature is missed is because it is not really very important and you can live without.

So, this is my point of view but I've tried to be as much objective as possible.

Francesco

---

### Post by Mateo on 2009-06-07
> **fr4nko said:**
> In my experience linux is a better programming environment because the programming tools are freely available just like the documentation. For example emacs is an excellent editor freely available. The same is true also for a debugger, like gdb. Also most of the library are freely available under the GNU GPL license and most of them are of excellent quality. You have also some developers utilities easily available like a good shell (command prompt), a make program, bison/yacc for parser generators and flex for lexer generators.

In windows you not even have a decent shell to type your command, everything has to be done with a visual IDE that is supposed to do everything you need. Of course the IDE is not compatible with anything except itself and once you have learnt how to use it... well you just know how to use a particular commercial product. May be is some years this product will be discontinued or may be your collegue is using a different commercial product. If you learn how to use "make" you will be able to use your knowledge on almost every system.

The drawbacks of programming on linux is that some tools are not so polished and full featured like in windows so sometimes you have to cope with a not well designed user interface or you just have to accept that you lack the feature X if you use free software tools. Anyway, my experience is that is a feature is missed is because it is not really very important and you can live without.

So, this is my point of view but I've tried to be as much objective as possible.

Francesco

I wouldn't bring up documentation in Linux's favor, it loses big time.  Of course c/c++ is well documented across the board, as is java.  But Ruby's documentation is downright atrocious.  PHP is a little better but far from good.  The .NET languages are amazingly well documented.  Just type any class or method on google and the first or second result with be MSDN which is a very good resource.

Actually one of the things that is great about .NET is that you don't even need to always go to the web to find documentation because usually intellisense will tell you all you need to know.  You also learn about new classes/methods that you otherwise would not.

---

### Post by cmay on 2009-06-07
when i started to learn programming i used turbo pascal (freepascal) on windows. i also had wx devcpp at my install and i could make gui programs using that and the lazarus envoronment almost from start. i had the exe creator so i could make real programs as a newbie with out any experience at all. (not in anyway great programs but still )

on linux i never found out yet how to make a deb package. i compile over commandline and use geany and  what ever editor is on the system . mostly nano for quick edits ,gedit for larger edits and i write in geany and practise using geany.

i read tons of unix tutorials and i fond it rewarding and hard to begin with. the thing is in my opinion from a absolute beginners point of view (which i stil rightfully consider my self to be) the advantage in windows is that lost of tools are there to make it easy and simple but in linux there is all the free sources and lots of information available and one thing more. 

the concept in windows is different. windows makes use of gui and the apps are almost some that can do many more thigns than just the purpose it has. because the fullscreen view and lack of workspaces makes it more practical. and one more thing is fileformats are different. 
in linux there is xml files and txt files and bash shell scripts mostly.

to answer the question. why is linux the better to (learn) program in for a person like me is that i can actually begin writing small shell scripts and small commandline programs that are worth some thing other than the experience and it is the linux/unix spirit to do so. on  windows i would get stuck in having to read partly secret api and write programs that uses file formats and uses gui to blend in and be useful there, 

a good example is wordcount (wc ) on windows and on linux. 
on linux its a part of the k&r c programming language book wich ,most learning or  using c read and it can wiht few adaptions be a fuill blown commandline prorgam that works. 

it just does not work on windows. the example from the book counts wrong and would never really  be used by anyone unless there was a gui version made. 


in linux you have lots of small programs designed to one thing and do it well. they can be combined to do ohter things in pipelines or part of scripts and the user is free to write new programs or shell scripts using already existing programs. 

its the spririt of linux programming i find the most rewarding thing to use that as a platform to learn on.

---

### Post by samjh on 2009-06-07
> **.Maleficus. said:**
> Could you give an example?  Because I fail to see how that's true (the infrastructure part, I have no arguments with the free tools).  In Windows, I can open Visual Studio, write my code, click the "Run" button and test it out.  After that, I can easily package it with an installer or as a standalone .exe, in a matter of clicks.  On Linux, I can open up Vim, write my code, do a " :!% " and test it out.  After that, I can release the source, or make an number of installers (.deb, Arch PKGBUILD, .rpm, etc).  I see almost no difference.

Visual Studio is third-party software which is not usually part of a Windows installation.

In Linux and most Unix-like operating systems, bash (or some other shell), make, and gcc traditionally form part of the baseline installation (Ubuntu and some other user-centric distros are odd cases).  That means you have scripting, compilation, and build management in a baseline Unix-like system.

---

