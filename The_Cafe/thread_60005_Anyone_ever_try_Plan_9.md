---
title: "Anyone ever try Plan 9?"
date: 2005-08-26
forum: The Cafe
---

### Post by rolfotto on 2005-08-26
If you don't know what Plan 9 is:
[http://www.cs.bell-labs.com/plan9dist/](http://www.cs.bell-labs.com/plan9dist/)

It's a kernel started by some of the original authors of Unix and it's an attempt at a better system - similiar to unix but aimed to fix Unix's problems that were too deeply ingrained in Unix itself (and the original design philosophy) to hope to fix it on that platform.  An attempt to remove the crud and start from scratch.

Even though it can run Unix (or Posix) compliant software, at it's core it has it's own compilers and what not.  It also attempts to speak to everything in a single language, 9P, and it tries to treat everything as a local resource, whether it's on your computer or on a network.

To my understanding, since 2000 it was given away as a free and open software...... but the problem is that there seems to be no real interest outside it's hardcore following (sortof like BeOS or OS/2)

Anyway, it sounds great on paper..... but the proof is in the pudding.

I'd like to try it - after all, Unix was the successor to Multics and the C language was the successor to the B language...... so it's not too far out that Unix might get too old someday and a better underlying kernel system and philosophy might take hold.

Linus and others already took some (but not all) features of Plan 9 and put it in the Linux kernel..... who knows, maybe a future kernel might be fashioned after Plan 9 instead of Unix :)  But I suspect that the change might be to radical with some of the existing software.

Anyway, anyone have some actual experience with it?  Since I'm done with my experimenting with Linux Distros for now, I'd like to play around with it.

---

### Post by endy on 2005-08-26
[QUOTE=rolfotto]
<SNIP>
Linus and others already took some (but not all) features of Plan 9 and put it in the Linux kernel..... who knows, maybe a future kernel might be fashioned after Plan 9 instead of Unix :)  But I suspect that the change might be to radical with some of the existing software.

Anyway, anyone have some actual experience with it?  Since I'm done with my experimenting with Linux Distros for now, I'd like to play around with it.[/QUOTE]

Interesting stuff but I think it's fair to say that [Hurd](http://en.wikipedia.org/wiki/Hurd) is likely to be the next big thing to superseed Linux (the kernel that is).

Anyway, I've not experimented with Plan9 but it does sound interesting, last thing I tried to get going was a [L4 microkernel](http://en.wikipedia.org/wiki/L4_microkernel_family), but alas I couldn't get the demo disks to boot on my hardware.. perhaps time for another go :)

---

### Post by Juergen on 2005-08-26
There's also [Inferno](http://www.vitanuova.com/products.html), the successor of plan 9
This thing can run as full OS **or** as virtual OS on top of Linux, Windows or even Plan 9.

---

### Post by BWF89 on 2005-08-26
[QUOTE=endy]Interesting stuff but I think it's fair to say that [Hurd](http://en.wikipedia.org/wiki/Hurd) is likely to be the next big thing to superseed Linux (the kernel that is).[/QUOTE]
But hardly anyone works on the HURD anymore and theres hundreds of people working on the Linux Kernal.

---

### Post by slux on 2005-08-26
I doubt Hurd is really going to make many people switch even if it becomes mature at some point in the unforeseeable future. Of course, changes in computer hardware might some day make it more appealing.

I'd like to try Plan 9 as well although I understand it's very much a research OS.

UNIX certainly isn't perfect but the overall experience is very positive. It's well-defined, very portable and today has a large software base. I don't see it going away in a long, long time. After all, Linux is just getting started and even OS X chose it as the underlying architecture. :) And using a modern GNU/Linux distribution is considerably different compared to using an old school UNIX like Solaris or even *BSD.

Be sure to try BeOS if you want to see something really different that could actually be used daily on the desktop. It'll also make you appreciate the huge amount of software available for GNU/Linux today. :) BeOS R5 can be downloaded for no fee and you can buy Zeta for a commercial and updated version. Then there's the free version called Haiku that is beginning to look good but still in early phase of development.

ReactOS is a bit of fun and SkyOS has looked interesting in screenshots but I haven't been interested enough to shell out the money to become part of the beta program. :)

There's some interesting stuff among the various Linux distros as well, SymphonyOS, GoboLinux and Foresight all are worth checking out.

---

### Post by Kvark on 2005-08-26
Makes me wonder... If another kernel like Plan 9 or Hurd would replace Linux one day... Would all the linux distros, linux communities, linux programs linux [whatever] be renamed to hurd [whatever], that'd be a lot of hassle just for a kernel change... Or would it all still be called Linux despite that it doesn't run on the Linux kernel anymore?

---

### Post by macgyver2 on 2005-08-26
[QUOTE=Juergen]There's also [Inferno]("http://www.vitanuova.com/products.html"), the successor of plan 9
This thing can run as full OS **or** as virtual OS on top of Linux, Windows or even Plan 9.[/QUOTE]
Cool, I'm gonna have to take a look at this.  Something to play around with.  Thanks.

---

### Post by endy on 2005-08-26
[QUOTE=slux]
<SNIP>
I don't see it going away in a long, long time. After all, Linux is just getting started and even OS X chose it as the underlying architecture. :)[/QUOTE]

Erm, I think I'm right in saying Mac OS X doesnt' have any Linux in it. It uses a modified Mach Microkernel and the open source Darwin environment which is based on BSD. Then Apple's proprietary GUI Aqua runs on top so no Linux there :)

Kvark, IIRC HURD aims to be fully compatible with current Linux apps to make the change over as easy as possible.

This is all going from what I've read, I'm no kernel expert :)

---

### Post by kanem on 2005-08-26
[QUOTE=Kvark]Makes me wonder... If another kernel like Plan 9 or Hurd would replace Linux one day... Would all the linux distros, linux communities, linux programs linux [whatever] be renamed to hurd [whatever], that'd be a lot of hassle just for a kernel change... Or would it all still be called Linux despite that it doesn't run on the Linux kernel anymore?[/QUOTE]That brings to light why it's innapropriate to call these operating systems 'Linux' and the programs 'Linux programs'. Linux is only the kernel, and it's easier to replace than the GNU software. You could do it today by just switching to BSD. 

Debian's full distro name is Debian GNU/Linux. They are working on Hurd which is called [Debian GNU/Hurd](http://www.debian.org/ports/hurd/).

---

### Post by poofyhairguy on 2005-08-26
[QUOTE=kanem]That brings to light why it's innapropriate to call these operating systems 'Linux' and the programs 'Linux programs'. Linux is only the kernel, and it's easier to replace than the GNU software. [/QUOTE]

Instead of calling Ubuntu "A linux OS" I often call it "a GNU OS." Gnu just isn't used enough I think.

---

### Post by Brunellus on 2005-08-26
[QUOTE=poofyhairguy]Instead of calling Ubuntu "A linux OS" I often call it "a GNU OS." Gnu just isn't used enough I think.[/QUOTE]
 because people assocaite GNU with frothing-at-the-mouth, unshaven, foul-smelling, ill-mannered street-preaching Stallmanites.  What's a gnu, anyway?  An African ungulate?  yuck!

Linux is a penguin, a kid-philosopher with a security blanket, an affable Finnish hacker.  What's not to love?

---

### Post by drizek on 2005-08-26
[QUOTE=poofyhairguy]Instead of calling Ubuntu "A linux OS" I often call it "a GNU OS." Gnu just isn't used enough I think.[/QUOTE]

thats because gnu sounds stupid. 

we need a new name.

---

### Post by slux on 2005-08-27
Well, then people should realize that appearances aren't everything and that RMS is one of the great philosophers of our time, who may be remembered long after the Linux kernel has been switched to something different.

They should also remember what kind of sacrifices it takes to devote one's life to an ideal and that had it not been for Stallman over twenty years ago, we might well not have Linux today. (It could have existed for a while as something proprietary and quickly faded).

---

### Post by Brunellus on 2005-08-27
[QUOTE=slux]Well, then people should realize that appearances aren't everything and that RMS is one of the great philosophers of our time, who may be remembered long after the Linux kernel has been switched to something different.

They should also remember what kind of sacrifices it takes to devote one's life to an ideal and that had it not been for Stallman over twenty years ago, we might well not have Linux today. (It could have existed for a while as something proprietary and quickly faded).[/QUOTE]
 ...which proves my point exactly.  You've spoken of RMS in tones that recall Korean Workers' Party functionaries' glowing descriptions of Kim Il Sung.

None of which endears us to 'normal people' who are usually not swayed by appeals to the thought of the "greatest philosophers of our time,' or the stories that upon the birth of the Great Leader, flowers bloomed on Mount Paektu in midwinter.

---

### Post by kanem on 2005-08-27
This is pretty cool. Debian just released a live cd of their [GNU/kFreeBSD](http://www.us.debian.org/ports/kfreebsd-gnu/) distribution. So a FreeBSD kernel with all the goodnes of apt-get and thousands of apps. I never knew they had a distro based around BSD.

---

### Post by gaffurabi on 2009-02-13
Plan 9 still didnt turn out to be very popular. wonder why it cannot be widely adopted ?

---

### Post by cmay on 2009-02-13
i have never been able to get it installed. i did not even get to a livecd enviroment but i tried many times. i would like to see what it was like. i read all about there was on the home page and i tink it looks interesting same as minix does. difference is that i have used minix on a older computer of mine for study while reading the book. which i will do sometime soon again. same time i wanted to try this new and improved unix version as the home page states  its aiming to be. i really would like to have been able to play with it for some time but it could not be done. but minix is also good for a minimal unix like experimenting enviroment and much better documented.

---

### Post by Grant A. on 2009-02-13
To clear up what I'm seeing in this thread:

We are using the GNU Operating System, Linux is just the kernel it uses, and the portability of GNU has shown that Linux is very disposable.

---

### Post by yarikos on 2010-06-27
> **gaffurabi said:**
> Plan 9 still didnt turn out to be very popular. wonder why it cannot be widely adopted ?

I believe that's because it does things in unpopular ways. Modern programmers are bound to Java/C++/DLLs/RPCs - the technologies which shall never find its way into Plan 9 world - and do not bother to learn to think different. Modern users expect a GUI with titlebars, 3D buttons, taskbars and drop menus - and refuse to pick the idea behind rio and acme. Maybe it is better because Plan 9 ways are very addictive: once you're on, you are lost to the *NIX world...

---

### Post by yarikos on 2010-06-27
> **Juergen said:**
> There's also [Inferno](http://www.vitanuova.com/products.html), the successor of plan 9
This thing can run as full OS **or** as virtual OS on top of Linux, Windows or even Plan 9.

I wouldn't threat Inferno as a successor of Plan 9 but rather its descendant, derivative.
Despite appearing similar at a first look, deeper study shows how different they are.

As a side note, there are 9vx project which makes Plan 9 kernel to run in user mode hosted on a *NIX OS, just like Inferno does.

---

