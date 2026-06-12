---
title: "What's the oldest piece of code in Ubuntu, and when was it written?"
date: 2008-05-02
forum: The Cafe
---

### Post by Sporkman on 2008-05-02
Any takers?

I'll bet there's some stuff written in the 70's in there...

---

### Post by tamoneya on 2008-05-02
well it is probably easier to say what is the oldest piece of code in the kernel.  The kernel has been around the longest and although there have been many changes I am sure there is some ANCIENT code in there.

---

### Post by blithen on 2008-05-02
> **tamoneya said:**
> well it is probably easier to say what is the oldest piece of code in the kernel.  The kernel has been around the longest and although there have been many changes I am sure there is some ANCIENT code in there.

Exactly what I was thinking.

---

### Post by amingv on 2008-05-02
If I was asked that I would say gcc (The GNU C Compiler) is older than the kernel, but I wouldn't know what's the oldest of them all though.

EDIT:
Verified; gcc development  was started in 1985 and released in 1987; whereas the Linux kernel started development in 1991 and was released the same year (being developed in bazaar style).
Sources:
[http://en.wikipedia.org/wiki/GNU_Compiler_Collection#History](http://en.wikipedia.org/wiki/GNU_Compiler_Collection#History)
[http://en.wikipedia.org/wiki/Linux_kernel#History](http://en.wikipedia.org/wiki/Linux_kernel#History)

---

### Post by tamoneya on 2008-05-02
This article seems to think it is 1973
[http://perens.com/SCO/SCOCopiedCode.html](http://perens.com/SCO/SCOCopiedCode.html)

---

### Post by MaindotC on 2008-05-02
I don't trust any source except wikipedia.

---

### Post by jakupl on 2008-05-02
> **strAlan said:**
> I don't trust any source except wikipedia.

haha! why would you trust wikipedia above anything?

---

### Post by acelin on 2008-05-02
> **jakupl said:**
> haha! why would you trust wikipedia above anything?

jakupl is awesome, eh ignores witty comments and doesn't afraid of anything.

---

### Post by Kingsley on 2008-05-02
> **strAlan said:**
> I don't trust any source except wikipedia.

Good choice.

---

### Post by SunnyRabbiera on 2008-05-02
yeh gcc is the oldest, with the kernel itself coming in second probably.

---

### Post by jakupl on 2008-05-02
[quote="acelin"]jakupl is awesome, eh ignores witty comments and doesn't afraid of anything.[/quote]

hehe should I keep shut for a while? ;) :oops:

---

### Post by yssida on 2008-05-02
How about vi? Started in 1976. There are probably more.

---

### Post by tamoneya on 2008-05-02
gcc was released in 1987.  While the linux kernel was started in 1995 it probably still has some code from its predecessor UNIX in it.

---

### Post by MaindotC on 2008-05-02
Yeah back when Stallman and Linus were using levers to store and release electrical charges to memory...

---

### Post by yssida on 2008-05-02
Actually my friend, I believe it was punch cards.

---

### Post by nrs on 2008-05-02
If you mean individual line / blocks. I think it'd be impossible to tell. Even going by modification dates can be misleading because it could've been a trivial change. If you mean oldest project; GCC, and other GNU projects. I very much doubt they have much original code left in them though. If you include software that isn't in the default install, but can be added through repos, maybe Emacs?

---

### Post by nrs on 2008-05-02
> **tamoneya said:**
> gcc was released in 1987.  While the linux kernel was started in 1995 it probably still has some code from its predecessor UNIX in it.

Neither GNU or Linux have a genetic relationship with UNIX.

---

### Post by tamoneya on 2008-05-02
> **yssida said:**
> Actually my friend, I believe it was punch cards.

Punch cards would be the first method of coding but we are not trying to figure that out.  We want to know what the oldest code in linux is and that is a bunch of source code.  The ISO's dont ship with punch cards although I am pretty sure that most of the people on these forums would enjoy it if they did.

---

### Post by amingv on 2008-05-02
> **nrs said:**
> If you mean individual line / blocks. I think it'd be impossible to tell.

Well,
```
int main(){
```
could aguably be considered the first line of code. :)
j/k

---

### Post by tamoneya on 2008-05-02
> **nrs said:**
> Neither GNU or Linux have a genetic relationship with UNIX.

Linux came from minix which came from UNIX 7th edition
[http://www.levenez.com/unix/history.html#04](http://www.levenez.com/unix/history.html#04)

---

### Post by MaindotC on 2008-05-02
> **yssida said:**
> Actually my friend, I believe it was punch cards.

There was a time when punch cards were the thing but in my assembly language class the professor showed us a program that looked like a telephone switchboard.  You had to use wires with plugs on them to stick into the board and form connections and then plug those into another set of plugs that transferred the charge and stored your data.  Probably after punchcards.

---

### Post by yssida on 2008-05-02
> **tamoneya said:**
> Punch cards would be the first method of coding but we are not trying to figure that out.  We want to know what the oldest code in linux is and that is a bunch of source code.  The ISO's dont ship with punch cards although I am pretty sure that most of the people on these forums would enjoy it if they did.

That {EDIT: reply you quoted }would be my tongue in cheek reply to strAlan's post above :) {no, not the one above,but the one above my earlier post :oops: }

---

### Post by yssida on 2008-05-02
> **tamoneya said:**
> Linux came from minix which came from UNIX 7th edition
[http://www.levenez.com/unix/history.html#04](http://www.levenez.com/unix/history.html#04)

I don't think it's really derived from Minix, but rather inspired by it.So I don't think it came from Minix.

"Although Linux 0.01 was written using Minix as an example and starting point, no code from Minix was actually used in it (Tanenbaum agrees on this point)."-Wikipedia

---

### Post by amingv on 2008-05-02
> **tamoneya said:**
> Linux came from minix which came from UNIX 7th edition
[http://www.levenez.com/unix/history.html#04](http://www.levenez.com/unix/history.html#04)

It was based on minix, but the code is completely original:
[QUOTE=kernel.org]Linux is a clone of the operating system Unix, **written from scratch** by Linus Torvalds with assistance from a loosely-knit team of hackers across the Net.[/QUOTE]

Also in the link I provided from wikipedia there's a quote from Linus in a minix newsgroup where he states his project is "free of minix code" (the citation is there, too).

---

### Post by nrs on 2008-05-02
> **tamoneya said:**
> Linux came from minix which came from UNIX 7th edition
[http://www.levenez.com/unix/history.html#04](http://www.levenez.com/unix/history.html#04)
No. MINIX does not have a genetic relationship with UNIX, and Linux doesn't have a genetic relationship with MINIX. 

Let's get this straight from the source: Andy Tanenbaum. 

> Years later, I was teaching a course on operating systems and using John Lions' book on UNIX Version 6. **_When AT&T decided to forbid the teaching of the UNIX internals, I decided to write my own version of UNIX, free of all AT&T code and restrictions_**, so I could teach from it. My inspiration was not my time at Bell Labs, although the knowledge that one person could write a UNIX-like operating system (Ken Thompson wrote UNICS on a PDP-7) told me it could be done. My real inspiration was an off-hand remark by Butler Lampson in an operating systems course I took from him when I was a Ph.D. student at Berkeley. Lampson had just finished describing the pioneering CTSS operating system and said, in his inimitable way: "Is there anybody here who couldn't write CTSS in a month?" Nobody raised his hand. I concluded that you'd have to be real dumb not to be able to write an operating system in a month. The paper cited above is an operating system I wrote at Berkeley with the help of Bill Benson. It took a lot more than a month, but I am not as smart as Butler. Nobody is.

**_I set out to write a minimal UNIX clone, MINIX, and did it alone. The code was 100% free of AT&T's intellectual property. _**

> Thus, of course, Linus didn't sit down in a vacuum and suddenly type in the Linux source code. He had my book, was running MINIX, and undoubtedly knew the history (since it is in my book). But the code was his. The proof of this is that he messed the design up.

> I told him that MINIX had clearly had a huge influence on Linux in many ways, from the layout of the file system to the names in the source tree, but I didn't think Linus had used any of my code.

---

### Post by tamoneya on 2008-05-02
sorry my bad

---

### Post by nrs on 2008-05-02
> **tamoneya said:**
> sorry my bad

You have nothing to be sorry for. If that graph tells you anything it's that the relationship between everything is a little complicated. You weren't completely wrong either, the relationship is mostly correct but it's strictly surrogate.

---

### Post by toupeiro on 2008-05-02
My guess would be "ed"  The defacto UNIX text editor which predates even vi.  It was derrived from QED which was used in the mid 60's.

ed still exists in ubuntu.

---

### Post by SomeGuyDude on 2008-05-02
> **jakupl said:**
> haha! why would you trust wikipedia above anything?

I read that Wikipedia is more reliable than the Encyclopedia Britannica, Lexus Nexus, and the Library of Congress combined.

---

### Post by nrs on 2008-05-02
> **toupeiro said:**
> My guess would be "ed"  The defacto UNIX text editor which predates even vi.  It was derrived from QED which was used in the mid 60's.

ed still exists in ubuntu.

AFAIK it's a GNU implementation of it, not the original.

---

### Post by amingv on 2008-05-02
> **SomeGuyDude said:**
> I read that Wikipedia is more reliable than the Encyclopedia Britannica, Lexus Nexus, and the Library of Congress combined.

It is also slightly cheaper.

---

### Post by toupeiro on 2008-05-02
> **nrs said:**
> AFAIK it's a GNU implementation of it, not the original.

I am sure some of the original code is still implemented.  Its not like its very sophisticated.  All one really needs to do is use a GNU compiler to make a GNU implementation. :)

---

### Post by koenn on 2008-05-02
> **toupeiro said:**
> I am sure some of the original code is still implemented.  Its not like its very sophisticated.  All one really needs to do is use a GNU compiler to make a GNU implementation. :)
Given that the GNU project was started to re-create unix, but free of licenses etc., it would have been rather stupid to re-use the (licensed, copyrighted, ...) code and just 'compile it with a GNU compiler'. 
Gnu stands for "gnu is _not unix_", to indicate that they did not use unix code.

---

### Post by nrs on 2008-05-02
> **toupeiro said:**
> I am sure some of the original code is still implemented.  Its not like its very sophisticated.  All one really needs to do is use a GNU compiler to make a GNU implementation. :)

If only :'). Apple uses GCC.

---

### Post by Tomatz on 2008-05-02
> **tamoneya said:**
> well it is probably easier to say what is the oldest piece of code in the kernel.  The kernel has been around the longest and although there have been many changes I am sure there is some ANCIENT code in there.

Actually the telnet client's code would be much older than the kernel. As to what part is the oldest i have no idea.

---

### Post by toupeiro on 2008-05-02
> **koenn said:**
> Given that the GNU project was started to re-create unix, but free of licenses etc., it would have been rather stupid to re-use the (licensed, copyrighted, ...) code and just 'compile it with a GNU compiler'. 
Gnu stands for "gnu is _not unix_", to indicate that they did not use unix code.

1.  GNU is an operating system, ed is an application... very different from the guidelines for the GNU Operating system...  

2.  ed being distributed under GPL indicates a change in license, not necessarily in code.

my point:  its not very stupid at all..  Its done all the time!

---

### Post by nrs on 2008-05-02
> **toupeiro said:**
> 1.  GNU is an operating system, ed is an application... very different from an Operating system...  

2.  ed being distributed under GPL indicates a change in license, not necessarily in code.

An operating system is a collection of applications. ed was a part of the UNIX operating system. 

Put it this way, if the GNU project could've just taken the source code from one of the UNIXs and changed the license, there wouldn't really have been a need to write everything from scratch, which they did, and there wouldn't even be a need the project itself, would there?

---

### Post by ghowells on 2008-05-02
I would also have to put in a vote for some of the stuff in the bsdgames package.  Hunt the Wumpus is practically an antique!

---

### Post by toupeiro on 2008-05-02
> **nrs said:**
> An operating system is a collection of applications. ed was a part of the UNIX operating system. 

Put it this way, if the GNU project could've just taken the source code from one of the UNIXs and changed the license, there wouldn't really have been a need to write everything from scratch, which they did, and there wouldn't even be a need the project itself, would there?


I dont have any facts to base myself on for this debate, but let me explain why I think as I do: 

ed was an application written by Ken Thompson, who was basically the founder of the UNIX operating system, but there was also several other UNIX variants, the biggest being in the late 70's.  CB-UNIX was formed which turned into system-v, a variant that sprung off HP-UX, AIX, IRIS, and eventually worked itself into Solaris which was originally a branch of BSD.  All these UNIX OSes were covered under different licenses as they developed, yet programs like ed were incorporated into all of them.  To the best I have been able to research, as soon as it was possible, eds source was distributed under GPL, in which case there would be one source for all OSes, including GNU.  This process was the case with many pieces of software, I don't think its so far fetched to believe the same was done with ed.  There were definately applications that were completely rewritten for GNU, and others that made it into GNU via GPL.  If not, as you say, why would you even need such a project.  Having never worked with it myself, I couldn't tell you if ed was available in stallmans first GNU/OS.  But, I am certain GNUemacs was. ;)  I understand the principles behind Stallmans OS and license, but I don't think its so far fetched to think that ed has been perpetual source.

---

### Post by GavinZac on 2008-05-02
> **amingv said:**
> It is also slightly cheaper.

And has "Don't Panic" written in large, friendly letters on the cover.

---

### Post by Erik Trybom on 2008-05-02
So do we have a winner yet? According to Wikipedia Ed predates Vi, which was released in 1976. Would that make Ed the oldest piece of code in Ubuntu?

Neither the Linux kernel nor anything from the GNU toolchain existed at this time. Make was written in 1977, but I don't think GNU Make contains any of that code. Development on BSD also started in 1977, so probably none of those packages are older than Ed.

---

### Post by koenn on 2008-05-02
> **toupeiro said:**
> I dont have any facts to base myself on for this debate, but let me explain why I think as I do: ...

Better get the facts. Just because there was an 'ed' in Unix doesn't mean GNU would just copy and recompile it. That would indeed be stupid, 'cause it would jeapardize the project (patent claims, copyright infringement, licensing issues ... remember the SCO case ?). I assume a man like Stallman would have had the foresight and prudence to stay away from such hazards.
5yes, that's an assumption, but there's supporting evidence). 


> **Erik Trybom said:**
> So do we have a winner yet? According to Wikipedia Ed predates Vi, which was released in 1976. Would that make Ed the oldest piece of code in Ubuntu?

**From the gnu ed source files :** [http://download.savannah.gnu.org/releases/ed/](http://download.savannah.gnu.org/releases/ed/)
AUTHORS:
> 
GNU ed THANKS file - last updated on 15 November 1994.

GNU ed **originated** with the editor algorithm from Brian W. Kernighan &
P. J. Plauger's wonderful book "Software Tools in Pascal," Addison-Wesley,
**1981.**

ed.c
> 
    Copyright (C) 1993, 1994 Andrew Moore, Talke Studio
    Copyright (C) 2006, 2007, 2008 Antonio Diaz Diaz.

Changelog starts at December 1993

---

### Post by skymera on 2008-05-02
> **SomeGuyDude said:**
> I read that Wikipedia is more reliable than the Encyclopedia Britannica, Lexus Nexus, and the Library of Congress combined.

Why Wiki as a reliable source?

It's written by the public at the end of the day.
I can go on and edit the whole Linux page saying it tastes like bacon.
Im pretty sure it doesn't.

If it does, my hard drive is in trouble ^_^

---

### Post by Sporkman on 2008-05-02
> **nrs said:**
> > Thus, of course, Linus didn't sit down in a vacuum and suddenly type in the Linux source code. He had my book, was running MINIX, and undoubtedly knew the history (since it is in my book). But the code was his. The proof of this is that he messed the design up.

:lol:

---

### Post by Sporkman on 2008-05-02
> **SomeGuyDude said:**
> I read that Wikipedia is more reliable than the Encyclopedia Britannica, Lexus Nexus, and the Library of Congress combined.


> Bart: So Dean Martin would show up at the last minute and do everything in just one take?
Homer: That's right.
Bart: But Wikipedia said he was "passionate about rehearsal".
Homer: Don't you worry about Wikipedia. We'll change it when we get home. *We'll change a lot of things.* 

-Simpsons, *Apocalypse Cow*

[http://en.wikiquote.org/wiki/The_Simpsons/Season_19#Apocalypse_Cow_.5B19.17.5D](http://en.wikiquote.org/wiki/The_Simpsons/Season_19#Apocalypse_Cow_.5B19.17.5D)

---

### Post by Steveway on 2008-05-02
> **skymera said:**
> Why Wiki as a reliable source?

It's written by the public at the end of the day.
I can go on and edit the whole Linux page saying it tastes like bacon.
Im pretty sure it doesn't.

If it does, my hard drive is in trouble ^_^

The good thing of Wikipedia is that it is watched over all the time. If you change the article like you said then it will be reverted in a blink of an eye.
It's the same model that Linux is developed in, everyone can contribute but if you wreck havoc then nobody will trust you and your stuff will not get to the official one.
Spread your FUD somewhere else, gosh.

---

### Post by Sporkman on 2008-05-02
> **skymera said:**
> Why Wiki as a reliable source?

It's written by the public at the end of the day.
I can go on and edit the whole Linux page saying it tastes like bacon.
Im pretty sure it doesn't.


You could, but your change would be reverted within an hour. This is more of a problem for thinly followed topics, such that those articles aren't followed very closely by many.

Now, if someone were doing research on Linux, and by bad luck happened to come upon your modified Linux article before it was reverted, well then they might have a disappointing (yet exceptionally fast & stable) breakfast...

---

### Post by phrostbyte on 2008-05-02
I'd say bsdgames.

---

### Post by toupeiro on 2008-05-02
> **koenn said:**
> Better get the facts. Just because there was an 'ed' in Unix doesn't mean GNU would just copy and recompile it. That would indeed be stupid, 'cause it would jeapardize the project (patent claims, copyright infringement, licensing issues ... remember the SCO case ?). I assume a man like Stallman would have had the foresight and prudence to stay away from such hazards.
5yes, that's an assumption, but there's supporting evidence). 




**From the gnu ed source files :** [http://download.savannah.gnu.org/releases/ed/](http://download.savannah.gnu.org/releases/ed/)
AUTHORS:


ed.c

Changelog starts at December 1993

So I guess another point you are making here is that sourcing an algorithm from a pascal book in 1981 and later using that same algorithm in a c based application which you likely created from scratch, you are saying there is no chance that algorithm used in pascal, demonstrated in that book was not also used in PL-M or original C compilations of ed? You're saying Brian Kernighan and P.J. Plauger had no citations from Ken Thompson and Dennis Ritchie's code?  Are you sure this is a fact? You gave me some facts in your last post, but in giving me them I still think you have more facts to get, as well as I.  Since I'm not going to go and buy a book to try to prove my theory correct, id say its fair enough to say GNU ed the application is not the oldest piece of perpetual code.

In fact, I'll go a step further and say that by your logic in demonstrating that going one source back is enough evidence to prove that there is no original design in the code in question, you are hard pressed to find anything very old in linux.

---

### Post by zmjjmz on 2008-05-02
X maybe?

---

### Post by ice60 on 2008-05-02
> **SomeGuyDude said:**
> I read that Wikipedia is more reliable than the Encyclopedia Britannica, Lexus Nexus, and the Library of Congress combined.
lol.

have you seen 'The Truth According To Wikipedia' it's on youtube i think.
[http://youtube.com/watch?v=WMSinyx_Ab0](http://youtube.com/watch?v=WMSinyx_Ab0)

---

### Post by koenn on 2008-05-02
> **toupeiro said:**
> So I guess another point you are making here is that sourcing an algorithm from a pascal book in 1981 and later using that same algorithm in a c based application which you likely created from scratch, you are saying there is no chance that algorithm used in pascal, demonstrated in that book was not also used in PL-M or original C compilations of ed? You're saying Brian Kernighan and P.J. Plauger had no citations from Ken Thompson and Dennis Ritchie's code? 
There's a big difference between an algorithm and an implementation. The same algorithm can be implemented in several ways, in different languages, using different programming styles, etc. 
The fact that the autors of gnu ed mention that they based their version of ed on an algorithm they found in a book published in 1981, means imo that
1- they created their own code to implement that algorithm
2- they didn't write that code before 1981

All the rest is speculation.

---

### Post by CREEPING DEATH on 2008-05-02
I'd say Bash or an editor.

CD

---

### Post by toupeiro on 2008-05-02
> **koenn said:**
> There's a big difference between an algorithm and an implementation. The same algorithm can be implemented in several ways, in different languages, using different programming styles, etc. 
The fact that the autors of gnu ed mention that they based their version of ed on an algorithm they found in a book published in 1981, means imo that
1- they created their own code to implement that algorithm
2- they didn't write that code before 1981

All the rest is speculation.

Not if that algorithm is the heart of your implementation.  Ask any geologist or anyone with a career in math and science if there is a big difference.  In many circumstances, the algorithm is what is protected, not the code around it.  I'd say my speculation is as good as yours...

---

### Post by iSplicer on 2008-05-02
> **strAlan said:**
> I don't trust any source except wikipedia.

why? Wikipedia is written by the public, so why trust it so much?

---

### Post by steveneddy on 2008-05-02
I believe the oldest piece of code would be the zero.

Because software is only the one and zero, and the computer started in the late 30's turned off, off is zero and the one is on. So my answer is the zero. Zero is the oldest piece of code in Linux.

Now, lets close this thread and move on to something a little more interesting.

---

### Post by koenn on 2008-05-03
> **toupeiro said:**
> Not if that algorithm is the heart of your implementation.  Ask any geologist or anyone with a career in math and science if there is a big difference.  In many circumstances, the algorithm is what is protected, not the code around it.  I'd say my speculation is as good as yours...

ask a programmer in stead. 

and you have it backwards : it's code and implementation that is protected, not algorithms. You can not copyright an idea or an abstraction, only text. you can patent inventions, not the scientific principle they are based on - although lately, the patent system is being abused by people patenting ideas rather than concrete "inventions".

I'd say my speculation is far more plausible than yours

---

### Post by koenn on 2008-05-03
Off Topic
> **koenn said:**
> ask a programmer in stead. 

By lack of a programmer at hand, I asked google :

consider the bubble sort algorithm. It's a simple algorithm to sort items. It goes something like :

1. put your items in a row
2  compare each item with the next. If an item is bigger than the following one, make them swap places. (Repeat for all items)
3. Repeat step 2 untill you find you did not have to swap anything. Your row is now sorted

_Implementations_
Here's a list of 21 different implementations. They differ by language, but it illustrates how the same algorithm can be implemented in many different ways : [http://en.wikibooks.org/wiki/Algorithm_implementation/Sorting/Bubble_sort](http://en.wikibooks.org/wiki/Algorithm_implementation/Sorting/Bubble_sort)

Here are 4 different implementations in the same language (C++)
[http://en.wikibooks.org/wiki/Algorithm_implementation/Sorting/Bubble_sort#C.2B.2B](http://en.wikibooks.org/wiki/Algorithm_implementation/Sorting/Bubble_sort#C.2B.2B)
[http://www.paked.net/subject_pages/computer_science/prog2.htm](http://www.paked.net/subject_pages/computer_science/prog2.htm)
[http://tuxv.blogspot.com/2007/04/bubble-sort.html](http://tuxv.blogspot.com/2007/04/bubble-sort.html)
[http://www.datastructures.info/what-is-bubble-sort-and-how-does-it-work/](http://www.datastructures.info/what-is-bubble-sort-and-how-does-it-work/)

Note that most of these implementations use arrays. but you could also implement the same algorithm using linked lists, vectors, or some other container.

---

### Post by thomashauk on 2008-05-03
There is some BSD code in the Kernal which could be very old.

---

### Post by Foster Grant on 2008-05-03
X dates from the early 1980s (and itself stems from the W windowing system), so it would have to be on the list.

---

### Post by toupeiro on 2008-05-03
> **koenn said:**
> ask a programmer in stead. 

and you have it backwards : it's code and implementation that is protected, not algorithms. You can not copyright an idea or an abstraction, only text. you can patent inventions, not the scientific principle they are based on - although lately, the patent system is being abused by people patenting ideas rather than concrete "inventions".

I'd say my speculation is far more plausible than yours

I hate to break it to you, but I do not have it wrong about copywritten algorithms.  the company I work for has thousands of them, as algorithms usually have a direct impact on the results you are trying to achieve. The code surrounding the algorithm used to generate the results can be changed by whomever, for whomever, but unless its our company changing it, the same algorithm cannot be legally utilized without permission. All you are really doing is talking about once side of a coin, forgetting that there is another.  It doesn't make you any more correct or incorrect than I...

---

### Post by qazwsx on 2008-05-03
I think gnu project merged freely aviable code in their project.
Allmoust impossible to find answer, I guess.

---

### Post by koenn on 2008-05-03
> **toupeiro said:**
> I hate to break it to you, but I do not have it wrong about copywritten algorithms.  the company I work for has thousands of them, as algorithms usually have a direct impact on the results you are trying to achieve. The code surrounding the algorithm used to generate the results can be changed by whomever, for whomever, but unless its our company changing it, the same algorithm cannot be legally utilized without permission. All you are really doing is talking about once side of a coin, forgetting that there is another.  It doesn't make you any more correct or incorrect than I...

You're in the USA, right ? That would explain your twisted view on patents.  

Patents were conceived to make public _inventions_, not mere ideas or concepts. An algorithm is a description of a process, and usually quite abstract, and not eligible for a patent. A given implementation of an algorithm, i.e. the source code or a program, would be something tangible, and patentable. There's some grey area in between, because some patents are more abstract than others, but usually this distinction holds. In fact, in 1972, the U.S. Supreme Court found that "We do not hold that no process patent could ever qualify ... " but also ruled that a patent for a process should not be allowed if it "in practical effect would be a patent on the algorithm itself". ([http://caselaw.lp.findlaw.com/scripts/getcase.pl?navby=CASE&court=US&vol=409&page=63](http://caselaw.lp.findlaw.com/scripts/getcase.pl?navby=CASE&court=US&vol=409&page=63) )
However, in the 1980s and 90s, it became accepted to patent software, algorithms and even mere ideas about things a computer could do - at least in the U.S., but this is actually a pervertion of the patent system. In Europe and other parts of the world, the patent system has remained closer to its original goal.

In any case, it still seems more plausible to me that the Gnu project would have created a line editor by implementing a published algorithm than by copying source code and risk legal trouble, especially since the gnu project was started as a reaction against patents, copyrights and licensing.

---

### Post by jmolina on 2009-04-01
Yeah, you are right. According to Rich Burridge (GNOME developer), the multi-precision arithmetic engine used on his gcalctool utility (the default gnome calculator, so it's in Ubuntu), comes from a fortran code written in the 70's.

More information here: [http://blogs.sun.com/richb/entry/the_oldest_running_computer_code](http://blogs.sun.com/richb/entry/the_oldest_running_computer_code)

You can also look for the quota.h and bsd_comp.c files on the Linux kernel, they are borrowed from BSD, so they're also strong candidates.

And many of the code on util-linux.... And X.org... But I think the gnome calculator is the oldest. If you look at the license file, you will find it was written in 1985 or 86, and then ported to gtk.  And the CDE calc uses the same code.  SUN decided to license it under the GPL recently.

---

### Post by MaxIBoy on 2009-04-01
EDIT: Blammed, point has been made elsewhere.

---

### Post by Dr. C on 2009-04-01
I would guess some code RMS modified in his youth that subsequently found its way in the GNU project.

> In 1971, when Richard Stallman started his career at MIT, he worked in a group which used free software exclusively. Even computer companies often distributed free software. Programmers were free to cooperate with each other, and often did from [http://www.gnu.org/gnu/gnu-history.html]("http://www.gnu.org/gnu/gnu-history.html")

---

