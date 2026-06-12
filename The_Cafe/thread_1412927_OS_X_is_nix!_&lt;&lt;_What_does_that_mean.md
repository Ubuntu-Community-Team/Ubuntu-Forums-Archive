---
title: "OS X is *nix?! &lt;&lt; What does that mean?"
date: 2010-02-21
forum: The Cafe
---

### Post by makaki on 2010-02-21
Hi guys, I know that OS X is based on Unix or it's *nix or what ever (can't find the prober term). What does that *really* mean? Does is it mean that I can play with it the same as with Linux? I'm just too confused about this idea...What can I do in Linux that I can't with Mac OS X? They are booth unixy...so what's the difference?

1-What's the difference from the end-user point of view?
2-What's the difference from a CS or computer engineer point of view? i.e what would programmers...etc miss from Linux or OS X?

Thanks in advance.

[COLOR=Red]EDIT: I wanted to add this as a comment but I preferred to just append it.[/COLOR]

[COLOR=Navy]OK let's talk about the programmer, developer, cs, engineer...etc

Let's *suppose* this: I'm a C, Ruby and Java programmer, also I'm a web developer & designer and cs student. Add to this that I'm a Linux user for 4 years and used to it. What are the benefits and disadvantage of switching to OS X?

i.e what would someone miss from Linux and hate about OSX? Also what would I find great about OS X that I didn't find in Linux?

I spoke with two professional guys (really professionals and don't ask for the names) and they booth said this: "The programming tools on OS X are  superior to what you have on Linux" What does that mean? What tools are they talking about?!

I also want to quote from one of them this: "[/COLOR]Look at it like this:  of 39 professional Java coders I'm looking at right now, 29 are on Mac systems."
"All 29 of us code in a variety of languages.  The tools on OS X are superior to what you have on Linux."
[COLOR=Navy]
Well I'm really a Java programmer and I only use Vim to code and firefox to browse the Javadoc and API. So what great tools?

I can't use XCode cuz it's an IDE and I use Vim. I don't need cocoa framework cuz I'm not an objective-C programmer....so? What are those great tools?! What's gonna be different to me?[/COLOR]

---

### Post by BarfBag on 2010-02-21
Linux is based off of Unix.  BSD is based off of Unix.  Darwin is based off of BSD.  Mac OS X is based off of Darwin.  There's actually much more to the family tree, but that's basically it in relation to your question.  Mac OS X is, indeed, a Unix-based operating system.

What's the difference from the end-user point of view?

It depends on the kind of end-user.

What's the difference from a CS or computer engineer point of view? i.e what would programmers...etc miss from Linux or OS X?

Perhaps those who are more familiar with BSD could give a better representation, but from what I can gather, Linux has broader hardware support and better package management.

Hope this helps.  :)

---

### Post by Hwæt on 2010-02-21
If you have the source code for a Linux program, you could compile it on a Mac, provided you install the correct dependencies.

Binary wise, no, they are not compatible. Mac's kernel is derived from NeXTSTEP's kernel, which itself was derived from the Mach (this is not a misspelling) kernel and from BSD Unix's kernel. The modern Mac kernel itself does use some code from FreeBSD's kernel, but a lot of it has been rewritten, from what I've heard.

Mac OS X is completely POSIX-complaint and the source code for any given *nix program should run on it. However, most software for the Mac can't be run on Linux in most cases, due to the fact they often use the proprietary cocoa API, which I do not believe Apple has choked up the source code for.

---

### Post by Hwæt on 2010-02-21
> **BarfBag said:**
> Linux is based off of Unix.

Not true. Linux was developed independently, as was its userland, GNU. Hence the name, "GNU's Not Unix". Linux is only Unix-like because it is mostly POSIX-compliant, which means that it follows a set of open guidelines on how it should interact with hardware and software in general.

GNU was made by reverse engineering Unix code, or by the devs guessing how a program worked. It shares no code with the various Unices.

---

### Post by kk0sse54 on 2010-02-21
As far as I know Mac OS X *is* Unix, linux and *BSD is not. Just means that OS X got the unix certification.

Edit: Perhaps I'm wrong and OS X is just certified through the Open Group...

---

### Post by BarfBag on 2010-02-21
> **Hwæt said:**
> Not true. Linux was developed independently, as was its userland, GNU. Hence the name, "GNU's Not Unix". Linux is only Unix-like because it is mostly POSIX-compliant, which means that it follows a set of open guidelines on how it should interact with hardware and software in general.

GNU was made by reverse engineering Unix code, or by the devs guessing how a program worked. It shares no code with the various Unices.

This is interesting.  Thanks.

---

### Post by mickie.kext on 2010-02-21
> **C!oud said:**
> As far as I know Mac OS X *is* Unix, linux and *BSD is not. Just means that OS X got the unix certification.

Edit: Perhaps I'm wrong and OS X is just certified through the Open Group...



Mac OS X is UNIX only by trademark which a joke as it can be bought from [The Open Group]("http://www.opengroup.org/"). The same way Red Hat could buy UNIX trademark and slap it on RHEL. Same could do iXsystems for FreeBSD. It just required to have POSIX compatible OS and enough money, and FreeBSD and Linux are POSIX compatible. The reason why RHEL and FreeBSD officially and legally are not UNIXes is just money.

EIDT: Edi..t

---

### Post by kk0sse54 on 2010-02-21
> **mickie.kext said:**
> Mac OS X is UNIX only by trademark which a joke as it can be bought from [The Open Group]("http://www.opengroup.org/"). The same way Red Hat could buy UNIX trademark and slap it on RHEL. Same could do iXsystems for FreeBSD. It just required to have POSIX compatible OS and enough money, and FreeBSD and Linux are POSIX compatible. The reason why RHEL and FreeBSD officially and legally are not UNIXes is just money.


[http://www.netbsd.org/about/call-it-a-duck.html](http://www.netbsd.org/about/call-it-a-duck.html)

---

### Post by RiceMonster on 2010-02-21
I think Red Hat could probably get RHEL certified if they wanted to, but I don't think anyone cares about getting Linux certified.

---

### Post by schauerlich on 2010-02-21
> **Hwæt said:**
> If you have the source code for a Linux program, you could compile it on a Mac, provided you install the correct dependencies.

Binary wise, no, they are not compatible. Mac's kernel is derived from NeXTSTEP's kernel, which itself was derived from the Mach (this is not a misspelling) kernel and from BSD Unix's kernel. The modern Mac kernel itself does use some code from FreeBSD's kernel, but a lot of it has been rewritten, from what I've heard.

Mac OS X is completely POSIX-complaint and the source code for any given *nix program should run on it. However, most software for the Mac can't be run on Linux in most cases, due to the fact they often use the proprietary cocoa API, which I do not believe Apple has choked up the source code for.

This sums it up pretty well.

MacPorts and Fink both provide repositories for ported Linux and BSD apps. MacPorts is based on the BSD ports system, and Fink uses apt.

---

### Post by mickie.kext on 2010-02-21
> **RiceMonster said:**
> I think Red Hat could probably get RHEL certified if they wanted to, but I don't think anyone cares about getting Linux certified.

Exactly. I did't meant that they do not have money, I just think they have already put money in promoting Linux brand, so they do not want to change brand to UNIX and start over.

---

### Post by dragos240 on 2010-02-21
*nix just means unix-like. Mac OSX uses darwin for it's base operating system, with a shiny GUI on top. Linux is a unix-like system, built originally to replace minux, now most of that code has been completely re-written.

---

### Post by Kenny_Strawn on 2010-02-22
It is Unix-like, but if you want to port Mac apps over to Linux, good luck. They use the proprietary Cocoa and Carbon APIs (toolkits) along with a proprietary GUI called Aqua that does not even come close to X.org. 

Even though the Mac has UNIX roots and is POSIX compliant, everything graphical about it will NOT work on Linux. You would need a compatibility layer like WINE to get it to work (although it will be easier, because you won't have the different filesystems and directory trees/names to deal with).

---

### Post by makaki on 2010-02-22
Can anybody tell me what tools are they talking about?!

---

### Post by bashveank on 2010-02-22
> **makaki said:**
> Can anybody tell me what tools are they talking about?!

Don't worry about it. This whole thing is a non sequitur, as whether something is "real Unix" or "Unix-like" doesn't matter one bit to anyone that doesn't already care (even then, you have to really push it in order to make a big deal...)

---

