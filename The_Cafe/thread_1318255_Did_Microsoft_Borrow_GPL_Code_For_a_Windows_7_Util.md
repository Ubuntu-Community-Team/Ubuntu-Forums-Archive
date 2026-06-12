---
title: "Did Microsoft Borrow GPL Code For a Windows 7 Utility?"
date: 2009-11-07
forum: The Cafe
---

### Post by wulfgang on 2009-11-07
[http://tech.slashdot.org/story/09/11/07/1547214/Did-Microsoft-Borrow-GPL-Code-For-a-Windows-7-Utility?from=rss](http://tech.slashdot.org/story/09/11/07/1547214/Did-Microsoft-Borrow-GPL-Code-For-a-Windows-7-Utility?from=rss)

---

### Post by streed on 2009-11-07
Wow... That's pretty suprising coming from Microsoft.

---

### Post by kernelhaxor on 2009-11-07
That article lacks evidence.  All the evidence that exists is one method - ReadBytes ..
I'll wait till there is more conclusive evidence.  So at this point this is just some guy speculating?

---

### Post by Frak on 2009-11-07
One method that is pretty much THE canonical method to do it.

If he came up with pages of text, I would have believed him, but this? Sheesh!

---

### Post by zekopeko on 2009-11-07
> **Frak said:**
> One method that is pretty much THE canonical method to do it.

If he came up with pages of text, I would have believed him, but this? Sheesh!

What can you expect from diggers/slashdoters?
The title reads like a Glen Beck statement.

---

### Post by tom66 on 2009-11-07
If you look at the two methods, they are extremely similar. The only difference is that in Microsoft's version, they have a function, while in ImageReader, it's part of an if block (perhaps this means that Microsoft only needed part of a function).

Constants are expanded in the compiled version, and the coding style is different (presumably due to the decompiler formatting it that way) and some names are different.

---

### Post by Frak on 2009-11-07
> **zekopeko said:**
> What can you expect from diggers/slashdoters?
The title reads like a Glen Beck statement.
QFT

(Quoted for truth)

---

### Post by pwnst*r on 2009-11-07
[QUOTE=some dude on /.]Seriously, what he shows to be evidence looks like code that was written straight from reading the ISO disk image specification. Next up, school math class accused of mass cheating for solving math problems in similar ways.[/QUOTE]

ahahahaha

---

### Post by julianb on 2009-11-16
Since the code for Windows kernel & software and the code for Linux kernel & software often use the same programming languages, windows and open source software are almost the same thing.

[/bad-logic]

---

### Post by phrostbyte on 2009-11-16
Yes, why yes they did. :p

It's funny when you go a week back and [some] people thought this would be such an absurd thing. When Microsoft is involved, I've always had a "suspension of disbelief" and it has yet to fail me. :)

---

### Post by Sealbhach on 2009-11-16
> **streed said:**
> Wow... That's pretty suprising coming from Microsoft.

Not really that surprising. They've used BSD code before, although that's under a different license. If you have Windows XP and run:

> 
C:\WINDOWS\system32>strings *.exe | grep -i university 
you get output like this:
```


C:\WINDOWS\system32\finger.exe: @(#) Copyright (c) 1980 The Regents  of  the University of California.
C:\WINDOWS\system32\ftp.exe: @(#) Copyright (c) 1983 The Regents of the  University of California.
C:\WINDOWS\system32\nslookup.exe: @(#) Copyright (c) 1985,1989 Regents  of the University of California.
C:\WINDOWS\system32\rcp.exe: @(#) Copyright (c) 1983 The Regents of the  University of California.
C:\WINDOWS\system32\rsh.exe: @(#) Copyright (c) 1983 The Regents of the  University of California.
C:\WINDOWS\system32\vmnetdhcp.exe: $Id: inet_addr.c,v 1.1.1.1 1999/11/22 00:57:05 edward Exp $ Copyright (c) 1983, 1990, 1993 The Regents of the University of California. All rights reserved.

```More info on this: [http://www.kuro5hin.org/?op=displaystory;sid=2001/6/19/05641/7357](http://www.kuro5hin.org/?op=displaystory;sid=2001/6/19/05641/7357)


.

---

### Post by Giant Speck on 2009-11-16
> **zekopeko said:**
> What can you expect from diggers/slashdoters?
The title reads like a Glen Beck statement.

No, if the title read like a Glen Beck statement, it wouldn't be a question.  And it'd be interrupted halfway to allow for melodramatic sobbing.

---

### Post by koenn on 2009-11-16
[http://blogs.computerworld.com/15092/microsoft_does_the_right_open_source_thing](http://blogs.computerworld.com/15092/microsoft_does_the_right_open_source_thing)

looks like the OP was right.

---

### Post by t0p on 2009-11-16
> **koenn said:**
> [http://blogs.computerworld.com/15092/microsoft_does_the_right_open_source_thing](http://blogs.computerworld.com/15092/microsoft_does_the_right_open_source_thing)

looks like the OP was right.

While it certainly is good that Microsoft have admitted to using GPLed code and have resolved to relicence it correctly; it does not reflect well on Microsoft that commentators find it so staggering that they are going to obey the law.  "Normally Microsoft are criminals, but this time they're going to be good".  Hmm.

I find it amusing that Microsoft emphasized that purloining the code was "not intentional".  The code accidentally fell into a computer.

It *is* rather surprising that Microsoft have decided to relicence the code properly.  They could have ripped it out and replaced it with something proprietary.  But they've decided to stick with GPLed code.  Does this mean Microsoft have changed their opinion of the GPL?  Ballmer once compared the GPL to a virus, infecting code with its insidious freedom.  But now it's not so bad.

One of the comments at the site linked to above says: "Microsoft will surely have a patent on this software in a few weeks."  That'll make it, what, 239 Microsoft patents that Linux violates?  Before long, the whole of Linux will be owned by Microsoft.  Then they can rename it "Windows 8" and we'll all be united against the evil Apple!

---

### Post by koenn on 2009-11-16
> **t0p said:**
> While it certainly is good that Microsoft have admitted to using GPLed code and have resolved to relicence it correctly; it does not reflect well on Microsoft that commentators find it so staggering that they are going to obey the law.  "Normally Microsoft are criminals, but this time they're going to be good".  Hmm.

Hmm indeed.

> **t0p said:**
> 
I find it amusing that Microsoft emphasized that purloining the code was "not intentional".  The code accidentally fell into a computer.

It was 3rd party code - something they bought or so, and they didn"t find out that it was plagiarism untill after the release.

> **t0p said:**
> 
It *is* rather surprising that Microsoft have decided to relicence the code properly.  They could have ripped it out and replaced it with something proprietary.  But they've decided to stick with GPLed code.  Does this mean Microsoft have changed their opinion of the GPL?  Ballmer once compared the GPL to a virus, infecting code with its insidious freedom.  But now it's not so bad.

They've distributed GPL'd code before - their old "Services for Unix" included some GNU programs. 
So it's probably more a case of opportunism, hypocrisie and marketing strategy than of a change in policies. 


> **t0p said:**
> 
One of the comments at the site linked to above says: "Microsoft will surely have a patent on this software in a few weeks."  That'll make it, what, 239 Microsoft patents that Linux violates?  Before long, the whole of Linux will be owned by Microsoft.  Then they can rename it "Windows 8" and we'll all be united against the evil Apple!

Is it even possible to patent something after it has been established that someone else created it first ?

---

### Post by Frak on 2009-11-16
> **phrostbyte said:**
> Yes, why yes they did. :p

It's funny when you go a week back and [some] people thought this would be such an absurd thing. When Microsoft is involved, I've always had a "suspension of disbelief" and it has yet to fail me. :)
That'd be great if it was Microsoft's fault. It wasn't. It was the fault of a 3rd party studio. So did Microsoft borrow GPL code? No.

OMG MICRO$OFT IS TEH EVILZ. DEY BE STEELIN R CODEZ!1!

---

### Post by koenn on 2009-11-16
> **Frak said:**
> That'd be great if it was Microsoft's fault. It wasn't. It was the fault of a 3rd party studio. So did Microsoft borrow GPL code? No.

They distributed under their name and brand, as part of their current flaship product. 

As a MS spokesman put it: "While we had contracted with a third party to create the tool, we share responsibility as we did not catch it as part of our code review process."

They seem to be more capable of facing facts than you are.

---

### Post by t0p on 2009-11-16
> **Frak said:**
> That'd be great if it was Microsoft's fault. It wasn't. It was the fault of a 3rd party studio. So did Microsoft borrow GPL code? No.

OMG MICRO$OFT IS TEH EVILZ. DEY BE STEELIN R CODEZ!1!

I don't question Microsoft's version of events.  But in Hypothetical Land, it was pretty cool that the code in question was written by a third party.  If it had been created in-house, Microsoft would have had to blame it on a "rogue programmer" or something.

It is quite amazing that Microsoft use software written by third parties without checking it first.  This means that third party coders can create "back doors" and other 3vil h4x0r tricks into Microsoft software.  So security-wise, Windows 7 is really poor.  You'd have to be an idiot to use software that has god-only-knows what vulnerabilities and spywares built into it.

Microsoft's admission has presented us all with the best reason yet why we shouldn't use Windows 7.  Microsoft don't have a clue what's in it!

---

### Post by zekopeko on 2009-11-16
> **t0p said:**
> I don't question Microsoft's version of events.  But in Hypothetical Land, it was pretty cool that the code in question was written by a third party.  If it had been created in-house, Microsoft would have had to blame it on a "rogue programmer" or something.

It is quite amazing that Microsoft use software written by third parties without checking it first.  This means that third party coders can create "back doors" and other 3vil h4x0r tricks into Microsoft software.  So security-wise, Windows 7 is really poor.  You'd have to be an idiot to use software that has god-only-knows what vulnerabilities and spywares built into it.

Microsoft's admission has presented us all with the best reason yet why we shouldn't use Windows 7.  Microsoft don't have a clue what's in it!

I LOL'd. Funny post. Let me put some sanity in it.
The code in question was AFAIK something really standard. If you know what to look for you could find dozens of examples in various programming languages on the net.
They did the code review and I doubt that the reviewer knew that the code was GPLed since it was such a basic thing. Code review means that you look at the code and see if it does what the author says. 

The same kind of "logic" could be applied on Linux and security bugs that passed code review for inclusion in mainline kernel tree. In the end you trust people that you gave the job to do the job and not some-evil-ZOMG!-Linux-is-giving-my-info-to-Nigerian-scamer-thing.

---

### Post by zekopeko on 2009-11-16
> **koenn said:**
> They distributed under their name and brand, as part of their current flaship product. 

As a MS spokesman put it: "While we had contracted with a third party to create the tool, we share responsibility as we did not catch it as part of our code review process."

They seem to be more capable of facing facts than you are.

But they didn't "steal it". The contracted party did that. MS didn't catch it during the code review. Which really is strange since they are all anti-Linux brain eating zombies that are bent on ruling the world with their evil OS ;)

---

### Post by koenn on 2009-11-16
what i see is the irony.

A company so adamant about "intellectual property" caught violating someone else's software license - and admitting that their code review processes were  unable to catch this violation. 
Puts their retoric about license and patent violations in a whole new light, me thinks. 

A company claiming that for innovative, trustworthy, quality software you have to come to them rather than look at those dodgy free software alternatives,  and then releases free software themselves - and they didn't even notice it.

---

### Post by zekopeko on 2009-11-16
> **koenn said:**
> what i see is the irony.

A company so adamant about "intellectual property" caught violating someone else's software license - and admitting that their code review processes were  unable to catch this violation. 
Puts their retoric about license and patent violations in a whole new light, me thinks. 

A company claiming that for innovative, trustworthy, quality software you have to come to them rather than look at those dodgy free software alternatives,  and then releases free software themselves - and they didn't even notice it.

Microsoft released a great deal of open source software.
I could continue to explain things but I'm just gonna leave all of you here, so that you can continue to personify and deify a transnational company with networked divisions.

---

### Post by t0p on 2009-11-16
> **zekopeko said:**
> 
They did the code review and I doubt that the reviewer knew that the code was GPLed since it was such a basic thing. Code review means that you look at the code and see if it does what the author says. 

The same kind of "logic" could be applied on Linux and security bugs that passed code review for inclusion in mainline kernel tree. In the end you trust people that you gave the job to do the job and not some-evil-ZOMG!-Linux-is-giving-my-info-to-Nigerian-scamer-thing.

While my previous post was (obviously) not entirely serious, I think it contained some good points.  Namely that we cannot be entirely confident in software released by Microsoft.

Microsoft made a big thing of the fact that the utility in question was created by a third party.  The clear implication was that if the utility had been produced in-house, the use of GPLed code would have been detected.  Otherwise the fact it was produced by a third party is neither here nor there.

Microsoft are therefore admitting that they rely on these third parties to audit their own code.  So if a third party set out to deceive Microsoft, they might be able to get away with it.

It is the closed-source nature of Microsoft products that makes this a serious danger.  Any code-literate end user can audit Linux code.  But only Microsoft and its trusted associates can audit Microsoft code.  Really, none of us end users knows for sure what is in Windows 7.  And we can't ever get to know.  We have to trust Microsoft's quality control; which has been revealed to be wanting.

---

### Post by koenn on 2009-11-16
> **zekopeko said:**
> Microsoft released a great deal of open source software.
They also released a great deal of FUD about open source software

> **zekopeko said:**
> 
I could continue to explain things  here,
please do

> **zekopeko said:**
> 
but I'm just gonna leave all of you so that you can continue to personify and deify a transnational company with networked divisions.
don't worry, I'm sure Microsoft will be fine even without you coming to their defense.

---

### Post by Frak on 2009-11-16
[Microsoft isn't evil, fanboys.]("http://news.cnet.com/8301-13505_3-10398203-16.html?tag=mncol")

You guys are making Ubuntu look worse by_the_day.

---

### Post by starcannon on 2009-11-16
> **Frak said:**
> [Microsoft isn't evil, fanboys.]("http://news.cnet.com/8301-13505_3-10398203-16.html?tag=mncol")

You guys are making Ubuntu look worse by_the_day.
Who are "you guys"?
Users, bloggers, CNET writers?
The only thing getting more cliché than a fanboy, is an anti-fanboy-fanboy.

*snipped my bad information* 
There is no need to be offensive and generalizing.

---

### Post by Frak on 2009-11-16
> **starcannon said:**
> I read your "I give up" article, and it seems your pretty bitter about your development experience; but there is no need to be offensive and generalizing.

That wasn't me. That was the head EEEBuntu developer.

---

### Post by starcannon on 2009-11-16
> **Frak said:**
> That wasn't me. That was the head EEEBuntu developer.
Ah my bad, I misunderstood your position in another thread.

Still, no need to lump everyone together like that.

I'd also point out that on the issue of MS and the "mistake"; that if someone had "accidentally" used some of their code, they'd be sued into submission... poor Tom Tom.

---

### Post by koenn on 2009-11-16
> **Frak said:**
> fanboys
I usually avoid the use of the word fanboy, because the exsessive use has rendered it meaningless.

I also think you're the one  showing fanboy-like behaviour here, as in :
> **koenn said:**
> 
They seem to be more capable of facing facts than you are.

---

### Post by benj1 on 2009-11-16
> **Frak said:**
> [Microsoft isn't evil, fanboys.]("http://news.cnet.com/8301-13505_3-10398203-16.html?tag=mncol")

You guys are making Ubuntu look worse by_the_day.

why are we making ubuntu look worse?

its funny, as someone pointed out above the irony of microsoft getting caught for stealing others IP (or at the least distributing it). Now its releasing the code under the gpl, which they describe as a virus.

what would happen if the boot was on the other foot? 
oh wait it is according to microsoft, maybe this will persuade them to be merciful with us when they finally decide to sue

---

### Post by Frak on 2009-11-16
> **koenn said:**
> I also think you're the one  showing fanboy-like behaviour here, as in :

You deny more than a lot of people here. For a fairly long time resident, a bit more humility would be in order. You can't just keep serving Ubuntu and Open Source on the silver platter you do so frequently.

---

### Post by Techsnap on 2009-11-16
Although they're not included by default, nobody complains when people "borrow" .dlls for use with WINE now do they?

---

### Post by zekopeko on 2009-11-16
> **t0p said:**
> While my previous post was (obviously) not entirely serious, I think it contained some good points.  Namely that we cannot be entirely confident in software released by Microsoft.

You can't be certain about anything. If you don't know how to code then you are trusting the developers by using their software. FLOSS gets mad props for giving you human readable code but then again did you look at all 3 million lines of kernel code?

> Microsoft made a big thing of the fact that the utility in question was created by a third party.  The clear implication was that if the utility had been produced in-house, the use of GPLed code would have been detected.  Otherwise the fact it was produced by a third party is neither here nor there.

Microsoft are therefore admitting that they rely on these third parties to audit their own code.  So if a third party set out to deceive Microsoft, they might be able to get away with it.

This just proves that you haven't actually read all the info. The "big thing" was a blog post from their community manager explaining the situation. They stated what happened and moved on.
And they don't use 3rd parties to audit code. That is done in house to see if the code is up to their standards. The coding part was outsourced to a 3rd party but not the auditing. And I'm sure that they vet their code for malicious things. Not to mention that the company that would do that would die a horrible death (ah the free market economy). 

> It is the closed-source nature of Microsoft products that makes this a serious danger.  Any code-literate end user can audit Linux code.  But only Microsoft and its trusted associates can audit Microsoft code.  Really, none of us end users knows for sure what is in Windows 7.  And we can't ever get to know.  We have to trust Microsoft's quality control; which has been revealed to be wanting.

Be surprised and amazed:
[http://en.wikipedia.org/wiki/Microsoft_Software_Assurance](http://en.wikipedia.org/wiki/Microsoft_Software_Assurance)
Look under benefits. Windows code isn't some great secret. Thousands of individuals have access to it.

Ask yourself: When I give my laptop/dekstop to the nice guys in computer repair shop,do I always look ,after the repair has been done, if the nice servicemen installed an evil hardware key-logger?

---

### Post by zekopeko on 2009-11-16
> **starcannon said:**
> Who are "you guys"?
Users, bloggers, CNET writers?
The only thing getting more cliché than a fanboy, is an anti-fanboy-fanboy.
 
There is no need to be offensive and generalizing.

Aren't people doing that when they say Microsoft is evil? A company of some 90 000 people that are on 6 continents in different autonomous business divisions are ALL labeled evil when your average Linux fanboy starts yapping.

---

### Post by koenn on 2009-11-16
> **Frak said:**
> You deny more than a lot of people here.
For a fairly long time resident, a bit more humility would be in order.
You can't just keep serving Ubuntu and Open Source on the silver platter you do so frequently.

Care to put that in plain English? I got no idea what you're talking about

---

### Post by zekopeko on 2009-11-16
> **starcannon said:**
> Ah my bad, I misunderstood your position in another thread.

Still, no need to lump everyone together like that.

I'd also point out that on the issue of MS and the "mistake"; that if someone had "accidentally" used some of their code, they'd be sued into submission... poor Tom Tom.

Different things patent and copyright infringement are.

---

### Post by Sealbhach on 2009-11-16
> **zekopeko said:**
> Aren't people doing that when they say Microsoft is evil? A company of some 90 000 people that are on 6 continents in different autonomous business divisions are ALL labeled evil when your average Linux fanboy starts yapping.

I don't know why this thread turned out like this, but you, zekopeko are the only one who brought up the "Microsoft is evil" meme. If you search through the thread for "evil" you will see this:

[http://ubuntuforums.org/search.php?searchid=66875406](http://ubuntuforums.org/search.php?searchid=66875406)

Sometimes, people just project their own meaning into a thread, regardless of the actual content therein. Maybe this is the case here?

.

---

### Post by koenn on 2009-11-16
> **zekopeko said:**
> Aren't people doing that when they say Microsoft is evil? A company of some 90 000 people that are on 6 continents in different autonomous business divisions are ALL labeled evil when your average Linux fanboy starts yapping.
A company presents itself as a single entity with a corporate image. It's that company people refer to, not each of the 90.000 individual employees.

---

### Post by koenn on 2009-11-16
> **sealbhach said:**
> i don't know why this thread turned out like this, but you, zekopeko are the only one who brought up the "microsoft is evil" meme. If you search through the thread for "evil" you will see this:

[http://ubuntuforums.org/search.php?searchid=66875406](http://ubuntuforums.org/search.php?searchid=66875406)

sometimes, people just project their own meaning into a thread, regardless of the actual content therein. Maybe this is the case here?


+1

---

### Post by koenn on 2009-11-16
> **zekopeko said:**
> Different things patent and copyright infringement are.
But usually lumped together in one Intellectual Property pile , by companies such as Microsoft.
Besides that, the analogy stands.

---

### Post by zekopeko on 2009-11-16
> **Sealbhach said:**
> I don't know why this thread turned out like this, but you, zekopeko are the only one who brought up the "Microsoft is evil" meme. If you search through the thread for "evil" you will see this:

[http://ubuntuforums.org/search.php?searchid=66875406](http://ubuntuforums.org/search.php?searchid=66875406)

Sometimes, people just project their own meaning into a thread, regardless of the actual content therein. Maybe this is the case here?

.

I read between the lines ;) (if you are alluding that I'm steering the thread in some shadowy direction for my own nefarious purposes let me just state that it isn't so).

---

### Post by koenn on 2009-11-16
> **zekopeko said:**
> I read between the lines ;) .
Maybe you misread between the lines ;) .

---

### Post by zekopeko on 2009-11-16
> **koenn said:**
> A company presents itself as a single entity with a corporate image. It's that company people refer to, not each of the 90.000 individual employees.

And this is the crux of what I mind when referring to MS as evil.
There are people in MS that love open source and want to move the company in that direction but when people say "MS is evil. He works for evil" our potential FLOSS friends are demonized.

There should be a distinction from MS the corporate company controlled by the board of directors and MS the company that human beings work at (that love FLOSS).

---

### Post by zekopeko on 2009-11-16
> **koenn said:**
> Maybe you misread between the lines ;) .

Always possible when communicating through this medium.
But then again I reacted to what I read as simple MS bashing (reason be damned type, that is).

---

### Post by pwnst*r on 2009-11-16
> **koenn said:**
> Care to put that in plain English? I got no idea what you're talking about

looks like plain English to me.

---

### Post by starcannon on 2009-11-16
> **koenn said:**
> A company presents itself as a single entity with a corporate image. It's that company people refer to, not each of the 90.000 individual employees.
This is correct.

I might say; "That car is red", but the car has some black parts, some chrome parts, some white parts, all visible. When people speak of their opinion of MS, they refer to the company/corporate entity, not the individual pieces of the corporation, this is the common context when people speak of companies. I think zekopeko knows this, and I think the mincing of words to the point of absurdum was meant as a subtle(or not so) attempt at trolling.

---

### Post by phrostbyte on 2009-11-16
> **koenn said:**
> But usually lumped together in one Intellectual Property pile , by companies such as Microsoft.
Besides that, the analogy stands.

It's worth noting that even the GPLv2 includes a patent grant. So by releasing something GPLv2 they would have a hard time suing you for using it afterwords, even with patents.

---

### Post by Frak on 2009-11-16
> **pwnst*r said:**
> looks like plain English to me.
This.

Three points I just have to mention:
1. It was commited by a 3rd party studio. You can say that falls under Microsoft's umbrella all day, but at the end of the day, it was still the 3rd party studio.

2. There is a lot, LOT of open source code out there, GPL or otherwise, and it's hard to decipher code that's canonical compared to code that's original. Compare that to the mass amount of code out there, there's no way to check it all. You can come close, but you can't do it all.

3. Respect Microsoft for how they handled the situation:
a. They recognized the problem.
b. They retracted the project from their site.
c. They launched an audit into the code.
d. They aknowledged that code was indeed stolen.
e. They released possible causes of problems in finding the code and naming all the parties involved.
f. They complied with the license and released the source code.

They did that, and did it in a timely manner. They never refuted the statements, and they were never beligerant to investigate. They did what was the best to do, and if you want to bash them on that, go ahead. I guess finding ammunition these days is hard enough, you have to go after a company just doing their job.

---

### Post by koenn on 2009-11-17
> **pwnst*r said:**
> looks like plain English to me.
looks like a string of plain english words allright, but AFAIK those things are meant to convey meaning, which in this case they fail to do.

besides, I wasn't asking you.

---

### Post by koenn on 2009-11-17
> **Frak said:**
> 

Three points I just have to mention:
1. It was commited by a 3rd party studio. You can say that falls under Microsoft's umbrella all day, but at the end of the day, it was still the 3rd party studio.

I already pointed out the 3rd party about 36 posts back. 
And MS admits at least partial responsibility. 

> **Frak said:**
> 
2. There is a lot, LOT of open source code out there, GPL or otherwise, and it's hard to decipher code that's canonical compared to code that's original. Compare that to the mass amount of code out there, there's no way to check it all. You can come close, but you can't do it all.

Hence the irony in MS's many law suites over patent infringement 

> **Frak said:**
> 
3. Respect Microsoft for how they handled the situation:

Respect MS for complying with legal obligations. OK.

> **Frak said:**
> 
 ... if you want to bash them on that, go ahead. I guess finding ammunition these days is hard enough, you have to go after a company just doing their job.
They screwed up in this case, and people comment on it. It's what happens on forums. Read the first 12 posts of this thread and tell me who's bashing who.

---

### Post by zekopeko on 2009-11-17
> **starcannon said:**
> This is correct.

I might say; "That car is red", but the car has some black parts, some chrome parts, some white parts, all visible. When people speak of their opinion of MS, they refer to the company/corporate entity, not the individual pieces of the corporation, this is the common context when people speak of companies. I think zekopeko knows this, and I think the mincing of words to the point of absurdum was meant as a subtle(or not so) attempt at trolling.

Well then people are wrong IMO. As I have pointed out already MS is a transnational corporation that is made up of autonomous divisions. That means that perhaps the Management division doesn't like Linux but the Developer division loves us. MS isn't a monolithic entity. It has various interest groups with diverging visions of the future of MS.
Perhaps it would be smart to nurture the relationship with the parts that love or are at least fair in dealings with the FLOSS projects.

---

### Post by phrostbyte on 2009-11-18
Anyone know if they released the code for this yet?

---

