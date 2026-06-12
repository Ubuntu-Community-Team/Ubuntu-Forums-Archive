---
title: "Is my view of GNU/Linux not being Unix right?"
date: 2008-10-15
forum: The Cafe
---

### Post by HungryMan on 2008-10-15
I know GNU means GNU Not Unix, so apparently it isn't Unix. Linus Torvalds also wrote the Linux kernel to sort of replace Unix, when AT&T and UC Berkeley were having disputes about it. But since it functions like Unix, it is often misappropriately labeled a unix derivative. And, to quote Jaime Hyneman (replacing salami with Unix); "It may look like Unix. It may smell like Unix. It may even taste like Unix. But it's not!"
So, am I right believing that GNU/Linux was never Unix in the first place, and never will be; and even if it functions like Unix and runs Unix programs it is not Unix (or a Unix derivative)? Or am i missing the whole picture by a long shot?

By the way, to straighten things out (as I know you may think that I've answered my own question). The question is not "Is Linux Unix (or a Unix derivative)?. I'm just not satisfied being told that GNU/Linux is not Unix, I need to know exactly why.

Thanks for clearing things out for me in advance!

---

### Post by SunnyRabbiera on 2008-10-15
Linux is unix like, a more "true" unix would be BSD.

---

### Post by LaRoza on 2008-10-15
> **HungryMan said:**
> I know GNU means GNU Not Unix, so apparently it isn't Unix. 

Back then, Unix was an actual operating system.

> 
Linus Torvalds also wrote the Linux kernel to sort of replace Unix, when AT&T and UC Berkeley were having disputes about it. But since it functions like Unix, it is often misappropriately labeled a unix derivative.
It is Unix like.

> 
So, am I right believing that GNU/Linux was never Unix in the first place, and never will be; and even if it functions like Unix and runs Unix programs it is not Unix (or a Unix derivative)? Or am i missing the whole picture by a long shot?

One could get it certified, like Apple did with OS X: [http://en.wikipedia.org/wiki/Single_UNIX_Specification](http://en.wikipedia.org/wiki/Single_UNIX_Specification)

> 
By the way, to straighten things out (as I know you may think that I've answered my own question). The question is not "Is Linux Unix (or a Unix derivative)?. I'm just not satisfied being told that GNU/Linux is not Unix, I need to know exactly why.


Back in the day, there were proprietary Unix systems, and an OS used for learning, Minix. Minix shared no Unix code, but was Unix like. It had a restricted license, although you could get the source (it was an OS to learn about OS's). Linus made Linux based on Minix, but not using any Minix code. GNU lacked a good kernel, so all the GNU utils and applications were put on Linux and there was a functional operating system.

---

### Post by LaRoza on 2008-10-15
> **SunnyRabbiera said:**
> Linux is unix like, a more "true" unix would be BSD.

BSD is Unix like. 

The only distinguishing feature between Unix like and Unix is being certified.

---

### Post by SunnyRabbiera on 2008-10-15
> **LaRoza said:**
> BSD is Unix like. 

The only distinguishing feature between Unix like and Unix is being certified.

yes though BSD is more tied into the original Unix bloodline then Linux.

---

### Post by samjh on 2008-10-15
> **HungryMan said:**
> I know GNU means GNU Not Unix, so apparently it isn't Unix. Linus Torvalds also wrote the Linux kernel to sort of replace Unix, when AT&T and UC Berkeley were having disputes about it. But since it functions like Unix, it is often misappropriately labeled a unix derivative. And, to quote Jaime Hyneman (replacing salami with Unix); "It may look like Unix. It may smell like Unix. It may even taste like Unix. But it's not!"
So, am I right believing that GNU/Linux was never Unix in the first place, and never will be; and even if it functions like Unix and runs Unix programs it is not Unix (or a Unix derivative)? Or am i missing the whole picture by a long shot?

Linus developed Linux as a experiment to learn about how operating systems work.  At the time, MINIX (developed by Prof. A Tannenbaum) was developed for such a purpose, but it was non-free.  So Linus set about making his own, free operating system for learning.

MINIX takes a lot from UNIX, but it is not UNIX.  MINIX is described as "UNIX-like" (it was compatible with Version 7 Unix to a large degree).  Likewise, Linux is also UNIX-like.

GNU was a separate entity to the whole Linux effort.  GNU was the name for its own operating system kernel, called "Hurd".  But Hurd failed to attract enough developers and it was pretty much a pipe-dream.  Seeing how Linux was progressing, GNU jumped on the Linux bandwagon, with GNU developers and Linus porting GNU libraries and tools over to Linux.  This is why some people demand Linux to be called, GNU/Linux.

"GNU is Not Unix", has nothing to do with Linux.  It refers to Hurd. :)

So in summary, Linux is not UNIX.  But like Hurd and MINIX, Linux derives its designs and ideas from UNIX, and is UNIX-like.

---

### Post by jespdj on 2008-10-15
Linux was written completely from scratch, not based on the original Unix source code, so therefore Linux is not Unix.

See [Wikipedia about Unix](http://en.wikipedia.org/wiki/Unix), it contains a chart of the lineage of Unix and many Unix-derived or Unix-like operating systems.

Also see [http://en.wikipedia.org/wiki/Unix-like](http://en.wikipedia.org/wiki/Unix-like)

---

### Post by LaRoza on 2008-10-15
> **samjh said:**
> GNU was a separate entity to the whole Linux effort.  GNU was the name for its own operating system kernel, called "Hurd".  But Hurd failed to attract enough developers and it was pretty much a pipe-dream.
I don't know. I tried it out (Debain with Hurd) and I installed it. It wouldn't boot, but that is beside the point.

> 
Seeing how Linux was progressing, GNU jumped on the Linux bandwagon, with GNU developers and Linus porting GNU libraries and tools over to Linux.  This is why some people demand Linux to be called, GNU/Linux.


Linux was also made with gcc, probably the most important piece of software.

---

### Post by Half-Left on 2008-10-15
Linux is a clone of Unix but like said, written from scratch.

---

### Post by samjh on 2008-10-15
> **LaRoza said:**
> I don't know. I tried it out (Debain with Hurd) and I installed it. It wouldn't boot, but that is beside the point.Hurd has progressed since the early-90s, which was the time frame I was referring to.  However Hurd is still not mature.

---

### Post by LaRoza on 2008-10-15
> **samjh said:**
> Hurd has progressed since the early-90s, which was the time frame I was referring to.  However Hurd is still not mature.

I know. I was joking about it.

---

### Post by civillian on 2008-10-15
You can use debian with hurd (and it's reasonable, as far as it goes!) right now (if you REALLY want!

---

### Post by HungryMan on 2008-10-15
So I was right!
So is it more appropriate of GNU/Linux to be called a Unix clone because:
a.) It has no code from Unix?
b.) Was never Unix in the first place?
c.) Behaves like Unix, but is in no way, Unix?

I understand it clearly now, GNU/Linux was written to act like Unix, but was not based off (code-wise) it.
So GNU/Linux is like a Tiger trained to look and behave like a Lion (No reference to OS X...seriously. I did not write this as a joke.). The Tiger was never a Lion in the first place, but is very similar that people would generally still call it a Lion.

---

### Post by igknighted on 2008-10-15
> **HungryMan said:**
> So I was right!
So is it more appropriate of GNU/Linux to be called a Unix clone because:
a.) It has no code from Unix?
b.) Was never Unix in the first place?
c.) Behaves like Unix, but is in no way, Unix?

I understand it clearly now, GNU/Linux was written to act like Unix, but was not based off (code-wise) it.
So GNU/Linux is like a Tiger trained to look and behave like a Lion (No reference to OS X...seriously. I did not write this as a joke.). The Tiger was never a Lion in the first place, but is very similar that people would generally still call it a Lion.

Yes... but no.

You are 100% right based off of the definition of UNIX circa 1990.  But now UNIX is merely a certification of adherence to standards, the actual code used is rather trivial.  Linux could be certified UNIX very easily if any of the major corporate backers sought certification as UNIX (Novell, Oracle, etc.).  So it is not UNIX (90's) for sure, but it is not UNIX by todays definition because no one has bothered to get it certified.

---

### Post by LaRoza on 2008-10-15
> **HungryMan said:**
> So I was right!
So is it more appropriate of GNU/Linux to be called a Unix clone because:
a.) It has no code from Unix?

No. Even if it had code from Unix, to be called Unix it would have to be certified.

> 
b.) Was never Unix in the first place?

Right.

> 
c.) Behaves like Unix, but is in no way, Unix?

No. Unix is a certification. Linux may be compliant with the specifications, but without being certified, it cannot be a Unix. 

> 
So GNU/Linux is like a Tiger trained to look and behave like a Lion (No reference to OS X...seriously. I did not write this as a joke.). The Tiger was never a Lion in the first place, but is very similar that people would generally still call it a Lion.
No. It is more like IBM clones. IBM made their agreements foolishly. Compaq was able to legally make a clone of the IBM system, release their specs (not IBM's, but Compaq's) and this caused IBM's market share to fall. IBM's OS (MS-DOS) ran on the clones and the clones were cheaper and anyone could make them. This caused the clones to be more popular than the original and they swept the market, as they all were compatible and used the same OS (MS-DOS). The fact that other systems were out (Mac's and various Unix's) and were better, didn't matter if they couldn't be widespread.

Linux is like the IBM clones. It is a free portable clone of a system and it has ofter taken the market because of this.

---

### Post by HungryMan on 2008-10-15
> No. It is more like IBM clones. IBM made their agreements foolishly. Compaq was able to legally make a clone of the IBM system, release their specs (not IBM's, but Compaq's) and this caused IBM's market share to fall. IBM's OS (MS-DOS) ran on the clones and the clones were cheaper and anyone could make them. This caused the clones to be more popular than the original and they swept the market, as they all were compatible and used the same OS (MS-DOS). The fact that other systems were out (Mac's and various Unix's) and were better, didn't matter if they couldn't be widespread.

Linux is like the IBM clones. It is a free portable clone of a system and it has ofter taken the market because of this..

Can you please elaborate on this, I really don't understand the analogy. Thanks.

---

### Post by LaRoza on 2008-10-15
> **HungryMan said:**
> Can you please elaborate on this, I really don't understand the analogy. Thanks.

IBM made PC's, and shipped them with MS-DOS. Apple made Macs and shipped them with Mac OS.

IBM's computers where theirs. No one could use copy their designs without violating laws. Specifically, the BIOS code. Everything else could be bought (processors and other hardware). However, using [Clean room design reverse engineering](http://en.wikipedia.org/wiki/Clean_room_design) a clone of IBM PC's became possible: [http://en.wikipedia.org/wiki/IBM_PC_compatible#Origins](http://en.wikipedia.org/wiki/IBM_PC_compatible#Origins)

These clones didn't restrict or require licensing to use. So, they were able to legally get a clone of a closed system (the IBM BIOS) and then release it for free without violating any rules. Now anyone could make an IBM compatible computer. Apple was popular back then, yet quickly fell behind because only Apple could make Apple computers and Apple's OS didn't run on other systems (still doesn't, but not because of technical reasons). 

Apple could have allowed other people to make computers for their OS, but they didn't. 

Same with Linux and Minix. Unix wasn't free to copy, so Minix was made to be like it, yet not copy the code. The result was a clone of Unix. Linux did the same with Minix. 

I guess you could say it is like looking at something, like a building, and then making one just like it without copying the original design plans. Of course, there are interior differences, but it works and acts the same way.

---

### Post by HungryMan on 2008-10-15
Many thanks for clarifying that LaRoza. The Lion-Tiger analogy was really off.
On a side note, I did further reading on the topic and it turns out that OS X is certified Unix-compliant, though it seems that none of the BSD's and GNU/Linuxes are. Though that doesn't seem to matter though as "GNU is not Unix" and it seems that the Windows family theoretically can be Unix-compliant too. Anyway, I don't see the connection of Unix-compliance and the quality of the OS (correct me if I'm wrong though).

---

### Post by samjh on 2008-10-15
> **HungryMan said:**
> On a side note, I did further reading on the topic and it turns out that OS X is certified Unix-compliant, though it seems that none of the BSD's and GNU/Linuxes are. Though that doesn't seem to matter though as "GNU is not Unix" and it seems that the Windows family theoretically can be Unix-compliant too. Anyway, I don't see the connection of Unix-compliance and the quality of the OS (correct me if I'm wrong though).

There is a thing called the Single Unix Specification (SUS), which is used to certify whether an operating system is "Unix".

Certification costs money.  In the case of SUS, it's in the order of tens of thousands of dollars per year.  So it's really just far too expensive for free projects like BSD and Linux.

SUS is heavily derived from the POSIX standards.  Both BSD and Linux have very good compliance with POSIX.  BSD has their own standards-conformance effort, and Linux has the Linux Standard Base, which aims for maximum POSIX compliance and is very closely compliant with SUS as well.

It's good for BSD and Linux to be compatible with Unix, but it's not absolutely essential.  It's certainly not a measure of quality of either BSD or Linux projects.  The most important thing in my opinion is for the operating systems to be compatible enough so that software written for one can be relatively easily ported to another, which is already the case anyway.

---

### Post by forrestcupp on 2008-10-15
> **samjh said:**
> 
SUS is heavily derived from the POSIX standards.  Both BSD and Linux have very good compliance with POSIX.I'm glad someone brought up POSIX standards.

A lot of people understand the Unix certification, but they're too young to remember the actual Unix OS of old.  I think one of the best examples of a modern descendant of the Unix OS would be Solaris by Sun Microsystems.  

For a very long time, Unix wouldn't run on an x86 system.  I remember even in the early 90's when you had to buy a SPARC system to run a Unix OS.  It was *very* expensive to have a Unix box.  That's one big reason Linus created Linux.  It was to be able to run a Unix-like system on an x86 computer on a college student's budget.

---

### Post by az on 2008-10-15
> **samjh said:**
> 
"GNU is Not Unix", has nothing to do with Linux.  It refers to Hurd. :)


No.  The Hurd is a kernel for the GNU operating system.  The Hurd was never as popular as the Linux kernel and so the overwhelming majority of GNU operating systems run the Linux kernel.  But the Hurd, like the Linux kernel is not the operating system.  It's just the kernel.

For example, Ubuntu is a GNU operating system that runs the linux kernel.  There are other ways to run GNU without either a Linux or Hurd kernel:
[http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)

or run

apt-cache show crosshurd


"Gnu is not Unix" refers to the Unix operating system's proprietary nature.  In this phrase Unix is synonymous with "proprietary".

The phrase is meant to celebrate the fact that you are running a free/libre Unix clone.  It's like saying "GNU is like Unix but without being proprietary like Unix."


No, it's not clear, but what do you expect from a self-referential description?

---

### Post by kinematic on 2008-10-15
> **samjh said:**
> GNU was a separate entity to the whole Linux effort.  GNU was the name for its own operating system kernel, called "Hurd".  But Hurd failed to attract enough developers and it was pretty much a pipe-dream.  Seeing how Linux was progressing, GNU jumped on the Linux bandwagon, with GNU developers and Linus porting GNU libraries and tools over to Linux.  This is why some people demand Linux to be called, GNU/Linux.

GNU is an operating system. not another name for the hurd kernel and
the Linux kernel was ported to the GNU operating system, not the other way around.

---

### Post by koenn on 2008-10-15
> **kinematic said:**
> [QUOTE=samjh;5968829]....Seeing how Linux was progressing, GNU jumped on the Linux bandwagon, with GNU developers and Linus porting GNU libraries and tools over to Linux.  This is why some people demand Linux to be called, GNU/Linux.
the Linux kernel was ported to the GNU operating system, not the other way around.[/QUOTE]
+1
As Laroza said, the GNU utilities such as GNU C Compiler where used to create the Linux kernel. Then the Linux kernel -, gnu utilities and other basic programs created by the GNU project,  were bundled to form a rudimentary Linux operating system. The creators of all that GNU software would have preferred that OS  being called a  GNU/Linux operating system

basically, without GNU, it would have been extremely hard both for Linus to create Linux, and for the Linux kernel to evolve in a full OS.

---

### Post by LaRoza on 2008-10-15
> **kinematic said:**
> GNU is an operating system. not another name for the hurd kernel and
the Linux kernel was ported to the GNU operating system, not the other way around.

And to complicate matters, Hurd isn't a kernel. It is a kernel (like the Mach kernel) and a bunch of servers.

---

### Post by david_lynch on 2008-10-15
> **LaRoza said:**
> 
Back in the day, there were proprietary Unix systems, and an OS used for learning, Minix. Minix shared no Unix code, but was Unix like. It had a restricted license, although you could get the source (it was an OS to learn about OS's). Linus made Linux based on Minix, but not using any Minix code. GNU lacked a good kernel, so all the GNU utils and applications were put on Linux and there was a functional operating system.
Linus was inspired by minix, but linux was never based on minix in any way, shape or form. In fact, it was so radically different from minix that there was a famous flame war between linus and the creator of minix, professor tannenbaum. 

Linux was based on the book "The Design of the Unix Operating System" by Maurice J Bach, but Linus did temporarily use a minix file system in the first weeks of his experiment. The minix fs was discarded very quickly and replaced by extfs and xiafs.

---

### Post by az on 2008-10-15
> **koenn said:**
> 
basically, without GNU, it would have been extremely hard both for Linus to create Linux, and for the Linux kernel to evolve in a full OS.

The linux kernel did not evolve into a full OS.  The full OS is GNU.  You can run Xorg, Gnome, Openoffice on a GNU system without using the linux kernel.

Nexenta is another example of a GNU system (Ubuntu) that uses a Solaris kernel.

[http://www.nexenta.org/os](http://www.nexenta.org/os)

---

### Post by koenn on 2008-10-16
> **az said:**
> The linux kernel did not evolve into a full OS.  The full OS is GNU.  You can run Xorg, Gnome, Openoffice on a GNU system without using the linux kernel.

Nexenta is another example of a GNU system (Ubuntu) that uses a Solaris kernel.

[http://www.nexenta.org/os](http://www.nexenta.org/os)
yeah, I'm aware of all that, but I was just focusing on the the role of the Linux kernel in the whole GNU / Linux thing to counter that "bandwagon" nonsense someone posted -you know, the one I quoted in my post.

---

### Post by Half-Left on 2008-10-16
Ironic that RMS doesn't recommend Ubuntu as a GNU distro or Linux one to use. :)

---

### Post by LaRoza on 2008-10-16
> **Half-Left said:**
> Ironic that RMS doesn't recommend Ubuntu as a GNU distro or Linux one to use. :)

No, Ubuntu isn't completely free, although gNewSense is based on Ubuntu.

---

### Post by HungryMan on 2008-10-22
> **LaRoza said:**
> No, Ubuntu isn't completely free, although gNewSense is based on Ubuntu.

Free in what sense ($$ or liberty)?

---

### Post by Ozor Mox on 2008-10-22
> **HungryMan said:**
> Free in what sense ($$ or liberty)?

As in freedom. GNU only recommends operating systems that not only use free software exclusively, but also that provide no means to install non-free software. That's why Ubuntu, Debian and even Gobuntu are not recommended, but gNewSense is.

---

### Post by HungryMan on 2008-10-23
this is off-topic, but I need to voice my concern about the GPL.
I think the GPL has become restrictive already (i.e. Creative Commons is not compatible with GPL, though there is a CC-GPL), and it's slowly beginning to defeat it's purpose of sharing intellectual property.

Now, I didn't mean to be rude. That's what I think. But if I were in the situation were I were to license my intellectual property, I wouldn't mind to use multiple licenses (my very own SCL,GPL,CC...).

---

### Post by koenn on 2008-10-23
> **HungryMan said:**
> this is off-topic, but I need to voice my concern about the GPL.
I think the GPL has become restrictive already (i.e. Creative Commons is not compatible with GPL, though there is a CC-GPL), and it's slowly beginning to defeat it's purpose of sharing intellectual property.


you're right, it is off-topic.
It's also misinformed : GPL is a software license, while CC explicitely says CC is not intended for software licensing and that you're better of using a license eg from the Free Software Foundation (that would be GPL, then). So compatibility between CC and GPL is a non-issue.
[http://wiki.creativecommons.org/FFAQ#Can_I_license_software_using_CC_licenses.3F](http://wiki.creativecommons.org/FFAQ#Can_I_license_software_using_CC_licenses.3F)

and the purpose of GPL is to ensure that GPL-licensed software and works derived thereof, are and remain free - and that's what the GPL does.

---

### Post by HungryMan on 2008-10-23
> **koenn said:**
> you're right, it is off-topic.
It's also misinformed : GPL is a software license, while CC explicitely says CC is not intended for software licensing and that you're better of using a license eg from the Free Software Foundation (that would be GPL, then). So compatibility between CC and GPL is a non-issue.
[http://wiki.creativecommons.org/FFAQ#Can_I_license_software_using_CC_licenses.3F](http://wiki.creativecommons.org/FFAQ#Can_I_license_software_using_CC_licenses.3F)

and the purpose of GPL is to ensure that GPL-licensed software and works derived thereof, are and remain free - and that's what the GPL does.

Ok, thanks for explaining that to me. (BTW, There's no such thing as CC-GPL, I was wrong, sorry)
But I'm curious, for example I made a game licensed under the GPL, can I use artwork/3d models/music/sound effects/etc... licensed under CC?

[http://www.linux.com/feature/119212](http://www.linux.com/feature/119212) says that the most viable solution to be able to share IP with a wider audience is to multi-license (that's how I understood it at least)

That's my last off-topic post, if I have more questions, I'd gladly discuss it in a more appropriate thread, not one that is apparently about my views of GNU/Linux being right or wrong. :) peace

---

### Post by koenn on 2008-10-23
> **HungryMan said:**
> Ok, thanks for explaining that to me. (BTW, There's no such thing as CC-GPL, I was wrong, sorry)
But I'm curious, for example I made a game licensed under the GPL, can I use artwork/3d models/music/sound effects/etc... licensed under CC?

[http://www.linux.com/feature/119212](http://www.linux.com/feature/119212) says that the most viable solution to be able to share IP with a wider audience is to multi-license (that's how I understood it at least)

That's my last off-topic post, if I have more questions, I'd gladly discuss it in a more appropriate thread, not one that is apparently about my views of GNU/Linux being right or wrong. :) peace
It all depends on what you want. You choose the license according to the rights you want or don't want your users to have. If you're writing software and want to release it under the GPL but your software includes artwork that you don't want GPL'd, then you've created your own problem, right ? And you're free to choose a different license, make up a license that suits your purposes, or separate the artwork from the actual program in such a way that they can be licensed separately. 
The only restriction is that you can not re-license existing GPL'd code. But you're not obliged to use existing GPL'd code, so that is not a real problem.

---

