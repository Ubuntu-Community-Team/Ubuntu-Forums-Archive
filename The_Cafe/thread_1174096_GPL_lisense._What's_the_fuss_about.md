---
title: "GPL lisense. What's the fuss about?"
date: 2009-05-30
forum: The Cafe
---

### Post by dragos240 on 2009-05-30
Okay, so I was bored today and decided to test out solaris or opensolaris, I joined the irc there and asked the difference between the two and asked what would be the advantages of opensolaris and linux. Then there was a very flamy topic about how the GPL lisense was very closed off, and that I would never find a piece of software for linux that didn't use it. GPL is all about distributing and being open, but it seems that it's not good enough for them. Regardless, I'm going to test out opensolaris.

---

### Post by Icehuck on 2009-05-30
> **dragos240 said:**
> Okay, so I was bored today and decided to test out solaris or opensolaris, I joined the irc there and asked the difference between the two and asked what would be the advantages of opensolaris and linux. Then there was a very flamy topic about how the GPL lisense was very closed off, and that I would never find a piece of software for linux that didn't use it. GPL is all about distributing and being open, but it seems that it's not good enough for them. Regardless, I'm going to test out opensolaris.

The GPL is more restrictive then the CDDL. Basically, if want to take code from GPL and make part of if proprietary, you can't. With the CPPL license you can make part of it proprietary. The CPPL give you the choice on how to manage software you create.

---

### Post by dspari1 on 2009-05-30
> **dragos240 said:**
> Okay, so I was bored today and decided to test out solaris or opensolaris, I joined the irc there and asked the difference between the two and asked what would be the advantages of opensolaris and linux. Then there was a very flamy topic about how the GPL lisense was very closed off, and that I would never find a piece of software for linux that didn't use it. GPL is all about distributing and being open, but it seems that it's not good enough for them. Regardless, I'm going to test out opensolaris.

The BSD license is that kind of license, and companies like Microsoft and Apple are free to use any BSD code into their product, charge as much as they want, and not give even one line of code back.

I respect all developers that want to use the BSD license since it is ultimately their choice and their hard work.

In return, those OpenSolaris users on that IRC channel should also respect the developers that don't want their code to be abused and prefer the GPL license where if any GPL code is used, the source code for the new product must also be released under the GPL.

Note: I'm aware that CDDL is the license used, but it has the same problem that the BSD license has.

---

### Post by MikeTheC on 2009-05-30
While I don't have an issue per-se with the BSD license, ultimately I think a lot of folk fail to grasp the bigger picture and what's going on out there in the technology world. Frankly, this is a battle, folks, and the "other side" is out for considerably more than just how they write their software.

In my view, GPL is the ultimate defense. There's also nothing stopping someone from accessing GPL'd code from their app (without making their own app GPL'd) but that involves not being stupid about it.

On the part of users (individuals or businesses), well... Let me give you an analogy. Women as a rule are turned off by needy guys. The more a guy allows himself to feel desperate about a particular woman, the more she's in control and the less likely she's going to be interested in him. Nothing against women, don't get me wrong, but this all works fundamentally the same way.

There are other better ways of getting things done, but when we give in or beg or whatever and the other side (that is, businesses or industry or government or commercial software developers or whatever) senses this, they know they can convince us their way is the right one and we'll all just go along with it. And because we're unwilling to stand up and fight, we've already lost the battle.

Now, I'm not going to say you folks should get down on your knees and kiss the ground Linus or Richard walk on, but you need to understand (particularly in the case of RMS) there's been a lot of time, effort and energy spent on bringing something to the world that's to your benefit. Don't be so willing to just throw it away.

---

### Post by rookcifer on 2009-05-30
> **dragos240 said:**
> Okay, so I was bored today and decided to test out solaris or opensolaris, I joined the irc there and asked the difference between the two and asked what would be the advantages of opensolaris and linux. Then there was a very flamy topic about how the GPL lisense was very closed off, and that I would never find a piece of software for linux that didn't use it. GPL is all about distributing and being open, but it seems that it's not good enough for them. Regardless, I'm going to test out opensolaris.

Main difference -- GPL requires that those who use and modify the code must return that modified code back to the community.  The BSD license has no such stipulation (which is how Apple uses it).  

The license OpenSolaris uses is some concoction by Sun.  I am not sure of the specifics of it, but I do know that it is not compatible with the GPL.  This is why Linux does not have ZFS or DTrace, even though many Linux users would love to have both.  Linus Torvalds himself even met with some of the Sun devs about getting ZFS GPL compatible, but the meeting ended up a stalemate.

---

### Post by original_jamingrit on 2009-05-30
I am not a lawyer, and I don't know everything there is to know about the GPL, but maybe I can explain somewhat.

By some groups, the GPL is considered closed off. This is because, for some purposes, it's too protective of software freedom.  This seems like a weird contradiction, but hear me out.

Some free software groups, particularly the *BSD supporters, don't like that the GPL is "stuck" to whatever software it's attached to.  So the only licenses you can add to that are ones that are GPL compatible, and you cannot "remove" the GPL (unless you are the original developer/authour of that program, depending on whether or not you've accepted any patches also had licenses attached by their contributors).  This is all pretty complicated, so that's one reason why some free-software supporters may prefer to avoid the GPL.

As I understand it, when something is released with the typical BSD license, the GPL license may also be added, (and vice versa since the two are compatible).  But the GPL limits some of the freedoms granted by the BSD license.

As you can see on [wikipedia]("http://http://en.wikipedia.org/wiki/BSD_license"), BSD licenses do not require you (as the (re)distributor) to provide source or binaries (it may be one or the other or both), usually requires you give credit where credit is due, and does not permit you to misrepresent the original authours you may have gotten the software from (similar to how no Ubuntu derivatives are allowed to say they are endorsed by Ubuntu, although in Ubuntu's case that's more of a trademark thing then a license thing).  This allows entities like Apple to take your software and make it their own (which is essentially what Mac OSX is, a heavily modified BSD kernel and OS).

So, what the GPL does (and rightly so, in my opinion) is prevent people from taking free software and making it a commodity.  This is in line of the GPL's original spirit of "by hackers, for hackers" (obviously, I mean hackers in the good sense).

Long story short, BSD lisences are mostly do-what-you-want, whereas GPL means share and share-alike.  I'm not familiar with Opensolaris' lisence, but it's probably more in line with *BSD than GPL (ignoring the fact that they still have a corporate overlord :-P).

---

### Post by schauerlich on 2009-05-30
> **rookcifer said:**
> Main difference -- GPL requires that those who use and modify the code must return that modified code back to the community.  The BSD license has no such stipulation (which is how Apple uses it).

Apple releases all of the FOSS-derived code back to the community. Check the link in my sig (common misconceptions about Mac OS X)

---

### Post by SKLP on 2009-05-30
The main issue (in my view) is not mainly that the GPL does not allow to link with proprietary applications, it's rather that it only allows linking with a "GPL-compatible" license, meaning GPL has to be able to turn the whole derivative works into GPL for it to be acceptable for the GPL to link to it.

This can cause even licenses that are similar in spirit to not be compatible, which I think is just sad. For instance, GPLv3 is not compatible with the GPLv2 by itself (most GPLv2 apps can be used under GPLv3 as well due to they being explicity licensed under "GPLv2 or later".

IMO it would not be a problem to simply use permissive licenses for most open source software today, and It's what I would use for my software. However, I'll gladly use GPL over non-free software. But permissive licenses "feel" a lot more free to me, as they will allow you to combine software under for instance any number of permissive open source licenses (without one license *SPREADING* to the whole combined work).

(Just my 2 cents..)

---

### Post by schauerlich on 2009-05-30
In general: Permissive "BSD-style" licenses give more freedom to the programmers using the code, while copyleft "GPL-style" licenses give more freedom to the code itself.

---

### Post by MikeTheC on 2009-05-30
> **SKLP said:**
> But permissive licenses "feel" a lot more free to me, as they will allow you to combine software under for instance any number of permissive open source licenses (without one license *SPREADING* to the whole combined work).
The greatest concern that I and others have with this is simply that people less principled than ourselves and creatively devious may find ways to exploit this.

---

### Post by original_jamingrit on 2009-05-30
> **EDavidBurg said:**
> Apple releases all of the FOSS-derived code back to the community. Check the link in my sig (common misconceptions about Mac OS X)

Interesting, thanks for the link.

---

### Post by SunnyRabbiera on 2009-05-30
> **EDavidBurg said:**
> Apple releases all of the FOSS-derived code back to the community. Check the link in my sig (common misconceptions about Mac OS X)

Right and I am Barack Obama, president of the united states.
Apple has contributed little if anything back to linux, webkit and CUPS are the only things they really contribute but nothing else.

---

### Post by schauerlich on 2009-05-30
> **SunnyRabbiera said:**
> Right and I am Barack Obama, president of the united states.
Apple has contributed little if anything back to linux, webkit and CUPS are the only things they really contribute but nothing else.

Apple doesn't use Linux code. [WebKit](http://webkit.org/) is a FOSS project. So is CUPS. I'm not sure what your point here is.

Again, I refer you to the link in my sig. It contains many more links about Apple's FOSS contributions that may interest you. Apple has a bunch of source code available for download, modification and redistribution.

---

### Post by tubezninja on 2009-05-30
> **SunnyRabbiera said:**
> Right and I am Barack Obama, president of the united states.
Apple has contributed little if anything back to linux, webkit and CUPS are the only things they really contribute but nothing else.

You're right about one thing: Apple doesn't contribute to linux *directly* in that they don't hold the hands of linux developers and say "here you go..." 

But I don't see where they are morally or legally obligated to do so.  And I'm sure there'd be a lot of angry "OMG I"M LEAVING UBUNTU" threads if they did and Ubuntu devs stood for it.

Even so, they DO contribute to _FOSS_, and quite substantially.  I think the ability to print and surf the web are rather significant features.  their contributions to zeroconf are notable, too. Would you be more satisfied if they coded the kernel for you as well?

---

### Post by ssam on 2009-05-30
> **rookcifer said:**
> The license OpenSolaris uses is some concoction by Sun.  I am not sure of the specifics of it, but I do know that it is not compatible with the GPL.  This is why Linux does not have ZFS or DTrace, even though many Linux users would love to have both.  Linus Torvalds himself even met with some of the Sun devs about getting ZFS GPL compatible, but the meeting ended up a stalemate.

there is nothing to stop anyone righting a ZFS module for linux (appart from maybe patents, but that does not generally stop people).

Microsoft never released the code for FAT or NTFS under a GPL compatible licence, ditto for HFS and several other filesystems. so someone sat down and figured out how they worked and wrote new code and released as GPL.

I can't see why this can't be done for ZFS.

--
PS i think the GPL is great as it keeps things free. it will always be possible to hack and modify linux.

Mac OS X contains a mix of free, open and proprietary code. You can't make changes to the system and run them. you can download just the kernel and modify that, but it's far from Mac OS X, i.e. no GUI.

According to wikipedia FreeBSD contains "three- and four-clause BSD licenses, as well as the GPL, LGPL, ISC, CDDL and Beerware licenses". Its not impossible that they could add closed source bits in the future, and then you might loose the ability to hack on FreeBSD (unless you stayed with an old version).

---

