---
title: "What Linus Has To Say About OpenBSD's Ideals"
date: 2008-07-16
forum: The Cafe
---

### Post by tdrusk on 2008-07-16
[http://article.gmane.org/gmane.linux.kernel/706950](http://article.gmane.org/gmane.linux.kernel/706950)

> On Tue, 15 Jul 2008, Linus Torvalds wrote:
> 
> So as far as I'm concerned, "disclosing" is the fixing of the bug. It's 
> the "look at the source" approach.

Btw, and you may not like this, since you are so focused on security, one 
reason I refuse to bother with the whole security circus is that I think 
it glorifies - and thus encourages - the wrong behavior.

It makes "heroes" out of security people, as if the people who don't just 
fix normal bugs aren't as important.

In fact, all the boring normal bugs are __way__ more important, just because 
there's a lot more of them. I don't think some spectacular security hole 
should be glorified or cared about as being any more "special" than a 
random spectacular crash due to bad locking.

Security people are often the black-and-white kind of people that I can't 
stand. I think the OpenBSD crowd is a bunch of masturbating monkeys, in 
that they make such a big deal about concentrating on security to the 
point where they pretty much admit that nothing else matters to them.

To me, security is important. But it's no less important than everything 
***else*** that is also important!

            Linus


lol. I love his sense of humor.

On a more serious note. Do you think security is more important than stability or do you agree with Linus?

---

### Post by kevin11951 on 2008-07-16
yeah, i... speechless.

---

### Post by tuxxy on 2008-07-16
lol that was a classic line :lolflag:

---

### Post by original_jamingrit on 2008-07-16
monkeys?

I don't think OpenBSD's only focus is on security.  But I do agree with Linus, to some extent.  If a system is neither stable or secure, why put sensitive information on it at all?

---

### Post by Foster Grant on 2008-07-16
> **original_jamingrit said:**
> monkeys?

I don't think OpenBSD's only focus is on security.

[img]http://openbsd.org/images/puffy43.gif[/img]

Seems somewhat important to them, especially considering the text under that graphic on OpenBSD's home page: "Only two remote holes in the default install, in more than 10 years!"

---

### Post by Joshuwa on 2008-07-16
That statement says more about Linus than it does about OpenBSD, in my opinion.

---

### Post by Canis familiaris on 2008-07-16
The thing I like about Linus is that he is not afraid to speak his mind.

But in my opinion, security is little bit more important. I mean you would prefer losing your credit card no. than getting it leaked to people who could take advantage.

---

### Post by tdrusk on 2008-07-16
> **Anurag_panda said:**
> The thing I like about Linus is that he is not afraid to speak his mind.

But in my opinion, security is little bit more important. I mean you would prefer losing your credit card no. than getting it leaked to people who could take advantage.
But, if you use your computer to make money and it looses all your data you won't have any money.

Kinda chicken or eggish.

I think moderation is key, which both do.

---

### Post by Bachstelze on 2008-07-16
> **Joshuwa said:**
> That statement says more about Linus than it does about OpenBSD, in my opinion.

Amen. Can this guy actually read?

[http://openbsd.org/goals.html](http://openbsd.org/goals.html)

---

### Post by cardinals_fan on 2008-07-16
Security AND stability both come from clean, audited code.  Which is why NetBSD (and OpenBSD, which was a fork) have both.

---

### Post by Polygon on 2008-07-16
even though they might claim that they dont focus on just security...maybe in actuality they are a bit 'security obsessed'?

i dont think this guy would just make this comment (hilarious i might add) without experiencing what he claims first hand..

---

### Post by Koori23 on 2008-07-16
somebody please correct me if I'm wrong. Perhaps I did not read this the way I should have...

I think the fundamental argument is flawed. Not having the "Ubuntu Splashscreen" display during system boot up, but after that 30 seconds is fine.. That's a bug.

Having some whacktard be able to control my system because of some obvious flaw in the code.. That's a bug too.. But to me, that's a more serious bug.

To me that statement sounds like it came out of Microsoft or Apple.. A bug is a bug and none of them are anymore important than the other.

Comparing software bugs by the shear number of issues fixed in a given month doesn't do anything for me. It seems that's exactly what Linus just backed up..

Again, I say.. I could be wrong, however that's the first thing that popped into my head after I read that.

---

### Post by YaroMan86 on 2008-07-16
Well, considering how Linux is so much better in quality and capability than BSD at this point... are we really surprised that Linus thinks BSD's focus is off?

As for what bugs get priority, yes, security is extremely important. But there's also such things as showstoppers and major bugs that sap functionality, memory leaks, buffer over- or under-runs.

Bottom line, security bugs are not the only critical bugs out there.

---

### Post by cmay on 2008-07-16
seems linus speaks his mind freely.
might not the way i would comment on subjects that really matters to me.
other than that i dont know what to say about it as i am not the great expert on security.
but its nice to know that linux is written by a guy that is somehow concerned about security and that he is not a boring type of person.
maybe thats why linux is so fun to use.:)

---

### Post by original_jamingrit on 2008-07-16
> **Foster Grant said:**
> Seems somewhat important to them...
I know it's more important than most other things for them, but OpenBSD is still more than just about security.

> **Joshuwa said:**
> That statement says more about Linus than it does about OpenBSD, in my opinion.
Agreed, this statement was mostly in regard to urging users of one kernel to upgrade to another without a detailed explanation.  That led into the bug disclosure thread.  While I think it would be good for bug disclosure, there's no need to punish users that don't upgrade by giving the attackers key hints.  So, I'm not sure if I agree on that stance.

This also reminds me of [Tin Foil Hat Linux](http://tinfoilhat.shmoo.com/) a now-abandoned distro (targeted at embedded) that claims to be 'an exercise in over-engineering'.  Security can be fun, too.

---

### Post by RiceMonster on 2008-07-16
> **Koori23 said:**
> A bug is a bug and none of them are anymore important than the other.

If you would read, that's exactly what he was saying.

[quote=Linus Torvalds]To me, security is important. But it's no less important than everything 
*else* that is also important![/quote]

He's saying that he thinks that security is important, but people shouldn't be given more credit for fixing security holes than those who fix regular bugs.

---

### Post by cardinals_fan on 2008-07-16
> **YaroMan86 said:**
> Well, considering how Linux is so much better in quality and capability than BSD at this point... are we really surprised that Linus thinks BSD's focus is off?

As for what bugs get priority, yes, security is extremely important. But there's also such things as showstoppers and major bugs that sap functionality, memory leaks, buffer over- or under-runs.

Bottom line, security bugs are not the only critical bugs out there.
/opinion

NetBSD is, **_IMHO_**, better than any Linux distro.  The only reason I don't use it full-time is because NVIDIA doesn't release NetBSD drivers.  And OpenSolaris is another story (and another kernel).

---

### Post by ghindo on 2008-07-16
> **HymnToLife said:**
> Amen. Can this guy actually read?

[http://openbsd.org/goals.html](http://openbsd.org/goals.html)> Pay attention to security problems and fix them before anyone else does. (Try to be the #1 most secure operating system).Also, stated goals doesn't always equate to what a project's *actual* focus may be.

---

### Post by tdrusk on 2008-07-16
> **Polygon said:**
> 
i dont think this guy would just make this comment (hilarious i might add) without experiencing what he claims first hand..
Was that a pun?

I might try out NetBSD. By the comments of one of the above user it seems pretty happenin'.

---

### Post by Arthur Archnix on 2008-07-16
Linus is a self-fellating monkey. I wish he'd STHU or share is poignant thoughts in private emails, not public mailing lists.

---

### Post by cardinals_fan on 2008-07-16
> **tdrusk said:**
> 
I might try out NetBSD. By the comments of one of the above user it seems pretty happenin'.
I love it.  It's a lot like Slackware, but is a BSD and has a packaging system like FreeBSD.

---

### Post by keiichidono on 2008-07-16
I always see you advocating OpenSolaris and BSD, I think I'll give it a try. Couldn't hurt.

About the article, I feel Linus is just speaking his mind on the matter and that's perfectly fine. I can't say i agree or disagree though, I don't give a damn what bugs are prioritized as long as my system is functional for me and works good.

---

### Post by RiceMonster on 2008-07-16
I'm going to try FreeBSD, NetBSD and OpenBSD on my next distro hopping binge. Not sure when that will be. OpenSolaris doesn't really interest me at this point.

---

### Post by samjh on 2008-07-16
OpenBSD is pretty infamous for being obsessed about security.

Linus could have put it more diplomatically, but essentially what he says is true.  Security should not be given overbearing importance at the expense of other important errors.

---

### Post by BrokeBody on 2008-07-16
Heh, just what we could expect from Linus. :)

As for OpenBSD developers, it would be really nice from them if they could tune up their installer a bit instead of making me to calculate cylinders on my hard drive in the 21st century rather than doing it automatically. :lolflag:

---

### Post by Foster Grant on 2008-07-16
> **RiceMonster said:**
> I'm going to try FreeBSD, NetBSD and OpenBSD on my next distro hopping binge. Not sure when that will be. OpenSolaris doesn't really interest me at this point.

No love for PC-BSD?

---

### Post by AnonCat on 2008-07-16
> Pay attention to security problems and fix them before anyone else does. (Try to be the #1 most secure operating system).

I copied the above line from the OpenBSD site and I'd say it's a noble goal.  I might have to try BSD now since security is what drove me from Windows to Linux.

---

### Post by klange on 2008-07-16
The next time I see an OpenBSD user, I'll be sure to call them a masturbating monkey because my lord God told me to.

Linus' statements are always out there, it's something most people have come to expect from him - a very frank, and usually rude, expression of his feelings.

---

### Post by RiceMonster on 2008-07-16
> **Foster Grant said:**
> No love for PC-BSD?

Forgot about that one. I'll have to give it a try too.

---

### Post by DeadSuperHero on 2008-07-16
I'm just kind of shocked by his arrogance. He wrote a kernel with the GNU userland. BSD was meant to be a full-blown operating system.

On top of that, aren't most people here always arguing that Linux was made to be "Secure and Stable"? If Linus is arguing the unimportance of security, how does that reflect on everyone else in the community?

@CalvinB: OpenSolaris is great. It's a little...different. However, there's a big set of pluses that it has going for it:

-The Flash plugin is fantastic. It honestly beats out Flash for Linux, and possibly Flash for Mac OSX.
-It has nifty tools, such as the ZFS filesystem, and DTrace. I haven't used DTrace yet, but it's a neat concept.
-Native Java support. You can take tarballs of Frostwire, Azureus, and other apps, and know for sure that it's compatible.
-Many Linux apps can be compiled for Solaris. However, it takes some tweaking to make the code fully Solaris-Compatible. Things like Audacity are currently being ported.
-A common codebase, as there's only ONE distro. And it's compatible all the way back to Solaris 2.
-Corporate support from Sun Microsystems. This helps get other companies to port their drivers, and a recent deal with Fluendo means that we'll be able to watch wmv's and play mp3's legally.
-OpenOffice, Netbeans, ScummVM, and Eclipse all have official Solaris builds!
-Gnome's configurations have been set up to be surprisingly user-friendly.

It's still premature, but I really like it. Not too sure whether I'd recommend it to everybody just yet, though.

---

### Post by Foster Grant on 2008-07-16
> **Mr. Psychopath said:**
> He wrote a kernel with the GNU userland. 

Half correct: He wrote a kernel (possibly the only kernel that began its life cycle as a terminal emulator), mainly because he was trying to teach himself programming on the 386 chip.

Others added the userland. As he noted in the USENET posting announcing his new kernel, it wasn't "going to be big and professional like GNU" and "probably never will support anything other than AT-harddisks" because that was all he had. Ye-e-e-e-eah ... famous last words and whatnot.

I have no idea why you're referring to his arrogance. I have no idea why you're saying he's arguing the unimportance of security. All that's been discussed already.

---

### Post by keiichidono on 2008-07-16
It sounds sweet, I might just dual-boot with Ubuntu. One thing that sounds sexy is the flash plugin thing, does it fix the PusleAudio problem that doesn't allow me to play two sources at once? Does it fix the freezing and stuff?

---

### Post by DeadSuperHero on 2008-07-16
> **Foster Grant said:**
> Half correct

Sorry, I meant to say that he wrote the kernel and packaged it with GNU tools and the GNU userland.

---

### Post by cardinals_fan on 2008-07-16
> **CalvinB said:**
> I always see you advocating OpenSolaris and BSD, I think I'll give it a try. Couldn't hurt.

About the article, I feel Linus is just speaking his mind on the matter and that's perfectly fine. I can't say i agree or disagree though, I don't give a damn what bugs are prioritized as long as my system is functional for me and works good.
I have a lot of affection for the purer UNIX OSs.
> **RiceMonster said:**
> I'm going to try FreeBSD, NetBSD and OpenBSD on my next distro hopping binge. Not sure when that will be. OpenSolaris doesn't really interest me at this point.
OpenSolaris is actually really nice.  It's a bit slow, but has tons of nice features, is quite stable for a first major release, has out-of-the-box Java and good Flash available, and is fun to mess around with.  My only real problem with it is the weak package management (the official repos are tiny and the Blastwave repository has a number of out-of-date packages).  It's still worth a try (you can order a free CD if you don't want to download it).

---

### Post by Canis familiaris on 2008-07-17
What exactly are advantages of BSD?

---

### Post by dracule on 2008-07-17
I still have nightmares of OpenSolaris' old java desktop..... so i am afraid to even try it again because it was slow.

I do not use the BSD's for a couple reasons..

From what i have experienced, the release cycle is much slower

It does not have the drivers I need.

It has a much much smaller community, thus questions dont get answered as fast if at all.

Usually the packages in the repos/package site are a couple of months behind.

Has a dumb mascot (lol j/k)


Linux just is more complete IMO and works much better.

---

### Post by toupeiro on 2008-07-17
Eh... so Linus spouted off on BSD...  I'm sure thats never happened coming from any BSD dev's before... 

Anyway, OpenSolaris is definitely worth trying out.  It feels a lot like linux while remaining solaris under the hood.  I happen to run the nexenta flavor of it.  I have the official release, but haven't done much with it.

---

### Post by bilijoe on 2008-07-17
If you have Ubuntu, why would you use BSD--or anything else, for that matter.  (Unless, I suppose, you're a geek, who just likes playing around with different OSs.  Nothing wrong with that.  But me, I just want to use my computer.)

On the stability vs. security issue,  if you don't have stability, then you don't have anything.  But, in today's world, if you are connected to the outside, security is pretty important.  Let's see, if I were in a skyscraper, would I rather have a good stable foundation under the building, or an awesome security force?  Hmmm.  Me thinks, if the building falls down, then the security force gets squashed just like the rest of us.  But then, if your security force is asleep at the switch, some terrorist might sneak in and blow up your foundation.

Isn't this kind of a ridiculous argument?  Isn't it a little like asking which is more important on your car, the accelerator, or the breaks?  If you can't stop, you'd be a fool to go.  On the other hand, if you can't go, you don't need to stop.

You guys work it out.  Linus said what he thought, and "I may disagree with what you say, but I'll defend, to the death, your right to say it." **Evelyn Beatrice Hall**, ([1868]("http://en.wikipedia.org/wiki/1868") - [1919]("http://en.wikipedia.org/wiki/1919"))

---

### Post by BrokeBody on 2008-07-17
> **Mr. Psychopath said:**
> A common codebase, as there's only ONE distro.

There's quite a few distros based on Solaris.

---

### Post by gunashekar on 2008-07-18
> **tdrusk said:**
> But, if you use your computer to make money and it looses all your data you won't have any money.
.

The probability of loosing "all your data" is diminishing fast. If it is important data, I am sure such data will be backed -up , mirrored several times over and these days it is no big deal.

---

### Post by MaxIBoy on 2008-07-18
All I'm saying is, his comments would make me uncomfortable if only Linux was more common.

---

### Post by kwagner on 2008-07-20
> **cardinals_fan said:**
> /opinion

NetBSD is, **_IMHO_**, better than any Linux distro.  The only reason I don't use it full-time is because NVIDIA doesn't release NetBSD drivers.  And OpenSolaris is another story (and another kernel).

Ditto!
You forgot to mention FreeBSD.
And IMO, since I've used both since around 1994: 
"Linux for play. *BSDs for work" ;)

---

### Post by knattlhuber on 2008-08-27
> I think the OpenBSD crowd is a bunch of masturbating monkeys
Masturbating Monkey, huh? Sounds like a name for a future Ubuntu version.. :)

---

### Post by Erik Trybom on 2008-08-27
Linus makes a point, does so in a provokative way, and manages to offend random organisation. Gee, we've never seen *that* before.

---

### Post by Dremora on 2008-08-27
I think that Linus is correct here, I'd rather see crashers fixed, and new functionality.

If it doesn't work, who cares how secure it is?

---

### Post by Dremora on 2008-08-27
> **MaxIBoy said:**
> All I'm saying is, his comments would make me uncomfortable if only Linux was more common.

Most prominent free software proponents are offensive trolls.

Of course, this also goes for corporate CEO's like Steve Ballmer and Steve Jobs.

Anyhow, if you find them offensive, go use something else, that was created by different sets of trolls. :lolflag:

Oddly enough, while I've usually disagreed with Richard Stallman, Linus Torvalds has usually been right on the money. :)

Torvalds has said that the BSD license would have been preferable over the GPL, except that it would allow for the kind of abuse that Apple did with FreeBSD code, so he chose GPL even though it was a "horrible political document".

---

### Post by FranMichaels on 2008-08-27
> **Dremora said:**
> Torvalds has said that the BSD license would have been preferable over the GPL, except that it would allow for the kind of abuse that Apple did with FreeBSD code, so he chose GPL even though it was a "horrible political document".

When was this? I googled and found nothing (well actually just this post...) 

Now Linus choose the GPL way before Apple had OS X, the reason was indeed the tit for tat aspect.

Linus Torvalds -
Subject	An Ode to GPLv2 (was Re: GPLv3 Position Statement)
[http://lkml.org/lkml/2006/9/24/246](http://lkml.org/lkml/2006/9/24/246)

---

### Post by Dremora on 2008-08-27
> **FranMichaels said:**
> When was this? I googled and found nothing (well actually just this post...) 

Now Linus choose the GPL way before Apple had OS X, the reason was indeed the tit for tat aspect.

Linus Torvalds -
Subject	An Ode to GPLv2 (was Re: GPLv3 Position Statement)
[http://lkml.org/lkml/2006/9/24/246](http://lkml.org/lkml/2006/9/24/246)

It was in one of his speeches on Google Video, but I don't remember which one exactly, I was laughing over that though when he sais "GPL....which we all know is a horrible political document"

I think the speech was from 2004.

---

### Post by RATM_Owns on 2008-08-27
Digg users: Wanking Walruses
OpenBSD Group: Masturbating Monkeys

What next?

---

### Post by LateNiteTV on 2008-08-27
linus is just lashing out because his operating is turning into a giant <bip> of fail.

---

### Post by RiceMonster on 2008-08-27
> **RATM_Owns said:**
> Digg users: Wanking Walruses
OpenBSD Group: Masturbating Monkeys

What next?

My guess:

Solaris Users: Fapping Flamingos

> **LateNiteTV said:**
> linus is just lashing out because his operating is turning into a giant clusterfuck of fail.

Uh, he's made comments like that before. The problem is people take it dead seriously, rather than light-hearted as he intended.

---

