---
title: "Is the Linux development model flawed?"
date: 2007-06-09
forum: The Cafe
---

### Post by Prisma on 2007-06-09
**This article have been taken from Techworld.com:**
[COLOR="Indigo"][I][B][SIZE="3"]
Is the Linux development model flawed?[/SIZE][/B]
An upcoming summit will see much navel-gazing as Linux for the desktop stalls

By Manek Dubash, Techworld

Back in the early 1990s, when Linux initiator Linus Torwalds and open source software started to make headlines, the idea of giving software away seemed crazy. Looking at the headway the movement has made since then, you might be forgiven for wondering why Linux desktops have failed to become as ubiquitous as Linux servers are. 

Oh, how they laughed when the open source movement started. But today, Linux is present in almost every enterprise and, according to market researcher IDC, it's set to keep on growing. In fact, Linux server sales have hit their second consecutive quarter of double-digit growth and constitute 12.7 percent of the overall server market, or $1.6 billion for the first quarter of 2007, reckons the research company.

What's more, server technology has moved forward in leaps and bounds, with virtualisation - now the accepted way of helping to combat the combined treats of humungous and expensive power consumption and adding to the global climate crisis - only the latest technology to make it into the Linux kernel.

So there are millions of Linux boxes out there, performing tasks such as serving Web pages and hosting databases. And there's a fair number of Linux machines running as desktops, mainly for technically savvy enthusiasts and computer professionals. Exact numbers are impossible to come by for a free OS, but estimates made on the Ubuntu forum -- Ubuntu is the fastest growing and probably the most-used desktop distro today -- suggest that the numbers could be between 500,000 and one million.
Enterprise desktops: the promised land

Yet there's one area in which Linux appears to have stalled: the enterprise desktop. What's holding it back?

There's a number of reasons cited by critics. They include lack of technical support, lack of hardware drivers, lack of standard documentation, and lack of appropriate skills in the enterprise IT team. Plus there's the cost of switching desktop users over to Linux, in time, hardware and software, and of training them, none of which will come cheap.

But even if the move can be cost-justified -- and there are bound to be hidden and unexpected costs -- there may be other reasons too. Linux developers have argued for some time that drivers for most hardware are now available and that hardware support shouldn't be an issue any more.

Up to a point that's true. However, once you stray off the beaten path and want support for, for example, a 3G PC Card for a laptop, things can start to get messy. Yes, you can make it work, but it's not pretty and it often requires individual tuning. And that's just one example.
Linux development in crisis?

But it's worse than that.

Coming up next week is Linux' first collaboration summit, organised by the Linux Foundation and aimed at developers. The tagline is that the event "will bring together the brightest minds in the Linux ecosystem to discuss where Linux is, where it needs to go and how we can all help get it there."

In discussions before the event, it seems that some honesty is being called for. Linux is no longer the poor relation but a heavily used enterprise-level tool. Yet there are areas where the technology falls well below what could be expected of an OS at this level -- and it may even be that the OS development model is in part to blame.

For example, Torvalds has said that the file system and power management need improvement, and that device drivers in particular often work but don't implement advanced functions.

One example is power management. "We're still pretty stupid about power management," Linux kernel developer Morton says. Devices are able to support low-power states. For example, a network card that's not receiving incoming traffic can go to a lower-power state. But Linux supports only on and off and, Morton says, "we're having trouble getting off and on working."

Another is file systems, which will need an overhaul if they're to stand up to the rate of increase in hard disk capacities but not speed. File system developer Val Henson points out that disk capacities are likely to grow by a factor of 16 by 2013, but that bandwidth will only grow by a factor of five, and seek time by a factor of 1.2. That means that the file-system-checking utility, fsck, will take longer and longer to run -- it could take days.

Torwalds has also offered veiled criticism of the way the open source development model operates. He singled out the development workflow process. Much of the work done by the Linux kernel on startup and during operation is wasted because some developers aren't exploiting the capabilities of some of the latest code libraries. Examples include the repeated opening of the same files by different modules within the kernel, and over-zealous checking of the hardware specification.

Morton also reckons that developers either don't or can't profile their code -- in other words, find out what the code is doing to the hardware, how much cache and main memory it uses, and which chunks of code actually execute.

For the end user, all this can translate into hardware devices that don't run as efficiently they did under Windows, that use more power and run down laptop batteries quicker, and which take longer to start up and run than they should. Some developers complain about how some Linux desktops doesn't seem as 'snappy' on low-spec machines.

If Linux is to make the final leap into the average user's machine, especially in the enterprise, all these matters need to be addressed.

One solution could be greater central control and tighter checking procedures and metrics before code is passed off. However, it remains to be seen if the community can make the collective effort to fix this following the summit, where these and other issues will be aired.

If it doesn't, though, then it gives critics carte blanche to argue that the open source development model is flawed. And that's an argument to be taken seriously. 

[/I]
[/COLOR]i think this is a good article to discuss on this forums. :D What are your views about it?

---

### Post by EdThaSlayer on 2007-06-09
I have never really thought about the power management. My laptop still seems to run for as long as it does on Windows(only if Windows is playing some games).

---

### Post by cantormath on 2007-06-09
I actually have something to say about this.

I really think the linux community, at least the ubuntu community, should spend alot more time working on hardware issues.   We need less beryl and more bios.  I dont think that people should stop working on beryl or any other project necessarily, I just think that the ubuntu dev community would be addressing a larger portion of people if they found more hardware work-arounds or reverse-engineered more hardware drivers.  This change is overwhelmingly needed with respect to laptop hardware, _specifically_ for the laptop BIOS..


If the goal is to take the desktop community by storm, we will have alot more longterm users, everyday users, if users laptops do not shut off when they play a movie and open firefox at the same time for more then a couple minutes.  I know this is not our communities fault, however, it is our communities problem.

I think this more important then any application.

---

### Post by 3rdalbum on 2007-06-09
I've never heard anyone say "I'd use Linux, but it starts up too slowly and my laptop battery runs down too quickly".

Run Windows with a full security suite, and you'll find it starting slower and thrashing the disk more than Linux.

These factors are not a "Linux desktop blocker". Also, disks will not increase by a factor of 16 by 2013 - that number is ridiculous. If you calculate it out, the average user will supposedly have 5.1 terrabytes of internal hard disk space in 5 years time. That's not realistic.

---

### Post by jiminycricket on 2007-06-09
They're already doing this.

Google lkml for intel Powertop.  

Here's the link to the OP's story, btw: [http://www.techworld.com/security/features/index.cfm?featureid=3443&pagtype=samechan](http://www.techworld.com/security/features/index.cfm?featureid=3443&pagtype=samechan)

---

### Post by Mathiasdm on 2007-06-09
> **3rdalbum said:**
> I've never heard anyone say "I'd use Linux, but it starts up too slowly and my laptop battery runs down too quickly".

Run Windows with a full security suite, and you'll find it starting slower and thrashing the disk more than Linux.

These factors are not a "Linux desktop blocker". **Also, disks will not increase by a factor of 16 by 2013 - that number is ridiculous.** If you calculate it out, the average user will supposedly have 5.1 terrabytes of internal hard disk space in 5 years time. That's not realistic.

Hard drives follow Moore's law, meaning their capacity doubles every 18 months. By that count, by 2013, hard drive capacity will increase by a factor of 16 by 2013.

However, in the last few years, the increase seems to go a bit slower.

8 years ago, our brand new computer had a 10 GB capacity. That was quite a lot back then. Nowadays, 320 GB disks are perfectly normal. Capacity increases exponentially ;) Or at least it has for quite a while.

---

### Post by kamaboko on 2007-06-09
Finally,  a good Linux article.   I think there were a lot of great points made.  With respect to my laptop and Ubuntu, it does eat the battery much faster than Windows XP Home.  Moreover, it runs much hotter.  That's a minor issue to the bigger picture though.  One thing the author failed to mention is that  the vast majority of Linux servers in the enterprise environment are paid OS's such as Red Hat.  Red Hat, though not my favorite OS in terms of functionality and intuitiveness, has seen the light: If Linux is going to work, it has to be a for profit model like MS.  Programmers and developers have to be on the payroll working toward a unified goal, and this costs money.  Quality does not come for free.  Ultimately, IMO, this is the goal of every Linux distro; get the people hooked on it b/c we have the best one, then charge to support it down the road.  The problem is that there are too damn many distro's out there each with varying levels of development and support.  No business person is going to bet the bank on such clusterf*** of disorganization, not to mention a complete lack of enterprise business software.

---

### Post by jiminycricket on 2007-06-09
> **kamaboko said:**
> Finally,  a good Linux article.   I think there were a lot of great points made.  With respect to my laptop and Ubuntu, it does eat the battery much faster than Windows XP Home.  Moreover, it runs much hotter.  That's a minor issue to the bigger picture though.  One thing the author failed to mention is that  the vast majority of Linux servers in the enterprise environment are paid OS's such as Red Hat.  Red Hat, though not my favorite OS in terms of functionality and intuitiveness, has seen the light: If Linux is going to work, it has to be a for profit model like MS.  Programmers and developers have to be on the payroll working toward a unified goal, and this costs money.  Quality does not come for free.  Ultimately, IMO, this is the goal of every Linux distro; get the people hooked on it b/c we have the best one, then charge to support it down the road.  The problem is that there are too damn many distro's out there each with varying levels of development and support.  No business person is going to bet the bank on such clusterf*** of disorganization, not to mention a complete lack of enterprise business software.


:popcorn:

Water must be cloudy under there.

---

### Post by DoctorMO on 2007-06-09
Oooh I'm scared!

> Yet there are areas where the technology falls well below what could be expected of an OS at this level

Not really, for an OS that will compile on the most systems, run with the most hardware and do a wide variety of things in a sane manner I consider the quality of the technology to be above what could be expected. I don't know if anyone has ever had a chance to look at proprietory code for embedded and kernel level services; it's horrible, a mess. you wonder how any of it works and when companies port their code to the linux kernel it often gets rejected with a long list of things that need to happen in order to fix it and clean it up.

This article just wants to raise the blood pressure levels of good solid free software developers and doesn't make hardly any good or specific points. with a good helping of over reaching ideas and lack of understanding.

I label this: TROLL

---

### Post by DoctorMO on 2007-06-09
> Programmers and developers have to be on the payroll working toward a unified goal, and this costs money. Quality does not come for free. Ultimately, IMO, this is the goal of every Linux distro; get the people hooked on it b/c we have the best one, then charge to support it down the road. The problem is that there are too damn many distro's out there each with varying levels of development and support. No business person is going to bet the bank on such clusterf*** of disorganization, not to mention a complete lack of enterprise business software.

Another person who doesn't understand how free software development works. go back to your cathedral.

---

### Post by kamaboko on 2007-06-09
> **DoctorMO said:**
> Another person who doesn't understand how free software development works. go back to your cathedral.

On the contrary, I know it all too well.  Go back to business 101 and this time pay attention.

---

### Post by needtolookatascreenshot on 2007-06-09
> **kamaboko said:**
> On the contrary, I know it all too well.  Go back to business 101 and this time pay attention.

No, apparently you don't. Otherwise you would argue why it is flawed and not just proclaim it is and then immediately start to insult people.

And don't get me started on your little "there are too many distros" rant. As long as you can't show why yet an other hobbyist distro should in any way be bad for people who want to run an enterprise distro like Red Hat, you simply don't have a point.


Anyway, back on topic:
I think it was an incredibly weak article.
Why?
It's not that it doesn't make some valid points, but it's beyond me how these points together with the linux community addressing them as the article describes it should add up to a flawed development model.

To sum it up, the article doesn't live up to its sensasionalist headline.

---

### Post by qamelian on 2007-06-09
> **kamaboko said:**
> On the contrary, I know it all too well.  Go back to business 101 and this time pay attention.

Apparently you don't. Go back to the history of free (as in freedom) software development...and pay attention. See? Anyone can make an unfounded statement...and make it worthless. Unless your prepared to say why Business 101 applies, your assertion is pointless and without value. The merits of the f/oss development model are documented on most site related to the f/oss movement. Where's your backup?

---

### Post by mech7 on 2007-06-09
> **needtolookatascreenshot said:**
> And don't get me started on your little "there are too many distros" rant. As long as you can't show why yet an other hobbyist distro should in any way be bad for people who want to run an enterprise distro like Red Hat, you simply don't have a point.

Well i suppose everybody can see that too many distro's is a bad thing and especially the stupid ones.. when i had never installed linux before and saw the christian and satanic edition i first thought it was a joke, but then i saw it was real thinking the os must be a joke too :)

---

### Post by deadowl on 2007-06-09
The issues are there and people want to address them, so yea, there's the economic model for you. It works.

---

### Post by Erik Trybom on 2007-06-09
I think it's pretty obvious that the free software development model has its pros and cons, just as proprietary developing has. This article however does little to illuminate those issues.

Yes, Linux has problems that need to be addressed. Perhaps some of them are harder to address because of faults within the development model, but I believe most of those problems has to do with not getting enough support from the hardware manufacturers. It's a lot easier making an OS if the card makers supply the drivers for you - or at least the specs, so you don't have to guess how it works. 

I don't think that's only a question of making the drivers open source though - I think it's also a question of having more than one percent of the desktop market.

---

### Post by AndyCooll on 2007-06-09
> **needtolookatascreenshot said:**
> Anyway, back on topic:
I think it was an incredibly weak article.
Why?
It's not that it doesn't make some valid points, but it's beyond me how these points together with the linux community addressing them as the article describes it should add up to a flawed development model.

To sum it up, the article doesn't live up to its sensasionalist headline.

I take a slightly different viewpoint (though I agree with alot of what you say). I think it was quite a good article ...purely because it raises some interesting points for consideration. Like you I disagree with the articles title, since I certainly do not think the open-source development model is flawed. Indeed, is its strength. Where I think it makes an interesting point is in the need to consider in some way how certain areas of development perhaps need to be more cohesive. Where the article fails, is that the writer clearly doesn't understand the open-source development model and while they raise some interesting points they don't provide any decent answers.

:cool:

---

### Post by use a name on 2007-06-09
Most points in the article are pretty well known and NOT a result of poor linux development (drivers, acpi, etc).

One thing that I think is interesting is this:
> Torwalds has also offered veiled criticism of the way the open source development model operates. He singled out the development workflow process. Much of the work done by the Linux kernel on startup and during operation is wasted because some developers aren't exploiting the capabilities of some of the latest code libraries. Examples include the repeated opening of the same files by different modules within the kernel, and over-zealous checking of the hardware specification.
If this is true, then it should get some attention indeed. If there are standard issues with this, then it would be good if programmers were told what to do (examples, howto's, etc).

On the other hand, yeah right, the other operating systems don't suffer from this problem at all!

---

### Post by cantormath on 2007-06-10
> **mech7 said:**
> Well i suppose everybody can see that too many distro's is a bad thing and especially the stupid ones.. when i had never installed linux before and saw the christian and satanic edition i first thought it was a joke, but then i saw it was real thinking the os must be a joke too :)

having multiple distros was the point. Anyone can take linux and make it their own.  Best part is, you get to use anyone you want.
Remember, linux is just the kernel.

---

### Post by nutz on 2007-06-10
> **3rdalbum said:**
> I've never heard anyone say "I'd use Linux, but it starts up too slowly and my laptop battery runs down too quickly".

Run Windows with a full security suite, and you'll find it starting slower and thrashing the disk more than Linux.

These factors are not a "Linux desktop blocker". Also, disks will not increase by a factor of 16 by 2013 - that number is ridiculous. If you calculate it out, the average user will supposedly have 5.1 terrabytes of internal hard disk space in 5 years time. That's not realistic.

You can get a 1 terabyte drive these days. I think that figure will be pretty close; especially in the age of HD content...

---

### Post by nutz on 2007-06-10
Your average user just wants an easy to use system where everything works and they have to do as little as possible to make it work. This is clear with each new release of Windows and the way it gets dumbed down a little more each time. The general public just loves it that much more, Microsoft knows exactly what they want...

If you want to win the average desktop space all you have to do is have an OS that is stupid easy to use where everything works and the user has to put forth as little effort as possible. And if it looks cool then even better…

Linux is not there yet and it may never be since the average Linux user isn't the kind of person that needs his computer dumbed down in order to use it. Because of this it is hard for a Linux user to relate when they make silly complaints about drivers not being there and such. As if that is really the fault of the OS...

I thought drivers were the hardware vendors’ responsibility? The real question here is why do so few hardware vendors make drivers for Linux? Solve that and Linux will take a huge step forward.

---

### Post by kamaboko on 2007-06-10
> **cantormath said:**
> having multiple distros was the point. Anyone can take linux and make it their own.  Best part is, you get to use anyone you want.
Remember, linux is just the kernel.

Sure, have as many distros as you want.  That's fine with me.  But never expect large businesses to embrace Linux simply b/c of that.  Sure, they'll use it for file/web servers, but beyond that it's dead.  No IT staff wants to take care of 30+ flavors of Linux in a working environment.  No quality software development company wants to write code that caters to 30+ distros of Linux.  It would be a financial overhead nightmare supporting that many distros.  To make my point go to sourceforge.net and run a search for the most popular Linux projects.  As of this posting, here's what I got:


1. Inkscape: A Linux, Windows & OSX vector graphics editor (SVG format) featuring transparency, gradients, node editing, pattern fills, PNG export, and more. Aiming for capabilities similar to Illustrator, CorelDraw, Visio, etc.

2. amsn: A very nice MSN compatible messenger application, aMSN Messenger is a multiplatform MSN messenger clone. Works pretty much like its Windows based counterpart. Perfect for keeping in touch with those friends who have not yet seen the light. Works on linux

3. Audacity: A fast multi-track audio editor and recorder for Linux, BSD, Mac OS, and Windows. Supports WAV, AIFF, Ogg, and MP3 formats. Features include envelope editing, mixing, built-in effects and plug-ins, all with unlimited undo.

I could go on, but I won't.  The point being, they're pity little apps that rank up their with text editors and MP3 rippers.  There's nothing or very very little being developed for the enterprise level. Why?  No one wants to do it for free.  Until this happens, Linux will be relegated to file/web servers and fringe home users.

---

### Post by Tundro Walker on 2007-06-10
> **DoctorMO said:**
> Another person who doesn't understand how free software development works. go back to your cathedral.

I agree with Doc (that quality software doesn't always come from a group of paid developers.)  Look at Napster.  Wasn't the most elegant program, but one guy created a little program that changed a lot of how the music industry does business (mostly by waking them up to the digital age.)  Look at Firefox...OpenOffice.org...Gimp..  There's lots of cases of really ingenious things being developed by one or a few people..for free.  A lot of the worlds innovations usually come from some person or a group of folks who simply thought "outside the box" on their spare time.  Usually it's the confinement of work that pushes them to think outside the box on their spare time.  EG: your stuck doing it "the man's way" at your job, and its tedious and boring and you aren't motivated to over-perform, because someone else will profit from your great ideas.  But, in your spare-time, you can delve into all the really cool ideas you have, or collaborate online with others about it, and maybe something cool will come of it.

A lot of folks use a "90% to 10%" ratio to compare things, and I'll use that in comparing paid vs. free software development.  At a company that pays developers to do stuff, there will be a 90% chance that the project gets done, but it'll only be about 10% creative or innovative, and maybe 10% overdue.  If it's a free-ware / open-source project done by an impassioned developer or group of developers, it has a 10% chance of getting done, but a 90% chance of being really creative or innovative.  

I know those ratios sound outlandish, and they probably are, but I wanted to focus peoples' attention on how large corporate "paid to work" mentality usually sucks the creativity / innovation out of lots of folks (not all, but a lot).  That's why major achievements are usually done by single people or small groups outside the corporate office.  Folks sitting at home, nothing better to do than to "think tank" about an issue, and come up with really novel solutions.  You have all the time in the world to do so, and no pressure to get results "by Friday" due to some stupid corporate schedule.

After all...look at Einstein...

---

### Post by Polygon on 2007-06-10
> **kamaboko said:**
> Sure, have as many distros as you want.  That's fine with me.  But never expect large businesses to embrace Linux simply b/c of that.  Sure, they'll use it for file/web servers, but beyond that it's dead.  No IT staff wants to take care of 30+ flavors of Linux in a working environment.  No quality software development company wants to write code that caters to 30+ distros of Linux.  It would be a financial overhead nightmare supporting that many distros.  

orly?

they dont need to support 300+ distros. If an IT staff wants to take care of multiple distros, he can do so using the command line, which every distro has.  All a IT person needs to do is make sure that all of the linux computers he is responsible of has certain programs installed, and if anything goes wrong all he has to do is use the terminal and configure certain settings from there. And not to mention that if a company wanted to use a linux distro in their company, they would most likely pick one and install that ONE distro on all of their computers.

and writing programs for linux? give me a break. All they have to do is write a program specify or even include the dependencies for that program and it will run on ANY linux machine. the same thing goes for windows. When you install a program your installing the code, and all of the little libraries that you most likely have 50 copies of because every program you install has that library included. The same thing goes for linux, except you have one copy and every program that uses it uses that copy. 

for example if a "enterpirse" level company creates a program for linux, if they write it in python, then all a linux user needs, regardless of what distro he runs, is python to run the program. 

Google uses a modified ubuntu installation on their workstations, are they considered a large business?

---

### Post by G Morgan on 2007-06-10
> **kamaboko said:**
> Sure, have as many distros as you want.  That's fine with me.  But never expect large businesses to embrace Linux simply b/c of that.  Sure, they'll use it for file/web servers, but beyond that it's dead.  No IT staff wants to take care of 30+ flavors of Linux in a working environment.  No quality software development company wants to write code that caters to 30+ distros of Linux.  It would be a financial overhead nightmare supporting that many distros.  To make my point go to sourceforge.net and run a search for the most popular Linux projects.  As of this posting, here's what I got:


1. Inkscape: A Linux, Windows & OSX vector graphics editor (SVG format) featuring transparency, gradients, node editing, pattern fills, PNG export, and more. Aiming for capabilities similar to Illustrator, CorelDraw, Visio, etc.

2. amsn: A very nice MSN compatible messenger application, aMSN Messenger is a multiplatform MSN messenger clone. Works pretty much like its Windows based counterpart. Perfect for keeping in touch with those friends who have not yet seen the light. Works on linux

3. Audacity: A fast multi-track audio editor and recorder for Linux, BSD, Mac OS, and Windows. Supports WAV, AIFF, Ogg, and MP3 formats. Features include envelope editing, mixing, built-in effects and plug-ins, all with unlimited undo.

I could go on, but I won't.  The point being, they're pity little apps that rank up their with text editors and MP3 rippers.  There's nothing or very very little being developed for the enterprise level. Why?  No one wants to do it for free.  Until this happens, Linux will be relegated to file/web servers and fringe home users.

Firefox and OOo don't count clearly. Number of distros isn't an issue. There are one or two core distros that will set a standard for third party apps (LSB) and they will write for that. We can support that across all distros.

You clearly know nothing about software development if you think this is a real issue at all. Easily solved, just a matter of defining the standard. This is well in hand.

---

### Post by Tomosaur on 2007-06-10
The 'too many distros' argument is a total lie. The most popular distros are Debian and Red Hat based, so really, only two distrobutions need to be supported, and even then the only damn difference really is package management. Know how to get a Red Hat package to work on Debian? 'sudo alien myrpm.rpm' Oooo, difficult. Yes, some distros have their quirks, but any programmer worth his salt knows that these are problems which can be solved by simply being a good programmer. Don't hard code path names, don't assume encoding type, don't assume system specs. Linux solves these issues inherently, virtually everything you do revolves around environmental variables, which is why you see "check it's in your path" so much. All Linux distros use the Linux kernel. All devs have to do is say 'you need kernel version xxx', just like they say 'you need Windows 98'. Anything else is a piece of cake. Dependencies? Sorted - even easier than in Windows, in fact. Far less messy, centrally organised (per-distribution), and, for the most part, don't require expensive cross-licencing. The issue of open-source vs propietary is still a problem for many developers, and the GPL is still viewed negatively by most of the massive development corporations, for any number of reasons.

The main, overriding reason why nobody ever releases propietary apps for Linux is that most of the hardcore Linux users do not want or need propietary apps. We need a groundswell of adoption by home users before the developer's perspective will shift, and this is happening slowly but surely. Added to this - we have a pool of developers who have never used Linux, let alone program for it. Then we have the massive backlog of restrictively licensed code which needs to be re-engineered for a more open development base on Linux. All of this is being fixed, it will take time, and things like the MS-Novell deal really put a hamper on things. Every time Microsoft plants an obstruction, the Linux community has to scramble to work around it. GPL3, for example, will go a long way to invalidating Microsoft's claims over Linux - but it will create its own problems along with it. Some libraries will not use it, others will object to it, and other libraries will become defunct because of it. We need a central place where all of this is organised, not the mish-mash of websites and mailing lists we have now. Distribution based repository systems are all well and good, but they do nothing to solve the main problem - which is inter-distribution compatibility. If we had a central repository which managed everything for every distrobution, then the problem would be halved.

---

### Post by kamaboko on 2007-06-10
> **G Morgan said:**
> Firefox and OOo don't count clearly. Number of distros isn't an issue. There are one or two core distros that will set a standard for third party apps (LSB) and they will write for that. We can support that across all distros.

You clearly know nothing about software development if you think this is a real issue at all. Easily solved, just a matter of defining the standard. This is well in hand.

Lol...you make me laugh.  You clearly know absolutely nothing about business.

---

### Post by macogw on 2007-06-10
Val was mentioned!  She's cool :)  The day we met, she was talking about how there's another filesystem that does fsck on different parts of the disk (but without requiring lots of partitions) so that you don't have to wait 10 minutes for it to finish each check, maybe just two.  And I think she said it could go while you were working.  I'm gonna go ask her about that real quick...crap, she's idle on IRC.  I'll ask later.

---

### Post by G Morgan on 2007-06-11
> **kamaboko said:**
> Lol...you make me laugh.  You clearly know absolutely nothing about business.

There's me thinking that the market starts diverse before market forces naturally cull products. You know sort of like we once had many operating systems before the market narrowed it down to just Windows. I'm sorry but you are talking nonsense from beginning to end.

Number of distros isn't an issue. Products will be supported on the most popular distro via LSB, this is similar to what happens now when all the corporate services* currently support RHEL except they will support a universall standard instead of simply RPM. They will work on all other LSB compliant distros as a matter of fact but will be unsupported on less popular platforms. We will be left with 1 or 2 mainstream distros and the traditional Linux user can still use Gentoo or Slackware without interfering with corporate Linux.

We don't need to cull our projects for Linux to succeed in the marketplace. Industry will pick a distro and standardise around it. We will provide a means for some form of genericness between distros. Already in hand. 

*like Oracle, JBoss, VMware etc.

---

### Post by runningwithscissors on 2007-06-11
> **kamaboko said:**
> No quality software development company wants to write code that caters to 30+ distros of Linux. 
Hey! Did I not tell you that that is completely wrong? You don't need to write different code for different distributions.

About Linux and large companies. Well, I couldn't give a **** really. Linux was here before they came around. It will be here after they leave too. We don't need to make any concessions for them.

---

### Post by cantormath on 2007-06-11
> **kamaboko said:**
> Lol...you make me laugh.  You clearly know absolutely nothing about business.

There are more Linux/Unix machines in this world then MS.  Most of them are owned by business and/or governments.  If you think the consumer market makes up "business" then you are missing the big picture as well.  There is a ton of money in FOSS if you know what you are doing.  If you expect to get paid alot of money being a point click engineer, well, we are trying to put you out of a job.

We own the server world.......we are now just starting to go for the desktop world. One of many victories: Dell Laptops and Desktops on sale.......next, it will  be your computer.
:D

---

### Post by karellen on 2007-06-11
why do always a discussion like this one has to end in a "linux/open-source vs windows/microsot" argument?
:confused:

---

### Post by G Morgan on 2007-06-11
> **cantormath said:**
> There are more Linux/Unix machines in this world then MS.  Most of them are owned by business and/or governments.  If you think the consumer market makes up "business" then you are missing the big picture as well.  There is a ton of money in FOSS if you know what you are doing.  If you expect to get paid alot of money being a point click engineer, well, we are trying to put you out of a job.

We own the server world.......we are now just starting to go for the desktop world. One of many victories: Dell Laptops and Desktops on sale.......next, it will  be your computer.
:D

Please don't shatter people's realities. The fact that Windows runs barely anything interesting escapes most people. When the NY:SE, as a big corporate entity, decided to upgrade their systems from the legacy AIX infrastructure they were running I'm sure Windows Server was right at the top of their list of solutions but they chose Linux because as poor stock brokers they couldn't afford Windows.

You use Windows if you want to do some simple document editing or mess with some images or sound in a relatively easy way. Doing real, mission critical, work is the place of solutions like Linux, Solaris and BSD.

---

### Post by santy_kushwaha on 2007-06-11
[COLOR="Red"]**thnx for u reminder but we already knew that**[/COLOR]

---

### Post by G Morgan on 2007-06-11
> **karellen said:**
> why do always a discussion like this one has to end in a "linux/open-source vs windows/microsot" argument?
:confused:

Because there is always some MS fan who comes in with few facts and a poor understanding of actually how the computer landscape breaks down and makes basic, tired and largely unsupported attacks on a process they don't understand. ;)

Of course there are flaws in the development model, there are flaws in everything. There are times when waterfall development processes are better than iterative processes but they are rare. The same argument, really it is wrong to talk about OSS as a different process. Generally it's a modified type of iterative development while generally proprietary land is still an archaic waterfall shop.

The largest problem with OSS is the idiom 'Make something that is useful today, don't plan to take over the world'. This statement is perfectly sound but often it isn't possible to make something useful today and you must do a lot of work to get to a point where traditional OSS can take over. This is why many good applications we have started off as a very poor but working proprietary project which we took and made a million times better. This enables us to jump the useful today gap even if 99% of the work was later done by us. Take Eclipse and Netbeans, both were god awful if working IDE's. Now both projects are very good and approaching best of breed status.

In any case the point is we don't always follow the development model to the letter. A model is an ideal, we have people instead of machines to make them fit the non ideal situations. Often we need fudges to cover the gaps like they have in any model in any industry.

---

### Post by cantormath on 2007-06-11
> **G Morgan said:**
> Please don't shatter people's realities. The fact that Windows runs barely anything interesting escapes most people. When the NY:SE, as a big corporate entity, decided to upgrade their systems from the legacy AIX infrastructure they were running I'm sure Windows Server was right at the top of their list of solutions but they chose Linux because as poor stock brokers they couldn't afford Windows.

You use Windows if you want to do some simple document editing or mess with some images or sound in a relatively easy way. Doing real, mission critical, work is the place of solutions like Linux, Solaris and BSD.

You forgot about the spreadsheets and the bitchen calculator.......Windows has that down.:D

You can do all that stuff with the same easy in linux.  You just have the option to  do whatever you want in linux as well.

---

### Post by airtonix on 2007-06-15
yeah life is easier when you cant see the horizon and know that you can run in any direction..

life is easier when your being beaten in the head wit ha club...whilst being told to "keep-diggin-you-worthless-peseant"

life is easier when you have no choice

life is easier when "you-betters" make your cultural-socio-economic policies without consulting or considering you.

life is just plain damn easy under augsto pinchette.....just soo damn easy taking all those clubs to the head.

but for you....freedom is the hardest thing.....to know you can do what ever you want within your own morality is something that scares the absolute fecal currency out of your mouth......

didnt mathew say something like this about the priests in the bible....they who know the path yet fear the destination.

---

