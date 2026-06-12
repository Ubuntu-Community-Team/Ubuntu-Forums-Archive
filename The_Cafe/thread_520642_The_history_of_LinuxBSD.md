---
title: "The history of Linux/BSD"
date: 2007-08-08
forum: The Cafe
---

### Post by Turboaaa2001 on 2007-08-08
I have worked with Debian based Linux\Unix distros for several years now and feel that I am missing out on some history.

I could just google what I need (and I am doing so) but I would like to here from the great people here in this community.

I have a good understanding of the begining, but I need to know what is

GNU
BSD
Debian
etc..

and how they relate to each other. After I gather all the information I'm going to cut-and-paste key parts and type in the links between them. After that I'm printing it out and placing it in my folder for my personal records.

I would also like links to trusted articals that have ANY kind of relevance to this project, but I'm more interested in YOUR words so please respond!

Please help me create this document, I know it has been done before, I just want to put together my own.

---

### Post by tbroderick on 2007-08-08
Why not go to Wikipedia?

---

### Post by ErusGuleilmus on 2007-08-08
Defiantly Wikipedia, it is after all the summation of all human knowledge ever!

---

### Post by wolfen69 on 2007-08-08
i guess google ISNT your friend. you're obviously not putting in the right keywords. i can found out the history of the dust particle on my cpu fan on google. wow.

---

### Post by Darkhack on 2007-08-08
Here is a very brief summary with Wikipedia links for more detailed information.

In 1969 Bell Labs (now AT&T) created the [UNIX]("http://en.wikipedia.org/wiki/Unix") operating system.  It was the first OS to use a portable language called [C]("http://en.wikipedia.org/wiki/C_%28programming_language%29").  This meant that it could run on different machines where at the time, an OS was typically built for exactly one model of computer.  It become very well known for the UNIX philosophy which is that a program should "do one thing, but do it well" as UNIX was mainly a collection of very small simple programs.

In the 1980s many companies began creating their own versions of UNIX as AT&T was now licensing it.  Companies like Sun, IBM and even Microsoft had their own versions; SunOS (now Solaris), AIX, and Xenix which was later sold to Santa Cruz Operation (SCO... yes *that* SCO).  Because companies were modifying the code for their own purposes and redistributing it, there were now many versions of UNIX that were not binary compatible and many that weren't even source compatible meaning that one would have to port their software to each version of UNIX if they wanted to make software for the platform and not be limited to one particular implementation.

The University of California in Berkeley was interested in UNIX and was able to get a license to work on the source code.  Overtime they had completely replaced all of the copyrighted code and could thus release their new clone under a new license and called their system the [Berkeley Software Distribution]("http://en.wikipedia.org/wiki/BSD") (BSD).  However in 1992 legal action was filed against them over copyright issues.  Because the system worked almost exactly like AT&T's version they believed that they were using copyrighted code in their system.  In 1994 the lawsuit ended and Berkeley only needed to remove 3 lines of code and modify 70 in order to not violate AT&T's copyright.

Earlier on however, [Richard Stallman]("http://en.wikipedia.org/wiki/Richard_Stallman"), a hacker from MIT wanted to create a "free" version of UNIX for the community.  Stallman referred to the meaning of free as in liberty and not as in price as shown in the [GNU General Public License]("http://en.wikipedia.org/wiki/GPL") (GPL).  In 1985 Stallman formed the [Free Software Foundation]("http://en.wikipedia.org/wiki/Free_Software_Foundation") (FSF) to help create a UNIX-like operating system that wasn't actually UNIX so (like BSD) they could use their own license.  He called the system [GNU]("http://en.wikipedia.org/wiki/GNU") (pronounced guh-new) which is a recursive acronym for Gnu's Not Unix.  It was similar, but it was in fact not UNIX.

By 1990 they had finished nearly all of the required tools for an operating system (the shell, compilers, libraries, etc) but they lacked one thing, a kernel which is the core of an OS.  Until now they had been writing their code on a proprietary version of UNIX.  Work then began on the kernel which was to be known as [HURD]("http://en.wikipedia.org/wiki/HURD").  It was designed to be a [microkernel]("http://en.wikipedia.org/wiki/Microkernel") because at the time it was believed that microkernels were more stable and reliable.  17 years later, the HURD still isn't even closed to finished.  Problems began early on as the HURD was extremely difficult to debug.  The separate processes of the kernel used a message passing system to communicate but when crashes occurred it was unknown which message was being passed to cause it and which processes were communicating to end up causing it.  It's like trying to figure out how a 16 car pile up occurred after the fact because they weren't able to actually see how the software ran.  It was basically extremely complex.

During this time in the early 90s, there was another UNIX like system out there called Minix which was a microkernel but it was far more successful in its development and still runs today.  However back then it was under a more restrictive license (now BSD) thus it was not suitable for Stallman's purpose.  A Finnish College student by the name of [Linus Torvalds]("http://en.wikipedia.org/wiki/Linus_Torvalds") was attending the University of Helsinki and used Minix on his own personal system.  There were a few quirks with the system that he wanted to fix and he eventually started his own OS called [Linux]("http://en.wikipedia.org/wiki/Linux").  He developed to OS not only to fix his problems with Minix but also to help him learn the 386 architecture which was very new at the time.  Linux was also going to be a [monolithic kernel]("http://en.wikipedia.org/wiki/Monolithic_kernel") which was easier for him to develop.  

Torvalds was aware of the GNU project and believed that HURD would be the dominating kernel but nevertheless he released his kernel along with some GNU applications.  He originally wanted to call it Freax (because it was free) but when he uploaded to FTP, the server admin instead chose the name Linux (Linus with an 'x' as is tradition in the name of UNIX-like systems) which Torvalds decided to stick to.

Okay so, here is the situation.  The HURD is in development and people were becoming impatient, BSD was in legal trouble and no programmers wanted to risk ending up as part of the lawsuit and Minix was too restrictive to be considered free software.  Linux was the obvious choice among the bunch.  It was more immature than the others but as developers joined the project, it grew fast.  The GNU system was still popular even though the kernel for it wasn't finished so people began combining Linux with GNU to create a complete usable OS.  Some people began calling the entire system Linux but many in the FSF didn't like the name because Linux was just a kernel and they had written much of the software needed for an OS which ran on Linux.  Stallman proposed that the system instead be called GNU/Linux to signify this and the HURD became known as GNU/HURD to show that GNU could run on multiple kernels.

Torvalds was just a kernel developer and didn't do much with GNU directly.  Users were basically on their own to figure it out.  The idea of distributions or "distros" began to develop and [Debian]("http://en.wikipedia.org/wiki/Debian") was one which had formed, named after the developer Ian and his wife Debra (Debra + Ian = Debian).  The distro managers helped ease the process by combining GNU and Linux into a complete system and providing an installer as well as some other basic packages.

Development on Linux continued and fast forward to 2007 we now have easy to use distros like [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_Linux") which are extremely easy to use and are very full featured.  Stallman is still a long haired hippie and Torvalds now has a wife and three young daughters and is currently living in Portland Oregon.

---

### Post by tgalati4 on 2007-08-08
There's an awesome poster out there that shows the Linux family tree, including the re-entrant branches.  I don't have the link handy, but it's cool.

---

### Post by SunnyRabbiera on 2007-08-08
No actually Linux and BSD were created by elves, everyone knows that :P

---

### Post by WishingWell on 2007-08-08
It should be noted that the first Linux distribution was Slackware and it's not correct that BSD had legal trouble at the time when Linux was put together with GNU, the real reason was that Richard didn't like the BSD licence and talked Linus into using his version of a "free" licence.

---

### Post by jrusso2 on 2007-08-08
> **WishingWell said:**
> It should be noted that the first Linux distribution was Slackware and it's not correct that BSD had legal trouble at the time when Linux was put together with GNU, the real reason was that Richard didn't like the BSD licence and talked Linus into using his version of a "free" licence.

I believe SLS was first

---

### Post by WishingWell on 2007-08-08
> **jrusso2 said:**
> I believe SLS was first

Actually, i believe there was some Swedish distro before that, but the first distro that could actually do more than boot was Slackware, it's from 1993 and the oldest distro still out there.

I don't think the distros before it would even compile GNU software.

---

### Post by dfreer on 2007-08-08
[https://netfiles.uiuc.edu/rhasan/linux/](https://netfiles.uiuc.edu/rhasan/linux/)
Isn't a bad read, although I can't confirm accuracy at all.

> **SunnyRabbiera said:**
> No actually Linux and BSD were created by elves, everyone knows that :P

Actually, linux was a gift to men from the almighty Tux, who was created by the FSM to govern mankind by secretly observing our actions from desktop wallpapers around the interweb.

In short, Tux watches you while you surf pr0n 0.o

---

### Post by bonzodog on 2007-08-08
The first 3 linux distros (sometimes still referred to as 'root distros') were SLS, Debian, and Redhat. Debian and Redhat shared the commonality of using the System V unix init system and some of its processes, whereas Patrick Volkerding, who started SLS (Soft Landing Systems), decided that the BSD Unix way was faster and cleaner.SLS was later renamed to Slackware, which for some reason got to version 4, then skipped straight to version 7.

---

### Post by tbroderick on 2007-08-08
> **bonzodog said:**
> The first 3 linux distros (sometimes still referred to as 'root distros') were SLS, Debian, and Redhat. Debian and Redhat shared the commonality of using the System V unix init system and some of its processes, whereas Patrick Volkerding, who started SLS (Soft Landing Systems), decided that the BSD Unix way was faster and cleaner.SLS was later renamed to Slackware, which for some reason got to version 4, then skipped straight to version 7.


SLS, Debian and Red Hat were not the first three distros. Peter MacDonald founded SLS not Patrick Volkerding. Patrick Volkerding started Slackware which was initially based off SLS. SLS was not renamed to Slackware.

---

### Post by WishingWell on 2007-08-08
> **bonzodog said:**
> The first 3 linux distros (sometimes still referred to as 'root distros') were SLS, Debian, and Redhat. Debian and Redhat shared the commonality of using the System V unix init system and some of its processes, whereas Patrick Volkerding, who started SLS (Soft Landing Systems), decided that the BSD Unix way was faster and cleaner.SLS was later renamed to Slackware, which for some reason got to version 4, then skipped straight to version 7.

There is nothing in that that is correct, SLS wasn't renamed Slackware at all and there are lots of distros from Slackware to Debian and Redhat.

Why do people on this forum know so many things that are just wrong?

You haven't even gotten the part about the init system right, Slackware chose the BSD init because he believed that the BSD's would prevail, not for any other reason, he's said so himself.

---

### Post by WishingWell on 2007-08-08
> **tbroderick said:**
> SLS, Debian and Red Hat were not the first three distros. Peter MacDonald founded SLS not Patrick Volkerding. Patrick Volkerding started Slackware which was initially based off SLS. SLS was not renamed to Slackware.

Thank you.

---

### Post by Hex_Mandos on 2007-08-08
Ygrassil?

---

### Post by WishingWell on 2007-08-08
> **Hex_Mandos said:**
> Ygrassil?

Yup, that was what i was looking for before.

---

### Post by jiminycricket on 2007-08-08
Some info on BSD history: [Open Sources: Voices from the Open Source Revolution    Twenty Years of Berkeley Unix    From AT&T-Owned to Freely Redistributable       by    Marshall Kirk McKusick](http://www.oreilly.com/catalog/opensources/book/kirkmck.html)

Also, Groklaw has a good book on UNIX/Linux/GNU/BSD history by Peter H Salus.  You can probably buy it as a physical book somewhere, too.  It's under a creativ commons no derivs license, but maybe you can include it in your document?

[The Daemon, the GNU & the Penguin ~ by Dr. Peter Salus on Groklaw]("http://www.groklaw.net/staticpages/index.php?page=20051013231901859")

---

### Post by Turboaaa2001 on 2007-08-08
Ok, first I want to say that I asked here first before looking it up because of the debates that I knew would happen.

Google and Wiki is the next step in the search, but I wanted to here from the actual people who have been around the block a few times. I also plan on using quotes from this thread (after asking for permision from the writer of course)

Right now I have a few posts that are conflicting with each other. I will be using this to hunt down the facts.  I have some vacation time comming up that I hopw to dedicate to this project.

Again any help would be appreciated. If you have something specific to say about the history of Linux and where you think it will lead, then please give you input!

This "paper" is based on facts only and not my own feelings or opinions (as history is sometimes distorted).

---

### Post by WishingWell on 2007-08-09
> **Turboaaa2001 said:**
> Ok, first I want to say that I asked here first before looking it up because of the debates that I knew would happen.

Google and Wiki is the next step in the search, but I wanted to here from the actual people who have been around the block a few times. I also plan on using quotes from this thread (after asking for permision from the writer of course)

Right now I have a few posts that are conflicting with each other. I will be using this to hunt down the facts.  I have some vacation time comming up that I hopw to dedicate to this project.

Again any help would be appreciated. If you have something specific to say about the history of Linux and where you think it will lead, then please give you input!

This "paper" is based on facts only and not my own feelings or opinions (as history is sometimes distorted).

This is what i hate about this forum, people will comment no matter if they know or not.

You should have hunted down the facts before you posted, that is the point, let me make this a bit easier, BSD became FreeBSD, forked to NetBSD forked to OpenBSD, that is all the BSD history you'll need, for Linux there was a local Swedish version, and then there was SLS, which both were not even capable of compiling software (it might have changed when i left it for BSD) but Slackware is the key to the first real distribution that you could use and compile your own software on, this is 1993.

Since then a whole heap of commercial and none commercial distros have arrived, don't fool yourself, Canonical wants a piece of the pie just like everyone else, this isn't out of the goodness of their hearts, if you think it is, well... LOL at you i guess.

There are projects like Slackware and FreeBSD that have stood their ground without involving a big company name to steer the development.

But they are rare, i just scoff at Ubuntu being referred to as free these days, they implemented a piece of code that while it is in itself free it is tied to non free software and the user isn't even made aware of it, that sound worse than WGA to me because the user is forced to confirm there while on Ubuntu, they just sneak it over.

I trust Canonical less than Microsoft for that very reason, at least they are honest about it.

---

### Post by Turboaaa2001 on 2007-08-09
Your description is too dry. I'm writing an in deph history for my own benefit. You gave me so little to work with...

The other thing is that I know so little about the history I don't know where to start. Thats why I posted here to

1. Get people like you to through random non-sense into the works.
2. Compare what people have said.
3. Discover what people say here is either true or false by using Google, Wiki, and contacting the actual IP owners (that last one is taken with a grain of salt)

Another thing is that I do not completely trust Wiki because it's created by the general public, and I never take anything at face value....

---

### Post by KiwiNZ on 2007-08-09
Try these links below
 
[http://static.userland.com/userLandDiscussArchive/msg019844.html](http://static.userland.com/userLandDiscussArchive/msg019844.html)
 
[http://www.netaction.org/opensrc/future/](http://www.netaction.org/opensrc/future/)
 
[http://www.netc.org/openoptions/background/history.html](http://www.netc.org/openoptions/background/history.html)

---

