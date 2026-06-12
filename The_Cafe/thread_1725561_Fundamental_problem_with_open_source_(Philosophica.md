---
title: "Fundamental problem with open source? (Philosophical)"
date: 2011-04-09
forum: The Cafe
---

### Post by Learning Linux 2011 on 2011-04-09
I was reading a post earlier that said there were essentially no medical records programs for Linux.

I got to thinking maybe that is a fundamental problem with open source.   What if you *have to* keep the source code secret?  What if the information deals with something sensitive like medical records?  

Is there a solution?

Is there a way to maintain strict control of a program and profit from it using Linux?

---

### Post by wojox on 2011-04-09
You can use all the open source tools to create programs and such and distribute them as proprietary.

Look at Red Hat.

---

### Post by SeijiSensei on 2011-04-09
Medical records systems are largely proprietary with closed-source software. That doesn't mean there aren't open-sourced medical records solutions like [VistA]("http://en.wikipedia.org/wiki/VistA"), but most places like hospitals want to be dealing with the GE's of the world who provide the hardware like MRI's as well as the software to manage them.

I'm just putting the finishing touches on a PHP-based system for one of my clients to enable their patients to make appointments over the Internet.  You could read the entire source code of the application, but unless you have the encryption key, you wouldn't be able to read the AES256-encrypted patient records I create.

---

### Post by s1baker on 2011-04-09
Source code is the non-compiled executable for a program, the part that a human can read. The data that an executable writes is separate from the executable.
 You can store the data that a programs writes in an encrypted folder, on another HD or SD card or CD, etc.

---

### Post by Locke_99GS on 2011-04-09
> **Learning Linux 2011 said:**
> I was reading a post earlier that said there were essentially no medical records programs for Linux.
 

There's plenty of things that don't exist on Linux. Nobody has taken the time to create them yet.

> I got to thinking maybe that is a fundamental problem with open source.

That nobody has made medical record-keeping software via an open source coding process is a fundamental flaw? I don't quite follow.

> What if you *have to* keep the source code secret?

If the source code is secret, then is not open source.

> What if the information deals with something sensitive like medical records?

I'd reckon you better encrypt the sensitive information then. But, what does that have to do with open source record-keeping software?  

> 
Is there a solution?


I still don't quite follow what the problem is that requires a solution - unless you want a solution to the lack of open source medical record-keeping software? Here: [http://cplusplus.com](http://cplusplus.com) Get to it then.

> Is there a way to maintain strict control of a program and profit from it using Linux?

Absolutely - happens all the time. Linux and Open-source don't mean things don't cost money - it's a freedom thing. I pay money for commercial products that are ran on opensource firmwares and softwares all the time, actually, you probably do to.

---

### Post by Learning Linux 2011 on 2011-04-09
> **SeijiSensei said:**
> Medical records systems are largely proprietary with closed-source software. That doesn't mean there aren't open-sourced medical records solutions like [VistA]("http://en.wikipedia.org/wiki/VistA"), but most places like hospitals want to be dealing with the GE's of the world who provide the hardware like MRI's as well as the software to manage them.

I'm just putting the finishing touches on a PHP-based system for one of my clients to enable their patients to make appointments over the Internet.  You could read the entire source code of the application, but unless you have the encryption key, you wouldn't be able to read the AES256-encrypted patient records I create.

This is just a philosophical discussion, but can I ask how you are profiting from it?  
Can/will you sell the program itself?  Being open source, what is to prevent people from copying it?  If they have access to the source code, they could just compile it themselves and it seems to me that you wouldn't have much say in that. Are you copyrighting it?
If so, may I ask (again philosophically) how you would defend your copyright, or do you have any interest in enforcing it?

You might make money by providing installation and tech support, but once they figured it out, it seems to me you would be out of the picture.  Then they could even sell the program to others, and you would have no say in that because it is open source.

I guess what I am really getting at is, doesn't this hinder the adoption of open source?

---

### Post by Learning Linux 2011 on 2011-04-09
[]("http://ubuntuforums.org/member.php?u=543645")By the way, I don't JUST mean medical records software, that is an example.

---

### Post by Learning Linux 2011 on 2011-04-09
I guess part of what I am talking about is that I have been involved in computers for a long time.  I loved Windows 95 when it came out, but (maybe it is just me) it seems like Windows has been going down hill ever since.  I got to thinking maybe I liked Windows 95 because it was new.  I was using DOS and Windows 3.1(1) before that, and I tried OS/2 as well.  
Windows 98 was ok, although it seemed to have alot of extra flashy things.  Windows ME was a disaster. Windows 2000 was a great *operating system*, but "broke" so many pieces of software, it was almost unusable by the average person, and corporations didn't (or couldn't) pay for all the hassles.
Windows XP was put out about a year and a half (I think a record back then) to "fix" all of the problems with Windows 2000's compatibility.  But then of course, Windows XP developed all of the notorious problems like viruses, malware, etc.  So then MS comes out with Vista (Windows 6), which just reintroduced all the problems that Windows 2000 had with hardware and software not working, although it did seem to help somewhat with the security problem.  Then just like Windows XP, they introduced Windows 7 (which is actually Windows 6.1) to help with the compatibility problems, but essentially "stripped" Vista of many things and introduced other problems.

I've been experimenting with Linux, and I was happy, but then I read that post about the medical records software and got disheartened that maybe I (and the rest of the world) couldn't get away from Windows after all.  I guess I am looking for a little hope.

---

### Post by SeijiSensei on 2011-04-09
> **Learning Linux 2011 said:**
> This is just a philosophical discussion, but can I ask how you are profiting from it?  
Can/will you sell the program itself?  Being open source, what is to prevent people from copying it?  If they have access to the source code, they could just compile it themselves and it seems to me that you wouldn't have much say in that. Are you copyrighting it?
If so, may I ask (again philosophically) how you would defend your copyright, or do you have any interest in enforcing it?

You need to understand a lot more about how this works.  What I wrote is a "[work-for-hire]("http://en.wikipedia.org/wiki/Work_for_hire")."  I don't own the copyright in this product; the client who contracted me to write it owns it.  This is a common contractual situation in many similar areas.  Take movies.  Only the producer(s) own the copyright to a film.  Everyone else has a "work-for-hire" relationship unless they manage to get the producers to agree to a very unusual contract.  That's why a screenwriter can't sue for a bigger share of the profits on a hit film.  She gave away her rights in the script when she contracted with the producer.

As to how I make money, I was paid a fee for writing this software.  I also have a long-term support contract with this client that pays me a monthly fee.  If they want to extend or change the software, I get paid a fee for the time I spend making the modifications.  

Does my client have an interest in profiting off my work?  No, not really.  They run a community health center.  They have an IT staff, but those folks are not knowledgeable in the areas I work in.  It's also a lot cheaper to have me as a contractor than to hire a full-time staff person with benefits and overheads.  It's possible that they could shop this application around to other health centers, though I doubt that will happen.  If they licensed it to another center, they wouldn't owe me anything.  On the other hand, that other health center may well decide to hire me to maintain the software, and possibly to make modifications to it that fit its local requirements.  If the work were GPL-licensed, we'd have to give back the modifications, but as it stands now the work doesn't fall under any specific license since it isn't being redistributed.

> I guess what I am really getting at is, doesn't this hinder the adoption of open source?

RedHat is about to surpass a billion dollars in annual revenues earned by writing, maintaining and redistributing open-source software, much of it under the GPL. Does that answer your question?

If you want to study a good example of an open-source application that has licensed users who pay for it, look no further than the [vBulletin]("http://www.vbulletin.com/") software that runs this forum.

---

### Post by RedRat on 2011-04-09
Philosophically I don't see any difference between writing a medical program for Linux or for Windows, the issues will be the same. You can write the code and compile it, making a bin file. You would install it on the appropriate Linux platform, e.g., Red Hat. You may have to include some dependencies just like in a Windows program.

As to copying the program, the bin file, yes you could do that. Programs can be pirated in Windows, Apple, and Linux. Even the bin or executables in Windows can be dis-assembled and the code figured out. That goes on. 

You have touched on a problem of open source software, code written by basement code jockeys versus those working for open source software companies. Many Linux programs are written by volunteers, programs to solve an immediate problem. The coder is happy with it and releases it to the world. However, some do not find that it does everything they want and the original coder doesn't feel like expanding his program, he may give out the original code and tell those who complain "here's the code, you add to it or debug it, I'm finished with it". Sometimes this dead ends a program.

You do have software companies that hire programmers and they write and maintain the programs they create, they debug them, extend them. But they do it for money, they charge for them. Open Source does not mean free programs. 

If you want to use a Linux OS as your base and write programs for it, go for it. Write a good one and you could charge for it. Linux does provide added security for your programs and that would be a reason to use it as a base.

---

### Post by qyot27 on 2011-04-09
> **Learning Linux 2011 said:**
> You might make money by providing installation and tech support, but once they figured it out, it seems to me you would be out of the picture.  Then they could even sell the program to others, and you would have no say in that because it is open source.
This touches on a couple of core philosophical differences between open source and proprietary software.

On the one hand, while it is fully possible for anybody to download and compile a program, how many users actually do compile their own stuff?  Let's face it, an overwhelming number of users are not interested in doing that.  This means they have a couple options: pay for the convenience of having someone else compile it for you, or find someone who does it for free.  Particular market pressures in relation to open source software often do act to drive software prices down to [effectively] zero.  

But there are situations where mere convenience wins out - as an example, one could even abstract this further, and claim that sometimes it specifically **is** provided support that makes a purchase likely.  Such as the case when dealing with the open source and freely available Wine, vs. its commercialized versions like CrossOver: while it's certainly my opinion that CrossOver is a waste of money, that hasn't stopped people from buying it either because they're so used to paying for software, or because they don't like using the command line, or because they want the assurance that CrossOver is marketed to provide for the specific programs they want to run.

The other point is that, also noting the aforementioned work-for-hire methodology often employed, the real drive behind open source really isn't money.  By that I mean that those releasing their software as open source are often doing it for multiple non-monetary reasons: altruism, a sense of contributing to a community they respect, educational purposes, the sheer love of the freedom involved, the issue of making a piece of software potentially sustainable into the future...the list goes on.

In essence, proprietary software is one person/company standing alone in their endeavor, open source is (or at least, has the strong *potential* to be) an entire community or group standing united in that same endeavor.  There is strength in numbers, even though that doesn't guarantee that strength will be entirely well organized.  Open source is nebulous like that: some areas are extremely efficient and entrenched (the actual underlying Linux kernel and GNU tools, for instance), and there are others where the offerings are not really treaded yet (the prosumer video editing segment is one).  But the point is that those areas are likely better today than they were 10 years ago, and in another 10 years they'll be better than they are today, if history is any indication.

> I guess what I am really getting at is, doesn't this hinder the adoption of open source?
Certainly hasn't hindered Mozilla (Firefox's success has led to pretty respectable gains, after all) or Apple (Darwin, the core operating system OSX is built from, is [open source](http://opensource.apple.com/release/mac-os-x-1067/)).

---

### Post by SeijiSensei on 2011-04-09
> **RedRat said:**
> Philosophically I don't see any difference between writing a medical program for Linux or for Windows, the issues will be the same. You can write the code and compile it, making a bin file.

If you're just distributing the binaries without the accompanying source code, it's not an open-source program.  Clearly closed-source binaries for Linux are no different than closed-source binaries for Windows or any other platform.  That's not really the issue here.

> You do have software companies that hire programmers and they write and maintain the programs they create, they debug them, extend them. But they do it for money, they charge for them. Open Source does not mean free programs.

No, but it's harder to enforce copyrights in programs that are open-sourced.  This has been a growing issue as Linux becomes embedded in more and more appliances, the [TiVO]("http://en.wikipedia.org/wiki/Tivoization") case being the most famous.  Version 3 of the General Public License is designed to cover cases like this, but it hasn't been adopted by many major projects covered by GPL 2, including the [Linux kernel]("http://www.zdnet.com/news/torvalds-no-gpl-3-for-linux/146510") itself.  Collectively-written software like the kernel has special problems since, even if Linus wanted to convert the licensing from GPLv2 to GPLv3, he'd have to get the agreement of all the people who authored any of the code in the kernel.  That's essentially an impossible task at this point.

> **qyot27 said:**
> Certainly hasn't hindered Mozilla (Firefox's success has led to pretty respectable gains, after all)

[Questions]("http://www.businessweek.com/technology/content/mar2009/tc20090311_813488.htm") remain about how the Mozilla Foundation will cope when its healthy [subsidy]("http://news.cnet.com/8301-1023_3-10028096-93.html") from Google comes to an end this year.  (In 2007, income from the Google deal constituted over 88% of the Foundation's revenues of $75 million.)

---

### Post by d3v1150m471c on 2011-04-10
on the contrary, open source has the potential to become more secure than much of the proprietary because the community can access it and patch it. if the concern is accessing records that don't belong to someone, and encrypted file is still an encrypted file. if the algorithm is written properly, it being open won't make a difference.

---

### Post by Learning Linux 2011 on 2011-04-10
> **SeijiSensei said:**
> You need to understand a lot more about how this works.  What I wrote is a "[work-for-hire]("http://en.wikipedia.org/wiki/Work_for_hire")."  I don't own the copyright in this product; the client who contracted me to write it owns it.  This is a common contractual situation in many similar areas.  Take movies.  Only the producer(s) own the copyright to a film.  Everyone else has a "work-for-hire" relationship unless they manage to get the producers to agree to a very unusual contract.  That's why a screenwriter can't sue for a bigger share of the profits on a hit film.  She gave away her rights in the script when she contracted with the producer.

As to how I make money, I was paid a fee for writing this software.  I also have a long-term support contract with this client that pays me a monthly fee.  If they want to extend or change the software, I get paid a fee for the time I spend making the modifications.  

Does my client have an interest in profiting off my work?  No, not really.  They run a community health center.  They have an IT staff, but those folks are not knowledgeable in the areas I work in.  It's also a lot cheaper to have me as a contractor than to hire a full-time staff person with benefits and overheads.  It's possible that they could shop this application around to other health centers, though I doubt that will happen.  If they licensed it to another center, they wouldn't owe me anything.  On the other hand, that other health center may well decide to hire me to maintain the software, and possibly to make modifications to it that fit its local requirements.  If the work were GPL-licensed, we'd have to give back the modifications, but as it stands now the work doesn't fall under any specific license since it isn't being redistributed.



RedHat is about to surpass a billion dollars in annual revenues earned by writing, maintaining and redistributing open-source software, much of it under the GPL. Does that answer your question?

If you want to study a good example of an open-source application that has licensed users who pay for it, look no further than the [vBulletin]("http://www.vbulletin.com/") software that runs this forum.

Oh, ok, so you are a paid consultant in this case.  But what if you wrote the software without being hired?  You just wrote the software because you saw a need and then tried to distribute it yourself?  Suppose you sold it to a clinic and they paid you and maybe even had a year long support contract, but then after that they really liked the software so they sold it to a bunch of other clinics nearby.  What would prevent them from doing that?  How could you maintain control of the software if it was open source?
If you were a Windows or Mac developer, you could sue the clinic, but with Linux it is my understanding that you could not sue the clinic, since it is open source software.

If I copy a movie and then redistribute it, I could face criminal prosecution.  If I copy and redistribute (for profit) open source software, I doubt I would or could be punished.
If I copied and redistributed Windows software for profit, I could be prosecuted.


I also don't understand the Red Hat reference.  I used Red Hat many years ago when it was totally free (although I bought it in a box for simplicity).  Back then it was freely distributable, they just charged for support.  I'm not sure what their business model is now, but couldn't I just redistribute that old source code, or even the new source code since it is based on previous source code?  And then charge for support, effectively diminishing their support-related income?  

And then I guess that bring up another point that I was/am trying to get at: isn't Red Hat taking advantage of developers?  If I write a piece of software, and I want to profit from it (and copyright it?), wouldn't it seem unfair that Red Hat would/could include my software in their release?  Or even if I just chose to give away my software, it doesn't seem right that Red Hat can profit from that.

---

### Post by Learning Linux 2011 on 2011-04-10
> **RedRat said:**
> 

As to copying the program, the bin file, yes you could do that. Programs can be pirated in Windows, Apple, and Linux. 


Maybe that is part of my question, can you *pirate* Linux programs?  Being that Linux is free and open source?


> 
If you want to use a Linux OS as your base and write programs for it, go  for it. Write a good one and you could charge for it. Linux does  provide added security for your programs and that would be a reason to  use it as a base.


But how could I maintain control of it?

And what do you mean by "security", do you mean it as in little or no viruses?

---

### Post by Learning Linux 2011 on 2011-04-10
> **SeijiSensei said:**
> If you're just distributing the binaries without the accompanying source code, it's not an open-source program.  Clearly closed-source binaries for Linux are no different than closed-source binaries for Windows or any other platform.  

Hmm, maybe that is something.

If you distribute source code, is it more-or-less automatically open source?  Can you copyright that code? (which it seems to me would make it more-or-less *not* open source, since it is copyrighted)

If you distribute an executable without source code, is it more-or-less automatically not open source, even though it is released for Linux?

---

### Post by DrSeemann on 2011-04-10
offtopic: If you like so much philosophy you should start by reading, investigating, thinking...
I'm on ubuntu since 25 of March 2011, and I spent tons of hours reading about GPL, GNU Copyleft, forums, blogs, guides, etc.
I'm sorry if it seems rough words but it's hard for me to understand why you come to find answer on forums, when you can do some research by yourself and then share your opinion.
I really enjoyed reading some comments where there's explained "how to" make a profit from free software. And I'm pretty much going for it, doing some "real technician" service.

ontopic: You are trying to say that i.e if you make a free "Database" soft, it will be possible for people to access the Database files just because its a free software? :popcorn:

---

### Post by Learning Linux 2011 on 2011-04-10
So if a programmer wanted to write a program, sell it, and maintain control of it, the best solution would be to not distribute the source code and maybe require some kind of registration and/or unlocking mechanism?

Being Linux, that program would not automatically be open source/free/in the public domain?

---

### Post by Learning Linux 2011 on 2011-04-10
> **DrSeemann said:**
> offtopic: If you like so much philosophy you should start by reading, investigating, thinking...
I'm on ubuntu since 25 of March 2011, and I spent tons of hours reading about GPL, GNU Copyleft, forums, blogs, guides, etc.
I'm sorry if it seems rough words but it's hard for me to understand why you come to find answer on forums, when you can do some research by yourself and then share your opinion.
I really enjoyed reading some comments where there's explained "how to" make a profit from free software. And I'm pretty much going for it, doing some "real technician" service.

ontopic: You are trying to say that i.e if you make a free "Database" soft, it will be possible for people to access the Database files just because its a free software? :popcorn:

First of all, Dr. Semen is it?  Really?
Second you aren't a native English speaker, are you?
Third, I have read the GPL, etc. and I didn't get much out of it.  That's why I ask here.
Fourth, the point of forums is not for me to come here and just voice my opinion, it is to have a meaningful conversation with (reasonably) intelligent people and get their views.
Fifth, no that's not what I am saying.

---

### Post by tweaktolive on 2011-04-10
you should also look at Qt 
[http://qt.nokia.com/products/](http://qt.nokia.com/products/)

---

### Post by SeijiSensei on 2011-04-10
I don't think we can cover the entire range of "free software" philosophical issues in a forum thread.  Maybe you should start with Eric S. Raymond's [The Cathedral and the Bazaar]("http://www.catb.org/~esr/writings/homesteading/"), followed by visits to the [Open Software Initiative]("http://www.opensource.org/") and the [Free Software Foundation]("http://www.fsf.org/").  "Open-source" incorporates a wide range of views and some intense debates over the meaning of "open."

Let me try and answer your question about "control" of an open-source work since I think that's what puzzles you the most.  All software can be, and usually is, copyrighted, which grants its author exclusive control over how the software can be used, distributed, etc.  How the author chooses to exert that control is what matters.

The most restrictive license is the GPL, and it is based firmly within copyright law.  (It wouldn't work without copyright law.)  I, as the author of a GPL'd work, grant you a license to use, copy and even redistribute my work under the proviso that you also distribute, or make available in some specific ways, the source code of my work.  Ubuntu distributes the compiled binaries of the software it bundles, and it also makes source .debs available for each package as well.  Along with these requirements, the GPL includes an additional, important proviso:  if you make any changes to a GPL'd work, you must make those changes available to the public with source code as well.

Just because a program is open-source doesn't mean someone can't be sued for violating the license under which the program is distributed. There have been suits over both the restrictions I just mentioned, particularly the additional proviso concerning alterations to the original code.  The [FSF sued Cisco]("http://www.zdnet.co.uk/news/security/2010/07/19/windows-systems-at-risk-from-stuxnet-shortcut-malware-40089575/") a couple years back for using GPL software in its Linksys router line without providing the source code.  It is the beauty of the GPL that it enables the authors of software to control the fate of their creations while giving them away at the same time.  Licenses like the BSD and MIT licenses essentially put the source code into the public domain for anyone to do with as they wish.  Microsoft's incorporation of the BSD TCP/IP networking stack in Windows is in conformance with the BSD license.  If it had been licensed under the GPL, Microsoft would have had to reveal any modifications it made to that code.

"Control" in these situations has little to do with earning money from licensing fees, though.  One typical method by which people earn a living from open source is by working as a developer at some place like IBM, Canonical, Novell or RedHat where they are paid to participate in open source projects. A lot of kernel development happens this way.  The other method is charging for support.  That's how RedHat makes its money.

The "single-coder-in-a-basement" model applies to some open-source programs, but not projects like the Linux kernel, Firefox, Mono, or OpenOffice.  These are large, collaborative projects, typically with corporate sponsorship and often some salaried staff.

---

### Post by earthpigg on 2011-04-10
> **Learning Linux 2011 said:**
> Maybe that is part of my question, can you *pirate* Linux programs?  Being that Linux is free and open source?

But how could I maintain control of it?

And what do you mean by "security", do you mean it as in little or no viruses?

yes, you can pirate open source software. if you redistribute the software without adhering to the original license, you are violating copyright - eg, pirating. 

example: if i sell someone an ubuntu CD, and make them sign a contract wherein they promise not to make additional copies of it. that is piracy.

real life example: when Apple put the GNU Go game in their App Store, Apple committed piracy because their ToS violated the GPL. (The ToS says that users agree not to make additional copies of software obtained through the App Store.)


next q: how do you maintain control of it? trademark is one. Red Hat and Ubuntu are both names that, by themselves, have value.

You can redistribute Red Hat, for example, but every iota of Red Hat branding must be removed from the software. Look at CentOS. Similarly, Ubuntu derivatives cannot have the Ubuntu logo or call themselves _buntu.

> And what do you mean by "security", do you mean it as in little or no viruses?

no, as in: the company using the software down the chain can audit the source code themselves to make sure that their unique use of the software will not expose them to vulnerability. 

Access to source code is something Microsoft offers to nations (Russia, etc) and mega-corporations (Toyota, etc), but not to mere mortals (your local bank).

security also means that the methods and practices to address security vulnerabilities are visible to the user, and encourage *positive* participation by that 0.5% of programmers that are geniuses. 

in the proprietary world, someone finding & publishing a security vulnerability may find an arrest warrant issued for him - this encourages *negative* participation by that 0.5%. many/most geniuses don't care about money, but if you say "f-you" to them and **you do** care about money, then they will come after you there. 

Sony's playstation became **less** secure when they implemented **more** and **newer** and better **security** - because in doing so, they made the mistake of incidentally telling geniuses that they couldn't play with open source on his ps3 any more.

obvious response: "oh yea, sony? you think your corporate suits are smarter than any one of us?"

they responded to Sony's perceived insult by breaking every ounce of DRM on all ps3's across the globe, and sharing it with the world. want to play pirated games on your ps3? you can now, because Sony pissed off a handful of genius nerds.

back on topic: proprietary-centered outfits have to employ an army of security professionals working *independently* of MS's efforts - part of what they do is find vulnerabilities that Lord Ballmer has not seen fit to share the full details on.

in open source world, someone publishing a security vulnerability is instead told 'thank you for pointing this vulnerability out to us, can you please help us fix it?' - *and* they may even become popular, venerated, and respected in that community of programmers. did sony thank the programmers exploring the capabilities of their playstations? does microsoft thank the programmers that find security vulnerabilities? Apple? 

no, across the board. what are the biggest targets for genius programmers? cause -> effect.

that often means that the very same genius teenagers that are bad guys to closed source, are *good* guys to open source (hard to quantify that, because they rarely get identified by name for their bad guy stuff. and, this applies to 'some' not 'all' or even 'most'). open source encourages *positive* participation.

note the two definitions of 'hacker' that exist - evil geniuses in proprietary world, clever fun-loving and quirky programmers in the open source world. this is part of why.

it also means that instead of hiring an army of security professionals, firms reliant on open source can hire a few guys that work *with* the relevant open source projects.



these are broad strokes, and exceptions abound.

---

### Post by Locke_99GS on 2011-04-10
> **Learning Linux 2011 said:**
> If you distribute an executable without source code, is it more-or-less automatically not open source, even though it is released for Linux?

Are you asking whether you can create proprietary software on Linux and for Linux? Yes, you can. 

Distributing software for Linux does not automatically make it free. Flash and Java are two obvious examples of non-free applications that run natively on Linux. 

So are:
Opera web browser.
RAR archiver.
Adobe Acrobat Reader.
NOD32 and TrendMicro antivirus.
Nero cd burning software.
SpiderOak backup/sync utility.
PowerDVD and FluendoDVD DVD player software.
Autodesk Maya 3D graphics
Googe Earth
A slew of games including Doom3, America's Army, and World of Goo.
BitKeeper revision control (Linus used to use this for the kernel)
Dassault DraftSight CAD software
VMware and Parallels VM software.

There are of course many more.

You can use any development method you want when creating software on or for Linux, only be aware of the licenses of the libraries you choose to use, and how you link them.

---

### Post by bodhi.zazen on 2011-04-10
> **Learning Linux 2011 said:**
> I was reading a post earlier that said there were essentially no medical records programs for Linux.

I got to thinking maybe that is a fundamental problem with open source.   What if you *have to* keep the source code secret?  What if the information deals with something sensitive like medical records?  

Is there a solution?

Is there a way to maintain strict control of a program and profit from it using Linux?

I am moving this thread to the café.

The "problem" is that most medical institutions keep going with the "Industry standard" which is large EMR with huge price tags, often in the millions.

Why code an open medical record when you can make millions ?

And whoever informed you there are no "open EMR" is misinformed.

[http://www.oemr.org/](http://www.oemr.org/)

Medical is the same as all other business. We teach our children from grade school through college and grad school to use closed source, Windows or mac, in the public schools.

What is wrong with this picture ?

---

### Post by RedRat on 2011-04-10
[earthpigg]("http://ubuntuforums.org/member.php?u=561472"):
Thanks for your explanation, that is one of the best explanations that I have read. Far clearer than what I wrote.

---

### Post by ugm6hr on 2011-04-10
> **bodhi.zazen said:**
> The "problem" is that most medical institutions keep going with the "Industry standard" which is large EMR with huge price tags, often in the millions.

Why code an open medical record when you can make millions ?

And whoever informed you there are no "open EMR" is misinformed.

[http://www.oemr.org/](http://www.oemr.org/)

In fact, lots of hospitals & clinics have a custom-written solution. Why would they share that with their competitors once they'd paid for it? This has nothing to do with security of data.

And yes - there are *lots* of OSS EMR applications - just most are written in the developing world, for largely altruistic reasons. Nevertheless, another OSS example from the "developed" world: [http://www.oscarcanada.org/](http://www.oscarcanada.org/)

Remember, use of OSS in this kind of environment may not necessarily make it cheaper. The technical support requirements are massive - and critical - hence, it is "safer" to get support from the person who "wrote" it.

---

### Post by Chronon on 2011-04-10
> **Learning Linux 2011 said:**
> 
Being Linux, that program would not automatically be open source/free/in the public domain?

A programmer owns the copyright of his (or her) work by default.  They are free to license it under any terms they like.  If you didn't know there are many proprietary software packages for Linux (Mathematica, LabView and MatLab to name a few that I have used).

---

### Post by Artemis3 on 2011-04-10
> **Learning Linux 2011 said:**
> I was reading a post earlier that said there were essentially no medical records programs for Linux.

I got to thinking maybe that is a fundamental problem with open source.   What if you *have to* keep the source code secret?  What if the information deals with something sensitive like medical records?  

Is there a solution?

Is there a way to maintain strict control of a program and profit from it using Linux?

Wait, what has the data collected anything to do with the source of the programs processing it? Nobody is releasing their data to the public only because they use open solutions. You cannot mix the source of a program with the data generated/processed by it.

"Using linux" (an OS kernel) also has nothing to do with the applications running with it.

As for profits, they are made by developers producing the required applications, maintaining them or modifying them to suit your special purposes; or just give you support. The Freedom of Free software is that you are not tied to them, you can replace them at any time or even fix things yourself. You don't pay for licenses, you pay for actual work being done.

Maybe you should check things like this: [http://wiki.debian.org/DebianMed](http://wiki.debian.org/DebianMed)

---

### Post by Artemis3 on 2011-04-10
> **Learning Linux 2011 said:**
> Suppose you sold it to a clinic and they paid you and maybe even had a year long support contract, but then after that they really liked the software so they sold it to a bunch of other clinics nearby.  What would prevent them from doing that? Nothing prevents them from selling it, but nothing prevents me from giving it away. You can think of it this way, the first customer finances almost the entire cost of the project, but then the price will tend to go zero. Yes you can develop an excellent solution and sell it to a customer under these conditions. Its similar to institutional funding. "The conditions" are part of the price, and its also part of its strength. Unlike closed solution, not only you are not tied to the author, but a worldwide community can and will help you make it better, if simply because they can benefit from it themselves. Medicine is perfect, because most countries do have public health care; so there is an academic and humanitarian drive.

---

### Post by Artemis3 on 2011-04-10
> **Learning Linux 2011 said:**
> Being Linux, that program would not automatically be open source/free/in the public domain?

Linux is a kernel released under the terms of the GPL by his author. Any contribution made to it remains under this license, hence it is NOT Public Domain. The license explicitly says you have to follow the rules of Free Software (the 4 freedoms) else you can't use it at all. In short it is copyrighted and those are the terms of use.

Because Linux is only a kernel, you are not touching it when you develop an application which runs with it; that application can use any license you see fit, including closed/proprietary.

---

### Post by DrSeemann on 2011-04-10
> **Learning Linux 2011 said:**
> First of all, **Dr. Semen** is it?  Really?
Second you aren't a native English speaker, are you?
Third, I have read the GPL, etc. and **I didn't get much out of it**.  That's why I ask here.
Fourth, the point of forums is not for me to come here and just voice my opinion, it is to have a **meaningful conversation with (reasonably) intelligent** people and get their views.
Fifth, no that's not what I am saying.
Start by going to wikipedia and "getting some of" the philosophy concept.

---

### Post by Thewhistlingwind on 2011-04-10
Well if you HAVE to, then you have to. You can distribute proprietary applications using open source tools. [As an example ]("http://clisp.org/summary.html")

I don't see how you would ever HAVE to though, at least by nature of as a design specification. Any sensitive information can be implemented as an encrypted file or some other (theoretically) inaccessible data container. Theres no need to have sensitive information in the source. Though if you have algorithms or some such you want to keep under wraps, I guess you could just compile the parts you want to keep proprietary (And then implement them as an import or something.), but it doesn't matter. The bottom line is, if you put out bytecode or source, if theres juicy secrets in them, they can be extracted. Even if it does require extensive study of the binaries. :popcorn:

---

### Post by visitron on 2011-04-11
There are many fine applications for Linux that are proprietary and not open source;


Google Chrome
Opera
Adobe Systems Acrobat Reader
Fluendo DVD player
Maya
Intel C++ compiler
Mathematica
Maple
Lotus Notes

etc...

There are many more still.

As far as copyright, when you create a work be it music, a movie, book, software etc..
you automatically have a copyright to that work, it doesn't matter if it's free or for sale, closed source or 
open source.

exceptions exist If you created the work under employment for someone then the employer probably will own the copyright, or you are contractor, or sold the copyrights

---

### Post by jmszr on 2011-04-11
Learning Linux 2011,

Here is a link to a research paper concerning "Open Source, Open Standards, and Health Care Information Systems": [http://www.jmir.org/2011/1/e24/](http://www.jmir.org/2011/1/e24/) . 

While their research concentrates on health care IT, their findings may be generally applicable.

For the short version: [http://www.sciencedaily.com/releases/2011/03/110308124756.htm](http://www.sciencedaily.com/releases/2011/03/110308124756.htm) .

---

