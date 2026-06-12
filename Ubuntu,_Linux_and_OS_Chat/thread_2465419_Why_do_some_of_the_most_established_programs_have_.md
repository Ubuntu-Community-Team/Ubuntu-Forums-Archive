---
title: "Why do some of the most established programs have poor documentation?"
date: 2021-08-01
forum: Ubuntu, Linux and OS Chat
---

### Post by jcdenton1995 on 2021-08-01
Hello all,

Feel free to disagree with this if you like, but I find it odd that some of the most integral programs are really lacking in the documentation department. For example, recently I have been learning about udevd, and the documentation is so basic to say that it's a pretty integral component of some Linux distro's. Compare it with the documentation for something like Apache2, postfix or bash and it's pretty lacking.

Now I'm not complaining because all of this stuff is literally free in every sense of the word, but what I don't understand is why developer(s) would put so much time and effort into writing a sophisticated piece of software, only to not tell anyone else how to use it properly. Surely it's largely pointless at that point? Hypothetically one could write the most powerful and sophisticated program on earth, but if you didn't document how to interact with it for others then it's useless.

I have heard before that the documentation for proprietary/commercial software is way beyond what a lot of FOSS projects can offer, which would be understandable. I'd like to hear what others think and have experienced...

---

### Post by monkeybrain20122 on 2021-08-01
I guess writing documentations is boring for developers and often the users are experts so they can work things out so they just leave it at that, unless there is a substantial commercial user base like apache. I find a lot of software has incomplete, outdated and ambiguous documentation. Often after hours or days of googling and searching forums it turns out that I could have saved a lot of time if the documentation is just a little bit clearer, or a bit more up to date.  The other thing I hate are the stupid mailing lists. What year is this? 1991? My eyes hurt just trying to follow the quotes within quotes. I find the format of github or gitlab much more pleasant for asking questions and reporting bugs.

---

### Post by jcdenton1995 on 2021-08-03
> **monkeybrain20122 said:**
> I guess writing documentations is boring for developers and often the users are experts so they can work things out so they just leave it at that, unless there is a substantial commercial user base like apache. I find a lot of software has incomplete, outdated and ambiguous documentation. Often after hours or days of googling and searching forums it turns out that I could have saved a lot of time if the documentation is just a little bit clearer, or a bit more up to date.  The other thing I hate are the stupid mailing lists. What year is this? 1991? My eyes hurt just trying to follow the quotes within quotes. I find the format of github or gitlab much more pleasant for asking questions and reporting bugs.

I agree, definitely relate to the point about ambiguous documentation. Whenever I'm writing notes about something, I always use a very stiff and formal style, which can seem like overkill, but I know that at some point in the future I'll have forgotten a lot of it and will need a reference that can only be interpreted in one way. I think ambiguous wording in technical docs is sloppy.

I get what you're saying about the user base being able to work it out, I find it a bizarre thing for developers to expect though. I always relate things like this to mending cars, because that was my first love; a car is a physical thing and often not so complicated (although obviously more so as time passes) because many of it's systems involve physical concepts like combustion, gearing, friction, hydraulics, etc.. These are all intuitive things and relatively easy to understand because they are physical, just like we as humans are physical. In addition, broadly speaking almost all cars/trucks/vans are the same, and the skills learned working on one are directly transferable.

contrast that with computer programs which are inherently opaque (even FOSS is opaque for someone like me who only knows a tiny morsel of one or two programming languages). Short of just trying things, the documentation is really all a lot of people have to guide them; a program can't easily be inspected like a physical thing could be. Furthermore the slightest syntactical error or misconfiguration can just break the whole thing, so I find it bonkers that anyone who is writing a program that they intend others to use en masse would skimp on the documentation! It completely undermines all their efforts. It's not a complaint, just an observation.

---

### Post by TheFu on 2021-08-03
The udev team left the building about 10 yrs ago and handed over the code to the systemd team.  Udev was never meant to be touched by end-users. It is for admins and distro makers.  I've touched udev once in my entire 25+ yrs on Linux.  

It was to get a new phone recognized as a USB storage device on connection. Every phone/tablet and other devices that I've ever connected which *just worked* without any modification to udev.   Or they didn't work - ever.  I was shocked when a USB slide/negative scanner *just worked* that hadn't worked since Windows Vista. No 64-bit drivers were created for it and WinXP was the last Windows software for it.

I just scanned the udev, udev.conf and udevadm manpages. Seems there is plenty of information for using those tools. But I didn't try to do anything, so the documentation could be lacking or wrong.

Apache does 1 thing. It serves web pages.  That's relatively easy compared to udev which is basically a plug/driver manager for any sort of device that might ever be connected to a computer.  There must be 20,000 different USB devices that might be connected, each is just a little different.  Plus, many never planned on anyone using Linux with their devices.  Apache was always intended to be used on Unix-like OSes, since the beginning.

Now that the systemd team owns udev (they accepted the code so it wouldn't be abandoned), perhaps the detailed documentation is on freedesktop.org?  I didn't look, but [https://www.freedesktop.org/software/systemd/man/udev.html](https://www.freedesktop.org/software/systemd/man/udev.html)  All things in Unix require some background.  When we are self-taught, it is common to miss very important ideas which makes learning how some things work much harder.  Official training classes these days are forced to skip all sorts of concepts, since they are usually 1 week of intensive subject coverage, not the years of deeper knowledge that can only be gained by working with a mentor.  Unix admins still need to be mentored. There are just too many details to be captured in training or books or self-learned.

I also remember being very frustrated when I was first trying to understand manpages.  They seemed to be written in a foreign tong. Eventually, thanks to the other people in my team who refused to answer questions that were covered in the manpages, I was forced to learn to understand.  Long ago, all manpages used to provide an EXAMPLE section.  Then a bunch of people started trashing their systems by copy/pasting the examples without understanding, so almost all manpage examples were removed.  

Sorry, but I don't have a fix.

---

### Post by Tadaen_Sylvermane on 2021-08-03
> [COLOR=#000000]I also remember being very frustrated when I was first trying to understand manpages[/COLOR][COLOR=#000000]

This was and still is my biggest problem. I usually resort to googling syntax for some things because the man pages are about useless for that. They tell you options you can pass but not the structure of the whole command in some cases. You are left to try various ways until it works. Sed is the biggest one for me. 

> [/COLOR]COMMAND SYNOPSIS
This is just a brief synopsis of sed commands to serve as a reminder to those who already know sed; other doc&#8208;umentation (such as the texinfo document) must be consulted for fuller descriptions.
[COLOR=#000000]
 (ubuntu 20.04, assuming same everywhere). Kind of dumb. Why does it exist if it just tells you to go somewhere else. People say RTFM. The manual says go find texinfo. Where is that exactly?[/COLOR]

---

### Post by TheFu on 2021-08-03
```
$ info sed
```

GNU wanted everyone to use 'info' instead of man.  They lost on the format but haven't given up trying.  Every time GNU creates a manpage, they tend to add a "for more information, see the info".

```
$ man info
``` to get a summary.
```
$ info info
``` to get all the details.

Sorta like ```
man man
```, which explains how manpages are laid out, have different sections, and the goal for manpages.  Until someone actually reads the *man* manpage, they probably will not get all the information out of a manpage which is there and implied just by the format.

---

### Post by Tadaen_Sylvermane on 2021-08-03
Foot, meet mouth. Thank you.

---

### Post by TheFu on 2021-08-03
> **Tadaen_Sylvermane said:**
> Foot, meet mouth. Thank you.

Not really.  I've had the same complaint about info.  I see the GNU effort to push info pages like when a single protestor shows up to protest something that nobody else cares about. The issue is decided already, they just haven't given up.  Info pages have been around longer than I've been using Unix and they are still a pain. ;)

IMHO.

---

### Post by jcdenton1995 on 2021-08-04
> **TheFu said:**
> Official training classes these days are forced to skip all sorts of concepts, since they are usually 1 week of intensive subject coverage, not the years of deeper knowledge that can only be gained by working with a mentor.  Unix admins still need to be mentored. There are just too many details to be captured in training or books or self-learned.

I know what you mean, recently I completed the Linux Foundations "Introduction to Linux" course that is offered through edx.org. It's a 140 hour course that culminates in an open book test. I ended up scoring 99.7% over about 130 questions, but I honestly learned very little from it. The scope of the material was way too big and it just breezed over some topics that would realistically take a month or two alone to get to grips with. It also seemed confused about who it was aimed at, as it was advertised as being suitable for people with a "basic knowledge of computers" but soon winds up teaching bash scripting and configuring network interfaces from the command line, going into great detail about the old class A/B/C IP address space scheme, etc. In 2021 a "basic knowledge of computers" to me is being familiar with the established user applications and perhaps knowing how to install additional software, setup a printer etc.

It was the sort of course I can imagine people would get given at work because their manager thought it would be helpful, say if they were making the transition from windows to a Linux distro, but is actually just a chore with not enough focus on the relevant concepts. I used it as a bit of a curriculum, and often broke off to research the topics in more detail, but honestly I've learned much more from just reading documentation. 

> I also remember being very frustrated when I was first trying to  understand manpages.  They seemed to be written in a foreign tong.  Eventually, thanks to the other people in my team who refused to answer  questions that were covered in the manpages, I was forced to learn to  understand.  Long ago, all manpages used to provide an EXAMPLE section.   Then a bunch of people started trashing their systems by copy/pasting  the examples without understanding, so almost all manpage examples were  removed.

This resonates with me, for a while when I began reading official documentation, some of it was written in such esoteric language to the extent that some of the simplest points were totally lost on me. I'd read it three or four times and then suddenly have that epiphany where it just clicks, and I would think "why don't you just say that then!?" If I'm being honest I now realise sometimes it's necessary in order to avoid writing documentation which is ambiguous and open to interpretation, but other times I think it might just be a symptom of the way in which the developer thinks (programmatic/mathematical thinking). I've only been using Linux since the date that I joined Ubuntu Forums and, thankfully, I can read the docs with relative ease now (depending on the specific document of course).

My biggest beef now is documentation which doesn't contain the information I need, give me man bash any day of the week, it's hard to read and takes a long time to find what you're looking for, but you can be 99.9% sure the information you need is in there. I just can't stand airy fairy, ambiguous and incomplete documentation.

---

### Post by Irihapeti on 2021-08-05
Oh good. I'm glad I'm not the only one. I thought that man pages must be written in a fancy style that you only learn when you get a CS degree. You know, a bit like how med students have to learn all that esoteric medical terminology that the rest of us don't go near.

---

### Post by TheFu on 2021-08-05
> **Irihapeti said:**
> Oh good. I'm glad I'm not the only one. I thought that man pages must be written in a fancy style that you only learn when you get a CS degree. You know, a bit like how med students have to learn all that esoteric medical terminology that the rest of us don't go near.

For the first 6 months of reading manpages, I found them all difficult, then something *clicked* and they started making more and more sense.  manpages aren't training guides. They are references for people familiar, who just need to look something up.

In the old days, programs would come with a Users Guide, Administration Guide, Installation Guide. Each for a different type of reader.  Manpages are split into different sections, each with a specific audience. There are admin commands, user commands, games, .... here's the list.
```
       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions, e.g. /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]
```

If you need to modify a config file, the section 5 is what you want.

---

### Post by zebra2 on 2021-08-08
I've started using Ubuntu OS with Karmic Koala and from the beginning I have used the development version of Ubuntu as my primary OS.  I used Puppy Linux for at least a year before that.  I have encountered many problems over that time period and have become a very good "re-installer" using various methods depending on what was most appropriate for the moment.  To this day I have not failed to find a solution to any problem that I have had with Ubuntu or in fact any Linux OS. Linux has a reputation for being a "techy" experience.  That reputation by itself implies that there are a lot of really smart and experienced users around the Linux world.  Without question a new user will have to be able to follow directions and understand and know how to use google search.  In many cases google search will bring a user right back to this forum.  But understanding and following directions is a talent, a skill and qualitative. My very first customer died a few months ago that I supported with his network for twenty years. At the time just prior to his death he was paying me to answer the same questions he was paying me to answer twenty eight years ago. He was very successful at his business and was task oriented with his software. But regarding the internal workings and problem solving of the system and software he had nothing going at all.  I think the information available for most problems are adequate. The users that we have that can explain to others how to use that information I think are a blessing. Today I'm using Ubuntu Impish with Gnome 40.2 as my primary OS and as always have an updated reinstall disk near by.

---

### Post by monkeybrain20122 on 2021-08-08
That may also have something to do with the geeky personality of the devs. I know a few real geeks and they are the poorest communicators ever. You ask them some questions and they would go into details and commands without explaining what those things are supposed to do (or how to undo things, which is very important and is missing from a lot of tutorials and how-tos) No high level conceptual explanation ever, just details and jargon without proper definitions, lots of which probably irrelevant to the problem. In one aspect they tell you too much irrelevant details but often they are missing the key parts that you do need to know. Now imagine these people translating their rambling into manual. I used  to teach math, if I explain things like that to my students they would have thrown me out of the window,

---

### Post by zebra2 on 2021-08-08
+1 post #13

The instructions are plentiful.
The understand'ers  are few. 

If all else fails, follow the instructions.  (and keep an install disk nearby.)

---

### Post by TheFu on 2021-08-08
> **monkeybrain20122 said:**
> That may also have something to do with the geeky personality of the devs. I know a few real geeks and they are the poorest communicators ever. You ask them some questions and they would go into details and commands without explaining what those things are supposed to do (or how to undo things, which is very important and is missing from a lot of tutorials and how-tos) No high level conceptual explanation ever, just details and jargon without proper definitions, lots of which probably irrelevant to the problem. In one aspect they tell you too much irrelevant details but often they are missing the key parts that you do need to know. Now imagine these people translating their rambling into manual. I used  to teach math, if I explain things like that to my students they would have thrown me out of the window,

Communication is an issue with every expert in any field, not just software or hardware computer people.  Try to have a conversation about Algebra with a Math PhD and even with 21 college hours of math beyond calculus, you can't talk.  I've tried.  
Or talk to a botanist about their field. I've actually seen an IP networking expert and a packet network expert IN-THE-SAME room be unable to communicate using the same white board.  Their worlds didn't intersect.  After about 30 minutes of them sharing terms, a solution that would bridge the packet network onto the IP network was designed.  3 months later, we were deploying it.

When it comes to learning the definitions, that's an ongoing effort for everyone.  Very few people are interested in spending the time to get the required background skills to do even the most basic things. It is frustrating to people who actually did spend that time to learn those things. It probably took them years, yet someone else expects to learn enough in 2 paragraphs to answer a simple question - simple questions seldom have simple answers. That's the way of the world when there's no context around the question or who is asking and why.

---

### Post by monkeybrain20122 on 2021-08-08
> **TheFu said:**
> Communication is an issue with every expert in any field, not just software or hardware computer people.  Try to have a conversation about Algebra with a Math PhD and even with 21 college hours of math beyond calculus, you can't talk.  I've tried..

Actually you can explain some very advanced topics in mathematics such as topology and abstract algebra to even highschool students if you know what the key ideas are and omit the irrelevant details and mechanics. There are a few Russian mathematicians who are really good at that (e.g Arnold or Komolgorov if people know about these names) There are also very good popular  physics  (Hawking, Penrose, Greene etc) and biology (Dawkins) books for lay readers. Mind you, you won't become an expert or be able to read advanced textbooks after reading these, but at least you have an idea about the story. I think some subjects have a narrative, a conceptual framework (like mathematics, physics) Others are less so. Computer science can be very conceptual too if you go into "abstract" fields like computability (which is basically discrete mathematics and logic) but the application areas are more procedural driven, you do a, b and c then d works, a lot of rote memorization and seemingly random facts... There is probably a story behind that but many practitioners are not very good at telling it (or not even try as they tell you to RTFM) The mathematician David Hilbert talked about two types of learners: the conceptual learners and the procedural learners, I suppose many (most) coders are of the second kind on steroid.

---

### Post by TheFu on 2021-08-09
> **monkeybrain20122 said:**
>  Computer science can be very conceptual too if you go into "abstract" fields like computability (which is basically discrete mathematics and logic) but the application areas are more procedural driven, you do a, b and c then d works, a lot of rote memorization and seemingly random facts... There is probably a story behind that but many practitioners are not very good at telling it (or not even try as they tell you to RTFM).

Computer Science has very little to do with coding.  About 50% of the CS people I know cannot code anything. That surprised me.

Programming can be "lot of rote memorization and seemingly random facts", but that's the same as saying that Leonardo da Vinci was just a house painter.

Isn't math mostly "rot memorization and seemingly random facts?"  Didn't everyone get forced to memorize their "times tables?"  When someone hasn't learned basic skills that arithmetic, but wants to jump into n-dimensional calculus, there's a bit of a disconnect. We see that in these forums all the time. It is easy to ask "simple questions" without any background, then become frustrated when the answer isn't 1 command, but 15-35 commands, each needs to be exactly perfect.

And the manpages are still references, not beginning how-to teaching materials. If we read a manpage and don't understand the terms, then we, by definition, don't have the necessary background and need to learn those terms.

---

### Post by monkeybrain20122 on 2021-08-09
> **TheFu said:**
> 

Isn't math mostly "rot memorization and seemingly random facts?"  Didn't everyone get forced to memorize their "times tables?"

Well arithmetic is not really mathematics, neither is accounting, it is like saying spelling is literature. :)

---

### Post by TheFu on 2021-08-09
> **monkeybrain20122 said:**
> Well arithmetic is not really mathematics, neither is accounting, it is like saying spelling is literature. :)

To 99% of the world, arithmetic **is** mathematics. ;)

So, imagine trying to break up basic calculus into manpages that can immediately be put to practical, but exact, use by anyone who doesn't have any background in Theory of Limits.  What would the SEE ALSO section contain?

---

### Post by monkeybrain20122 on 2021-08-09
> **TheFu said:**
> To 99% of the world, arithmetic **is** mathematics. ;)

So, imagine trying to break up basic calculus into manpages that can immediately be put to practical, but exact, use by anyone who doesn't have any background in Theory of Limits.  What would the SEE ALSO section contain?

Who cares about 99% of the world, once upon the time 99% of the world thought the earth was flat and ghosts exist. :)

Actually, Newton did calculus without limit. I once taught a calculus course to college students without limit but along Newton's idea of infinitesimals (basically ignore all higher power terms, technically called o(x^2), and you recover all the usual formulas) These are quantities too small that can be ignored in first order approximations. ;) Basically a lot of American highschool textbooks do try to break up calculus into man pages and they are terrible with emphasis on mindless computations and plugging numbers into formulae but little conceptual development. Well you can do all these with computer algebra packages like maxima these days so those are mostly obsolete skills.

---

### Post by TheFu on 2021-08-09
> **monkeybrain20122 said:**
> Who cares about 99% of the world, once upon the time 99% of the world thought the earth was flat and ghosts exist. :)

Ok, then who cares about 99% of the world who cannot read manpages?

---

### Post by jcdenton1995 on 2021-08-10
> **monkeybrain20122 said:**
> The mathematician David Hilbert talked about two types of learners: the conceptual learners and the procedural learners, I suppose many (most) coders are of the second kind on steroid.

Interesting, In my self learning I've found both the concept and the procedure are key; the concept has to come first for me, and I learn it even if it doesn't make any sense at the time because I know when I dive into using / configuring something and I see the actual 'materials' one has to work with (for want of a better word), the concept will then fall into place because I end up saying "ah! that's that thing", and any number of variations of that. A good example for me is graphics libraries like OpenGL, I remember struggling furiously to try and understand conceptually what a graphics library was, because it was important to understand on a conceptual level, but actually interacting with one was out of the question. I would read article after article, even on the OpenGL website (that was the most opaque of them all) and would just end up asking myself "but what *is* it?". The procedural element was missing; I'm sure I would have understood the concept much sooner if I was writing code that contained function calls to OpenGL libraries, but without first learning the concept the practical aspect itself would be confusing. I think it can be chicken and egg.

I find so much online material focuses either too much on the concept *or* the procedure, and seldom addresses both in equal measure (I'm excluding official documentation as I understand it's not always expected to fully explain the relevant concepts, and sometimes exists more of a reference). I do however love it when I find the one that does, take this dated yet still relevant [guide to writing udev rules]("http://reactivated.net/writing_udev_rules.html") that I found the other week, I think it's a great example and will probably email the author to see if the site is still active.

---

