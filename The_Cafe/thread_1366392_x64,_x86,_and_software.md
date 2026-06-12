---
title: "x64, x86, and software"
date: 2009-12-28
forum: The Cafe
---

### Post by cartisdm on 2009-12-28
I know I could search around for these answers but honestly I'm just lazy and wanted to post something in the cafe to chat about :)

Why do they call 32bit x86 blah blah and 64bit x64 blah blah when your downloading an OS? That doesn't seem like a consistent way to label things (as opposed to x32 and x64).

I've (briefly) ran x64 Ubuntu on my machine in the past and it seemed enjoyable but didn't really do any testing with it.  I'm downloading the x64 Windows 7 professional ISO from my e-academy school account right now because...well, it's free so why not? :) Lately for work I've been doing a lot of encoding of large (2gb-5gb) videos using Adobe Media Encoder.  My understanding is this type of work is much faster using a 64bit OS, but will I need to get a 64bit version of Adobe CS4? Will I even be able to run 32bit software at all and just not reap the benefits of the speed I could get using 64bit versions?

In ubuntu I didn't have to worry about drivers and such.  Switching to x64 Windows 7 am I going to be pulling my hair out trying to get drivers for my machine? (currently running x84 Windows 7 RC Ultimate Edition)

---

### Post by Xbehave on 2009-12-28
x86 is the architecture 32 bit computers use (comes from history where 32bit pcs were 386, then 686 so *86 represents both)
x86_64 is a derivative 64 bit architecture
amd64 is synonymous with x86_64 because amd did it first
IA64 is some 64bit Intel invented but nobody uses it outside of the data  centers
x64 seams to be a term Microsoft (and sun) use for x86_64 but IMO x86_64 is better because x64 could be confused with ia64 or an inferior arch.

edit: i ninja'd out the x64 comment below, but wasn't fast enough dammit.

---

### Post by cartisdm on 2009-12-28
> **Xbehave said:**
> I have no idea what x64 is other than a typo :p

see thumbnail


I didn't know 64bit was a derivative of 32bit (x86) architecture.  I assumed it was something entirely separate and would have its own x?? name


EDIT: I see edits were made.  Thanks for the explanation, I guess it makes more sense now.  Any insight on my installation of x64 with Adobe CS4 32bit (and my concern for drivers)?

---

### Post by Danimoth on 2009-12-28
64-bit can see more than 3GB of RAM, so nowdays you would want to use that in most cases. Furthermore, 64-bit is supposed to be faster than 32-bit, assuming that the program your using also works in 64-bit and not through a compatibility layer. Personally, i found the differences to be negligible(if any) on some heavy programs i tried but other may disagree. 

You will have no problem running 32-bit applications. You cannot however run 64-bit applications on 32-bit. 


As for drivers it depends. Windows has some nice packed drivers which sometimes get you going, but you don't really want to rely on those. IE, windows is likely to install a drivers for you VGA, but you will definetely want to donwload the correct drivers from nvidia/ATI to make your VGA actually work well. 

As for the rest of the hardware, you need to check the vendor's website for Win7 drivers 64-bit. Some comments on this:
1) If you have an old laptop, then you probably are not going to be lucky
2) If you have a new laptop, then windows won't find many drivers, but you can definetely find them in the vendors webiste or even in the CD with no problem.
3) You will have an easier time in both cases for a desktop PC.

Two more comments, which are probably exceptions and not the norm, but thought i 'd mentioned them for kicks:
a) I have an HP 5470C scanner. I went to find drivers for win vista/7 64-bit and the website said: "Sorry, this device is not supported in 64-bit systems, please buy a new one from our shop". I got pissed with hp about this, as i have no problem using the scanner in 64-bit ubuntu/opensuse. 

b) I have ASUS Xonar D2X. Those guys haven't made any really functioning drivers for any windows version. They will seem to work, but if you actually try to use them, you will most likely get frustrated with the various screeches, sound disappearing, channels not playing etc, and that's not the kind of thing to expect from such an expensive sound card. So ASUS sucks in terms of drivers(good hardware though) but i was very surprised to see that the Xonar worked very well(Zero problems) when i installed ubuntu!

Again, i realize this is probably not the norm. 

Generally, you have to find most drivers separately, install them and make many reboots which will frustrate you. Is not as easy as in ubuntu, but i think you ll be fine :].

---

### Post by cartisdm on 2009-12-28
Cool, then I think as soon as my download is down I will begin working on installing x64 Windows 7 on my computer and dual boot it with a 64-bit Linux (either Mint or Ubuntu, dunno yet).  I thought about logging the hours on my timesheet and telling my boss it'll help me work "faster" in the long run since I'm doing all this decoding/encoding of video files but maybe that's stretching it a bit much :)

---

### Post by Xbehave on 2009-12-28
> **Danimoth said:**
> 64-bit can see more than 3GB of RAM, so nowdays you would want to use that in most cases.
Unless your processor and kernel have PAE, the limit is 4GiB not 3, although IIRC there was a bu in older versions of windows that made it have a 3.2GiB limit

---

### Post by Pogeymanz on 2009-12-28
x86_64 is named such because it's not truly a 64bit processor. It is a hybrid. From what I understand, a true 64 bit machine would not be able to run 32 bit software at all.

---

### Post by blueshiftoverwatch on 2009-12-28
> **Pogeymanz said:**
> x86_64 is named such because it's not truly a 64bit processor. It is a hybrid. From what I understand, a true 64 bit machine would not be able to run 32 bit software at all.
Why does being able to run the x86 instruction set make it not a true 64 bit processor? That just means it's not a RISC processor.

---

### Post by Pogeymanz on 2009-12-28
> **blueshiftoverwatch said:**
> Why does being able to run the x86 instruction set make it not a true 64 bit processor? That just means it's not a RISC processor.

I have no idea. Just what I've heard.

---

