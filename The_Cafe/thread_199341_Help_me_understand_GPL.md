---
title: "Help me understand GPL"
date: 2006-06-18
forum: The Cafe
---

### Post by forrestcupp on 2006-06-18
I'm really not trying to be a troll here, but I really need help understanding something about GNU GPL.  I have just recently, within a month, switched totally to linux and ubuntu.  I've dabbled before, but now I've made the switch.  I really love it, but I am also trying to understand all the different philosophies and protocols compared to windows based systems.  I understand the whole deal about software being "free as in speech, not free as in beer."  But the one thing I don't get is this:  If I happen to stumble across a certain little known software that was programmed by a small group of people, even though I have nothing to do with any aspect of that software and don't know the people involved, if it is GPL'ed, I am allowed to take it, make it well known, and sell it.  Then the unknown people don't get anything or really even any credit, and someone with nothing to do with it does.

Now, where is the logic in this?  Please help me understand.  I know that with bigger projects, one can just go somewhere else and get it free, but there are certain situations, like what I mentioned above, that I really don't see how this is fair.  If you don't believe this is allowed, you should reread the license.  This is how companies like Redhat and Novell can take a bunch of software packages that they didn't make, put them together, and sell it at Best Buy now for the same price as the latest Windows upgrade.

I'm really sorry about this post.  I really love Linux, but I just need help with this one thing that gets to me.  I also know that this doesn't really happen often as I mentioned above, but it's just the idea that it could "freely" happen.

---

### Post by G Morgan on 2006-06-18
Essentially if you distribute GPL'd code you'd have to release source under the GPL. Essentially if you took project A, improved it then started selling it the first person who bought it could request the source then distribute it for free himself ensuring that no GPL'd code could be locked in a proprietry product.

The best places to look for info are the FSF website and the Opensource definition.

The key difference in the GPL is a copyleft clause which means that GPL'd code stays GPL'd. Only the copyright holder could release it under a new license though he wouldn't be able to retract the current code already in circulation.

---

### Post by DoctorMO on 2006-06-18
Indeed!

If the business that sells the software makes improvements they must ensure that the source code is made available to the community. if they don't then they no longer have a liecence to redistrobute the original work.

the small team of developers never loose the right to continue developing.

any one else who buys the software from the business asuming that there are no tricks with media copyrights and brand trade marks and also sell the software under the same terms, because the business is not allowed to change the terms for which the software is granted.

It would be like me buying a copy of windows and then legaly copying disks and selling it on. (if windows was gpl (gawf))

---

### Post by kanem on 2006-06-18
Yes, you could take the code, advertise it, sell it and become rich and famous, while the original coders remain poor and anonymous. But that would never happen because:

1) the code is already available to everyone for free. Why should they buy it? If you put in a bunch of advertising to popularize it, that would just be your loss, because it will still get out that it's free and that someone else wrote it. If they do buy it from you, it's probably because of extras that you could give them, like official support, in which case that's what they're paying for, not the code.

2) like G Morgan said, you would have to release it under the GPL, so even if you made some amazing improvements to the code that made it worth buying, the first person who buys your modified version can (and probably would) make the code available on the net for anyone to use for free.

So sure, Red Hat can sell programs to people in Best Buy, but I don't think that's how they make their money. That stuff is just a side thing for people who like to buy boxed software. They would tell you themselves where you can download all of their GPL'd software for free. In fact, they have to.

---

### Post by G Morgan on 2006-06-18
Yeah Red Hat makes their money from services which is not precluded by the GPL.

---

### Post by GeneralZod on 2006-06-18
The Free Software mentality is only confusing if you think the primary motivation of its adherents is to make money and get famous by writing code.  Instead, a desire to simply write good software that anyone can use in any way they wish is often the overriding factor in starting a project.  That, plus a little bit of ego - someone taking someone else's project and claiming it as entirely their own work is *strongly* frowned upon (and futile anyway, as they are bound to be exposed in the end), so Free Software writers can usually be assured that they will get all the precious, precious kudos that is their due :)

---

### Post by forrestcupp on 2006-06-18
You guys make a good point.  I guess I really never thought about the fact that anyone who buys the software has the right to make available for free, which would definitely end up happening.  So even if no one has ever heard of the original programmers, it would still end up being available for free.  I still don't totally like it, but that thought helps me.  The problem with commercial distros is that a lot of times they offer a free, downloadable version, but it is crippled in more ways than just their support offerings.  For instance, I tried Mandrake (before it was Mandriva) before I stumbled upon Ubuntu.  I hated Mandrake because the free version kept trying to get me to buy the commercial version of it.  Also, I think they made you pay to download from their repositories.  Thank God for Ubuntu.

---

### Post by Lord Illidan on 2006-06-18
If you take Red Hat for example, you are legally allowed to take its source code and release another distro from it. Tao Live and CENT OS are two examples of Red Hat Enterprise Linux Clones.

Red Hat gains money from support, not from selling..

IMHO, the least ethical and money grabbers in the Linux market are Mandriva and Linspire... Linspire is going to release Freespire, so that might change. But Mandriva sucks. Club status, and the like, it would have been another Windows.

Open Suse is also a good free version of Suse. There is almost no point for commercial distributors to offer a pared down version of their distro, as people have lots of choice between other distros.

---

### Post by Iandefor on 2006-06-18
[quote=forrestcupp]So even if no one has ever heard of the original programmers, it would still end up being available for free.[/quote] Thing is, the original developers would undoubtedly pipe up. If someone took BUMPS and started selling it without attributing it to me, no way in hell would I take it lying down. I imagine it would be the same for a LOT of real developers, too.

Anywho, the money in OSS is in service and support, not in the product.

---

### Post by DoctorMO on 2006-06-18
That is where the money is because that is were the value is, software on it's own is not good enough because no one can write software that everyone can use and which contains no bugs. it's just too complicated. infact in the uk it's a legal grey area because the goods of sales act should cripple comercial software players for not providing a product which meet expected standards.

So support is where the real value lies, getting all this free code junk working on your computer is where it's at, you can earn far more money turning the tap on and off for someone than you can by selling them the tap manual.

---

### Post by forrestcupp on 2006-06-19
[QUOTE=Iandefor]
Anywho, the money in OSS is in service and support, not in the product.[/QUOTE]


Everyone keeps saying this, but that wasn't the original point.  While this may be true, it doesn't change the fact that GPL does say that anyone is free to take a GPL'ed piece of software and sell it.  I don't care if it doesn't happen, it's just the fact that it is allowed that bothers me.  If the programmers have an ethical standard that they aren't after fame or fortune, then it's not fair for someone else to be free to take that good intentioned piece of software and try to make a profit off of it, even if they would fail in the end.

Anyway, the fact that commercial distros are actually selling their support is ridiculous anyway.  I have never had a problem that is solvable, that I haven't been able to solve by these free forums.  I don't mind Redhat and all the rest selling their boxed software; there's nothing wrong with that for people who don't want to try to find free alternatives.  What bothers me is that not too many years ago these commercial distros were only around $30 or maybe $40.  They were an inexpensive alternative to Windows.  Now they sell for the same price as Windows.  That is one reason people don't use Linux.  People see it in the store, and they don't want to pay the same price for something that they "think" is inferior.

---

### Post by simonn on 2006-06-19
> **forrestcupp]Everyone keeps saying this, but that wasn't the original point.  While this may be true, it doesn't change the fact that GPL does say that anyone is free to take a GPL'ed piece of software and sell it.  I don't care if it doesn't happen, it's just the fact that it is allowed that bothers me. 
[/quote]

Developers know this is the case when they release something under the GPL and if they do not know it is nobody's fault that their own. 

> Anyway, the fact that commercial distros are actually selling their support is ridiculous anyway.  I have never had a problem that is solvable, that I haven't been able to solve by these free forums.
 
I would hazzard a guess that you are not losing $1000s an hour when you have a problem. Therefore, you are happy as you are.  

Businesses, however, are never happy with the idea of losing loads of money.

Redhat do not care about consumers. I doubt Ubuntu do much either. We make good guinea pigs and help with hype.

[quote]
I don't mind Redhat and all the rest selling their boxed software said:**
> 

This contradicts your first point. They are making money selling other people's GPLed software.

[quote]What bothers me is that not too many years ago these commercial distros were only around $30 or maybe $40.  They were an inexpensive alternative to Windows.  Now they sell for the same price as Windows.  That is one reason people don't use Linux.  People see it in the store, and they don't want to pay the same price for something that they "think" is inferior.

Then they discover Ubuntu or Fedora etc etc.

---

### Post by imagine on 2006-06-19
The GPL isn't a guide how to become rich and famous. The main concept behind the GPL and every other copyleft licence is that knowledge, ideas, or more specifically software should be free. That means that everybody is allowed to take the software, look at it, modify it, redistribute it, lease it, sell it, etc. The only restriction is that you have to give others also the same rights, so that the software not only *is* free but also *stays* free. That's called copyleft, ie you cannot take free code from somewhere and then put a copyright onto it.

So to answer your question: If you weren't allowed to take other peoples software and charge money for it, then this would be a restriction of your freedom. And the GPL is about giving freedom, not taking it away.


> Anyway, the fact that commercial distros are actually selling their support is ridiculous anyway. I have never had a problem that is solvable, that I haven't been able to solve by these free forums.
That is true for your desktop PC. You can ask friends or other people in mailinglists, webforums and newsgroups. Maybe they help you, maybe not.
But if an important server in a company breaks down you can't go there and hope that somebody helps you. You need a garantuee that you get help, quick help. And for that they have support contracts.
And a big company wouldn't only lose thousands of dollars every hour but millions. For a big bank a breakdown of three or four days so they cannot make any online transactions would be enough for insolvency.

---

### Post by forrestcupp on 2006-06-19
[QUOTE=simonn]


This contradicts your first point. They are making money selling other people's GPLed software.
[/QUOTE]

That didn't really contradict my first point if they are making their money off of their support.  The theoretical circumstances that I am talking about aren't about commercial distros, but rather about someone actually trying to make a profit off of a certain program or application that isn't theirs.  It's true that anyone that releases their software under this license knows this in advance so it's their own fault, but I'm just trying to understand why that point is even in there that someone could be at fault.

You do make a good point that commercial distros might be good for businesses who lose money for downtime.

---

### Post by az on 2006-06-19
[QUOTE=forrestcupp]trying to make a profit off of a certain program or application that isn't theirs.  .[/QUOTE]

It is theirs.  Something released under the GPL belongs to everybody.  The whole point of the GPL is to allow others to build upon your work.  More water floats the boat higher.

Just because someone else uses it doesn't take it away from you - especially in this case where they are obliged to release their improvements to the code.  So if they make it better, you get those changes and everybody is better off.

A basic tenet in programming is to reuse code as much as you can. 

[QUOTE=forrestcupp]
 so it's their own fault, but I'm just trying to understand why that point is even in there that someone could be at fault..[/QUOTE]

That implies that there is a winner and a loser.  In this case, there is a winner and a winner.

Most code written is not distributed.  Most program are written to solve a task and are kept in-house.  Not every project is aimed to be shrink-wrapped and sold at Wal-Mart.  

So, developers can earn their keep without even licencing their code (the licence is between then and you - if they are the only users of the code, no licence required)

Anyway, the business model for free-libre software is for professional services and support.  That can mean writing new code.  In this case, you pay the programmer for her day's work, but nore for ownership of the code.  The code belongs to everyone.

In a lot of cases, developing a free-libre product can eliminate your competition (why pay when you get it for free?) but you still make money from people who find value in paying you to write new code.

Every buck then goes into new code.  When someone spends money, the code gets better.  As opposed to proprietary software that is developed and people pay and pay for the code and it doesn't neccessarily get better because of that.

---

### Post by BWF89 on 2006-06-19
@forrestcupp: Don't worry, I took me like a year to completely understand the GPL, open source, and exactly how companies make money off of it.

---

### Post by forrestcupp on 2006-06-19
Well, help me understand one more thing.  What is the difference between "open-source" and "Free Software?"  Once Mark Shuttleworth said he preferred the term "Free Software."  I know about the Free Software Foundation, and that they are the supporters of GNU GPL, but what is the difference?  I have read the wikipedia article on this, and they didn't really explain the difference very well, only that there is a difference, and that people fight about it.

---

### Post by BWF89 on 2006-06-19
[QUOTE=forrestcupp]Well, help me understand one more thing.  What is the difference between "open-source" and "Free Software?"  Once Mark Shuttleworth said he preferred the term "Free Software."  I know about the Free Software Foundation, and that they are the supporters of GNU GPL, but what is the difference?  I have read the wikipedia article on this, and they didn't really explain the difference very well, only that there is a difference, and that people fight about it.[/QUOTE]
The 2 are about 99% the same thing but example is that the Artistic Licence is consitered to be open source by the open source people but not free software by the free software people because its too vague or something.

---

### Post by az on 2006-06-19
[QUOTE=forrestcupp]Well, help me understand one more thing.  What is the difference between "open-source" and "Free Software?"  Once Mark Shuttleworth said he preferred the term "Free Software."  I know about the Free Software Foundation, and that they are the supporters of GNU GPL, but what is the difference? [/QUOTE]
Good question.

Actually, gnu.org has a terminology page.  A good read.

Open source is just open source.  As opposed to closed source where you only get the binary.  When C code is compiled, you cannot reverse-compile it.  You get a binary file and that's it.  It may be accompanied with headers which describe how to call the functions if it is a shared library, but you still have no idea what it is doing.  Nor can you modify it.

"Free" is a less ambiguous term in other languages.  In english, "free" can mean free-as-in-freedom or free-as-in-no-charge.  In french it would be "libre" and "gratuit", respectively.  That's why I usually say free-libre software, to refer to software freedom.  Most people understand that I am being unambiguous.  Some think I am weird.

A really nice term is FLOSS which is free-libre open source software.  In terms of software licencing, there are only two kinds of software to think about: FLOSS and proprietary software.

Something can be proprietary (somebody else's property) and be free or chage: freeware.  Most spyware is freeware.  As far as I am concerned, just because I don't have to pay for something does not really make it appealing.

Likewise, something open source can be non-free.  You can have the source for something, but not be allowed to redistribute it or even modify it.  Again, this is proprietary open-source software.

FreeBSD is relased under a BSD-style licence which has very few rules.  That makes it more coplicated.  Someone can take a free-libre version of FreeBSD and turn it into something proprietary (Mac OSX).  You cannot do that to GPLed software because that is forbidden:  If something is GPLed, it will always be free.  So, there are different FLOSS licences.

However, there are almost as many proprietary software licences as there are proprietary applications.  Did you read every licence for every application on your windows box?

Depending on whom is speaking the terms "free software" "FLOSS" "open source" "linux software" and "linux" are all often used to mean the same thing.

---

### Post by G Morgan on 2006-06-19
The definition of open source is made more muddy by the fact the OSI definition clearly states that all OSS must allow for derivatives and redistribution. It depends on who you ask but according to the OSI (which all the licenses your likely to see called open source follow) having the code doesn't make something open source.

---

### Post by Iandefor on 2006-06-19
As I understand, Open Source simply means that the source code is accessible. Free Software is software that grants you four basic freedoms:
[LIST=1]
[*]The freedom to run the program, for any purpose.
[*]The freedom to study how the program works, and adapt it to your needs.   Access to the source code is a precondition for this.
[*]The freedom to redistribute copies so you can help your neighbor.
[*]The freedom to improve the program, and release your improvements      to the public, so that the whole community benefits.   Access to the source code is a precondition for this.[/LIST]http://www.gnu.org/philosophy/free-sw.html

---

### Post by Gustav on 2006-06-19
[QUOTE=Iandefor]As I understand, Open Source simply means that the source code is accessible. Free Software is software that grants you four basic freedoms:
[LIST=1]
[*]The freedom to run the program, for any purpose.
[*]The freedom to study how the program works, and adapt it to your needs.   Access to the source code is a precondition for this.
[*]The freedom to redistribute copies so you can help your neighbor.
[*]The freedom to improve the program, and release your improvements      to the public, so that the whole community benefits.   Access to the source code is a precondition for this.[/LIST]http://www.gnu.org/philosophy/free-sw.html[/QUOTE]
As I've understood it this is not true.

Open source programs should follow the open source definition: [http://www.opensource.org/docs/definition.php](http://www.opensource.org/docs/definition.php)
In that it sais lots of things about being able to change things and so on. In fact it's quite similar (but not the same) as free software.

The main difference is in the ideology. Free software promoters think that free software is a more ethical way while open source promoters just think it is a more effective way of developing code. (a little simplified, read this ([http://www.gnu.org/philosophy/free-software-for-freedom.html](http://www.gnu.org/philosophy/free-software-for-freedom.html)) for a better explanation)

I prefer the term free software by the way :)

---

### Post by Iandefor on 2006-06-19
[quote=Gustav]As I've understood it this is not true.

Open source programs should follow the open source definition: [http://www.opensource.org/docs/definition.php]("http://www.opensource.org/docs/definition.php")
In that it sais lots of things about being able to change things and so on. In fact it's quite similar (but not the same) as free software.

The main difference is in the ideology. Free software promoters think that free software is a more ethical way while open source promoters just think it is a more effective way of developing code. (a little simplified, read this ([http://www.gnu.org/philosophy/free-software-for-freedom.html]("http://www.gnu.org/philosophy/free-software-for-freedom.html")) for a better explanation)

I prefer the term free software by the way :)[/quote] Alrighty, that makes more sense. Thanks :).

---

### Post by az on 2006-06-19
[QUOTE=Gustav]As I've understood it this is not true.

Open source programs should follow the open source definition: [http://www.opensource.org/docs/definition.php](http://www.opensource.org/docs/definition.php)
In that it sais lots of things about being able to change things and so on. In fact it's quite similar (but not the same) as free software.

The main difference is in the ideology. Free software promoters think that free software is a more ethical way while open source promoters just think it is a more effective way of developing code. (a little simplified, read this ([http://www.gnu.org/philosophy/free-software-for-freedom.html](http://www.gnu.org/philosophy/free-software-for-freedom.html)) for a better explanation)

I prefer the term free software by the way :)[/QUOTE]

That actually confounds the issue.  Not a lot of people use the term "open source" in the way that the OSI define it.  Some do.  For the sake of clarity, "open source" does not have to imply "free-libre" (which is what the OSI's definition says)
[http://www.gnu.org/philosophy/free-software-for-freedom.html](http://www.gnu.org/philosophy/free-software-for-freedom.html)

The point is that to be clear, you have to differenciate between software that you can and cannot use at your discretion, software for which you can or cannot obtain the source code, software for which you can or cannot modify that source code, and software for which you can or cannot redistribute those changes.

So the term "proprietary" refers to any software where some of the freedoms are denied to you.  So proprietary can be open source (in the sense that you can obtain the full source code - you just cannot modify or redistribute it without certain conditions)

And the term free-libre refers to software that grants you all of the above freedoms.

Ubuntu follows the DSFG (debian free software guidelines) which are guidelines for various software licences.  In a nutshell, if something is GPL-compatible (free-libre, does not take away any of your freedoms) it is DFSG-compliant.  The only exception is that Ubuntu ships with some non-free (because they are binary-only) drivers.  

They are easily removed by removing the linux-restricted-modules packages.

---

### Post by mostwanted on 2006-06-19
I would like to make it clear that it isn't possible to take someone's code, change it and claim it as your own if it is GPL'ed. The copyright still stands and that derivative work you've made is owned by you AS WELL as the original copyright holder and you WILL have to credit him as well.

There recently was some controversy with the Listen music player over this exact term of the GPL, as he used much of the Quod Libet codebase without crediting the authors. He later complied to the terms.

It is the same sharing of the copyright that tells you that you need permission from ALL the programmers who have attributed to the project in order to relicense the code. This is why relicensing community projects with many outside pathces is a very difficult task and also why the GPL is considered a "viral" license compared to the very liberal BSD license which allows you to relicense a project without permission from other copyright holders (you still need to credit them though, Microsoft credits the BSD project in Windows NT and onwards because they used BSD code for their Internet protocol :P).

Hope that cleared up a few things!

---

### Post by forrestcupp on 2006-06-19
[QUOTE=mostwanted]I would like to make it clear that it isn't possible to take someone's code, change it and claim it as your own if it is GPL'ed. The copyright still stands and that derivative work you've made is owned by you AS WELL as the original copyright holder and you WILL have to credit him as well.

There recently was some controversy with the Listen music player over this exact term of the GPL, as he used much of the Quod Libet codebase without crediting the authors. He later complied to the terms.
[/QUOTE]

Well, it makes me feel a little better if that is how things actually work.

Let me ask you all another applicable question.  Should Linux really actually be called GNU/Linux or not?  Linus Torvalds seems to think that isn't necessarily the case.  It seems to me that there is a lot more to Linux than GNU and I don't know if they should take that much credit.  But I'm just learning here, so help me understand this, please.

---

### Post by az on 2006-06-19
[QUOTE=forrestcupp]  Should Linux really actually be called GNU/Linux or not?  .[/QUOTE]

Yes, but not many people go out of their way to do so.  But that is correct.  You can run an OS that is GNU using the Hurd kernel, or a BSD kernel. So then you would be running GNU/Hurd or GNU/FreeBSD.

Unix is an operating system environment.  The complete OS is that environment plus a kernel.  There are other unix operating systems that are not GNU.

[QUOTE=forrestcupp]
Linus Torvalds seems to think that isn't necessarily the case.  It seems to me that there is a lot more to Linux than GNU and I don't know if they should take that much credit.  But I'm just learning here, so help me understand this, please.[/QUOTE]

Just about every application is either built upon or built using the GNU toolchain and the userspace tools.  

Probably what you mean is that to have a complete picture, you should say something like "Ubuntu GNU/Linux", meaning all the ubuntu stuff, which runs on GNU and the linux kernel.  That would be correct to call it that but no one does.

You have to draw the line somewhere!

---

### Post by forrestcupp on 2006-06-19
[QUOTE=azz]Y

Just about every application is either built upon or built using the GNU toolchain and the userspace tools.  

Probably what you mean is that to have a complete picture, you should say something like "Ubuntu GNU/Linux", meaning all the ubuntu stuff, which runs on GNU and the linux kernel.  That would be correct to call it that but no one does.

You have to draw the line somewhere![/QUOTE]

But if I use proprietary drivers and codecs and such, doesn't that mean that it isn't pure GNU/Linux?

btw, azz, your picture makes me feel happier.

---

### Post by Gustav on 2006-06-20
[QUOTE=azz]You can run an OS that is GNU using the Hurd kernel, or a BSD kernel. So then you would be running GNU/Hurd or GNU/FreeBSD.[/QUOTE]
Sorry for being picky, but I have to disagree again. :)

Hurd is a part of the GNU project and therefore an OS with Hurd and GNU should just be called GNU. (Although it is much clearer what is meant with GNU/Hurd so everybody calles it that :))

---

### Post by Gustav on 2006-06-20
[QUOTE=forrestcupp]But if I use proprietary drivers and codecs and such, doesn't that mean that it isn't pure GNU/Linux?[/QUOTE]
That depends on what you mean with pure GNU/Linux. There are three alternatives (that I can think of):

1) In the philosophical/religous way:
Pure here means free and then it is not pure.

2) In the exclusive way:
Those drivers and codecs aren't part of either the GNU project nor the Linux kernel and therefore your system isn't pure.

3) In the inclusive way:
You normally don't say that a system becomes unpure just because you add some programs (that would mean that a pure windows is practicly unusable :)). Therefore your system is still a pure GNU/Linux.

As you phrased the question I would say nr. 3 applies for this case. :)

---

### Post by Kvark on 2006-06-20
[QUOTE=forrestcupp]It seems to me that there is a lot more to Linux than GNU[/QUOTE]
Linux is only the kernel and nothing else. It is a very important part of Ubuntu but there is a lot more to Ubuntu then just the Linux kernel. I actually think there is more Gnu software then Linux kernel stuff in Ubuntu. For example the Gnu Image Manipulation Program (Gimp), the Gimp ToolKit (GTK) and the Gnu Network Object Model Environment (Gnome).

But when it comes to the name... "Linux" sounds cool and "GNU" doesn't so "Linux" is the best name for the platform as a whole.

---

### Post by BoyOfDestiny on 2006-06-20
Really like this thread :)

Anyway, there is a particular speech by Richard Stallman I really enjoyed, it's quite long however...

[http://www.gnu.org/events/rms-nyu-2001-transcript.txt](http://www.gnu.org/events/rms-nyu-2001-transcript.txt)

Gives a little incite on what sparked the free software movement (believe it or not, a closed printer driver. :) )

After I read through it, a lot of things just "clicked" in regard to what Free Software really is.

---

### Post by az on 2006-06-20
[QUOTE=Gustav]Sorry for being picky, but I have to disagree again. :)

Hurd is a part of the GNU project and therefore an OS with Hurd and GNU should just be called GNU. (Although it is much clearer what is meant with GNU/Hurd so everybody calles it that :))[/QUOTE]

[http://www.gnu.org/software/hurd/hurd.html](http://www.gnu.org/software/hurd/hurd.html)
"The GNU system (also called GNU/Hurd) is completely self-contained ..."

---

### Post by forrestcupp on 2006-06-21
On this thread:

[http://www.ubuntuforums.org/showthread.php?t=138366](http://www.ubuntuforums.org/showthread.php?t=138366)

Is a perfect example of the possibility of my original complaint.

> Linspire responded to this demand, thinking having these products available in retail stores was a GOOD thing for open source. We put this package together and many retailers carried it and it even sold well. However, Linspire also got pounded on by "the community" for trying to "sell" open source software. (All profits went directly to open source projects.) So, even though OOoFF did quite well, and millions of retail shoppers could be exposed to Firefox and OpenOffice.org, we dropped the product. We never made any profit on it. By the time we paid for packaging and distribution costs, and with the low margins in retail software, this was just a project to help expose more people to Firefox and OpenOffice. Millions of people still purchase software through retail channels, and Microsoft loves having all that shelf space to themselves.


They were trying to sell (legally by the GPL license) OpenOffice.org and Firefox.  Then they got "pounded on" by the community.  Why did the community pound on them if they weren't breaking the rules, and that rule is acceptable?  This just enforces what I don't like about that part of the license.  I know they say they weren't making a profit, but this just shows the possibility of it.  A big name commercial company takes an opensource program and sells it.  I was taught that liberty is only liberty until you take away someone else's liberty.  So if you try to sell software to me, you've taken away a little piece of my liberty.

I'm not against retail software, just selling something that you didn't work on.

---

### Post by Gustav on 2006-06-21
I don't think it was anything wrong with selling OOoFF. The thing they did that was morally questionable was that they hid the fact that you can get the products for free if you download them. (It isn't against the GPL as far as I know though)

---

### Post by forrestcupp on 2006-06-21
That's my whole point! It's not against the GPL.  That's the only thing I don't like about the GPL.

---

### Post by Kvark on 2006-06-21
[QUOTE=forrestcupp]They were trying to sell (legally by the GPL license) OpenOffice.org and Firefox.  Then they got "pounded on" by the community.[/QUOTE]
Who where "the community" in this case? I am pretty sure the protests where from normal users who saw that the hated Linspire (yes most Linux users seem to hate them) where selling cost free programs for $20 and automatically assumed that $1 goes to pressing the CD while $19 goes straight into the hated Linspire's pocket. At least thats what I assumed at first. They probably wouldn't have been so upset if they had known the truth that most of the money went to the store because otherwise the stores wouldn't sell it and every cent of the little profit that was left for Linspire went into open source development. You can't make a judgement of the GPL licence based on what misinformed users whine about on some online forum or mailing list.

It's the developers that choose the GPL licence so it is only the developers' oppinions that matters here. If the developers like the GPL and stay with it then it is a good licence regardless of what anyone else thinks of it. Thats the way copyright works, all power to the copyright holders.

---

### Post by weasel fierce on 2006-06-21
Linspire in particular, generates a lot of bile and hatred, it seems.

I think its rather stupid, but generally, the smaller a particular community, the more rabid we get about "competition"

---

### Post by forrestcupp on 2006-06-21
[QUOTE=Kvark] You can't make a judgement of the GPL licence based on what misinformed users whine about on some online forum or mailing list.[/QUOTE]

I know Linspire says they didn't make a profit.  I'm just using this as an example of what is legally possible.  Someone else could do the same thing with the intent of making a large profit without going against GPL.  That is where I have a problem.

[QUOTE=Kvark]It's the developers that choose the GPL licence so it is only the developers' oppinions that matters here. If the developers like the GPL and stay with it then it is a good licence regardless of what anyone else thinks of it. Thats the way copyright works, all power to the copyright holders.[/QUOTE]

That is a very true statement.  If a developer is happy with GPL, then there's nothing wrong with it.  Maybe there should be a different opensource license available that doesn't allow someone to take other people's work and make a profit off of it.

By the way, the quote I posted from that forum was supposedly from the CEO of Linspire, not a bunch of whiners.

---

### Post by Kvark on 2006-06-21
[QUOTE=forrestcupp]Maybe there should be a different opensource license available that doesn't allow someone to take other people's work and make a profit off of it.[/QUOTE]
That is exactly what the [Aladdin Free Public License]("http://www.cs.wisc.edu/~ghost/doc/cvs/Public.htm") does. As far as I can tell it works exactly like GPL with the exception that you are not allowed to make profit off the software without paying the author.
> This License attempts to ensure that those who receive, redistribute, and contribute to the licensed Program according to the Open Source and Free Software philosophies have the right to do so, while retaining for the developer(s) of the Program the power to make those who use the Program to enhance the value of commercial products pay for the privilege of doing so.
But it is not a Free Software/Open Source licence since the very purpose of Free Software is to allow others to distribute and use it even if they make a profit in the proccess.

---

### Post by az on 2006-06-21
[QUOTE=forrestcupp]I know Linspire says they didn't make a profit.  I'm just using this as an example of what is legally possible.  Someone else could do the same thing with the intent of making a large profit without going against GPL.  That is where I have a problem.[/QUOTE]

Why?

You act like anyone who releases their code under the GPL is a victim.  Do you think every software developer who has released their stuff under a GPL licence feels that way?  Do you think *any* of them do?  I don't.

The truth is, linux geeks have had a tendancy to want to keep the stuff "pure" by being fine with complicated setups and obscure rules to follow.  Linspire was way ahead of the game by trying to be the user-friendly linux distribution.

AOL was the user-friendly face to the internet for a lot of people.  Did they contaminate the net?  No, they poured millions of dollars into it and help its growth.  Linspire wants to follow the same model.

In fact, I would think that if Linspire were to sell the same sort of boxed set of OO.org and Firefox today, they would get a lot less critticism than two years ago because linux users and free software enthusiasts are by-and-large more aware that it is important to make things easy and appealing to the end-user.  And to charge for that is no big deal.

Yes, it is complicated for a lot of people and to have a box and a manual works for them.

[QUOTE=forrestcupp]

That is a very true statement.  If a developer is happy with GPL, then there's nothing wrong with it.  Maybe there should be a different opensource license available that doesn't allow someone to take other people's work and make a profit off of it..[/QUOTE]

And not a lot of people would use it.  Software freedom is about a lot of things.  None of them are a vow of poverty.

A very important aspect of free software is that it is taken seriously.  It is supported.   For the software to maintain a level of support, you need to have people invest in it.  Preventing them from making a profit from it is ridiculous.

Anyway, if you want to write some software and release it under that kind of licence, it's your choice.  No one is going to stop you.  I'm certain that you would have a better shot at cultivating a community if you chose a licence like the GPL, though.  Good luck.

[QUOTE=forrestcupp]
By the way, the quote I posted from that forum was supposedly from the CEO of Linspire, not a bunch of whiners.[/QUOTE]

Yes, it was.  But he was refering to a bunch of whiners.

Could you imagine someone making fun of you at the supermarket because you chose to buy orange juice instead of squeezing it yourself from fresh oranges?  Same thing.

And while we are at it, Linspire give back to the community.  As opposed to Mepis or Xandros (two distros based on Debian).  I object to those two distros because they are not part of the open source community since they do not end up making the software any better by contributing back changes.  They even include some of their own software which they licence as proprietary.   

I would object to those two even if they were given out for free!

---

### Post by forrestcupp on 2006-06-22
Sorry for the rants, guys.  I'm new at this, and it's just taking me some time to adjust.  I'm used to Windows where all programmers are trying to make a buck, and even the free stuff makes it hard on you until you put money in their pocket.  Which there is nothing wrong with someone earning money through writing software.  The problem is that I came into the Linux community with a different idea of things than what they really are.  I guess my main problem is a trust issue.  I'm trying to adjust to the fact that I can trust that the community isn't out to screw someone over, and that they really are trying to work together to make things better.  It's almost like a utopian cyber-society, and it's just hard initially for me to accept that things really are like that.  I guess the software bullies would probably want to stay away from open source anyway.  I'm actually starting to understand things a little better.  While I don't like the fact that there is the possibility for someone to try to do self-centered things with someone else's software (even though it wouldn't avail), if there were a stipulation against that, it would make the license controlling, and take away freedom.  Also, I need to adjust to the fact that it isn't someone else's software; it's everyone's.  I just need to learn to relax and trust people, which is a hard thing to quickly change.  Just give me some time, and I'll be alright.  Sorry, guys.

Just one question, though.  Is it ok for someone to take pride in the fact that they came up with an idea and were the main programming contributor to an app?

---

### Post by az on 2006-06-22
[QUOTE=forrestcupp].  I'm trying to adjust to the fact that I can trust that the community isn't out to screw someone over, and that they really are trying to work together to make things better.  It's almost like a utopian cyber-society, and it's just hard initially for me to accept that things really are like that.  I guess the software bullies would probably want to stay away from open source anyway.  [/QUOTE]

The focus is not on the actual application, really.  It is on the community that revolves around it and contributes to it.  If the community cannot trust the software author to keep the software free, or doesn't allow others to contribute to the code, then that community will either find another project, or fork the code.  For a project to thrive, it has to be free to do so.

Anything that is GPLed can be forked at any time.  Why doesn't it happen very often?  Because it's not productive.  It's really a last resort.

Of the last few major projects that I know of which have forked, you could describe the internal problems that led to the forking as bullying.  For example, when Mambo was forked and Joomla was started, most of the Mambo developers were tired of the development of the project not being led into the direction that they wanted it to go - even though they were in the majority.

So I don't think it's utopian.  It's just a process that is very close to the actual people who make and use the code.  Sort of like the law of the market - if something is not popular, it dies, if something else is, it thrives.  The market decides.

[QUOTE=forrestcupp].  
I'm actually starting to understand things a little better.  While I don't like the fact that there is the possibility for someone to try to do self-centered things with someone else's software (even though it wouldn't avail)[/QUOTE]

Self-centered is not bad in of itself.  If your self-centered action has positive effects on the rest of the community, it is a good thing.  

[QUOTE=forrestcupp].  
Just one question, though.  Is it ok for someone to take pride in the fact that they came up with an idea and were the main programming contributor to an app?[/QUOTE]

Absolutely.  That's very important.  Just because you release something under a GPL licence does not mean that you no longer wrote it nor can get credit for it.  

It's just the opposite - copyleft refers to your copyright with distribution terms which guarantee that the code will remain free.  So it is clearly your work.  But others can use it and improve it under the condition that it remains under the same licence.

---

### Post by Footissimo on 2006-06-22
[QUOTE=forrestcupp] I hated Mandrake because the free version kept trying to get me to buy the commercial version of it.  Also, I think they made you pay to download from their repositories.  Thank God for Ubuntu.[/QUOTE]

Just a note:

I used Mandrake/iva 10.1, LE2005 and 2006 and I can't say I was ever bothered by notices to buy anything and you certainly don't have to pay anything for the repos (google easyurpmi).

---

