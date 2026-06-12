---
title: "The Unix Way vs The State of FOSS"
date: 2007-06-22
forum: The Cafe
---

### Post by @trophy on 2007-06-22
So, here's the deal:  I like Linux a lot.  I have worked on the Wintel platform since I was a wee lad, so when I finally learned about "teh linux" it was a lot to wrap my head around, but eventually I learned about the unix philosophy, and I thought it actually did make more sense.  So, I've tried lots of different distros, and eventually settled on my main machine running Ubuntu (because it's less headache to get everything working).

<rant>
But something I've noticed about FOSS is this:  it was explained to me that the unix philosophy is that there should be, for instance, one pile of code on the machine which handles printing, and that way nobody has to code a whole printing system into their word processors and spreadsheet programs... it already exists.  This is undoubtedly a Good Thing.  But what seems to happen in FOSS is that, for no apparent reason, some putz out there will see the current printing system, decide that it sucks, and fork it/write his own.  It's like when Martin Luther split from the Catholic church (which was, in itself, a Good Thing) but the result was that the Protestants ended up splitting any time there was a minor disagreement about anything, and now there's like 12,000 Protestant denominations.

The end result is that if I have one library that I prefer over another (as in "This one works with my hardware and that one doesn't.") I end up downloading some new package, which tells me it depends on the other library, and I'm like "Can't do it.  Can I install you anyway and just live without your printing features?"  And the usual answer is "Nope."
</rant>

So my question is... does anybody else feel that there's way too much re-inventing the wheel going on in the FOSS world?  And if so, what do you think could be done to improve the situation?

---

### Post by @trophy on 2007-06-22
24 views and 0 replies... *NOBODY* has any opinions on this?  Hmm... that's surprising...

---

### Post by juxtaposed on 2007-06-22
I agree with you :P

I don't know the technical stuff though.

---

### Post by lingnoi on 2007-06-22
You seem to be mixing two things. The UNIX way of having one program do one specific thing well and a programmers need to rewrite code that isn't his.

Normally rewriting doesn't really happen in open source unless the code is actually bad at implementing a new feature or needs to be optimized. Branching of code happens the most where people will take a snapshot of the code work on it and merge it back in. Forking a project happens even rarer for example Beryl and Compiz which are now merging back into one project.

---

### Post by amlucent23 on 2007-06-22
agreed. I to think there is too much choice sometimes. Some user just want to be told which program is best for doing a certain task and then learn to use/master that one program.

crude/bad example: listen, exhale, rythmbox, banshee.. the list goes on. I know they work differently under the hood but when I am trying to get someone to switch from MS to Ubuntu. They ask.. can I still use itunes. Explaining this is at best a debacle.

---

### Post by @trophy on 2007-06-22
> **lingnoi said:**
> You seem to be mixing two things. The UNIX way of having one program do one specific thing well and a programmers need to rewrite code that isn't his.

Normally rewriting doesn't really happen in open source unless the code is actually bad at implementing a new feature or needs to be optimized. Branching of code happens the most where people will take a snapshot of the code work on it and merge it back in. Forking a project happens even rarer for example Beryl and Compiz which are now merging back into one project.

Well what I'm talking about is like how when I went on sourceforge a while ago to find out about web systems to remotely control an MP3 server, I was shocked to discover that there were like 10,000 different projects doing that, and they were all virtually identical.  And every so often I like to re-invent the wheel just to learn how the whole thing works, so I can understand that, but at some point you have to figure that there's enough MP3 controllers written in PHP with a MySQL back-end out there.  

It kind of brought me back to my early days of Linux when I was REALLY intimidated by having LOTS of choices for everything and knowing absolutely nothing about any of the choices.  That was back when RH9 came out, and I installed it and there were I think 5 graphical text editors installed by default and I remember thinking to myself "Why do I need 5?  Are there significant differences between them?"

---

### Post by DoctorMO on 2007-06-22
The usual way it to write architectures which allow other developers to implement new features within the bounds.

o'course sometimes the original developers disappear, so you have no choice but the fork.

As for all those PHP projects, when a new idea is out there will be lots of start-ups; but then it should condense into a few projects; just like natural selection.

---

### Post by HeavyAl on 2007-06-22
> **amlucent23 said:**
>  I to think there is too much choice sometimes. 

Whoa! Slow down .. TOO MUCH CHOICE? LIFE is about choices, friends! There are many choices to be made, there is more than one way to skin a cat! You need the RIGHT TOOL for the JOB!

Sorry to yell, but Linux is ABOUT choice! If you don't like something, change it. Linux is also about LEARNING - many of the forks and modifications done on programs were done by people who at first had no programming experience but they wanted something specific so they got their hands dirty and they CHANGED what they didn't like. Then they found that other people also like things the way they did - which added to the community and allowed like minded individuals to CHOOSE the TOOLS that were RIGHT for THEM!

Yes, it can be confusing at times, but computers ARE confusing. They are not a single tool such as a shovel or a hammer - they are more of a swiss army knife - and you have to choose the right tool out of that knife for the given task at hand. Linux gives you access to more of these tools than any other OS - and beyond that it allows you to tweak these tools to your own specific needs.

Ok, I'm rambling out of control, I think. Hope I didn't offend anyone.

---

### Post by Ex-Cyber on 2007-06-22
"The UNIX way" has more or less been slowly dying even since UNIX went to Berkeley, and the current state of F/OSS and especially GNU and Linux is really its own thing that happens to share some of the same mechanisms. Whether that's good or bad depends on your perspective. See the paper [Program design in the UNIX environment](http://harmful.cat-v.org/cat-v/unix_prog_design.pdf) (PDF) by Rob Pike and Brian Kernighan for more insight into "the UNIX way", and if you want to see a modern OS that really carries on the UNIX tradition, have a look at [Plan 9 from Bell Labs](http://cm.bell-labs.com/plan9/) (but don't expect it to be a replacement for Ubuntu).

---

### Post by IYY on 2007-06-22
This current way of doing things has its advantages; mainly, it provides competition. Instead of having one project dominating the community, you have many projects competing against each other, so that the best ones win. It's like digital evolution. :p

---

### Post by @trophy on 2007-06-22
> **IYY said:**
> This current way of doing things has its advantages; mainly, it provides competition. Instead of having one project dominating the community, you have many projects competing against each other, so that the best ones win. It's like digital evolution. :p

But, to play Devil's Advocate for the moment, that also means that resources are divided.  Instead of having 100 developers and x amount of money/time working on a single solution to whatever, we have 10 projects each with 10 developers and x/10 money/time.

---

### Post by lingnoi on 2007-06-22
Thats true but it also means we have 10 projects looking at the problem in 10 different ways which leads to more innovation and competition.

---

### Post by @trophy on 2007-06-22
> **lingnoi said:**
> Thats true but it also means we have 10 projects looking at the problem in 10 different ways which leads to more innovation and competition.

Yeah, and I'm all about the innovation... I'm just wondering if we could keep the innovation but in such a way as to make a much more efficient use of resources.

---

### Post by macogw on 2007-06-23
Well, it sucks if it's saying you have to use something doesn't work, but overall it's a Good Thing.  There's still "do one thing and do it well" for most programs (though some people are starting to get on this "integration" bandwagon which I think simply presents more problems.  ex: QuickBooks. it has EVERYTHING and consequently you can't ever find ANYTHING).  It's just that there's more than one thing for each task.  Having more than one isn't bad.  If you don't like the way one program works or looks or whatever, use another.

---

### Post by @trophy on 2007-06-23
> **macogw said:**
> it has EVERYTHING and consequently you can't ever find ANYTHING


Those were my exact thoughts when I first tried out KDE.  And every time I've tried it since.  So I use GNOME, though I don't much care for it either.  And being a software designer myself, I understand it's a tough line to walk... you need to HAVE all the features, but keep the ones that nobody ever uses out of the way until they're needed.  Perhaps all we need is to kidnap all of the GUI designers at Apple... hmm.

---

### Post by macogw on 2007-06-25
> **@trophy said:**
> Those were my exact thoughts when I first tried out KDE.  And every time I've tried it since.  So I use GNOME, though I don't much care for it either.  And being a software designer myself, I understand it's a tough line to walk... you need to HAVE all the features, but keep the ones that nobody ever uses out of the way until they're needed.  Perhaps all we need is to kidnap all of the GUI designers at Apple... hmm.

No!  I hate Aqua.  Too much move-mouse-way-further-than-I-ever-want-to-move-it involved in accessing the menus.

---

### Post by Lord Illidan on 2007-06-25
> **@trophy said:**
> Well what I'm talking about is like how when I went on sourceforge a while ago to find out about web systems to remotely control an MP3 server, I was shocked to discover that there were like 10,000 different projects doing that, and they were all virtually identical.  And every so often I like to re-invent the wheel just to learn how the whole thing works, so I can understand that, but at some point you have to figure that there's enough MP3 controllers written in PHP with a MySQL back-end out there.  

It kind of brought me back to my early days of Linux when I was REALLY intimidated by having LOTS of choices for everything and knowing absolutely nothing about any of the choices.  That was back when RH9 came out, and I installed it and there were I think 5 graphical text editors installed by default and I remember thinking to myself "Why do I need 5?  Are there significant differences between them?"

I feel the same as you.

I like choice. I like the fact that I can pick and choose among different editors/music players/etc, but sometimes I think..what if the developers had agreed to make one real good application together?

We now ended up with a bunch of music players on the GNOME platform..each of which tries to copy Amarok, for example. IMHO, they've got a long way to go, but again, if they had tried to get a team together, they might have done wonders.

The same about the distro scene. Do we need 360 different distros? Sometimes, the only difference is the **license** and the artwork!

And what about projects on sourceforge? Don't get me started. Choice is good, but there is a saying "Too much of a good thing...."

---

### Post by macogw on 2007-06-25
> **Lord Illidan said:**
> 
We now ended up with a bunch of music players on the GNOME platform..each of which tries to copy Amarok, for example. IMHO, they've got a long way to go, but again, if they had tried to get a team together, they might have done wonders.

I, for one, am glad that Banshee lets me avoid using Amarok.

---

### Post by @trophy on 2007-06-25
> **macogw said:**
> No!  I hate Aqua.  Too much move-mouse-way-further-than-I-ever-want-to-move-it involved in accessing the menus.

No argument there... but in general everything is findable, and the lesser-used stuff stays out of your way until you need it.

---

### Post by slavik on 2007-06-25
mplayer has a new front end called "SMPlayer" which is probably buggier than the mplayer supplied one but one thing that I can tell you off the bat is that I like how it is somewhat of a cross between totem, mplayer and vlc

from mplayer - the engine (it actually depends on mplayer)
from vlc - separate window for playlist and such
from totem - how it looks in full screen (move mouse to the bottom and the control panel appears

the enhancement it makes over the stock mplayer UI is that it has buttons to choose audio and subtitle streams which mplayer does not have (have to use keyboard shortcuts).

It would be nice if GG included mplayer and smplayer by default instead of totem.

Here's a second example:
xine vs. gstreamer.
xine was nice but it got to the point where adding new codecs was not fun, so a new architecture needed to be designed, hence gstreamer came along. same goes for OSS -> ALSA.

It's like you have a computer that fits your need and you decide to add functionality to it and realize that you need to upgrade the system to get it. sometimes you need a whole new system. because a single CPU can't do true parallel computing the way an SMP system does.

Similar parallel can be drawn to cars, you can't put NOS or a 700HP engine into a toyota camry without changing the transmission and other things ...

think of it as an equilizer that has linked sliders where if you increase one, it will also increase the once next to it somewhat.

---

### Post by dca on 2007-06-25
Sourceforge, hmmm.  Let's take two very important applications:
 
PMS = Property Management System (for hotels, etc)
POS = Point of Sale (for retail, etc)
 
Both of these applications (more so, solutions) are very programmer intensive.  Inventories on room or product, customer databases, perform audits, etc, etc.  You can find a semi-decent one on sourceforge for each, however, the first one of those in either category that hits a home-run will be the first to move away from a GPL-style license.  They will rebuild it, charge a sh**-load of money for, sell it to you, and turn around & charge a yearly licensing/maint fee on top of that!

---

### Post by Ireclan on 2007-06-25
While I agree that there are now way too many software projects out there trying to do the same thing, in my opinion, that's the natural consequence of Linux. You have so many different programmers out there that want to do things THEIR WAY, and if they don't get things THEIR WAY with CURRENT WAY then they go code THEIR WAY. This leads to lots of innovation, but also lots of replication of features, hence the "reinventing the wheel" phenomenon.

---

### Post by macogw on 2007-06-25
> **slavik said:**
> 
xine vs. gstreamer.
xine was nice but it got to the point where adding new codecs was not fun, so a new architecture needed to be designed, hence gstreamer came along. same goes for OSS -> ALSA.
i prefer xine.  gstreamer is really buggy about dvds and wmv

---

