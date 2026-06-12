---
title: "MS Visual Studio"
date: 2014-09-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Ali_Nauman on 2014-09-12
Hey guys i wanted to ask if there will be any inconvenience if I use Linux .

The problem is my teacher has recommended me 

1.) G++ compiler
2.) Notepad ++
3.) MS Visual Studio 2012

What are the alternatives or I will have to purchase Windows .
I am currently using Linux Mint 17 and loving it. Plus really limited on resources because I am a computer science student .

Secondary question

Can you tell me where to get some free games ?

---

### Post by QIII on 2014-09-12
Hello!

Visual Studio 2012 is for Windows.  It will not run natively in Linux.

WineHQ lists it as "garbage".

Although one can use Mono to develop with C# and .NET on Linux, it's not likely your assignments would be accepted.

I would suggest either running Windows in a virtual machine or dual booting.  The first would probably be easier.

As for games ...  Well that's a question for the Gaming And Leisure forum, so please ask there.

---

### Post by Lars Noodén on 2014-09-13
> **Ali_Nauman said:**
> 1.) G++ compiler
2.) Notepad ++
3.) MS Visual Studio 2012

1) There is g++, the GNU C++ compiler, in the Ubuntu repositories.  You can install it from the Software Center, Synaptic or via apt-get.

2) There are several simple editors.  Two, gedit and geany, come to mind first if you are using plain Ubuntu.  Both can be used to show line numbers in whatever you are editing.  Geany is fancier and has some syntax highlighting.  If you are using KDE, then Kate is very good too.  

3) If you are talking about a general purpose IDE, then there are several.  I stayed with Emacs myself but for a more graphical experience there are Kdevelop, Netbeans and Eclipse.  If you are looking for something similar to (ugh) VB then there is Gambas.  IDEs though tend to be overkill unless you are working on larger programs with lots of modules, libraries, classes, etc.

---

### Post by buzzingrobot on 2014-09-13
Ask your instructor if assignments and exercises will be keyed specifically to Visual Studio and Windows, or to generic C++ code.

If it's the former, you'll need Windows.

---

### Post by etna2 on 2014-09-13
If G++ is one of the recommendations I think you might be able to get away with staying on Mint. After all, even if you switched over to Windows, G++ would not accept MSVC-specific extensions or whatnot. 

But the onus is still on you to find out exactly what the course requires and how assignments need to be completed or graded. For example, if the profs use Windows and require that the source code packages you create must provide a .sln file for easy compilation on their systems, then you must use Windows and Visual Studio. No questions asked.

If the course also includes material on C#, you can already start preparing to remove Linux on your laptop for at least the duration of the program you have enrolled in. Mono is very different from C# and .NET, and trying to be 'diiferent' only means additional confusion, especially if the course touches on Windows-specific content which is simply not available in Mono. School is not a place to 'be different', especially for introductory-level courses. Toe the line, use exactly what the school demands, gain sufficient fundamental knowledge in the material and obtain good grades, THEN we can talk about using different platforms.

---

