---
title: "My hard drive has just given up the ghost(or close, doesn't matter either way)"
date: 2008-06-10
forum: The Cafe
---

### Post by PmDematagoda on 2008-06-10
My 200Gb hard drive has just given up the ghost(or somewhere very close) on my desktop, and the weirdest thing is that it happened after a session of playing Enemy Territory and an even weirder thing is that it didn't crash the system, instead it suddenly made the whole drive read-only but of course this means that I can't use the X-Server and can only use the core OS(which I don't really need:-P).

Of course, since the drive is only read-only, I managed to salvage a lot of my data onto a hard drive through a Live CD, so now I can happily say bye to my rather new(can you believe it?) Samsung(maybe not) drive. A reason why I think I'll be keeping away from Samsung's is because my 60Gb WD drive still works properly and it is much more older than the Samsung, oh well, time to get either a WD or a Seagate.

And to anyone asking if I tried mounting it on a Live CD, yes, I did, it is still read-only, I also checked it with fsck but to no avail, the only thing I did not try is formatting it, might be a worth a try, I'll also put Windows on it if it works out. The reason for Windows? The Linux kernel seems to be having an age old bug of not playing nice with hard drive errors, so if one pops-up it just doesn't work very well with it and increases the load massively, Windows doesn't seem to be doing this so I might as well put it on and use it to the end of it's life.

---

### Post by SunnyRabbiera on 2008-06-10
Windows will not solve anything, honestly...

---

### Post by PmDematagoda on 2008-06-10
> **SunnyRabbiera said:**
> Windows will not solve anything, honestly...

I know it won't, there is no hope of fixing the HDD only using Windows(don't think there's any hope either), but I want to take a look at how long it'll last(curiosity). And strangely this is the first time an HDD failed on me in all my 10+ years of using a PC, so I am interested to see what you are all talking and shouting about;).

---

### Post by SunnyRabbiera on 2008-06-10
well windows is responsible for hard drive failures too, I have seen it happen many times.

---

### Post by PmDematagoda on 2008-06-10
> **SunnyRabbiera said:**
> well windows is responsible for hard drive failures too, I have seen it happen many times.

No OS has a clean record of hard drive failures and I am highly sure that Windows is no exception.

---

### Post by Fedz on 2008-06-10
WD are a better choice from what I've read on HD comparison tests, have you checked some out? :-)

Yeah! I'd put Window$ on the old drive and see how it goes - the OS is good for something then as a last resort but, if you've managed to retrieve your data why not wipe it and keep it for a later date as a back-up hard drives are as cheap as chips these days anyway ;-)

---

### Post by PmDematagoda on 2008-06-11
I haven't really checked out any comparison tests, just that I've heard good things about both WD and Seagate:).

Actually I just changed my plans, I am going to put FreeBSD on it(actually I've already done that), I've always been wanting to try it out, thought I might as well do it now:).

---

### Post by gameryoshi600 on 2008-06-11
yeah get a seagate or wd. if you got a spare hdd to put in your machine then do it. if not put dsl or puppy linux on a pen drive.

---

### Post by PmDematagoda on 2008-06-11
> **gameryoshi600 said:**
> yeah get a seagate or wd. if you got a spare hdd to put in your machine then do it. if not put dsl or puppy linux on a pen drive.

I had an extra 60Gb drive, so all was not lost, and I installed Ubuntu anew on that:).

---

### Post by PmDematagoda on 2008-06-13
Ok, I have just stepped into bad sector territory on FreeBSD as well, but I must admit, it does seem to be more robust with the bad sectors than Linux is, but I can't really prove this since I am not running a GUI yet(this is while trying to install KDE using the ports system).

---

### Post by az on 2008-06-13
What does S.M.A.R.T say is wrong with the drive?

To see all information provided by SMART on /dev/sda, run

sudo smartctl -a /dev/sda

To run a selftest on /dev/sda, run

sudo smartctl -t long /dev/sda

To view the results of the test, display all information (see above) or simply run

sudo smartctl -l selftest /dev/sda

---

### Post by PmDematagoda on 2008-06-13
Thanks az, I'll give the SMART self-assessment a try and see what it turns up.

---

### Post by beniwtv on 2008-06-13
Yep, I can agree with this.

Linux is *very* picky about the HDD it runs on. 

Personally, I see this as a good thing (tm). I'd rather have the OS advise me of failures as early as possible, instead of the OS hiding these errors and loose data (happened to me with Windows - twice).

Also, a recent story: My father has an old external USB HDD. It still runs well, but it had some errors in the FAT structure. Linux would mount it as read-only, and complain. This is better than allowing writes like Windows did - you can mess up much if you do so. Then my father scanned it in Windows, and now everything is well again.

While read-only is not the safest either, at least it's safer than read-write.

Cheers,

---

### Post by ellis rowell on 2008-06-13
I can't see that this is a HDD failure, you say you can still read it and it's "read only". Something must have made it read only. If you could find out what caused it you may be able to reverse it.

---

### Post by PmDematagoda on 2008-06-13
The selftest was finished without errors according to the log [here]("http://paste.ubuntu.com/19930") but I get read errors on both Linux and BSD, weird.

---

### Post by az on 2008-06-15
> **PmDematagoda said:**
> The selftest was finished without errors according to the log [here]("http://paste.ubuntu.com/19930") but I get read errors on both Linux and BSD, weird.

Then, the problem is probably due to a bad connection or a faulty controller on your motherboard.

---

### Post by PmDematagoda on 2008-06-15
> **az said:**
> Then, the problem is probably due to a bad connection or a faulty controller on your motherboard.

Is it possible on a SATA(just asking)?

Edit:- Also the first hard drive works properly(from what I've seen), dunno if that would help though. And also one thing, I am rather sure that there are bad sectors on the second drive since I can remember that Windows turned them up about 2 years ago.

---

