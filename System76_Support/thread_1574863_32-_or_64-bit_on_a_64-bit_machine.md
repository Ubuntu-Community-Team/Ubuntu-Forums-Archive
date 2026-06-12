---
title: "32- or 64-bit on a 64-bit machine?"
date: 2010-09-14
forum: System76 Support
---

### Post by robtg on 2010-09-14
Greetings.  Tonight I went to download the 10.4.1 refresh for my 4 GB Panp5 and saw what I thought was something odd.  A radio button on the download page lets you select 32-bit ("***Recommended for most users***") or 64-bit ("***Not recommended for daily desktop usage***").  Is this to be interpreted as lukewarm support for 64-bit Ubuntu?  Am I better off running the 32-bit version?  64-bit seems to run OK except for Flash which doesn't support my ISP's web-based E-mail portal (but does run OK with 32-bit Ubuntu).

That's the kind of disclaimer I'd expect to find on beta or pre-release software.

Rob

---

### Post by warfacegod on 2010-09-14
That disclaimer really needs to come down or be modified, at least. 64 bit is well supported.

---

### Post by TheBuzzSaw on 2010-09-14
I run 64-bit full time. The problems it once had really are gone now.

---

### Post by zaphod777 on 2010-09-15
flash used to be a pain the x64 version is buggy but the recent 10.1 x32 version works pretty well in x64 now.

I run x64 and don't have any issues.

---

### Post by sikander3786 on 2010-09-15
> **warfacegod said:**
> That disclaimer really needs to come down or be modified, at least. 64 bit is well supported.
It really needs to be modified to something like

32-bit, Recommended for most users.

64-bit, Recommended for 64-bit capable machines. (See your product documentation for details)

To the OP:

Flash is no longer the problem on a 64-bit machine, that's what I keep on hearing on this forum. Still there are many threads regarding this problem. If you want to go safe, do a 32-bit install and then install PAE Kernel for supporting RAM more that 4 GB.

---

### Post by zaphod777 on 2010-09-15
With the last release of flash the Ubuntu installer works flawlessly in x64.

---

### Post by isantop on 2010-09-15
I can confirm what the others are saying; there aren't any problems with 64-bit Ubuntu. 

There is a small minority of apps (Probably not more than 5%) that have a hard time running, if at all, on 64-bit. However, most of these are small, niche apps, and all of the major applications are available in 64-bit from the Ubuntu repositorty. We preinstall 64-bit on all of our machines (Except the Starling, which is a 32-bit machine) and we haven't had any problems with it.

---

### Post by msrinath80 on 2010-09-15
> **isantop said:**
> I can confirm what the others are saying; there aren't any problems with 64-bit Ubuntu. 

There is a small minority of apps (Probably not more than 5%) that have a hard time running, if at all, on 64-bit. However, most of these are small, niche apps, and all of the major applications are available in 64-bit from the Ubuntu repositorty. We preinstall 64-bit on all of our machines (Except the Starling, which is a 32-bit machine) and we haven't had any problems with it.

Actually, I've had tons of problems with npviewer.bin crashing. But ever since I moved to the 32-bit bigmem kernel, no problems whatsoever. Not a single crash in flash :)

---

### Post by mrodent on 2010-09-20
hmm... all rather confusing when you've just had a brand spanking new laptop delivered with an icore 5 CPU and an SSD hard drive and you can't wait to see how Ubuntu performs on it... in particular, why is this 64-bit file called "...amd64.iso" ???

are they trying to confuse newbies?

or are they too geeky for their own good and are **doomed **always to confuse newbies, whether they will or no?

---

### Post by isantop on 2010-09-20
I think it has to do with the fact that technically, the architecture the i5 uses is amd64.

A little history: made 64-bit work on a desktop level before Intel got it. For the sake of compatibility, Intel adopted it, and so now all of the 64-bit desktop processors are amd64.

---

### Post by warfacegod on 2010-09-20
The AMD .iso will work fine on your new laptop. What isantop is saying, translated into lay men's terms, is this; Intel got caught with their pants down on the 64 bit thing so they swiped AMD's way of doing things to catch up.

What's confusing to me is that there is a processor type in the .iso name in the first place. Last I knew, the kernels Ubuntu uses were totally processor type independent, aside from32 or 64. It seems to me to be a related aspect of the initial topic of this thread.

---

### Post by isantop on 2010-09-20
Precisely.

I believe that they say "amd64" instead of "x64"because that's the official name for that architecture, according to debian. Debian packages must have the architecture in the filename. Ubuntu uses the same nomenclature for its .iso's as it does for its packages.

---

### Post by ranch hand on 2010-09-20
> **mrodent said:**
> 
are they trying to confuse newbies?

or are they too geeky for their own good and are **doomed **always to confuse newbies, whether they will or no?
Yes and every one else too.  Planet ubuntu has moved to an alternate universe.

---

### Post by robtg on 2010-09-20
And for all it's worth, the 32-bit Flash that installs with a wrapper program was working OK with my ISP's web portal...and then it just stopped working.  I removed it and downloaded Adobe's latest experimental version of 64-bit Flash and now it's working again.  I love these little science-fair projects!

Rob

---

