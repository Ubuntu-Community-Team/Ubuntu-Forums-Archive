---
title: "copy audio CDs?"
date: 2010-09-10
forum: Ubuntu Studio
---

### Post by reiki on 2010-09-10
Long time Ubuntu user. Last night I tried to copy an audio CD in Ubuntu 10.04 (64-bit) and ran into all kinds of issues. Apparently Brasero is broken and it's a known issue, been bugged, and still no resolution.

So my question is:
If I install Ubuntu Studio do I have the same problem? Or can Ubuntu Studio copy an audio CD out of the box?

Thanks

---

### Post by TNT1 on 2010-09-10
Before you install ubuntu studio, why not just check the software center for another app to copy an audio cd, and find one that works for you?

---

### Post by reiki on 2010-09-10
Yeah.... well I ended up using cdrdao last night from the command line to copy a CD. Brasero didn't work, GnomeBaker didn't work, and I am reluctant to simply install K3B which I understand WILL work because of all of the KDE libraries it will pull in with it. Plus I've found that running KDE apps in Gnome isn't always the most stable way to go. 

I suppose I could copy audio CDs on my wife's laptop because she's still on the OLD LTS and I haven't "upgraded" her to the new 10.04 LTS. Partially because of problems like this. She'd NEVER be able to copy a cd using command line, even though she uses her Ubuntu laptop daily for everything.

This is like a core function that's broken and has been known about apparently since before the release of 10.04. Darn near unforgiveable in my book. Makes it pretty hard to champion the cause of converting folks when something as simple as copying a Cd has to be done from a command line using a string of cryptic parameters. 

Sorry.... it ticked me off as I had people over watching. I got it done, but rather inelegantly.

Hence my question about Ubuntu Studio. Does it have the same flaw using Brasero and/or GnomeBaker to make a copy of an audio CD?

---

### Post by TNT1 on 2010-09-10
Is it a 64 bit issue? I'm sure I've copied cd's before. Want me to try it? (I'm on 32bit wif PAE...)

---

### Post by TNT1 on 2010-09-10
Ah, right, guess I never copied a audio cd.

See here:
 			 			 			 		   		 		 		Please note that Ubuntu does not come with
cdda2wav, so Brasero is correct with telling
you that cdda2wav is missing.

Ubuntu unfortunately installs a broken and dead fork 
instead of the maintained original software.

If you like to get the working original software,
you may either fetch a recent original source from

[ftp://ftp.berlios.de/pub/cdrecord/alpha](ftp://ftp.berlios.de/pub/cdrecord/alpha)

[http://cdrecord.berlios.de/](http://cdrecord.berlios.de/)

or get one of the various precompiled versions of the
original software that are provided from helpful
people. There is no need to use non-free closed source
software and cdda2wav is even one of the best available
audio extractors.

[http://ubuntuforums.org/showthread.php?t=1470029&highlight=cdda2wav](http://ubuntuforums.org/showthread.php?t=1470029&highlight=cdda2wav)

---

### Post by TNT1 on 2010-09-10
> **reiki said:**
> 

So my question is:
If I install Ubuntu Studio do I have the same problem? Or can Ubuntu Studio copy an audio CD out of the box?

Thanks

Apparently it's Brasero that's buggy, so if ubuntu studio uses that, then you'll be in the same boat...

I'm a long time kde user, so I'd just install k3b... 

But I seem to rip from audio cd, to use as mp3 only, so this hasn't become an issue for me.

---

### Post by andrew.46 on 2010-09-11
Hi reiki,

> **reiki said:**
> Yeah.... well I ended up using cdrdao last night from the command line to copy a CD.

I have been a little mortified that with the ongoing problems copying audio cds under lucid and maverick this old guide of mine has not had more of a workout:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

I have used this method myself for many years although I will admit to slowly moving to [cdda2wav and cdrecord]("http://www.andrews-corner.org/burning.html#audio") more recently...

Andrew

---

### Post by reiki on 2010-09-11
Andrew-
Your old guide is what helped me in a crunch and I thank you for it.
The command line is a powerful tool. However when working in a GUI environment we've come to expect certain things and my opinion is that simply copying a CD is one of them.

I also found that I can use Sound Juicer to rip an audio CD to flac files and then use GnomeBaker to burn them to a CD. Gnomebaker does the transition from flac to CD audio files automatically.

This goes back to one of my pet peeves. Simple things should be simple. And while the back end of copying, trancoding, and writing files may be an involved process, the user experience should be a simple one.

Again, I thnk you for saving my butt by having that guide readily available and I hope to become more proficient at those processes, but when I'm in a hurry I just want to click, click, click and get it done. Know what I mean?

---

### Post by andrew.46 on 2010-09-11
Hi reiki,

> **reiki said:**
> Again, I thnk you for saving my butt by having that guide readily available and I hope to become more proficient at those processes, but when I'm in a hurry I just want to click, click, click and get it done. Know what I mean?

I agree with you completely and particularly when it deals with something as basic as copying an audio cd. The Launchpad bug report that deals with this problem:

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696)

was filed in February 2010 and it is perhaps not a good reflection on the Ubuntu *process* that the problem is ongoing...

Andrew

---

### Post by reiki on 2010-09-12
I've been watching the bug reports on this issue and I am frankly a bit disappointed in what appears to be finger pointing but no resolution. And my current understanding is that this is still broken so far in Meerkat. That's not to say it won't be addressed in time for Meerkat's release, but seriously.... Lucid is an LTS. 

If switching to KDE is the workaround, I may have to learn to use KDE instead of Gnome :)  I would simply install K3B but it will bring in so many dependencies, I may as well learn KDE instead.

---

