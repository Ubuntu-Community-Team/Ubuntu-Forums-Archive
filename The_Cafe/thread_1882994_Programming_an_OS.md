---
title: "Programming an OS"
date: 2011-11-18
forum: The Cafe
---

### Post by forrestcupp on 2011-11-18
I've been having an amusing conversation with an overly zealous person who believes he can achieve his dream of programming his own complete operating system from scratch. He has absolutely no programming experience, and he intends to do it as a side project in the evenings between playing computer games.

Even after telling him that the Linux kernel alone, not including all of the other parts of the OS, has over 10 million lines of code programmed over a span of 20 years by thousands of developers working together, he still is undaunted.

I can't wait for the beta to come out. :)

---

### Post by Majorix on 2011-11-18
That's a funny one :D

---

### Post by matt_symes on 2011-11-18
Does he understand the hardware either ?

Does he know about the GDT, LDT, IDT, ACPI, DMI, protected and real modes, PCIs, APCIs, assembler, rings, gates etc etc etc.

Pull his leg. Tell him he needs to learn HTML to write it in :)

---

### Post by forrestcupp on 2011-11-18
> **matt_symes said:**
> 
Pull his leg. Tell him he needs to learn HTML to write it in :)
He started out talking about how he was trying to learn Visual Basic. :D

---

### Post by thatguruguy on 2011-11-18
> **matt_symes said:**
> 
Pull his leg. Tell him he needs to learn HTML to write it in :)

Now, that's just silly. He will obviously need javascript, too.

---

### Post by forrestcupp on 2011-11-18
There is another guy on there who is actually giving him names of a bunch of books that teach about these things. I guess there's nothing wrong with giving him the proper resources and letting him learn for himself.

Why should I care if he jumps in over his head and gives up?

---

### Post by cgroza on 2011-11-18
I don't think he will go too far. I bet he will give up upon the first problem to get that kernel booted.

---

### Post by DangerOnTheRanger on 2011-11-18
I can personally testify that just getting something that can boot into protected mode takes around a week or so - this is no small task. Still, it's always hilarious to hear of people like this :D

---

### Post by matt_symes on 2011-11-18
> He started out talking about how he was trying to learn Visual Basic. :grin:

*chuckles to oneself*

---

### Post by lykwydchykyn on 2011-11-18
I know someone like this.  He's 10 years old. But he knows some python, at least.

---

### Post by MG&amp;TL on 2011-11-18
Tell him to have a look at linux from scratch or MikeOS.

Then give him a copy of "The C programming language" and see how he gets on. If he's any good, tell him to become a kernel devloper instead.

Visual Basic. :D

---

### Post by matt_symes on 2011-11-18
> **DangerOnTheRanger said:**
> I can personally testify that just getting something that can boot into protected mode takes around a week or so - this is no small task. Still, it's always hilarious to hear of people like this :D 

Yeap. Once did something similar myself using Bochs as an x86 emulator. Simple bootloader, booting to a keyboard and vesa controller kernel in protected mode using a flat memory model like Linux and Windows kernel.

T'was a good many years ago now.

---

### Post by matt_symes on 2011-11-18
> **MG&TL said:**
> Tell him to have a look at linux from scratch or MikeOS.

Then give him a copy of "The C programming language" and see how he gets on. If he's any good, tell him to become a kernel devloper instead.

Visual Basic. :D

This is good advice.

Get him to read the intel developers manuals as well. After all, he has to execute those privileged x86 instructions somehow.

---

### Post by MG&amp;TL on 2011-11-18
> **matt_symes said:**
> This is good advice.

Get him to read the intel developers manuals as well. After all, he has to execute those privileged x86 instructions somehow.

Oh god, I read bits of those. :shock: Give him/her a chance...:D

---

### Post by forrestcupp on 2011-11-18
> **MG&TL said:**
> Tell him to have a look at linux from scratch or MikeOS.

Then give him a copy of "The C programming language" and see how he gets on. If he's any good, tell him to become a kernel devloper instead.

Visual Basic. :D

Some of that has actually been discussed. We've brought up Linux From Scratch, and even tweaking Ubuntu and using Remastersys. I've also encouraged him to work towards becoming a part of GNU/Linux development.

I think he wants to actually create an entire OS from scratch, though. As I said earlier, someone else gave him info on a bunch of resources, so he can do whatever he wants with it.

I don't personally know the guy. It was a thread on a different forum.

---

### Post by BrokenKingpin on 2011-11-18
You see this all the time with new programmers. Another one is people with no programming experience who think they can create an MMO from scratch.

---

### Post by forrestcupp on 2011-11-18
> **BrokenKingpin said:**
> You see this all the time with new programmers. Another one is people with no programming experience who think they can create an MMO from scratch.

I know. I can understand wanting to create an MMO, but why do they always want to create a whole OS from scratch? :-k

---

### Post by MG&amp;TL on 2011-11-18
> **forrestcupp said:**
> I know. I can understand wanting to create an MMO, but why do they always want to create a whole OS from scratch? :-k

Because you assume it can't be as difficult as first thought.

I was first dispelled of that impression when I downloaded a kernel to see what it was like. :)-all of two months ago.

---

### Post by V for Vincent on 2011-11-18
Well, Linux does have a monolithic kernel. An embedded or microkernel-based OS can be done by one person. Though I doubt that's what your acquaintance has in mind.

---

### Post by YeOK on 2011-11-18
You have to respect his ambition. I would tell him to buy a book I read many years ago, "Programmer's Guide to the I. B. M. Personal Computer" by Peter Norton. 

It's old, it's assembler and most of it is based on DOS interrupts, but I've never read a book since; which gives you a better understanding of how computers actually work.

---

### Post by matt_symes on 2011-11-18
> **V for Vincent said:**
> Well, Linux does have a monolithic kernel. An embedded or microkernel-based OS can be done by one person. _*Though I doubt that's what your acquaintance has in mind*_.

*chuckles to oneself again*

---

### Post by MG&amp;TL on 2011-11-18
> **YeOK said:**
> ... I've never read a book since; which gives you a better understanding of how computers actually work.

I thought for a minute there you meant you had never read a book since, and that was what helped you with computers. :)

---

### Post by keithpeter on 2011-11-18
Hello forrestcupp and all

What age range is the chap concerned?

If adult, perhaps suggest that some bug tracking and squashing experience would be useful and to start a launchpad account and pick a few papercuts to work on.

Complexity revealed through details...

If child, then a raspberry pi might be easy enough to peek and poke some kind of system. I grew up on Sinclair ZX81 BASIC and BBC BASIC. Spaghetti code special :twisted:

The raspberry project is specifically designed to introduce hacking and peek/poke malarkey to a new generation...

[http://www.raspberrypi.org/](http://www.raspberrypi.org/)

---

### Post by Megaptera on 2011-11-18
> **forrestcupp said:**
> I've been having an amusing conversation with an overly zealous person who believes he can achieve his dream of programming his own complete operating system from scratch. ...

Well ...it's better than going out and mugging old ladies!

---

### Post by forrestcupp on 2011-11-18
> **YeOK said:**
> You have to respect his ambition. I would tell him to buy a book I read many years ago, "Programmer's Guide to the I. B. M. Personal Computer" by Peter Norton. 

It's old, it's assembler and most of it is based on DOS interrupts, but I've never read a book since; which gives you a better understanding of how computers actually work.The Commodore 64 Programmer's Reference Guide was pretty good, too. I almost knew that book by heart from cover to cover. It had a whole section on assembly language, and it mapped out every memory register in the operating system and KERNAL. (and yes, they did spell it with an 'a' :) ). I did some work switching the ROM to RAM and tweaking the operating system. Things are much, much different nowadays, though. ;)

> **Megaptera said:**
> Well ...it's better than going out and mugging old ladies!True! :lol:

---

### Post by lisati on 2011-11-18
Ah, the ambition! The nearest I've managed to making my own OS is modifying a program intended for a TRS-80 to unlock some disabled features on a [VZ300]("http://en.wikipedia.org/wiki/VZ300"), and that was some years ago. Apparently the firmware was influenced by that of the TRS-80.

---

### Post by Gremlinzzz on 2011-11-18
Start em with 
"Hello World"
:popcorn:

---

### Post by Gremlinzzz on 2011-11-18
How to make a OS in 4 hours:popcorn:
[http://www.youtube.com/watch?v=XZ5TajZYW6Y](http://www.youtube.com/watch?v=XZ5TajZYW6Y)

---

### Post by LinuxFan999 on 2011-11-18
> **Gremlinzzz said:**
> How to make a OS in 4 hours:popcorn:
[http://www.youtube.com/watch?v=XZ5TajZYW6Y](http://www.youtube.com/watch?v=XZ5TajZYW6Y)
Not funny! I'm tired of these Rickrolls.

---

### Post by forrestcupp on 2011-11-18
> **LinuxFan999 said:**
> Not funny! I'm tired of these Rickrolls.

I clicked on it even after I read your post just to make sure it really is a Rickroll. :)

---

### Post by Gremlinzzz on 2011-11-18
> **forrestcupp said:**
> I clicked on it even after I read your post just to make sure it really is a Rickroll. :)

OK,the Rickroll war is over:popcorn:

---

### Post by Thewhistlingwind on 2011-11-18
He can do it.

He just needs to be a wizard.

[http://os-blog.com/xv6-unix-v6-ported-to-ansi-c-x86/](http://os-blog.com/xv6-unix-v6-ported-to-ansi-c-x86/)

Your friend however, does not sound like he is Dennis Ritchie.

And at this point, Dennis can not help him.

---

### Post by Paddy Landau on 2011-11-18
It isn't [this guy]("http://ubuntuforums.org/showthread.php?t=1879806"), is it?

---

### Post by dniMretsaM on 2011-11-18
That's a lot of ambition. I'll be happy to be a GRUB developer...

---

### Post by DangerOnTheRanger on 2011-11-18
> **Paddy Landau said:**
> It isn't [this guy]("http://ubuntuforums.org/showthread.php?t=1879806"), is it?

From that guy's blog:

> **osdevel.blogspot.com]
Conclusion: if i try to create some operating system releated thing, it should not depend on any platform at all.
[/QUOTE]

Thank *goodness* I wasn't eating or drinking anything said:**
> 
this conception: Get ANY hardware, Get ANY popular kernel wich supported on your stuff, Get ANY virtual kernel (for example, mine ofc ) with an operating system, and run generic BASIC or ASM or whatever programs.


Don't forget this:

[QUOTE=osdevel.blogspot.com]
And the another thing: the console windows. Nobody uses them since 10 years ago, but everybody hails them. ***hattery. Nobody cares about some retard 40 year old obsolote unix *****. Peoples are want to use they computer. So i decided to complitely leave out the console from the operating system. 
[/QUOTE]

Good grief, this guy is hilarious.

---

### Post by Thewhistlingwind on 2011-11-18
> **DangerOnTheRanger said:**
> 

Good grief, this guy is hilarious.

On the subject of "No console".

The Macintosh tried that, they ended up using BSD.

---

### Post by matt_symes on 2011-11-18
Interesting blog entry.

One should never let reality get in the way of a good opinion.

One of the main roles of the kernel is resource management and to do that it has to have an intimate knowledge of the platform it runs on.

But you guys know that anyway; unfortunately not everybody does though.

---

### Post by jjex22 on 2011-11-18
> **YeOK said:**
> You have to respect his ambition. I would tell him to buy a book I read many years ago, "Programmer's Guide to the I. B. M. Personal Computer" by Peter Norton. 

> **forrestcupp said:**
> The Commodore 64 Programmer's Reference Guide was pretty good, too. I almost knew that book by heart from cover to cover. 
True! :lol:


going to add in the old classic 'Operating Systems: Design and Implementation 3rd ed' by Tanenbaum - get him playing around on  Minix and I'm sure the idea of writing an OS will dissipate faster than teens when the party runs dry.

Just point him at gentoo - as someone who has just begrudgingly retired a gentoo set up I can testify to the hassel of a truly "tailored" OS"

---

### Post by DangerOnTheRanger on 2011-11-18
> **matt_symes said:**
> Interesting blog entry.

One should never let reality get in the way of a good opinion.


Except when reality gives you a smack upside the head when you try to make a proprietary OS kernel based off your unsound opinion :)

---

### Post by forrestcupp on 2011-11-19
> **Paddy Landau said:**
> It isn't [this guy]("http://ubuntuforums.org/showthread.php?t=1879806"), is it?

No, that guy actually has some knowledge. The guy I was talking to was starting with absolutely no knowledge, other than knowing from a user perspective what an operating system is.

Maybe we need to start a small OS creation forum, and send all of these guys there to encourage each other's false hopes. :)

---

### Post by cgroza on 2011-11-19
I wonder if Linus had the same responses when he posted on a forum about his idea. :P
Who knows, maybe he will create a new OS that will compete in a world where Linux is the evil world dominating OS. :D
Maybe hi will even find another Richard Stallman to work with.

---

### Post by dniMretsaM on 2011-11-19
> **cgroza said:**
> I wonder if Linus had the same responses when he posted on a forum about his idea. :P
Who knows, maybe he will create a new OS that will compete in a world where Linux is the evil world dominating OS. :D
Maybe hi will even find another Richard Stallman to work with.

Possibly. But you have to remember he started as an under graduate comp. sci. student. Probably never used a GUI in his life.

---

### Post by MG&amp;TL on 2011-11-19
> **dniMretsaM said:**
> Possibly. But you have to remember he started as an under graduate comp. sci. student. Probably never used a GUI in his life.


Did GUIs exist beyond curses then?

---

### Post by dniMretsaM on 2011-11-19
> **MG&TL said:**
> Did GUIs exist beyond curses then?

The original Macintosh came out in 1984 with a GUI, mouse, etc.

---

### Post by Paddy Landau on 2011-11-19
> **forrestcupp said:**
> Maybe we need to start a small OS creation forum, and send all of these guys there to encourage each other's false hopes. :)
:lol: A few front webpages, a nice forum, and a virtual meeting place; it should be worth a few chuckles.

---

### Post by MG&amp;TL on 2011-11-19
> **dniMretsaM said:**
> The original Macintosh came out in 1984 with a GUI, mouse, etc.

Okay, I stand corrected. :D

Considering the Windows 95 interface I've just been looking at though...they can't have made much progress in that time....sorry, it's before my time. :(

---

### Post by /bin/sh on 2011-11-19
If he wants to make an os he will have to do 3 things:
1. Check out mikeos at [http://mikeos.berlios.de](http://mikeos.berlios.de).
2. Learn assembly.
3. Make his first bootloader in assembly.
Anybody who wants to be a serious programmer diggs himself to the very core of programming and learns assembly. Mikeos is where I got my inspiration of assembly, I then realised that assembly is the start of all programming.
Assembly is binary (maskin code) with mnemonics, for example:
in assembly: mov ax, 30 is 11001001 01101110 in binary.

---

### Post by matt_symes on 2011-11-19
> **dniMretsaM said:**
> The original Macintosh came out in 1984 with a GUI, mouse, etc.

Don't forget xerox.

---

### Post by lisati on 2011-11-19
There were a few [gems]("http://en.wikipedia.org/wiki/Graphical_Environment_Manager") around back in the '80s.

---

### Post by oldos2er on 2011-11-19
> **forrestcupp said:**
> I've been having an amusing conversation with an overly zealous person who believes he can achieve his dream of programming his own complete operating system from scratch. He has absolutely no programming experience, and he intends to do it as a side project in the evenings between playing computer games.

This reminds me of the last entry here: [http://www.rinkworks.com/stupid/cs_os.shtml](http://www.rinkworks.com/stupid/cs_os.shtml)

Old, but relevant.

---

### Post by dniMretsaM on 2011-11-19
> **MG&TL said:**
> Considering the Windows 95 interface I've just been looking at though...they can't have made much progress in that time....sorry, it's before my time. :(

Long before my time, too lol. I'm only 16.

> **matt_symes said:**
> Don't forget xerox.

It did exist, but it wasn't available to normal computer users (was there a such thing as a normal computer user back then?). Only to Xerox, then Apple, and then Microsoft. It's kind of funny that IBM turned down one of the greatest revolutions in computer history.

> **lisati said:**
> There were a few [gems]("http://en.wikipedia.org/wiki/Graphical_Environment_Manager") around back in the '80s.

Nice play on words. Lol. That came out ofter the first publicly available GUI did though (I think).

---

### Post by MG&amp;TL on 2011-11-20
> **dniMretsaM said:**
> Long before my time, too lol. I'm only 16.


15. :D

I remember my parents using it. And that was only because I was fascinated by the noise the CRT made.

---

### Post by Paddy Landau on 2011-11-20
> **dniMretsaM said:**
> I'm only 16.
> **MG&TL said:**
> 15.
Tsk, you youngsters.

I started when computers were already using [punched cards]("http://en.wikipedia.org/wiki/Punched_card"), [punched card punchers]("http://www-03.ibm.com/ibm/history/exhibits/vintage/vintage_4506VV4002.html") and [punched card readers]("http://www-03.ibm.com/ibm/history/exhibits/701/701_1415bx11.html"). If you dropped your pile of cards, you'd have to sit and sort the entire thing, so we were very, very careful when you carried them.

The older computer generation would have to program computers by pressing switches up-and-down. I was lucky!

In those days, "GUI" was spelled "gooey" and meant something sticky like a toffee. :)

---

### Post by MG&amp;TL on 2011-11-20
> **Paddy Landau said:**
> Tsk, you youngsters.

I started when computers were already using [punched cards]("http://en.wikipedia.org/wiki/Punched_card"), [punched card punchers]("http://www-03.ibm.com/ibm/history/exhibits/vintage/vintage_4506VV4002.html") and [punched card readers]("http://www-03.ibm.com/ibm/history/exhibits/701/701_1415bx11.html"). If you dropped your pile of cards, you'd have to sit and sort the entire thing, so we were very, very careful when you carried them.

The older computer generation would have to program computers by pressing switches up-and-down. I was lucky!

In those days, "GUI" was spelled "gooey" and meant something sticky like a toffee. :)


How on earth did you ever get anything useful done?

Well...true...the old days sound fun...

---

### Post by sffvba[e0rt on 2011-11-20
Back then they used the best graphics cards ever, your imagination :p


404

---

### Post by effenberg0x0 on 2011-11-20
After starting to code something and realizing that the simplest app sometimes will take you more than 10 hours a day during an entire month to get to a viable alpha stage, he will get tired and do something else. Maybe cure cancer.

---

### Post by Paddy Landau on 2011-11-20
> **MG&TL said:**
> How on earth did you ever get anything useful done?
Well... Instead of sitting in front of a computer, we did fun things.

---

### Post by boast on 2011-11-20
I can see it like creating your own embedded OS for a microcontroller. 

Like someone in the programming section wanted to make his own programming language. You can just parse the syntax and transform it into/compile it in C or directly into ASM.  

But I guess for someone with no programming experience, its just wishful thinking.

---

### Post by KiwiNZ on 2011-11-20
When I was 16 is was playing Rugby, Athletics and those other humans with differently shaped bodies :P

---

### Post by cgroza on 2011-11-20
> **dniMretsaM said:**
> Long before my time, too lol. I'm only 16.

16 too. But I still think sitting in front of a computer is still more fun than outside activities.

---

### Post by MG&amp;TL on 2011-11-20
> **cgroza said:**
> 16 too. But I still think sitting in front of a computer is still more fun than outside activities.

Nah, outdoor activities are on a par, but it's cold out there now. And wet.

---

### Post by JKyleOKC on 2011-11-20
> **Paddy Landau said:**
> If you dropped your pile of cards, you'd have to sit and sort the entire thing, so we were very, very careful when you carried them.Oh, the memories! Once, in those days, I spent almost 8 hours running an 80-column sort over some 2000 cards (data, not a program). They filled four big boxes. Then on the way from the sorting machine in Building 1 back to my office in Building 2, I tripped and dropped the lot. Didn't even try to fix it up...

Backup tapes existed -- but mine were paper tape with holes punched in it.

Things got a lot better when microcomputers came out. We could record our data on cassette tape. I still have a few of those programs, but nothing capable of reading them any more. Still have a few feet of those paper tapes up in the attic, for that matter, unless they have fed a family of mice...

---

### Post by cgroza on 2011-11-20
> **MG&TL said:**
> Nah, outdoor activities are on a par, but it's cold out there now. And wet.
That's exactly what makes the outdoor activities less fun. :D

---

### Post by dniMretsaM on 2011-11-20
> **KiwiNZ said:**
> When I was 16 is was playing Rugby, Athletics and those other humans with differently shaped bodies :P

I would love to play football ("American football" for those of you across the pond) for the high school, but the school district where I live doesn't let homeschoolers play on there sports teams. :( Anyway, it's nice to know I'm not the only youngling here.

---

### Post by MG&amp;TL on 2011-11-21
> **dniMretsaM said:**
> I would love to play football ("American football" for those of you across the pond) for the high school, but the school district where I live doesn't let homeschoolers play on there sports teams. :( Anyway, it's nice to know I'm not the only youngling here.

"youngling"- :D

I'm probably going to get shouted at for this, but isn't American football just a more violent version of English game rugby? *Avec *shoulder pads, obviously.

---

### Post by forrestcupp on 2011-11-21
> **cgroza said:**
> I wonder if Linus had the same responses when he posted on a forum about his idea. :P
Who knows, maybe he will create a new OS that will compete in a world where Linux is the evil world dominating OS. :D
Maybe hi will even find another Richard Stallman to work with.Even Linus didn't create a complete OS by himself. And if you look at it today, the Linux kernel is developed by thousands of people contributing to over 10 million lines of code. Plus, when Linus began working on Linux, operating systems were a lot simpler, especially command line ones.

> **oldos2er said:**
> This reminds me of the last entry here: [http://www.rinkworks.com/stupid/cs_os.shtml](http://www.rinkworks.com/stupid/cs_os.shtml)

Old, but relevant.All I can say is Wow! A $20-$100 bounty for a complete OS that is as full featured as WinXP Pro, so the guy can sell it.

> **MG&TL said:**
> 
I'm probably going to get shouted at for this, but isn't American football just a more violent version of English game rugby? *Avec *shoulder pads, obviously.Actually, rugby is probably more violent. They're similar, but not exactly the same. American football is definitely much more like rugby than it is like soccer, though.

---

