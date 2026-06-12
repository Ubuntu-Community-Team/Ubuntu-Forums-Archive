---
title: "Theo de Raadt, &quot;Linux stealing our code&quot;"
date: 2007-09-03
forum: The Cafe
---

### Post by Bachstelze on 2007-09-03
Everyone please forget what others might have told you about Theo being a complete A-hole and have a read :

```
From: Theo de Raadt <deraadt <at> cvs.openbsd.org>
Subject: That whole "Linux stealing our code" thing
Newsgroups: gmane.os.openbsd.misc
Date: 2007-09-01 01:40:52 GMT (3 days and 47 minutes ago)

[bcc'd to Eben Moglen so that people don't flood him]

I stopped making public statements in the recent controversy because
Eben Moglen started working behind the scenes to 'improve' what Linux
people are doing wrong with licensing, and he asked me to give him
pause, so his team could work.  Honestly, I was greatly troubled by
the situation, because even people like Alan Cox were giving other
Linux developers advice to ... break the law.  And furthermore, there
are even greater potential risks for how the various communities
interact.

For the record -- I was right and the Linux developers cannot change
the licenses in any of those ways proposed in those diffs, or that
conversation (http://lkml.org/lkml/2007/8/28/157).

It is illegal to modify a license unless you are the owner/author,
because it is a legal document.  If there are multiple owners/authors,
they must all agree.  A person who receives the file under two
licenses can use the file in either way....  but if they distribute
the file (modified or unmodified!), they must distribute it with the
existing license intact, because the licenses we all use have
statements which say that the license may not be removed.

It may seem that the licenses let one _distribute_ it under either
license, but this interpretation of the license is false -- it is
still illegal to break up, cut up, or modify someone else's legal
document, and, it cannot be replaced by another license because it may
not be removed.  Hence, a dual licensed file always remains dual
licensed, every time it is distributed.

Now I've been nice enough to give Eben and his team a few days time to
communicate inside the Linux community, to convince them that what
they have proposed/discussed is wrong at a legal level.  I think that
Eben also agrees with me that there are grave concerns about how this
leads to problems at the ethical and community levels (at some level,
a ethos is needed for Linux developers to work with *BSD developers).
And there are possibilities that similar issues could loom in the
larger open source communities who are writing applications.

Eben has thus far chosen not to make a public statement, but since
time is running out on people's memory, I am making one.  Also, I feel
that a lot of Linux "relicencing" meme-talkin' trolls basically have
attacked me very unfairly again, so I am not going to wait for Eben to
say something public about this.

In http://lkml.org/lkml/2007/8/29/183, Alan Cox managed to summarize
what Jiri Slaby and Luis Rodriguez were trying to do by proposing a
modification of a Dual Licenced file without the consent of all the
authors.  Alan asks "So whats the problem ?".  Well, Alan, I must
caution you -- your post is advising people to break the law.

I will attempt to describe in simple terms, based on what I have been
taught, how one must handle such licenses:

- If you receive dual licensed code, you may not delete the license
  you don't like and then distribute it.  It has to stay, because you
  may not edit someone's else's license -- which is a three-part legal
  document (For instance: Copyright notice, BSD, followed by GPL).

- If you receive ISC or BSD licensed code, you may not delete the
  license.  Same principle, since the notice says so.  It's the law.
  Really.

- If you add "large pieces of originality" to the code which are valid
  for copyright protection on their own, you may choose to put a different
  and seperate (must be non-conflicting...) license at the top of the file
  above the existing license.

    (Warning: things become less clear as to what the combination of
    licenses mean, though -- there are ethical traps, too).

- If you wish for everyone to remain friends, you should give code back.

  That means (at some ethical or friendliness level) you probably do
  not want to put a GPL at the top of a BSD or ISC file, because you
  would be telling the people who wrote the BSD or ISC file:

     "Thanks for what you wrote, but this is a one-way street, you give
     us code, and we take it, we give you you nothing back.  screw off."

In either case, I think a valuable lessons has been taught us here in
the BSD world -- there are many many GPL loving people who are going
to try to find any way to not give back and share (I will mention one
name: Luis Rodriguez has been a fanatic pushing us for dual licensed,
and I feel he is to blame for this particular problem).  Many of those
same people have been saying for years that BSD code can be stolen,
and that is why people should GPL their code.

Well, the lesson they have really taught us is that they consider the
GPL their best tool to take from us!

GPL fans said the great problem we would face is that companies would
take our BSD code, modify it, and not give back.  Nope -- the great
problem we face is that people would wrap the GPL around our code, and
lock us out in the same way that these supposed companies would lock
us out.  Just like the Linux community, we have many companies giving
us code back, all the time.  But once the code is GPL'd, we cannot get
it back.

Ironic.

I hope some people in the GPL community will give that some thought.
Your license may benefit you, but you could lose friends you need.
The GPL users have an opportunity to 'develop community', to keep an
ethic of sharing alive.

If the Linux developers wrap GPL's around things we worked very hard
on, it will definately not be viewed as community development.

Thank you for thinking about this.

[I ask that one person make sure that one copy of this ends up on the
linux kernel mailing list]
```

I know most people here are on the GPL side - for noble reasons, I hope -, so I want to ask them something. Does it not make you feel bad when you see that some people are using the GPL to take and not give back ? Sure, it is perfectly legal, but from an ethical point of view ? It certainly would, for me.

*P.S. : if all you're willing to answer is "stfu gpl is teh rox bsd suxorz lololol", don't bother. I have no will to read such garbage over and over again.*

---

### Post by Bachstelze on 2007-09-03
And for those who do not want to go through the whole thing, just read the first link Theo mentioned :

[http://lkml.org/lkml/2007/8/28/157](http://lkml.org/lkml/2007/8/28/157)

/me pukes

---

### Post by ComplexNumber on 2007-09-03
> Everyone please forget what others might have told you about Theo being a complete A-holei got that far and it reminded me about everything that he's said in the past. 
i didn't need to read anymore. Theo is an idiot. always has been, always will be.

---

### Post by yabbadabbadont on 2007-09-03
> **ComplexNumber said:**
> i got that far and it reminded me about everything that he's made in the past. 
i didn't need to read anymore. Theo is an idiot. always has been, always will be.

Even so, he is right in this one instance.  <insert usual disclaimers>

---

### Post by Bachstelze on 2007-09-03
> **ComplexNumber said:**
> i got that far and it reminded me about everything that he's made in the past. 

/me waits for *concrete* examples and *facts*, not FUD and thoughtless bashing.

---

### Post by ryno519 on 2007-09-03
If he doesn't like it then he should stop using the BSD license. Under that license it's perfectly acceptable for the code to be used "as a one way street". Tough ****. Pick a license that suits your needs better next time.

---

### Post by Bachstelze on 2007-09-03
> **ryno519 said:**
> If he doesn't like it then he should stop using the BSD license. Under that license it's perfectly acceptable for the code to be used "as a one way street".

Okey dokey, so you think it's "perfectly acceptable" for Linux to act just as bad as Windows.

Thanks, that's all I wanted to know :)

---

### Post by ComplexNumber on 2007-09-03
> **HymnToLife said:**
> /me waits for *concrete* examples and *facts*, not FUD and thoughtless bashing.
he's always going on his rants. he'll say anything to make linux look bad and BSD look superior. i've read enough of his comments in the past and more than enough to form a concrete opinion of him. he'll lie. exaggerate, anything. he's a fool.
here's some of his ranting:
[http://www.forbes.com/2005/06/16/linux-bsd-unix-cz_dl_0616theo.html](http://www.forbes.com/2005/06/16/linux-bsd-unix-cz_dl_0616theo.html)

---

### Post by Bachstelze on 2007-09-03
> **ComplexNumber said:**
> 
i wasn't  born yesterday.

Me neither. And I don't think it's very mature to say "I don't like you, therefore you cannot be right, even when you say that two plus two equal four". 

Just have a look at the link I posted in my second message...

---

### Post by yabbadabbadont on 2007-09-03
> **ComplexNumber said:**
> he's always going on his rants. he'll say anything to make linux look bad and BSD look superior. i've read enough of his comments in the past and more than enough to form a concrete opinion of him. he'll lie. exaggerate, anything. he's a fool.

[http://ubuntuforums.org/showpost.php?p=3305833&postcount=4](http://ubuntuforums.org/showpost.php?p=3305833&postcount=4)

No sense in typing it again.  :D

---

### Post by ryno519 on 2007-09-03
> **HymnToLife said:**
> Okey dokey, so you think it's "perfectly acceptable" for Linux to act just as bad as Windows.

Thanks, that's all I wanted to know :)

"Just as bad as Windows." I hear that a lot around here. They should consider making a Godwin-esque rule about that. It's about just as constructive as a Godwin in any case.

So tell me how using a license in a completely acceptable manner is bad? Perhaps the following would suit their needs

> 
 * Copyright (c) 1982, 1986, 1990, 1991, 1993
 *	The Regents of the University of California.  All rights reserved.
 *
 * Redistribution and use in source and binary forms, with or without
 * modification, are permitted provided that the following conditions
 * are met:
 * 1. Redistributions of source code must retain the above copyright
 *    notice, this list of conditions and the following disclaimer.
 * 2. Redistributions in binary form must reproduce the above 
copyright
 *    notice, this list of conditions and the following disclaimer in the
 *    documentation and/or other materials provided with the distribution.
 * 3. All advertising materials mentioning features or use of this software
 *    must display the following acknowledgement:
 *	This product includes software developed by the University of
 *	California, Berkeley and its contributors.
 * 4. Neither the name of the University nor the names of its contributors
 *    may be used to endorse or promote products derived from this software
 *    without specific prior written permission.
 *
 * THIS SOFTWARE IS PROVIDED BY THE REGENTS AND CONTRIBUTORS ``AS IS'' AND
 * ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
 * IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
 * ARE DISCLAIMED.  IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE
 * FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
 * DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS
 * OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
 * HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
 * LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY
 * OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF
 * SUCH DAMAGE.

PS: NO GNU/LINUX! :lolflag:
 

---

### Post by Bachstelze on 2007-09-03
> **ComplexNumber said:**
> 
here's some of his ranting:
[http://www.forbes.com/2005/06/16/linux-bsd-unix-cz_dl_0616theo.html](http://www.forbes.com/2005/06/16/linux-bsd-unix-cz_dl_0616theo.html)

How is that ranting ? To me, it's a very thoughtful and perfectly justified critic of Linux. You're the perfect illustration of [this thread](http://ubuntuforums.org/showthread.php?t=542303), point nuber one. All right to say someone is an idiot, not all right to say anything bad about Linux...

---

### Post by ComplexNumber on 2007-09-03
> **HymnToLife said:**
> How is that ranting ? To me, it's a very thoughtful and perfectly justified critic of Linux. You're the perfect illustration of [this thread]("http://ubuntuforums.org/showthread.php?t=542303"), point nuber one. All right to say someone is an idiot, not all right to say anything bad about Linux...
no. not because he says that linux is garbage, but because he is. that article is just the tip of the iceberg.

---

### Post by Bachstelze on 2007-09-03
> **ryno519 said:**
> "Just as bad as Windows." I hear that a lot around here. They should consider making a Godwin-esque rule about that. It's about just as constructive as a Godwin in any case.

Yep, actually you're right. At least, when they take BSD code to put in their OS, the guys at Microsoft respect the licence. Some Linux guys do not (see link in port #2).

That's indeed much of a difference, though perhaps not in the way you expected...

---

### Post by Frak on 2007-09-03
Sounds like a blowhard.
And that article makes Forbes look bad IMHO.

---

### Post by ryno519 on 2007-09-03
> **HymnToLife said:**
> Yep, actually you're right. At least, when they take BSD code to put in their OS, the guys at Microsoft respect the licence. Some Linux guys do not (see link in port #2).

That's indeed much of a difference, though perhaps not in the way you expected ;)

Hey, you're more than welcome to point out where in the BSD it says that the code must be ported back under the BSD license. Otherwise, Mr. Raadt is really complaining about the license he's using. If he doesn't like the way people use that license then tough cookies. He could always write his own license that would preclude that kind of use or he could live with it. It is completely to him. Personally, I don't see the problem.

Edit:

Just read the addition to your post. Interesting how disagreeing with you about how the use of a software license derides one of ethics, generosity and friendliness.

Edit 2:

I see that quote I was referring to in my edit is below me now. Hi down there! :)

---

### Post by Bachstelze on 2007-09-03
> **ryno519 said:**
> Hey, you're more than welcome to point out where in the BSD it says that the code must be ported back under the BSD license.

Nowhere. But I guess that settles it. I just wondered whether the average Linux user thinks it's okay to take and not give back when you have the right to do so, instead of giving back when you don't have to, just for the sake of ethics, generosity and friendliness - because yes, that's exactly what it is ! I had my answer, thanks.

---

### Post by p_quarles on 2007-09-03
> Yep, actually you're right. At least, when they take BSD code to put in their OS, the guys at Microsoft respect the licence. Some Linux guys do not (see link in port #2).
(IANAL) As I understand it, no BSD developer has ever released any code under a dual BSD and Microsoft license. That's the difference. MS and Apple and whatever other proprietary software companies are required by law to keep the copyright notice in the software. When you release code under two alternate (and *non-compatible*) licenses, you're in a different scenario. 

And, yes, Theo says Apple's really good about giving back code. How the **** does he know? Last time I checked, it wasn't available to the public. 

Beyond that, I will absolutely agree that it was incredibly rude and very stupid for the developer in question to try to strip the BSD license (whether he did so maliciously or not). 

That said: the last I read was that the issue has been resolved, and the BSD/GPL dual-license will stay.

---

### Post by Frak on 2007-09-03
Well, I guess I can say for much of us that we try to be generous and give back, and if not, they can take improved code from us, its all open.

But it sounds like to me that he's just finding another medium to attack Linux and say OpenBSD is better.

---

### Post by Bachstelze on 2007-09-03
> **ryno519 said:**
> 
Interesting how disagreeing with you about how the use of a software license derides one of ethics, generosity and friendliness.

You don't understand my point. As I told you, the BSD licence does not say you have to give back - that's what it's all about. So, there are two kinds of people who use BSD code :

1) Those who take and not give back, which includes Windows and Linux and which you said is "perfectly acceptable" - it is indeed perfectly their right.

2) Those who do give back even when they don't have to. And I'm very sorry but any dictionary will tell you that it's the very definition of "generosity", giving when you don't have to.


> **Frak said:**
> Well, I guess I can say for much of us that we try to be generous and give back, and if not, they can take improved code from us, its all open.

No, they can't ! Because whoever modified the code decided to GPL the modifications. Once again, it is perfectly his right *but* the BSD guy who wrote the original code can *not* take it, because you cannot release GPL'd code in a non-GPL project.

---

### Post by jrusso2 on 2007-09-03
I hate to think where we would all be if we had to rely on Open BSD as a desktop operating system.

I know I would not be happy with trying to use that.  Its good for a firewall or some appliance.

---

### Post by ComplexNumber on 2007-09-04
seems like the BSD guys have been doing to linux exactly what Theo claims that linux developers have been doing. allegedly, some of the BSD guys had been stealing GPL'd code. now Theo's rant, as quoted by the OP, now makes perfect sense.
pot. black. kettle.
[http://lxer.com/module/newswire/view/85224/](http://lxer.com/module/newswire/view/85224/)
[http://thread.gmane.org/gmane.linux.kernel.wireless.general/1558/focus=1558](http://thread.gmane.org/gmane.linux.kernel.wireless.general/1558/focus=1558)



> I, Michael Buesch, am one of the maintainers of the GPL'd Linux
wireless LAN driver for the Broadcom chip (bcm43xx).
The Copyright holders of bcm43xx (which includes me) want to talk
to you, OpenBSD bcw developers, about possible GPL license and therefore
Copyright violations in your bcw driver.

We believe that you might have directly copied code
out of bcm43xx (licensed under GPL v2), without our explicit permission,
into bcw (licensed under BSD license).
There are implementation details in bcm43xx that appear exactly
the same in bcw. These implementation details clearly don't come
from the open specifications at bcm-specs.sipsolutions.net
or bcm-v4.sipsolutions.net.

We have always made and still make a great effort to keep our code clean
of any Copyright issues (cleanroom design). Please make sure you also do.

A few examples follow of what we think might be GPL violations.
This list is far from being complete.

BCW_PHY_STACKSAVE()
BCW_ILT_STACKSAVE()
bcw_stack_save()
bcw_stack_restore()
These functions are a possible implementation of the specs when
they say "backup/restore a value".
Yet, it looks like you had exactly the same idea implementing this
generic description that I had.

bcw_set_opmode()
This function does not appear in the specifications.
I think Jiri Benc wrote it initially (and gave it its name) and
I extended it.

bcw_leds_switch_all()
is not in the specs, but a pure implementation detail of bcm43xx.

bcw_sprom_read()
This is obviously copied. Even the error message string is similiar.

bcw_phy_calc_loopback_gain()
I think it's no coincidence that you also decided to name the backup
variables like
    uint16_t backup_phy[15];
    uint16_t backup_radio[3];
    uint16_t backup_bband;

bcw_phy_init_pctl()
    uint16_t saved_batt = 0, saved_ratt = 0, saved_txctl1 = 0;
    int must_reset_txpower = 0;

bcw_phy_xmitpower()
Attenuation adjustment algorithms (while loops).

bcw_phy_lo_g_state()
This exactly matches bcm43xx, although the specs only have an abstract
description and diagram of the state machine.

bcw_phy_lo_g_deviation_subval()
/* XXX bcm43xx_voluntary_preempt() ? */
Nice comment there.
You might want to grep bcw for the string "bcm43xx"
and you will find more of them.

... and all the rest.

We'd like to have this issue resolved.
In general we are not against having a free (and BSD licensed) driver
in the BSD operating system. But you __have__ to cooperate with us if you'd
like to take our code and relicense it under BSD license. We intentionally
put the code under GPL license. We did __not__ do this, because "everybody
does this". We did this, among other reasons, because we
[citing Michael, Mon, 26 Dec 2005 13:03:44 +0100]
"don't think we should allow proprietary vendors to take our code
and close it again."

[citing Michael, Date unknown]
"What if Broadcom decides to take our LO measure state machine and
put it into the original driver? (The Rev Engineers told me they have
a very different weird solution for this in their code).
I really don't want to see this happen."

We'd like to offer you to start cooperating with us.
We respect you and your Copyright. You should also do so on our work.

We would not be opposed to relicensing parts of our code under the BSD
license on an explicit case-by-case base.
So if you ask "May I use this and that function" and if I own the
Copyright on that particular function, I will approve or deny your request.
Other Copyright holders of the bcm43xx code might act the same way.

We're not out for blood, just for a fair resolution.
We'd like you to start contacting us to resolve the issue now.

Have a nice day.--

---

### Post by Frak on 2007-09-04
> **jrusso2 said:**
> I hate to think where we would all be if we had to rely on Open BSD as a desktop operating system.

I know I would not be happy with trying to use that.  Its good for a firewall or some appliance.
I think I ran it on my toaster once, you know, just to make sure nobody "Hacked" it.

---

### Post by Bachstelze on 2007-09-04
@CN > Very true. So what can we conclude ? That Theo is no angel and neither is Linus nor anyone else. But the fact that Theo was obviously wrong in that Broadcom driver affair does not mean he cannot be right in another one.

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> You don't understand my point. As I told you, the BSD licence does not say you have to give back - that's what it's all about. So, there are two kinds of people who use BSD code :

1) Those who take and not give back, which includes Windows and Linux and which you said is "perfectly acceptable" - it is indeed perfectly their right.

2) Those who do give back even when they don't have to. And I'm very sorry but any dictionary will tell you that it's the very definition of "generosity", giving when you don't have to.

No, I understand your point just fine. I simply do not agree.

If a programmer wants to release code which uses or is derived from BSD code under a GPL license and release it to the public, he or she shouldn't be berated for not being generous. They simply chose their license of preference, which the BSD allows them to do. They also released code to a community free of charge, which is generous.

Again, I fail to see the problem. The license isn't violated and the code is released to the opensource community under the programmers license of choice.

---

### Post by tbroderick on 2007-09-04
> **ComplexNumber said:**
> seems like the BSD guys have been doing to linux exactly what Theo claims that linux developers have been doing. 
--

OpenBSD. FreeBSD is civilized. :)

---

### Post by Dimitriid on 2007-09-04
Such a pissing contest of egos, Id be happy if my code would get used, in fact id be happy to publish anonymously as a matter of fact.

---

### Post by Frak on 2007-09-04
Getting angry at someone for not being generous is known as selfishness.

Theo is looking like a great candidate right about know.

---

### Post by hanzomon4 on 2007-09-04
So what, they complain because the bsd license allows one to take and not give back? Isn't that what folks have been saying all along is a major weakness in the bsd licenses ability to protect freedom?

Regardless it's not stealing when you play by the rules, so don't hate the player hate the game? I think yes.

---

### Post by ComplexNumber on 2007-09-04
> **HymnToLife said:**
> @CN > Very true. So what can we conclude ? That Theo is no angel and neither is Linus nor anyone else. But the fact that Theo was obviously wrong in that Broadcom driver affair does not mean he cannot be right in another one.
it merely means that what he has said in the first post in this thread has no substance whatsoever.

---

### Post by Iandefor on 2007-09-04
It's a non-issue.

The license in ath5k reads:> Alternatively, this software may be distributed under the terms of the GNU General Public License ("GPL") version 2 as published by the Free Software Foundation.A person who wants to redistribute ath5k can do so under the terms of BSDL *or* GPLv2. Jiri Slaby is fully within his rights to redistribute under the GPLv2 under the terms of the license, and since he's redistributing under the GPLv2 *and not BSDL*, it only makes sense to change the code he redistributes to make it clear that the recipients of ath5k from Jiri are bound by GPLv2 and not by BSDL.

The arrangement is perfectly *legal*.

Theo's arguments from consistency with the Libre software ethic would only be relevant to developers who are in kernel development for ethical reasons, who (to the best of my knowledge) aren't very numerous in the kernel.

---

### Post by Bachstelze on 2007-09-04
Okay, this ill be my last message here, as most of you guys apparently fail to see the point, which pretty much proves it.

> **ryno519 said:**
> Again, I fail to see the problem. The license isn't violated and the code is released to the opensource community under the programmers license of choice.

No. The code is release to the GPL community. Any Open Source project using another licence cannot have it. As simple as that.

---

### Post by SunnyRabbiera on 2007-09-04
well for business a BSD style license might be beneficial, even I work with a modded version of it for some of my stuff.
this kind of arguing gets us nowhere, and its a shame when we have to do bash fests against eachother

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> Okay, this ill be my last message here, as most of you guys apparently fail to see the point, which pretty much proves it.



No. The code is release to the GPL community. Any Open Source project using another licence cannot have it. As simple as that.

"Fail to see the point" or "Fail to agree with me"?

Because as I said, I get your point, I just don't agree with you.

The GPL community is part of the opensource community last I checked.

---

### Post by Bachstelze on 2007-09-04
> **Iandefor said:**
> 
The license in ath5k reads:A person who wants to redistribute ath5k can do so under the terms of BSDL *or* GPLv2. Jiri Slaby is fully within his rights to redistribute under the GPLv2 under the terms of the license, and since he's redistributing under the GPLv2 *and not BSDL*, it only makes sense to change the code he redistributes to make it clear that the recipients of ath5k from Jiri are bound by GPLv2 and not by BSDL.

I guess you're wrong because the [SFLC](http://en.wikipedia.org/wiki/SFLC) said exactly the opposite and the two licenses are back in the files :

[http://marc.info/?l=linux-wireless&m=118857712529898&w=2](http://marc.info/?l=linux-wireless&m=118857712529898&w=2)

Indeed, Nick chose to redistribute the code under the GPL, and the GPL explicitly says that anyone who reditributes GPL code must pass on *all* the rights he has. Nick had the right to redistribute under the BSD licence, he must therefore also give that right. And anyway, because Jiri is the copyright owner of his code and Nick only of his, Nick cannot change the licence of Jiri's code. Legal problem solved...


> **ryno519 said:**
> 
The GPL community is part of the opensource community last I checked.

Yes. But is not the open source community as a whole. Thus you're wrong when you say the code is released "to the open source community".

---

### Post by Cynical on 2007-09-04
Theo's points don't make any sense. He always speaks of the BSD license as being more open and free than the GPL, and then complains when code isn't returned. It would be nice if people didn't pretend to be more altruistic than they are.

---

### Post by p_quarles on 2007-09-04
> **HymnToLife said:**
> most of you guys apparently fail to see the point, which pretty much proves it
I have a background in sentential logic and classical rhetoric. What you're saying here can be paraphrased thus:
"Ubuntu end-users mostly seem to think that it's legally okay -- if not exactly friendly -- to take code that is released under a radically unrestrictive license, expand upon that code, and then decline to share those expansions with the original developers. They believe that this is legally okay because the radically unrestrictive license under which the code was originally released explicity allows anyone to do this. Because Ubuntu end-users think this is okay, Linux kernel developers are hypocrites."

I'd give that a D at best.

---

### Post by yabbadabbadont on 2007-09-04
Besides which, there have been what, 10 or 15 distinct posters to this thread.  That is hardly a representative sample of "Ubuntu users".  ;)

---

### Post by Iandefor on 2007-09-04
> **HymnToLife said:**
> I guess you're wrong because the [SFLC]("http://en.wikipedia.org/wiki/SFLC") said exactly the opposite and the two licenses are back in the files :

[http://marc.info/?l=linux-wireless&m=118857712529898&w=2](http://marc.info/?l=linux-wireless&m=118857712529898&w=2)

Indeed, Nick chose to redistribute the code under the GPL, and the GPL explicitly says that anyone who reditributes GPL code must pass on *all* the rights he has. Nick had the right to redistribute under the BSD licence, he must therefore also give that right. And anyway, because Jiri is the copyright owner of his code and Nick only of his, Nick cannot change the licence of Jiri's code. Legal problem solved...I stand corrected, then.

Serves me right for being lazy, mostly uninterested in the case in the first place, and trusting Alan Cox's legal judgment.

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> 
Yes. But is not the open source community as a whole. Thus you're wrong when you say the code is released "to the open source community".

No, thus I'm right that it's released to the open source community. By your own admission the GPL community is part of the open source community. Anybody can use the code, or they can choose not to if they want to use an incompatible license.

---

### Post by Bachstelze on 2007-09-04
> **Cynical said:**
> Theo's points don't make any sense. He always speaks of the BSD license as being more open and free than the GPL, and then complains when code isn't returned.

It is, precisely because it allows people not to return the code. But, as I already said, Theo is no more angel than you or me, and after years and years of giving and getting almost nothing back, I fully understand his reaction. GPL people are cool, they force people to give back. Obviously, they can't be frustrated. I guess it's the good way to go if you want a fully-featured OS, as counting only on human generosity seems to be a bit too much, you have to push it a little...

---

### Post by Frak on 2007-09-04
HymnToLife, does any of your responses have to do with you releasing something under the BSD license and getting bad PR for it?

Because if Theo gets mad, well boo-hoo, If you can't stand the heat, stay in the shade.

---

### Post by Bachstelze on 2007-09-04
> **ryno519 said:**
> No, thus I'm right that it's released to the open source community. By your own admission the GPL community is part of the open source community. Anybody can use the code, or they can choose not to if they want to use an incompatible license.

And the GPL people know very ell that the BSD people will not be able to use it. It's a bit like giving candy to someone who has an allergy to sugar. "Why are you telling me I'm not generous when I give you candy ? You could eat it if you wanted to. Oh, it will make you sick ? Not my business, I gave it to you, period."

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> And the GPL people know very ell that the BSD people will not be able to use it. It's a bit like giving candy to someone who has an allergy to sugar. "Why are you telling me I'm not generous when I give you candy ? You could eat it if you wanted to. Oh, it will make you sick ? Not my business, I gave it to you, period."

I have a better analogy. 

It's like giving somebody code and telling them they can do whatever they like with it as long as they attach the original copyright notification to it and then complaining when they do whatever they like with it and only attach the original copyright notification to it.

I never did get analogies...

---

### Post by Bachstelze on 2007-09-04
I think it's more expressing one's disappointment and frustration than complaining. At least, that's how I feel it myself. Tell me, say you're a Linux developper, you spot a piece of BSD code that looks nice, you make a few modifications to it. What do you do ? Release your modifications under GPL or under BSD licence so it can benefit to the original author, too. Tell me, honestly.

---

### Post by yabbadabbadont on 2007-09-04
> **HymnToLife said:**
> you make a few modifications to it.

You would have to make significant, innovative, modifications before you would be able to do any re-licensing of your own.

Edit: To answer your question, personally, I would stick to whatever license was originally used.  This is what I would hope others would do when making major changes to code that I have written.

Edit2: But if I chose to release my code under a license such as the BSD license, then I wouldn't complain if someone decided to exercise their rights as granted by that license.

---

### Post by Iandefor on 2007-09-04
edit: nevermind.

---

### Post by jpkotta on 2007-09-04
OK, Theo is right about [this]("http://lkml.org/lkml/2007/8/28/157").  It is bullocks to take out that notice, or to just replace a license.  Shameful.

HOWEVER, Theo's points about Linux devs dual licensing code and making it impossible to share the other way, well that's TFB.  They (BSD) use a license that allows it, so they should just be quiet and admire all of the freedom.

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> I think it's more expressing one's disappointment and frustration than complaining. At least, that's how I feel it myself. Tell me, say you're a Linux developper, you spot a piece of BSD code that looks nice, you make a few modifications to it. What do you do ? Release your modifications under GPL or under BSD licence so it can benefit to the original author, too. Tell me, honestly.

If I made **significant** changes to the code I would probably release it under the same license I release most of my code under, the GPL. The original author is entitled to the code he wrote, I'm entitled to the code I wrote and can release it under any compatible license I please. The original author really shouldn't mind, because if he released it under the BSD license he said I could do exactly that.

---

### Post by Bachstelze on 2007-09-04
> **ryno519 said:**
> If I made **significant** changes to the code I would probably release it under the same license I release most of my code under, the GPL. The original author is entitled to the code he wrote, I'm entitled to the code I wrote and can release it under any compatible license I please. The original author really shouldn't mind, because if he released it under the BSD license he said I could do exactly that.

Indeed, he said you could do that, hoping you would be kind enough to give back even when nothing forces you to do so. But apparently, that's a bit too much to ask to most people...

And when I say "give", I mean, really, "give". Not "under this and that condition".

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> Indeed, he said you could do that, hoping you would be kind enough to give back even when nothing forces you to do so. But apparently, that's a bit too much to ask to most people...

Perhaps he was just hoping somebody would use and enjoy his code. Perhaps he doesn't care how it's used. Perhaps a dozen other reasons he released his code. The point is he said I could use it the way that I used it. I don't recall there being a grief clause in the BSD license one must be subjected to if they release derived works under a different license.

---

### Post by Polygon on 2007-09-04
they released the code under the bsd licence. If they didnt want people to take the code, and not give back, why did they licence it under the bsd licence in the first place? its hypocritical.

Sure it might not be FRIENDLY if they dont contribute back, but they arnt doing anything 'wrong', its just how the licence was written

as many people have stated before, if they are getting in a tussy that no one is contributing back to their code, then maybe they should of licensed it with something that forces them to give back.

---

### Post by Bachstelze on 2007-09-04
> **Polygon said:**
> 
Sure it might not be FRIENDLY if they dont contribute back, but they arnt doing anything 'wrong', its just how the licence was written


Precisely. It is not FRIENDLY. And that, to me, is enough to make it 'wrong', even though it is perfectly legal. I guess this is what comes between us ;)

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> Precisely. It is not FRIENDLY. And that, to me, is enough to make it 'wrong', even though it is perfectly legal. I guess this is what comes between us ;)

Just because something isn't friendly doesn't make it unfriendly. Perhaps using code people say we can use isn't tantamount to stealing. Just maybe. And maybe using code that we have consent from the owner to use so we can create something for end users is 'right'. I'm not finding a reason to think that not releasing derived works under the BSD is wrong, because nobody even asked us to. If BSD developers are having a problem with this on mass then they should release under a different license. If they keep saying we can release derived works under different licenses, guess what, we'll keep releasing derived works under different licenses, as it is a freedom the BSD license grants. It's also a freedom BSD developers seem to be quite proud of... most of them anyway.

---

### Post by Bachstelze on 2007-09-04
> **ryno519 said:**
> Just because something isn't friendly doesn't make it unfriendly.

To me, it does. Especially in the Open Source world where we should rather all cooperate to do away with M$ and friends, instead of locking others away from using allegedly-"open source" code.

And as I understood it, Theo only spoke of stealing referring to the Linux devs stripping the BSD licence away from the code, which was indeed illegal, and he was right. Just like the Linux people were right when they complained about a BSD developper stealing their code, and just like Theo was wrong in making excuses for him. Just because someone is wrong one day doesn't mean he cannot be right the day after.

---

### Post by Bachstelze on 2007-09-04
As a side-note, I am quite amazed by the level of correctness this thread remains at. I admit I feared it would degenerate into a flamewar but that does not seem to be the case...

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> To me, it does. Especially in the Open Source world where we should rather all cooperate to do away with M$ and friends, instead of locking others away from using allegedly-"open source" code.

And as I understood it, Theo only spoke of stealing referring to the Linux devs stripping the BSD licence away from the code, which was indeed illegal, and he was right. Just like the Linux people were right when they complained about a BSD developper stealing their code, and just like Theo was wrong in making excuses for him. Just because someone is wrong one day doesn't mean he cannot be right the day after.

To you, it might. Lucky for the rest of us the wording of the BSD and GPL license is clear enough to determine what both sides consider right and wrong. For instance, the BSD license doesn't consider releasing derived works under a different license wrong, therefore it can be assumed that doing so would not offend the author of the code who knowingly released his work under that license.

If I take a piece of BSD'd code and significantly change it and release it under the GPLv3 license, am I being unfriendly to the original author? Have I prevented him from using his original code? Have I used his code in a way he forbid me from using it? No, I haven't. I have not done a thing that he didn't say was perfectly, 100% acceptable for me to do with his code. To me, this is not in the least bit unfriendly. I'm completely in the limits of what the original developer said wouldn't bother him. If it does bother him, well, he should have said something earlier.

---

### Post by Bachstelze on 2007-09-04
If you don't *feel* you're doing something wrong, well, nothing we can do about it. I, personnaly, do feel wrong when I'm given something and give nothing back, regardless of what the person who gave me that thing feels about it.

[i]"Imagine all the people / Sharing all the world...
You may say I'm a dreamer / But I'm not the only one. / I hope someday, you'll join us / And the world can be as one."[/i]

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> If you don't *feel* you're doing something wrong, well, nothing we can do about it. I, personnaly, do feel wrong when I'm given something and give nothing back, regardless of what the person who gave me that thing feels about it.

[i]"Imagine all the people / Sharing all the world...
You may say I'm a dreamer / But I'm not the only one. / I hope someday, you'll join us / And the world can be as one."[/i]

You will hardly sway me with a song I hate. ;)

---

### Post by Bachstelze on 2007-09-04
> **ryno519 said:**
> You will hardly sway me with a song I hate. ;)

That pretty much sums it all up ;)

---

### Post by ryno519 on 2007-09-04
> **HymnToLife said:**
> That pretty much sums it all up ;)

The fact that I think John Lennon is overrated as a solo artist? :)

---

### Post by tbroderick on 2007-09-04
> **ryno519 said:**
> 
If I take a piece of BSD'd code and significantly change it and release it under the GPLv3 license, am I being unfriendly to the original author? Have I prevented him from using his original code? Have I used his code in a way he forbid me from using it? No, I haven't. I have not done a thing that he didn't say was perfectly, 100% acceptable for me to do with his code. To me, this is not in the least bit unfriendly. I'm completely in the limits of what the original developer said wouldn't bother him. If it does bother him, well, he should have said something earlier.

I'd say it's unfriendly. Not wrong, illegal or in violation of the license, but  unfriendly. If you wrapped GPL code around a OpenBSD driver, then OpenBSD would not be able to incorporate your changes. I think the intent of the original author is clear when they choose a BSD style license. There's nothing 'wrong' with wrapping GPL code around it, but you better believe the BSD community will call you out.

---

### Post by hanzomon4 on 2007-09-04
If you think it's unfriendly or wrong fine, but put the blame on the license that allows it.

---

### Post by tbroderick on 2007-09-04
> **hanzomon4 said:**
> If you think it's unfriendly or wrong fine, but put the blame on the license that allows it.

Who's blaming the BSD license?

---

### Post by DoktorSeven on 2007-09-04
Sorry, but if you wanted modifications to your code to be shared back, you should have chosen a license that requires this.  I have no sympathy for people who willingly choose the BSD license (or any license, for that matter) and then complain when the terms of the license isn't what they want.

That's the bottom line here.  You release under the BSD license, you have to expect people to take your code and use it without necessarily sharing back.  This is how the BSD license is.

---

### Post by Fbot1 on 2007-09-04
That's not illegal at all. When software is dual-licensed you can choose which terms you want to use. For example Opera doesn't need to be dual-licensed just because it uses Qt. Even if it was who cares? OpenBSD is crap anyway.

---

### Post by Miguel on 2007-09-04
Although I think Theo is partially right on this one, he loses all credibility when he calls the linux devs thieves. I think it was he alone who created a huge flamewar on the OpenBSD mailing lists with the bcm43xx author not because Michael was wrong, but because, to him, it looked like he was calling the openbsd developer a thief. It is then ironic that, 8 months later, he starts calling the linux devs thieves. Theo might say that *GPL folks started first*, but falling below their level makes all his posts on the bcm43xx thread void.

Regarding the license, I have really no idea. I'm a physicist, not a lawyer. That might influence my decission of keeping both licenses. While I might not like that somebody else takes the code to make it proprietary (does he still have to release his code under both licenses?) I respect the time the original author has saved me. If he is a BSD user, it is only fair that he can use my "improvements".

> OpenBSD is crap anyway.
Crap? Why? Their security record doesn't precisely point it that way.

---

### Post by Celegorm on 2007-09-04
So, it's not a problem for Apple to take BSD code, modify it, and release it under their own license, but when people do the same thing with the GPL it's bad?

---

### Post by fuscia on 2007-09-04
doesn't the GPL just keep a BSD designer from re-releasing code under the BSD license? i also don't understand how something can be dual licensed if there are conflicting provisions in those licenses.

---

### Post by Ozor Mox on 2007-09-04
This makes no sense. They licensed the code under the BSD license knowing full well that it allows this, and the GPL doesn't. If they have a problem with code being taken, why does the BSD license allow it?

---

### Post by Miguel on 2007-09-04
> **fuscia said:**
> doesn't the GPL just keep a BSD designer from re-releasing code under the BSD license?

Indeed. *THE* clause for distributing GPL code is attaching the GPL, which is incompatible with the BSD license.

>  i also don't understand how something can be dual licensed if there are conflicting provisions in those licenses.

Neither do I. And there's the case of Firefox, with its wonderful triple license. The only thing that seems clear to me is that the reason of dual-licensing low-level code is basically to help both the BSD and Linux users.

---

### Post by brentoboy on 2007-09-04
The compatability is a one way compatability.

The BSD license says (more or less) I retain the copyright on this, but you can use it however you want, and redistribute it under whatever license you want, so long as you give me some credit for my work.

GPL says that if you redistribute this, you have to keep it open, and you have to keep it GPL (the code I wrote, and the code I have mixed it with must be redistributed open source or not at all)

if something is bsd it does not restrict another developer redistributing it as GPL along with the extensions written by the gpl developer.

but, once it is gpl'd the freedom offered by the BSD license cannot be offered becuase bsd allows people to close their changes to the code if they redistribute it.

so, gpl can "wrap" bsd licensed code, it is compatable in that way.
but bsd cannot wrap a piece of gpl code and offer all the freedoms that bsd promises.

the whole thing comes back to the querstion:   what is more free?  freedom to do whatever you want with the code?  or freedom to use it however you want, but a requriement to keep it (and all derivatives) free.

I believe the restrictions on the GPL are what makes linux grow so much faster than bsd's.  So many more people are wlling to contributue code, if they know that it will remain open.   

And, if you think about it, the BSD guy here is essentially saying "I wish that I could enjoy the same benefits for changes to my own code that GPL guys enjoy when they publish their code."   Effectively, he is right to feel ripped off, he cant use extensions to his own code written by other people.   But, think about it....  if you want the benefits the GPL offers, GPL your dang code, then there is no conflict.

He has every right in the world to feel like people are running off with his code and not giving back.   But, he invited them to do so, so I dont get the problem.  The BSD guys could turn around and say "its now all GPL" and next year no one would care any different -- the two licenses only exist because historically, they existed.  Dropping BSD and going full force GPL would make both systems so much better becuase they could combine the best of both without all the bickering.

(that's what I think -- I'm probably wrong)

---

### Post by 23meg on 2007-09-04
[QUOTE=brentoboy](that's what I think -- I'm probably wrong)[/QUOTE]

You're so right that you're almost wrong.

---

### Post by starcraft.man on 2007-09-04
Wow, this really filled up pages fast. Just finished reading all of it. 

Amazing how similar this sounds to RMS and his near crusade to get people to say GNU/Linux everywhere. Don't get me wrong, nothing wrong with him informing people about how GNU and Linux (the kernel) have both played important roles in the OS. It's when he goes on rants/tirades against people who say Linux with no standing/enforceability/clause (in the GPL or anything else) that people must do so. I might add that I often use GNU/Linux interchangeably with Linux. I don't do so though because RMS indoctrinated me or because I feel forced by a license but because I think it's right.

Now as to this topic, it's very much the same as you can see. Theo can uses the BSD license (as others do), he can also tell people it's nice when you give back what you take (whether with just a BSD or a dual license). This going out and actively berating people who wrap their significant modifications in GPL though is just as annoying as RMS. He's got no justification to stand on and tell people they must contribute back their modifications. This changing licenses outright (like stripping BSD for GPL or vice versa) is obviously wrong and that can (and should) be enforced, it is a separate matter though not to be confused with the former.

As for it being "morally wrong" to license significant changes under just the GPL  (thus precluding it from BSD) I say it depends on how you look at it (as does most morality). Take X code for example and project Y was dual licensed, then let us stipulate that X will benefit Y in both performance and features if incorporated (the guy saw all the flaws in Y and corrected them). X is then licensed under the GPL only. Has anything wrong been done? I believe one can successfully argue no, nothing has. 

The GPL code is an improvement and the GPL side of Y will get the improvement, thus making them happy. The BSD side of Y is not hurt or otherwise made worse for wear, neither do they benefit from the changes. Directly they remain neutral. The BSD side may believe they were betrayed/hurt by not having the new code, this however is stemming from a sense of entitlement. You see there are three instances to be compared I suppose in the minds of some people. In the first the code is never released, no one is made happier. In case two, the code is GPLed only and the GPL side benefits while the BSD does not (remaining neutral). In the third, the code is dual licensed so that both may employ it making everyone happy.

The anger/resentment as I see it that the BSD folks have is "relative" to the third case where everyone is happy (the ideal case to some). In the "absolute" (by absolute I mean lowest happiness worst and most best) sense though more people were made happy by case 2 than were in the first case where no one has anything better. Thus, as has been shown before morality is really what you make of it. Incidentally, that's also why enforcing/legislating morality has been so hard for some governments...

Oh and personally I'm not taking sides on this BSD/GPL thing (just pointing out what I see). I think I'm a bit confused, the two licenses seem so completely incompatible that it boggles my mind how people dual license projects. By dual licensing it seems you nullify GPLing it as people can just use the BSD version of your code and forget about the clauses stipulated in the GPL version. So doesn't dual licensing effectively mean your licensing under BSD with a second token license under GPL that people can just ignore? If not, someone please correct me... I will certainly read up on this a bit more.

---

### Post by Anthem on 2007-09-04
> **jpkotta said:**
> OK, Theo is right about [this]("http://lkml.org/lkml/2007/8/28/157").  It is bullocks to take out that notice, or to just replace a license.  Shameful.
But it was caught by the Linux developers before the code ever made it into the tree.  And none of the BSD guys ever complained on the LKLM lists, they just wrote up complaints and forwarded them to everybody in the known world.  I mean, they'd posted it on the front page of Slashdot before notifying the Linux devs.

Contrast that to what happened just a couple months ago when GPL'd Linux Kernel code was found in Theo's BSD.  The kernel guys posted a polite notice on their list saying "We believe you may be using some of our code.  This isn't allowed, but we'd be willing to dual-license if you're interested" and Theo went ballistic and claimed the Linux devs were "inhuman."

The dude has issues.

---

### Post by @trophy on 2007-09-04
> **brentoboy said:**
> Dropping BSD and going full force GPL would make both systems so much better because they could combine the best of both without all the bickering.

(that's what I think -- I'm probably wrong)


Yeah, but that's tantamount to saying "Things would be so much easier if they would just cave to our demands."  Which, although true, is hardly helpful.  The BSD people have a different philosophy than the GPL people, and I think this case points out why we need both.

The GPL was made to make sure that the Mongolian hordes couldn't get ahold of our code.  Think of it as open source's Great Wall.  It lets in any code that wants to come in, at the price of being shackled with the gpl for all eternity.  This seems extreme, and it is, but it's that way because there are determined, competent attackers at the gates who are a lot better funded than us, and would like nothing more than to squash open source to help their own bottom line.

The BSD is more of a "We're all adults here.  Use this code for whatever you need it for, just give me credit and don't come crying to me when it blows up." license.  And we need that, if for no other reason than the fact that RMS's personal crusade will, from time to time, get in the way of some work that we're trying to do.

Each license is a tool designed to do a certain thing, and we need to hold onto both.  In other words, there's a reason there's both a microwave *and* an oven in your kitchen.

---

### Post by Miguel on 2007-09-04
> **Anthem said:**
> Contrast that to what happened just a couple months ago when GPL'd Linux Kernel code was found in Theo's BSD.  The kernel guys posted a polite notice on their list saying "We believe you may be using some of our code.  This isn't allowed, but we'd be willing to dual-license if you're interested" and Theo went ballistic and claimed the Linux devs were "inhuman."
.

And they were inhuman because... they supposedly called the BSD dev a thief. Cool.

As a side note, a plus 1 for atrophy. I subscribe to that post.

---

### Post by Bachstelze on 2007-09-04
I shouldn't have mentioned Theo, it seems some people are talking about him rather than the reall issue...

Forget about Theo, forget about the BSD and GPL, forget about everything and tell me. Do you feel, in the bottom of your hearts, that it is okay, when you're given something, to just take it and give nothing back ? If you do, well, feel free to do it, the BSD license allows this. But I really, sincerely pity you. And I hope you're not acting this way with your real-life friends, or you'll end up alone in no time.

---

### Post by Ozor Mox on 2007-09-04
But that's what the license says people can do with it! That is the freedom that it provides, total with no copyleft, so although I understand them being a bit peeved at their code being taken and nothing being given back, how can they complain about it?

It's like I put some stuff on a table in my front garden with a sign saying "free stuff, take what you want"...and then get all angry when I go out there a few hours later and it's all gone!

---

### Post by vexorian on 2007-09-04
I find it laughable that the people that adore permissive licenses over GPL are now complaining that X organization is... doing whatever they want to with code that is licensed with their permissive license...

If you wanted a viral license... you should have used a viral license...

---

### Post by Miguel on 2007-09-04
> **HymnToLife said:**
> I shouldn't have mentioned Theo, it seems some people are talking about him rather than the reall issue...

Forget about Theo, forget about the BSD and GPL, forget about everything and tell me. Do you feel, in the bottom of your hearts, that it is okay, when you're given something, to just take it and give nothing back ? If you do, well, feel free to do it, the BSD license allows this. But I really, sincerely pity you. And I hope you're not acting this way with your real-life friends, or you'll end up alone in no time.

As said before, I am a physicist. I publish my work so that others advance further based on what (little) I've done. Having my work quoted is a reason to be proud, and actually a way to measure how good someone is. Do I look like taking code and not giving back? That would be like making a wonderful discovery and then keep it secret.

---

### Post by @trophy on 2007-09-04
> **Ozor Mox said:**
> It's like I put some stuff on a table in my front garden with a sign saying "free stuff, take what you want"...and then get all angry when I go out there a few hours later and it's all gone!


LOL that reminds me of the yard sale my wife and I had a little while ago.  I decided to get rid of some of my old linux discs (I have tried just about every distro at one time or another, and had a whole spindle full of discs) so in an effort to spread the love I put the spindle out on one of the tables with a sign that said "Free", hoping that people would take one.  
Well, some computer-nerd type guy and his wife picked over our whole sale, insulting all of our stuff, and then he bought one 50 cent item, and after insulting some of the linux distributions represented in the stack, proceeded to take the whole effing spindle.  
I was mad, because then nobody else that came to our garage sale could have the use of those old versions of Slackware, etc, and they're probably going to just sit on that dude's desk doing nothing just like they sat on mine doing nothing.  
It especially made me mad later when some old guy was there asking about some problems his computer was having and we told him about Ubuntu, but I couldn't give him a disc because the other dude had already taken the spindle.

Next time I'm going to add "Take _one_." to my "Free" sign.

---

### Post by 23meg on 2007-09-04
[QUOTE=HymnToLife]Do you feel, in the bottom of your hearts, that it is okay, when you're given something, to just take it and give nothing back ?[/QUOTE]

If the giver has generously stated in advance "You can take whatever you want, without feeling obliged to give anything back", of course, yes. 

And if your analogy is with real world commodities, it doesn't really work, since you're not depriving anyone of their BSD licensed code when you "take" it, and the act of making code available isn't the equivalent of actively giving someone something.

---

### Post by Ozor Mox on 2007-09-04
You shouldn't have let him take it. When he asked why not, just alter the sign to say "Free - except to annoying computer nerds who won't use them"! :)

I would no way have let him take them after that!

---

### Post by Bachstelze on 2007-09-04
> **23meg said:**
> If the giver has generously stated in advance "You can take whatever you want, without feeling obliged to give anything back", of course, yes. 

Well, I don't. And neither does Theo, it seems. I guess we have "issues"... We expect the people to be generous, how silly of us !

---

### Post by brentoboy on 2007-09-04
> **@trophy said:**
> Yeah, but that's tantamount to saying "Things would be so much easier if they would just cave to our demands."  Which, although true, is hardly helpful.  

I'm not saying they should just do things our way, they can do whatever they like, and there is something to be said for both licenses.  

My point is that it sure sounds like they want the benefits of GPL (always having access to improvements made by others).   And, all they have to do to have those benefits is to go GPL. 

And, to be quite honest, I think the main reason they don't go GPL has more to do with sticking to your original guns and less to do with whether or not it is better.   When a bunch of egos get together and disagree with each other for several years about what is "best,"  it seems that sooner or later it is more about winning and less about what works the best.

The biggest problem is that there really is something to be said for both licenses.  but maybe the compatabilty between them is more imporatant than the benefits of either all by itself.

---

### Post by 23meg on 2007-09-04
> **HymnToLife said:**
> Well, I don't. And neither does Theo, it seems. I guess we have "issues"... We expect the people to be generous, how silly of us !

And the point is, if you expect all people to be generous all the time, you should say so in your license. A software license isn't just a scrap of legalese; it carries with it whole implications as to what kind of social structures will form around the software licensed with it.

---

### Post by Bachstelze on 2007-09-04
> **brentoboy said:**
> 
My point is that it sure sounds like they want the benefits of GPL (always having access to improvements made by others).   And, all they have to do to have those benefits is to go GPL. 

This is simply because this benefit of the GPL comes at a high cost : that the code is not available to everyone anymore. Not worth it, if you ask me.

But how about the other way around ? If they released their modifications under the original licence ? It would change nothing to them, one way or the other, the code would still be theirs to use. The only difference is that in one case, others could use it too, and in the other, thay couldn't. And, after all, that's what the GPL is all about, isn't it ? Locking people from using the code...

> **23meg said:**
> And the point is, if you expect all people to be generous all the time, you should say so in your license.

No. Because the very definition of generosity is giving even when *nothing* forces you to do so. How is it generous to give back when the license says you *must* do it ? And if they just added a line that said "Okay, you can do whatever you want but we would appreciate if you contributed back.", do you really think it would change anything to what people do ?

---

### Post by jrusso2 on 2007-09-04
Theo chose the license he wants to use.  If he doesn't like it then he should use GPL

---

### Post by starcraft.man on 2007-09-04
> **HymnToLife said:**
> This is simply because this benefit of the GPL comes at a high cost : that the code is not available to everyone anymore. Not worth it, if you ask me.

This depends how and what you define as "worth it". Some think the clauses of the GPL are more important than free access to everyone (many believe the GPL to be what keeps it mostly free). Others like you think openness to all parties comes first. Difference of opinion and both sides have merits/issues.
> 
But how about the other way around ? If they released their modifications under the original licence ? It would change nothing to them, one way or the other, the code would still be theirs to use. The only difference is that in one case, others could use it too, and in the other, thay couldn't. 

Then they would be using the BSD license and nullify the existence/purpose of the GPL (if applied to a large enough portion of the GPL projects). As I stipulated above this doesn't sit well with some people. And it most certainly would change things. It would mean that as is happening now others (whoever they may be, corporate or otherwise) could do what you don't like, take without giving (on a larger scale I imagine). That is the nature of the permissiveness of the BSD (as I've read it) and whether you (or Theo) like it or not people will likely always do it no matter how much you despise/pity/scold them. Because they can. The same reasons we (humans) do a lot of things (as a society, I'm not saying what you or I would do).
> 
And, after all, that's what the GPL is all about, isn't it ? Locking people from using the code...
That certainly isn't the purpose of the GPL as I read it, maybe you should have a second look?

> 
No. Because the very definition of generosity is giving even when *nothing* forces you to do so. How is it generous to give back when the license says you *must* do it ? And if they just added a line that said "Okay, you can do whatever you want but we would appreciate if you contributed back.", do you really think it would change anything to what people do ?
To counter this point Hymn, I direct you to my previous post (which it seems few people read/responded to... page 8) and my example. By it, code X was voluntarily licensed under the GPL, which helped out all the GPL people. No one forced him to license it this way, thus a case could be made that he was generous in both coding (with his free time) and in releasing it to the GPL folks (even if the BSD ones were snubbed). The simple fact is that from this view point, the BSD side never had the code so there isn't any entitlement to it (as you seem to think).

Oh and I believe quite a strong case could be made for the definition of generous being completely independent of whether it was voluntary or forced giving.

In the end the two licenses are different views of freedom. BSD believes in "let everyone have it and trust them to do whatever they like". GPL believes in "you may have our code so long as you respect the freedoms enshrined (enforced) in the license". They represent the two different models of freedom as a concept that exists, anarchy and social order by agreement. They are largely incompatible and yet as has been shown by the "one way street", the former can be encompassed within the later with less difficulty.

Well, I believe I've dealt with this issue of moral when it comes to the BSD/GPL discussion. Anything else to add?

---

### Post by BoyOfDestiny on 2007-09-04
> **HymnToLife said:**
> This is simply because this benefit of the GPL comes at a high cost : that the code is not available to everyone anymore. Not worth it, if you ask me.

But how about the other way around ? If they released their modifications under the original licence ? It would change nothing to them, one way or the other, the code would still be theirs to use. The only difference is that in one case, others could use it too, and in the other, thay couldn't. And, after all, that's what the GPL is all about, isn't it ? Locking people from using the code...



No. Because the very definition of generosity is giving even when *nothing* forces you to do so. How is it generous to give back when the license says you *must* do it ? And if they just added a line that said "Okay, you can do whatever you want but we would appreciate if you contributed back.", do you really think it would change anything to what people do ?

This is so false. The GPL never takes code from anyone. You can always view it, access it, study it. ALWAYS. When a company takes BSD code (which is permitted as BSD is a very permissive license.) you can't get the code anymore. Ask Apple or Microsoft. They've closed up the developers work, and now they [BSD] are stuck competing against it.

Not to mention the developers who licensed their code under GPL could dual license it BSD if they wanted too... It still belongs to them. They aren't treated like a doormat.

For BSD programmers to complain, hey, they took our code (even though the license allows it! and claim this as a benefit!) turn around say the GPL is viral yadda yadda. 

Yeah GPL is lock-in. It ensure you can always access, modify, build upon the code provided everyone gets the same right. BSD does not guarantee that. That's why GPL is a more a popular license several times over. Developers are not doormats. 

Do not whine about people taking your work, if you chose a license that allows it. I believe many people who do like that. If you write BSD code expecting things in return, choose a different "stricter" license. The GPL ensures a tit for tat...

Sheesh...

---

### Post by tbroderick on 2007-09-04
> **BoyOfDestiny said:**
> This is so false. The GPL never takes code from anyone. You can always view it, access it, study it. 

Not true. What happens if a Linux developer warps GPL code around an OpenBSD driver? OpenBSD is locked out of all the GPL code. They can see it, but can't use it. 

Yes, a dual-license solves the problem. Not everyone wants their GPL code to be dual-licensed though.

Of course BSD developers can complain. They complain when corporations don't give back too. Or about  firmware. Or  Intel. Or whatever. Just cause the choose a BSD license doesn't mean they can't complain. 

The GPL is viral. That's one of the reasons some developers choose a BSD license. Do you not think it would be a little hypocritical for GPL code to be wrapped around BSD code? One of the biggest gripes with the BSD license is there is no clause that forces derived code to remain BSD. The BSD license gives them the choice to give back or not. GPL proponents want you to choose the GPL because it ensures derived code will also be GPL, but when given the opportunity to ensure BSD code will remain BSD, they choose otherwise.

---

### Post by BoyOfDestiny on 2007-09-04
> **tbroderick said:**
> Not true. What happens if a Linux developer warps GPL code around an OpenBSD driver? OpenBSD is locked out of all the GPL code. They can see it, but can't use it. 

Yes, a dual-license solves the problem. Not everyone wants their GPL code to be dual-licensed though.

Of course BSD developers can complain. They complain when corporations don't give back too. Or about  firmware. Or  Intel. Or whatever. Just cause the choose a BSD license doesn't mean they can't complain. 

The GPL is viral. That's one of the reasons some developers choose a BSD license. Do you not think it would be a little hypocritical for GPL code to be wrapped around BSD code? One of the biggest gripes with the BSD license is there is no clause that forces derived code to remain BSD. The BSD license gives them the choice to give back or not. GPL proponents want you to choose the GPL because it ensures derived code will also be GPL, but when given the opportunity to ensure BSD code will remain BSD, they choose otherwise.

The point is they can still see the code. Have an easier time reverse-engineering it, re-implementing (and the code can get taken again by a GPL'er or Company and close it!!!)

Seriously, it's not hypocritical. If a BSD dev is upset this happens, they should pick a different license. I imagine some are very happy that their code can be "everywhere".

Now it is hypocritical for a BSD dev to complain. Here is why.
Blah blah the GPL is viral, BSD is SO MUCH better, since you are free to use it how you like...

Um guys... GPL and companies are using our code... and we can't get it back... This is disingenuous.

You cannot on the one hand say, our license is better since it's more Free, then complain when people utilize it as such.

As for the viral argument, sorry I'm a bit heated, it's just BSD and MS proponents use a similar argument. So I'm going to say I like this aspect of the GPL, however one can allow exceptions in the GPLv3. Case in point, Audacious switched to GPLv3, and made an exception for plugins to be any license...

Besides, a dev that contributes to a GPL project knows that's the way things work. They aren't tricked. Either you like BSD being so permissive or you don't. Pick a different license.

---

### Post by vexorian on 2007-09-04
> Not true. What happens if a Linux developer warps GPL code around an OpenBSD driver? OpenBSD is locked out of all the GPL code. They can see it, but can't use it. they are the ones who chose not to use the GPLed code, nobody is forcing them to use the BSD license.

---
This is the deal: The spirit of the BSD is to allow anyone do whatever they want with it, because, as I thought, the interest of a program being released as BSD is that the program is used and adapted by as much people as possible. Which is an objective totally different to code that can be used by everyone and can be modiffied as long as the changes can return back to the original source, which is the GPL purpose. I really think it is quite odd that people that make BSD code are complaining about people taking their code and not giving it back, it is quite lame to see them complaint against the GPL for what is actually a problem with their own license,

It seems they wanted something 'viral' that ensures that the code remains the way they wanted it to be, they didn't want the BSD license.

---

### Post by @trophy on 2007-09-04
> **vexorian said:**
> It seems they wanted something 'viral' that ensures that the code remains the way they wanted it to be, they didn't want the BSD license.

Either that or they wish the "something viral" wasn't necessary, and people would return the good faith just to be good human beings?

The situation is thus:  You have just written a piece of software.  You were going to only release it under BSD, but then you decided to be nice and GPL it to so that I could use it too.  Then, I used your code to make another program, and decided to release it GPL only instead of dual licensing my program so that I could return the good faith that you showed me.

You'd be pissed.  There wouldn't be a thing you could do about it, but you'd be pissed.  And you'd have every right to be.

---

### Post by BoyOfDestiny on 2007-09-04
> **@trophy said:**
> Either that or they wish the "something viral" wasn't necessary, and people would return the good faith just to be good human beings?

The situation is thus:  You have just written a piece of software.  You were going to only release it under BSD, but then you decided to be nice and GPL it to so that I could use it too.  Then, I used your code to make another program, and decided to release it GPL only instead of dual licensing my program so that I could return the good faith that you showed me.

You'd be pissed.  There wouldn't be a thing you could do about it, but you'd be pissed.  And you'd have every right to be.

If you give things freely and advertise the fact as a beneft, and EXPECT something in return... Prepare to be upset pretty often.

---

### Post by p_quarles on 2007-09-04
There's certainly nothing wrong with BSD coders asking for code to be returned so that they can benefit from it. The only thing I really dislike is this apparent tendency on the part of BSD devs to equate naive idealism with the moral high ground.

I hold myself to pretty high standards of behavior, or at least try to. That does not lead me to expect that everyone else I encounter will hold themselves to those same standards. This means: I read the lease before signing it, I make eye contact with drivers before crossing the street, and I use a long WPA2 passkey on my wireless router. 

It strikes me that a lot of the pro-BSD arguments (though not the good ones, of which there are many) are similar to old anarchist ideals: once you get rid of restrictions, people will no longer feel the need to steal, cheat and lie. Again, very naive. The GPL, on the other hand, is more in the tradition of Enlightenment reason: one person's freedom ends where another's begins.

---

### Post by vexorian on 2007-09-04
> The situation is thus: You have just written a piece of software. You were going to only release it under BSD, but then you decided to be nice and GPL it to so that I could use it too. Then, I used your code to make another program, and decided to release it GPL only instead of dual licensing my program so that I could return the good faith that you showed me.

Thanks for enlightening me, now the issue is way clearer. When "I" dual licensed something "I" forket it and thus changes could come only to one side of the work, If I didn't expect that as a possibility I should have kept a single license. "I" can't rely on good faith and the thing is that this isn't really about good faith either, it is about GPLd code staying GPL, there was no obligation or anything to do. It was "I" who made it GPL in the first place.

---

### Post by @trophy on 2007-09-04
> **BoyOfDestiny said:**
> If you give things freely and advertise the fact as a beneft, and EXPECT something in return... Prepare to be upset pretty often.

Pretty often, but not all the time.  Most people are inconsiderate pricks, but not all.

Look at it this way... the guy was gonna write stuff BSD only but then thought "Eh, it's no skin off my nose to GPL it too... so I'll do that."  Then when they were done with their project, they just went ahead with GPL-only, despite the fact that it is *even less* of a pain for them to add BSD than it was for the BSD guy to add GPL.  I suspect that they did so without thinking.  And that's why they can correctly be labeled "inconsiderate."

---

### Post by vexorian on 2007-09-04
> **vexorian said:**
> Thanks for enlightening me, now the issue is way clearer. When "I" dual licensed something "I" forket it and thus changes could come only to one side of the work, If I didn't expect that as a possibility I should have kept a single license. "I" can't rely on good faith and the thing is that this isn't really about good faith either, it is about GPLd code staying GPL, there was no obligation or anything to do. It was "I" who made it GPL in the first place.
Of course, unless "I" actually made a shortighted mistake and thought that if "I" dual licensed it I would get both sides work for me and then just show my true color later expecting the work for either of the licensed versions to go to both versions. "I" am the guy who mistakenly thought "I" could exploit developers by using this trick...

---

### Post by @trophy on 2007-09-04
> **p_quarles said:**
> It strikes me that a lot of the pro-BSD arguments (though not the good ones, of which there are many) are similar to old anarchist ideals: once you get rid of restrictions, people will no longer feel the need to steal, cheat and lie. Again, very naive. The GPL, on the other hand, is more in the tradition of Enlightenment reason: one person's freedom ends where another's begins.

Yeah I think the whole licenses/political ideas analogy is a good one, and that's exactly why I have some uneasiness with the GPL (though I still like it the best out of any open source licenses).  The one part of the Enlightenment that I disagree with most is the idea that life is a zero-sum game.  
I think that some people are actually evil, but most do things that hurt the group simply because they don't think.  If they were ever shown that playing nice is mutually beneficial, they'd start doing so.  And then everyone would benefit, which would mean an increase in the total amount of good, which would mean life isn't a zero-sum game.

---

### Post by 23meg on 2007-09-04
> **HymnToLife]No. Because the very definition of generosity is giving even when nothing forces you to do so. How is it generous to give back when the license says you must do it ? [/QUOTE]

It's either a matter of semantics, or the whole endeavor that includes all software ever licensed under BSD-like licenses relies upon the notion of naive generosity in a near-ideal world. If the latter is the case, I don't live in that world said:**
> And if they just added a line that said "Okay, you can do whatever you want but we would appreciate if you contributed back.", do you really think it would change anything to what people do ?

Depends on the people, and the context, the culture they're working in. Which of course would be heavily influenced by the license to which you'd add that clause. With the BSD-style licenses, I don't think it would. 

[QUOTE=p_quarles]There's certainly nothing wrong with BSD coders asking for code to be returned so that they can benefit from it. The only thing I really dislike is this apparent tendency on the part of BSD devs to equate naive idealism with the moral high ground.[/QUOTE]

Agreed, almost.

---

### Post by @trophy on 2007-09-04
> **vexorian said:**
> Of course, unless "I" actually made a shortighted mistake and thought that if "I" dual licensed it I would get both sides work for me and then just show my true color later expecting the work for either of the licensed versions to go to both versions. "I" am the guy who mistakenly thought "I" could exploit developers by using this trick...

I'd like to buy an "I"!

BTW sorry if using you in my example offended you.  That wasn't my intent at all.  Just trying to put faces on my simplified example.

---

### Post by vexorian on 2007-09-04
I used to admire the BSD guys with such a license and the ideal that their work should be for everyone even letting others lock them out later. I thought it was kind of noble, instead of the more practical GPL which ensures that a community owns the thing and wouldn't let anyone close it. 

I actually released projects under the zlib license which is awesomely close to the BSD license.

This situation makes me feel dissappointed at this since I am seeing a lot of BSD people complaining for others "taking and not giving back" which until today I thought was the intention of the BSD license not to restrict people from doing that. I find it very odd that BSD license supporters seem to be right now attacking people who did that, if they were consistent with the idealism of the BSD license they wouldn't be complaining, and there is not really a reason to complaint about it, unless BSD supporters actually think it is "right" to expect something in return, which does not make any sense for code that uses that license.

It is quite bizare that the very supporters of the BSD license seem to actually want a more "restrictive" license themselves.

---

### Post by dca on 2007-09-04
I dunno', it appears to me the sole purpose of RMS' GPL was to prevent at any cost the possibility of future great software, ie:  Linux kernel, glibc, x, gnome, etc, whatever, amen, becoming Windows Server 2010 (or TiVO for that matter, LOL)...
 
Everything else is ancillary.  It sounds a lot like sour grapes on Theo's side but before the flames start at me I can see his point of view.  Way back when I did some 8 bit programming in business basic primarily for property management systems (in hotels).  My main concern when licensing was the possibility of someone stealing it and reaping the rewards.  Not the rewards of taking it and making it better but the eventuality they'd take it make something better or add to it, close source it, and make money off of it when I wasn't able to....

---

### Post by brentoboy on 2007-09-04
> **HymnToLife said:**
> But how about the other way around ? If they released their modifications under the original licence ? 
...
And if they just added a line that said "Okay, you can do whatever you want but we would appreciate if you contributed back.", do you really think it would change anything to what people do ?

I think there is something to be said or that.
It does seem to me that, if a "linux" dev takes a piece of code that is licensed under BSD, it makes sense to turn around and give their changes back to the BSD crowd under a BSD license.

Even if they end up turning around and using that piece of code in a larger GPL project that requires that the GPL apply to the code when it is distributed as part of the Linux project.

It is kind of rude to make open source changes to someone else's open source code, and then, not let them get the full benefit of those changes.    I certainly agree that grabbing a chunk of BSD code and modifying it and then not returning your mods to the original author under the same level of freedom that he gave you is rude and unthankful.

But, obviously, to use a chunk of BSD code in a GPL program requires that you turn around and release the whole thing under the dual license (aka GPL with a "thank you BSD" statement).

---

### Post by @trophy on 2007-09-04
> **dca said:**
> Way back when I did some 8 bit programming in business basic primarily for property management systems (in hotels).  My main concern when licensing was the possibility of someone stealing it and reaping the rewards.  Not the rewards of taking it and making it better but the eventuality they'd take it make something better or add to it, close source it, and make money off of it when I wasn't able to....


Yeah, but if you did this "way back when" and haven't touched it in years, then if someone else figures out how to make money off of it, good for them.  It's not like you would have done so if they didn't.  Yeah, you'll be mad that you didn't think of it first, but that happens to me whenever other people figure out how to make money whether they use my code or not.

---

### Post by Bachstelze on 2007-09-04
I don't know how many times I've repeated this yet so this will be the last one.

> **vexorian said:**
> 
It is quite bizare that the very supporters of the BSD license seem to actually want a more "restrictive" license themselves.

**No, they don't !** What they want, or rather hope, is that people will play it nice and contribute back without being forced to do so ! **Just because you can does not mean you should, and neither does it mean it's okay.** The fact that people will take the code and not give back is a necessary evil if you want to put as few restrictions as possible. And a necessary evil is still evil.

---

### Post by Fbot1 on 2007-09-04
They are not not giving back and they have plenty of reasons to not dual-license it.

---

### Post by Bachstelze on 2007-09-04
> **Fbot1 said:**
> They are not not giving back and they have plenty of reasons to not dual-license it.

Thanks for this very interesting in-depth analysis.

---

### Post by Fbot1 on 2007-09-04
> **HymnToLife said:**
> Thanks for this very interesting in-depth analysis.

You're welcome.

---

### Post by Steveway on 2007-09-04
> I think there is something to be said or that.
It does seem to me that, if a "linux" dev takes a piece of code that is licensed under BSD, it makes sense to turn around and give their changes back to the BSD crowd under a BSD license.

Even if they end up turning around and using that piece of code in a larger GPL project that requires that the GPL apply to the code when it is distributed as part of the Linux project.

It is kind of rude to make open source changes to someone else's open source code, and then, not let them get the full benefit of those changes. I certainly agree that grabbing a chunk of BSD code and modifying it and then not returning your mods to the original author under the same level of freedom that he gave you is rude and unthankful.

But, obviously, to use a chunk of BSD code in a GPL program requires that you turn around and release the whole thing under the dual license (aka GPL with a "thank you BSD" statement).
Well but they clearly say: "Here is our code, take it, do whatever the heck you want with it, you don't need to give us back anything." -basically the BSD-license
If they really wanted to get back what they gave then they should have said: "Here is our code, take it, do whatever you want but if you change anything then give us the changes under the same requirements." -basically the GPL
It's their choice, they made the choice and now they say  "Wähhh wähhh, they are stealing our code and don't give anything back."
How stupid is that? If you have choosen the BSD-license for your code then you should know what the posibillities are and that includes that people are going to use your code and that they don't give anything back.
I, as a rational thinking person, don't mind that this is "morally" not the nicest thing.

---

### Post by dca on 2007-09-04
> **@trophy said:**
> Yeah, but if you did this "way back when" and haven't touched it in years, then if someone else figures out how to make money off of it, good for them.  It's not like you would have done so if they didn't.  Yeah, you'll be mad that you didn't think of it first, but that happens to me whenever other people figure out how to make money whether they use my code or not.

Indeed...  However, we can't all be one of the twenty thousand programmers on MS' payroll.  Things changed when people (or companies) started programming or writing programs for Windows specifically instead of an OS agnostic programming language or converting projects to OS agnostic platforms.  Hence, why MS' attempt at their open-source initiative is an exercise in hilarity.  The way things have become since that time with how fast the BSD project and Linux kernel project have grown is you not only have to be a programmer, you have to be a politician.

---

### Post by Tom Mann on 2007-09-04
hmmm....


OK my first question here is are BSDL and GPL compatible with one another?

Second: If so, what connects them and what is the result; If not why are developers releasing under both licences?

Third: If they are and developers are releasing under both licences? What is the point of complaining about the issue when the developer is the number one authority on how their code is used; and has first word in changing the licence if the existing agreement causes issues?

I'm sorry, HymnToLife, unless you are a developer, you have no say in this. If you are, and truly believe this of the GPL, then change your licences pronto.

NB: Sorry if I've copied any posts, especially after page 7 when I got fed up of reading the same arguments. I personally believe we have a fanperson in our midst.

---

### Post by tbroderick on 2007-09-04
> **dca said:**
> I dunno', it appears to me the sole purpose of RMS' GPL was to prevent at any cost the possibility of future great software, ie:  Linux kernel, glibc, x, gnome, etc, whatever, amen, becoming Windows Server 2010 (or TiVO for that matter, LOL)....

Xorg is MIT/X11 not GPL.

---

### Post by Bachstelze on 2007-09-04
> **Tom Mann said:**
> I'm sorry, HymnToLife, unless you are a developer, you have no say in this. If you are, and truly believe this of the GPL, then change your licences pronto.

Thanks for the kind words of advice but I didn't wait for you to go as far away as I could from the GPL.

---

### Post by dca on 2007-09-04
> **tbroderick said:**
> Xorg is MIT/X11 not GPL.

sorry.

---

### Post by tbroderick on 2007-09-04
> **Steveway said:**
> If you have choosen the BSD-license for your code then you should know what the posibillities are and that includes that people are going to use your code and that they don't give anything back.


Do GPL developers only give back code because they are forced to or because it's a good development model?

---

### Post by Steveway on 2007-09-04
> **tbroderick said:**
> Do GPL developers only give back code because they are forced to or because it's a good development model?

Don't ask me.
Ask the developers.
But it certainly is a little bit from both.

---

### Post by Tom Mann on 2007-09-04
> **HymnToLife said:**
> Thanks for the kind words of advice but I didn't wait for you to go as far away as I could from the GPL.

Ok. One last question. Why are you on the website of a GPL Product?

---

### Post by @trophy on 2007-09-04
> **Tom Mann said:**
> Ok. One last question. Why are you on the website of a GPL Product?

Because ubuntu's a good piece of software?  It does what it's supposed to do and tries to stay out of the way of the user.

Also, there's lots of licenses represented in ubuntu.  Not just the GPL.

---

### Post by Bachstelze on 2007-09-04
> **Tom Mann said:**
> Ok. One last question. Why are you on the website of a GPL Product?

That's an *excellent* idea for the GPLv4 ! "Any individual using a non-GPL license for his or her code may not visit the website of a GPL product." Great ! You should submit that pronto.

---

### Post by Fbot1 on 2007-09-04
> **HymnToLife said:**
> That's an *excellent* idea for the GPLv4 ! "Any individual using a non-GPL license for his or her code may not visit the website of a GPL product." Great ! You should submit that pronto.

It was a question.

---

### Post by Bachstelze on 2007-09-04
> **Fbot1 said:**
> It was a question.

Think I'm too dumb to read between the lines, do you ? But let's answer the question, since it seems of utter importance to know why I'm here : simply because I like Ubuntu and the whole "humanity" spirit behind it. As simple as that. And if you don't like me liking Ubuntu even though I disagree with the licence most of it's software is distributed under, there's nothing I can do about it.

---

### Post by Fbot1 on 2007-09-04
> **HymnToLife said:**
> Think I'm too dumb to read between the lines, do you ? But let's answer the question, since it seems so important to know why I'm here : simply because I like Ubuntu and the whole "humanity" spirit behind it. As simple as that. And if you don't like me liking Ubuntu even though I disagree with the licence most of it's software is distributed under, there's nothing I can do about it.

See, that wasn't all that hard.

---

### Post by @trophy on 2007-09-04
Whoa people... the conversation's getting a little unfriendly in here.
Let's debate without getting mad at each other.

To quote the almost-never-right MOG "It's *software*, for God's sake!"

---

### Post by koenn on 2007-09-04
There seems to be a rather broad consensus that a BSD-license says "here's what I made, do with it what you want", and that you can even re-license it under more restrictive terms. 
If that's what the BSD license says, then taking BSD-licensed code, use it to create a derivative, or just modify it, and redistribute the result under any other license, would be OK. No amount of pittyful "it's sooo unfair" and naive "why can't we all just share" whining is going to change that. Licences are legal agreements - like contracts. If you're going to rely on an unspoken, un-mentioned, purely assumed gentlemen's agreements to "give back", you had better make sure that the other party is aware of such an agreement. 


So, I had a Look at **a **bsd-style license : It does clearly say :
> * Redistribution and use in source and binary forms, with or without 
 * modification, are permitted [B]provided that the following conditions
 * are met:[/B]
 * 1. Redistributions of source code [B]must retain the above copyright
 *    notice, this list of conditions and the following disclaimer.[/B]
 * 2. Redistributions in binary form [B]must reproduce the above copyright
 *    notice, this list of conditions and the following disclaime[/B]r in the
 *    documentation and/or other materials provided with the distribution.

One *could* assume that the requirement to retain the license when redistributing, in fact means that a BSD-licensed needs to be redistributed under a BSD-license, and nothing else. 

That makes BSD licenses just as viral as the GPL  (!)

- but it puts De Raadt etc in the right : you can not re-license BSD-licensed code under GPL. You could, arguably, license your own modifications : additions / .... under a license of your choosing. 

A major difference witt e.g. GPL is that BSD licenses **don't require** that you provide source code when you distribute binaries. 
So you could take BSD code, adapt it, compile it, and distribute it (in, say, a winsock.dll implementing BSD TCP/IP to go with your proprietary OS or a proprietary network application - not uncommon in the 90's ) without any obligation to provide the source code, (but whoever obtains that winsock.dll can re-use and redistribute it as he sees fit, under the BSD license.)

So, maybe those BSD people have a point. 
More in-depth analiysis here : [http://www.groklaw.net/article.php?story=20070114093427179](http://www.groklaw.net/article.php?story=20070114093427179)

---

### Post by Steveway on 2007-09-04
Sorry but I just laughed out loud irl because of @trophys post.
Nothing against your post or against you but it just reminded me of something:



[IMG]http://img126.imageshack.us/img126/1079/neeeeeeerdski7.jpg[/IMG] Neeeeeeeeeeeeeeeeerds!

I'm a nerd myself and I'm proud, but this thread is so ... well... yes.

---

### Post by @trophy on 2007-09-04
> **Steveway said:**
> 

[IMG]http://img126.imageshack.us/img126/1079/neeeeeeerdski7.jpg[/IMG] Neeeeeeeeeeeeeeeeerds!

I'm a nerd myself and I'm proud, but this thread is so ... well... yes.

God I love that movie...

---

### Post by afonic on 2007-09-04
> **HymnToLife said:**
> 
**No, they don't !** What they want, or rather hope, is that people will play it nice and contribute back without being forced to do so ! **Just because you can does not mean you should, and neither does it mean it's okay.** The fact that people will take the code and not give back is a necessary evil if you want to put as few restrictions as possible. And a necessary evil is still evil.

Thats right but you don't see to the other side.

You are a Linux developer. You take some BSD code, improve it, add new bits to it and then release it as BSD again. Now, you have spend MANY hours doing so but feel proud for it.

Then one day, lets say Orange comes, takes your code (which is BSD licensed), makes a few changes and releases iStupid, a great program based 99% on your code with kinky GUI. They are cool. You are not.

Now would that have happened if you used GPL? Maybe it would, but then you could have Orange's code as well.

What I am trying to say is that since you release your code under BSD you should not bitch if you don't get the improvements made by someone else back, because that someone may decide he needs to protect his work with GPL.

You want to get them, YES the right thing is to get them but the choice is not in your hands to make. Just because that other guy may not want to release his improvements under BSD license.

Thats why imho "Linux steals my BSD code" is bullshit.

---

### Post by Bachstelze on 2007-09-04
> **afonic said:**
> Thats why imho "Linux steals my BSD code" is bullshit.

Once again, the "Linux stealing our code" referred to Linux developper stripping the BSD license out of BSD licensed code without the author's permission, as described here :

[http://lkml.org/lkml/2007/8/28/157](http://lkml.org/lkml/2007/8/28/157)

Yes, this is a violation of the BSD license, and it is illegal, and it is stealing. And yes, there have been cases of BSD developpers stealing Linux code as well, and it was wrong. But it doesn't make Linux devs stealing BSD code right either.


Linux developpers taking BSD code, modifying it and releasing their modifications under the GPL *while keeping the original licence as required* is indeed *not* stealing, and no one ever said it was. But once again, you cannot expect people who give and are given nothing back to be OK with it and not tell you you're not playing it nice when you don't give back. Companies like Apple and M$ are not plaing it nice, Linux dev know it, BSD devs know it as well, and there's nothing either side can do about it.
What the Linux guys can do, however, is not acting like M$ and giving back, so that both sides can benefit from the work of each other. And if M$ benefits from it as well, well, M$ are the bad guys, they're acting bad, that's the normal state of things. Just ignore them and concentrate on the benefits the open source community *as a whole* could gain if everyone was acting friendly.

---

### Post by Fbot1 on 2007-09-04
> **koenn said:**
> you can not re-license BSD-licensed code under GPL.

That's not true, all that means is that you must retain the the copyright (which is to retain the copyright). The GPL requires that and more so it's entirely legit.

---

### Post by mikerduffy on 2007-09-04
> **Fbot1 said:**
> It was a question.

[http://en.wikipedia.org/wiki/Rhetorical_question](http://en.wikipedia.org/wiki/Rhetorical_question)

> **HymnToLife said:**
> Once again, the "Linux stealing our code" referred to Linux developper stripping the BSD license out of BSD licensed code without the author's permission, as described here :

[http://lkml.org/lkml/2007/8/28/157](http://lkml.org/lkml/2007/8/28/157)

Yes, this is a violation of the BSD license, and it is illegal, and it is stealing. And yes, there have been cases of BSD developpers stealing Linux code as well, and it was wrong. But it doesn't make Linux devs stealing BSD code right either.
No one seems to want to address this because it's much easier to rip on Straw Man de Raadt.  Just because Theo stated his opinion that a lot of GPL devs don't want to share, that doesn't mean there's anything wrong with the BSD license.  What is wrong is using fanaticism as an excuse to break the law, à la Rodriguez.

---

### Post by userundefine on 2007-09-04
> **HymnToLife said:**
> I know most people here are on the GPL side - for noble reasons, I hope -, so I want to ask them something. Does it not make you feel bad when you see that some people are using the GPL to take and not give back ? Sure, it is perfectly legal, but from an ethical point of view ? It certainly would, for me.
This is a pretty trite example and double standard.  Thousands of companies have probably taken from BSD code without giving anything back or even telling them.  They improve upon the code or use it for their own purposes and give nothing back, using whatever proprietary license they want.  BSD is OK with that, but it's not OK with people doing it when they put their modifications under a GPL license?  Why, because they can "see" the modifications whereas they wouldn't with a proprietary license?

The fact of the matter is their oh-so-FREE license states point blank that this is permissable, and if they wanted the changes contributed back under a BSD license the license should reflect that.  But oh, wouldn't that actually be the GPL?

There is nothing unethical about it whatsoever.  If a developer does not fully understand the terms of the license they choose to release a piece of software under, they shouldn't use it.  Period.

BTW, I have no problem with the BSD license, and whatever a developer chooses to use is fine by me.

(Furthermore, as addendum, the original author of the code that dual-licensed it himself said he did so so the code could be made gpl-only if someone wanted.  All this argument is just idle chatter.)

---

### Post by Bachstelze on 2007-09-04
> **userundefine said:**
> 
(Furthermore, as addendum, the original author of the code that dual-licensed it himself said he did so so the code could be made gpl-only if someone wanted. )

... wich is wrong. And if you watch the copyright notices, there has been BSD-only contributions prior to Jiri deciding to dual-license his. And those had been stripped out as well.

---

### Post by izanbardprince on 2007-09-04
> **HymnToLife said:**
> Okey dokey, so you think it's "perfectly acceptable" for Linux to act just as bad as Windows.

Thanks, that's all I wanted to know :)

Please.

Like Linux is doing anything worse than Apple, who took BSD, turned it into Mac OS, and never gave anything back at all.

---

### Post by Fbot1 on 2007-09-04
> **mikerduffy said:**
> [url]http://en.wikipedia.org/wiki/Rhetorical_question

Yeah, I never was very good with those, lol.

> **izanbardprince said:**
> Please.

Like Linux is doing anything worse than Apple, who took BSD, turned it into Mac OS, and never gave anything back at all.

They gave Darwin.

---

### Post by koenn on 2007-09-04
> **Fbot1 said:**
> 
 Originally Posted by koenn
you can not re-license BSD-licensed code under GPL.
---
That's not true, all that means is that you must retain the the copyright (which is to retain the copyright). The GPL requires that and more so it's entirely legit.

The reasoning is as follows : 

A/ They could have placed in the public domain, but they didn't : they explicitely expressed the "terms and conditiopns of use" in a license

B/ The license says that these "terms and conditions" (the copy right,  the permission to redistribute, the warranty disclaimer) needs to be repeated when redistributing. Imo, this implies that "you have the right to redistrubute provided you allow the same to your recipients". 

Try this one : 
1 - 
If someopne would redistribute unmodified BSD-code 
but remove the "copyright [owner], [year], All rights reserved" part of the notice , would you consider him in violation of the license ? 

2- 
If someopne would redistribute unmodified BSD-code 
but remove the disclaimer ("THIS SOFTWARE IS PROVIDED ... "AS IS" AND ANY WARRANTIES, INCLUDING ... FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. ") , would you consider him in violation of the license ? 

3- 
If someone would redistribute unmodified BSD-code 
but removes the "Redistribution and use in source and binary forms, with or without modification, are permitted" statement, 
would you consider him in violation of the license ? 

4-
If someone added additional requirements / restrictions / conditions to the list of conditions, would you consider him in violation of the license ? 

4-is the tricky one, and I'm glad I'm not a lawyer. But one could argue that adding additional restrictions (such as those imposed by GPL) alters the license the original copyrigh holders attached to it, while their express desire that their conditions be retained upon redistribution indicates they don't want alteration of these conditions.

---

### Post by Bachstelze on 2007-09-04
If the code has not been modified, it is obvious that you cannot wrap another licence around it, since you're not the copyright holder... You cannot change the licensing terms of a work that is not yours. 1, 2 and 3 are copyright violoations as well, since you don't comply with the terms of the license, which is the *sine qua non* condition to legally redistribute the code.

---

### Post by userundefine on 2007-09-04
> **HymnToLife said:**
> ... wich is wrong. And if you watch the copyright notices, there has been BSD-only contributions prior to Jiri deciding to dual-license his. And those had been stripped out as well.
I think most acknowledge that removing the BSD copyright is wrong.  And, the patch wasn't accepted.  So, insofar as this situation is concerned, it's irrelevant to the discussion at hand as set out in your original post.

I skipped 17 pages, so I don't know whether or not you agree with the rest of my post.

---

### Post by p_quarles on 2007-09-04
> 4- If someone added additional requirements / restrictions / conditions to the list of conditions, would you consider him in violation of the license ? 

4-is the tricky one, and I'm glad I'm not a lawyer. But one could argue that adding additional restrictions (such as those imposed by GPL) alters the license the original copyrigh holders attached to it, while their express desire that their conditions be retained upon redistribution indicates they don't want alteration of these conditions.
That's actually the main point on which the GPL and the BSDL differ. You *can *add certain kinds of restrictions to code that operates on top of BSD software. The obvious example is OS X. It is proprietary software, and can't be freely distributed. The BSD kernel on top of which it was built, however, is available (in its pre-Apple modified form) to anyone, either as a binary or as source. 

The GPL simply wouldn't allow that. You can certainly develop proprietary software that runs in Linux, but if it's integration with Linux works by modifying a GPL'd project (GTK+, the kernel, etc.), then the developers are required to make the source code available.

I'm not a lawyer either, but that's my understanding.

---

### Post by Bachstelze on 2007-09-04
> **userundefine said:**
> 
I skipped 17 pages, so I don't know whether or not you agree with the rest of my post.

I don't. We all agee that the Linux devs have the right to GPL-only their modification. The BSD license permits this. However, you say it's not unethical, I say it is. Simply because, especially in the Open Source world where we should all cooperate for the good of the whole community, I think that not acting friendly is acting unfriendly. And because I don't like to repeat myself, you'll have to go through the few previous pages to read more about it, if you're interested.

---

### Post by WishingWell on 2007-09-04
> **HymnToLife said:**
> Everyone please forget what others might have told you about Theo being a complete A-hole and have a read :

```
From: Theo de Raadt <deraadt <at> cvs.openbsd.org>
Subject: That whole "Linux stealing our code" thing
Newsgroups: gmane.os.openbsd.misc
Date: 2007-09-01 01:40:52 GMT (3 days and 47 minutes ago)

[bcc'd to Eben Moglen so that people don't flood him]

I stopped making public statements in the recent controversy because
Eben Moglen started working behind the scenes to 'improve' what Linux
people are doing wrong with licensing, and he asked me to give him
pause, so his team could work.  Honestly, I was greatly troubled by
the situation, because even people like Alan Cox were giving other
Linux developers advice to ... break the law.  And furthermore, there
are even greater potential risks for how the various communities
interact.

For the record -- I was right and the Linux developers cannot change
the licenses in any of those ways proposed in those diffs, or that
conversation (http://lkml.org/lkml/2007/8/28/157).

It is illegal to modify a license unless you are the owner/author,
because it is a legal document.  If there are multiple owners/authors,
they must all agree.  A person who receives the file under two
licenses can use the file in either way....  but if they distribute
the file (modified or unmodified!), they must distribute it with the
existing license intact, because the licenses we all use have
statements which say that the license may not be removed.

It may seem that the licenses let one _distribute_ it under either
license, but this interpretation of the license is false -- it is
still illegal to break up, cut up, or modify someone else's legal
document, and, it cannot be replaced by another license because it may
not be removed.  Hence, a dual licensed file always remains dual
licensed, every time it is distributed.

Now I've been nice enough to give Eben and his team a few days time to
communicate inside the Linux community, to convince them that what
they have proposed/discussed is wrong at a legal level.  I think that
Eben also agrees with me that there are grave concerns about how this
leads to problems at the ethical and community levels (at some level,
a ethos is needed for Linux developers to work with *BSD developers).
And there are possibilities that similar issues could loom in the
larger open source communities who are writing applications.

Eben has thus far chosen not to make a public statement, but since
time is running out on people's memory, I am making one.  Also, I feel
that a lot of Linux "relicencing" meme-talkin' trolls basically have
attacked me very unfairly again, so I am not going to wait for Eben to
say something public about this.

In http://lkml.org/lkml/2007/8/29/183, Alan Cox managed to summarize
what Jiri Slaby and Luis Rodriguez were trying to do by proposing a
modification of a Dual Licenced file without the consent of all the
authors.  Alan asks "So whats the problem ?".  Well, Alan, I must
caution you -- your post is advising people to break the law.

I will attempt to describe in simple terms, based on what I have been
taught, how one must handle such licenses:

- If you receive dual licensed code, you may not delete the license
  you don't like and then distribute it.  It has to stay, because you
  may not edit someone's else's license -- which is a three-part legal
  document (For instance: Copyright notice, BSD, followed by GPL).

- If you receive ISC or BSD licensed code, you may not delete the
  license.  Same principle, since the notice says so.  It's the law.
  Really.

- If you add "large pieces of originality" to the code which are valid
  for copyright protection on their own, you may choose to put a different
  and seperate (must be non-conflicting...) license at the top of the file
  above the existing license.

    (Warning: things become less clear as to what the combination of
    licenses mean, though -- there are ethical traps, too).

- If you wish for everyone to remain friends, you should give code back.

  That means (at some ethical or friendliness level) you probably do
  not want to put a GPL at the top of a BSD or ISC file, because you
  would be telling the people who wrote the BSD or ISC file:

     "Thanks for what you wrote, but this is a one-way street, you give
     us code, and we take it, we give you you nothing back.  screw off."

In either case, I think a valuable lessons has been taught us here in
the BSD world -- there are many many GPL loving people who are going
to try to find any way to not give back and share (I will mention one
name: Luis Rodriguez has been a fanatic pushing us for dual licensed,
and I feel he is to blame for this particular problem).  Many of those
same people have been saying for years that BSD code can be stolen,
and that is why people should GPL their code.

Well, the lesson they have really taught us is that they consider the
GPL their best tool to take from us!

GPL fans said the great problem we would face is that companies would
take our BSD code, modify it, and not give back.  Nope -- the great
problem we face is that people would wrap the GPL around our code, and
lock us out in the same way that these supposed companies would lock
us out.  Just like the Linux community, we have many companies giving
us code back, all the time.  But once the code is GPL'd, we cannot get
it back.

Ironic.

I hope some people in the GPL community will give that some thought.
Your license may benefit you, but you could lose friends you need.
The GPL users have an opportunity to 'develop community', to keep an
ethic of sharing alive.

If the Linux developers wrap GPL's around things we worked very hard
on, it will definately not be viewed as community development.

Thank you for thinking about this.

[I ask that one person make sure that one copy of this ends up on the
linux kernel mailing list]
```

I know most people here are on the GPL side - for noble reasons, I hope -, so I want to ask them something. Does it not make you feel bad when you see that some people are using the GPL to take and not give back ? Sure, it is perfectly legal, but from an ethical point of view ? It certainly would, for me.

*P.S. : if all you're willing to answer is "stfu gpl is teh rox bsd suxorz lololol", don't bother. I have no will to read such garbage over and over again.*

I've been following this and it has left a bad taste in my mouth, i believe that if Theo's contributions were better known and not plainly stolen by others then the donations might finally come in to OpenBSD.

---

### Post by WishingWell on 2007-09-04
No matter what license, what situation or what you have to do or don't have to do, there is a right and a wrong, some people claim morality over MS while not realizing that this is the EXACT same discussion as MS stealing BSD code, yet they have no problem badmouthing MS for doing it.

Either both are right or both are wrong, which is it?

---

### Post by Anthem on 2007-09-04
Great gravy, what a thread.

Linus is an interesting dude.  I don't worship him, but I respect him.  And one of the things he points out is that the brilliance of the GPLv2 is that it doesn't rely on ideals like Freedom or Generosity, it just allows people to be themselves.  Their selfish, greedy, lazy selves.  You want to use our code?  No problem.  Just give back your changes.  You don't have to maintain them, you don't have to become a part of the community, you don't have to do anything but give back your changes.

**Of course, your own selfish self-interest is going to show you that it's better to be part of the community, since that makes everything easier for you.  **You could maintain your own fork, but it's more work.  The lazy path is also the best path:  join the community.  Play nice, not because it's morally better, but because it works.  Less noble, perhaps, but more realistic.

The weakness of BSD (and the reason the BSDs really haven't taken off like Linux has) is that anybody can buy the head developer at any time and close all of the source code.  And it's been done, repeatedly.  This is why a lot of companies (like IBM, Intel, etc) won't contribute code to the BSDs, because that code could be closed and used against them.  With Linux, they know that somebody else might use it, but they'll always have what the other guy has.

---

### Post by afonic on 2007-09-04
> **HymnToLife said:**
> I don't. We all agee that the Linux devs have the right to GPL-only their modification. The BSD license permits this. However, you say it's not unethical, I say it is. Simply because, especially in the Open Source world where we should all cooperate for the good of the whole community, I think that not acting friendly is acting unfriendly. And because I don't like to repeat myself, you'll have to go through the few previous pages to read more about it, if you're interested.

I think you are missing the point. Cooperation is good, sharing code is even better but you can decide how you want to share your code. And if you ask me, I wouldn't code a line if it was to be released under BSD for the reasons mentioned above.

So, YES you are correct not sharing back is bad and unethical but sharing back under the BSD means your code can be used by anyone, for any reason, without giving something back. Some BSD developer accepts it and keeps coding. Some GPL developer though doesn't like the idea and licenses his changes under GPL.

I see nothing wrong with that.

PS. What I am saying is general. The incident for this thread has a valid point, just the title is pretty general. "Linux is stealing our code" etc

---

### Post by WishingWell on 2007-09-04
> **HymnToLife said:**
> I shouldn't have mentioned Theo, it seems some people are talking about him rather than the reall issue...

Forget about Theo, forget about the BSD and GPL, forget about everything and tell me. Do you feel, in the bottom of your hearts, that it is okay, when you're given something, to just take it and give nothing back ? If you do, well, feel free to do it, the BSD license allows this. But I really, sincerely pity you. And I hope you're not acting this way with your real-life friends, or you'll end up alone in no time.

It seems it's more important to the people of this forum to support the GPL than it is to support what is right.

It's sad and hypocritical.

---

### Post by WishingWell on 2007-09-04
> **Anthem said:**
> Great gravy, what a thread.

Linus is an interesting dude.  I don't worship him, but I respect him.  And one of the things he points out is that the brilliance of the GPLv2 is that it doesn't rely on ideals like Freedom or Generosity, it just allows people to be themselves.  Their selfish, greedy, lazy selves.  You want to use our code?  No problem.  Just give back your changes.  You don't have to maintain them, you don't have to become a part of the community, you don't have to do anything but give back your changes.

**Of course, your own selfish self-interest is going to show you that it's better to be part of the community, since that makes everything easier for you.  **You could maintain your own fork, but it's more work.  The lazy path is also the best path:  join the community.  Play nice, not because it's morally better, but because it works.  Less noble, perhaps, but more realistic.

The weakness of BSD (and the reason the BSDs really haven't taken off like Linux has) is that anybody can buy a developer at any time and close all of the source code.  And it's been done, repeatedly.  This is why a lot of companies (like IBM, Intel, etc) won't contribute code to the BSDs, because that code could be closed and used against them.  With Linux, they know that somebody else might use it, but they'll always have what the other guy has.

READ the article, "It is illegal to modify a license unless you are the owner/author, because it is a legal document.  If there are multiple owners/authors, they must all agree.  A person who receives the file under two licenses can use the file in either way....  but if they distribute
the file (modified or unmodified!), they must distribute it with the
existing license intact, because the licenses we all use have
statements which say that the license may not be removed."

---

### Post by Anthem on 2007-09-04
> **WishingWell said:**
> READ the article, "It is illegal to modify a license unless you are the owner/author, because it is a legal document.  If there are multiple owners/authors, they must all agree.  A person who receives the file under two licenses can use the file in either way....  but if they distribute
the file (modified or unmodified!), they must distribute it with the
existing license intact, because the licenses we all use have
statements which say that the license may not be removed."
I'm not talking about the article.  Clearly the code had to stay dual-licensed, and it did.  The whole thing got worked out on the lkml lists within a day or two of the original patch submittal, and the code never even got to the tree.  It's a non-event.

But your response had nothing to do with my post.

---

### Post by Fbot1 on 2007-09-04
> **WishingWell said:**
> READ the article, "It is illegal to modify a license unless you are the owner/author, because it is a legal document["].

That's not true. Lets use this little license as an example:
[HTML]
You must buy Fbot a hotdog.
[/HTML]

Say someone agrees to this but now they want to sell it to Gbot. Gbot is not necessarily required to buy Fbot a hotdog.

---

### Post by Anthem on 2007-09-04
> **Fbot1 said:**
> That's not true. Lets use this little license as an example:
[HTML]
You must buy Fbot a hotdog.
[/HTML]

Say someone agrees to this but now they want to sell it to Gbot. Gbot is not necessarily required to buy Fbot a hotdog.
I don't think that's helpful to this situation.

---

### Post by Bachstelze on 2007-09-04
> **Anthem said:**
> I don't think that's helpful to this situation.

Me neither. And anyway, that imaginary licence is not valid. "You must buy Fbot a hotdog", what for ? To use the code ? To redistribute it ? To re-sell it ?

---

### Post by Steveway on 2007-09-04
I think he meant a license like the free-beer license.
A pretty funny license btw.

---

### Post by Bachstelze on 2007-09-04
This one ? :p

```
/*-
 * ----------------------------------------------------------------------------
 * "THE BEER-WARE LICENSE" (Revision 42):
 * <phk@FreeBSD.ORG> wrote this file.  As long as you retain this notice you
 * can do whatever you want with this stuff. If we meet some day, and you think
 * this stuff is worth it, you can buy me a beer in return.   Poul-Henning Kamp
 * ----------------------------------------------------------------------------
 *
 * $OpenBSD: kern_tc.c,v 1.7 2006/11/15 17:25:40 jmc Exp $
 * $FreeBSD: src/sys/kern/kern_tc.c,v 1.148 2003/03/18 08:45:23 phk Exp $
 */

```

---

### Post by userundefine on 2007-09-04
> **HymnToLife said:**
> I don't. We all agee that the Linux devs have the right to GPL-only their modification. The BSD license permits this. However, you say it's not unethical, I say it is. Simply because, especially in the Open Source world where we should all cooperate for the good of the whole community, I think that not acting friendly is acting unfriendly. And because I don't like to repeat myself, you'll have to go through the few previous pages to read more about it, if you're interested.
I did go read them.  The difference in the "Open Source world" is that the GPL fosters community by forcing the hand of those who want to distribute the code, thus creating a community by default.  It is indeed "viral" in that way.  The BSD license creates no community and so all contributions back are not required, and therefore do not foster community by default.  Obviously, it is not absolutely necessary that the license foster community, but it helps.  You can argue the levels of altruism in each, but considering this is what the BSD license *wants* (i.e., not forcing people to contribute, just making good code), I think it's an exaggeration to say that GPL means not giving back.  The GPL makes no restrictions on use, the explanation of which you will see under the next quote.

> I just wondered whether the average Linux user thinks it's okay to take and not give back when you have the right to do so, instead of giving back when you don't have to, just for the sake of ethics, generosity and friendliness
Well, since our language has to be specific considering the nature of our conversation, it's somewhat disingenuous to say that releasing modifications under the GPL is not giving back.  The original author can still use them -- indeed, anyone can.  Distribution is the governing issue for licensing.  Users simply using are not in any way restricted by the BSD or GPL.  So your analogies to candy making you sick really are incorrect.

---

### Post by Bachstelze on 2007-09-04
> **userundefine said:**
> 
Well, since our language has to be specific considering the nature of our conversation, it's somewhat disingenuous to say that releasing modifications under the GPL is not giving back.  The original author can still use them -- indeed, anyone can.  Distribution is the governing issue for licensing.  Users simply using are not in any way restricted by the BSD or GPL.  So your analogies to candy making you sick really are incorrect.

What do "Users simply using" have to do with anything ? Fact is, GPL-only modifications to a file that comes from BSD cannot be included back in BSD. Thus, BSD users cannot use it. My analogy is perfectly correct.

---

### Post by Celegorm on 2007-09-04
If someone spends hours of their time making substantial modifications to a program and then lets anyone who wants to use, distribute, and modify the program, albeit under a more restrictive license than the original, I really don't see how they are being selfish and immoral. Also they have their own interests to consider if they find it offensive when someone takes their code and closes the source, which the BSD license permits. They may, however, be in breach of etiquette and ruffle some feathers. It is however, clearly immoral to simply take someone else's code, make cosmetic or no changes to it, and try to slap your own license of choice on it in place of the original author's.

---

### Post by userundefine on 2007-09-04
> **HymnToLife said:**
> What do "Users simply using" have to do with anything ? Fact is, GPL-only modifications to a file that comes from BSD cannot be included back in BSD. Thus, BSD users cannot use it. My analogy is perfectly correct.
No.  (And thanks for ignoring the rest of my post.)  The BSD license is not a EULA.  You as a user do not have to agree to the BSD license before you can use X program.  Same with the GPL.  I did not have to agree with the GPL in order to use X program it every day.

I'm not going to break down your analogy because I do not want this to devolve to a myopic discussion of hypothetical pursuits.  Perhaps you'd do well to stay away from them yourself.  "Fact is," the problem for you hinges on "generosity", the meaning of which changes according to which set of ethics you subscribe to.  This discussion devolves therefore to what the meaning of "generous" is, and I don't care to have a philosophical debate with you on that matter because it's quite certain to me that we disagree on what is or isn't "unethical."

However, you seem to think that because a BSD distribution cannot legally include it, then no one can use it.

> Thus, BSD users cannot use it

Wrong!  If I was running OpenBSD, I could download the BSD-GPL dual-licensed, GPL-modified code and use it just fine!  **BSD/GPL license does not restrict users, only people who want to distribute.**  Thus, the kernel, and Theo and company, who *distribute*.  How else do you think BSD users run KDE, Gnome, all kinds of GPL'd software?

---

### Post by saulgoode on 2007-09-04
> **WishingWell said:**
> READ the article, "It is illegal to modify a license unless you are the owner/author, because it is a legal document.  If there are multiple owners/authors, they must all agree.  A person who receives the file under two licenses can use the file in either way....  but if they distribute
the file (modified or unmodified!), they must distribute it with the
existing license intact, because the licenses we all use have
statements which say that the license may not be removed."

Mr De Raadt is wrong. A license *can* authorize recipients to modify the license upon redistribution. Software distributed under GPL V2 can offer the option to re-distribute under a later version, LGPL software can at any time be re-distributed as GPL software, MIT-licensed code can be "sublicensed", et cetera. The original authors of the 'ath5k' driver authorized re-distribution of their code under the GNU General Public License when they added the line:

***Alternatively, this software may be distributed under the terms of the GNU General Public License ("GPL") version 2 as published by the Free Software Foundation.***

Since GPL-licensing was offered as an "alternative", there is no requirement to retain the original BSD licensing. Removal of the BSD licensing terms was not illegal and you will notice that the resolution of the LKML discussion did not include distribution under BSD licensing terms.

---

### Post by Bachstelze on 2007-09-04
> **saulgoode said:**
> 
Since GPL-licensing was offered as an "alternative", there is no requirement to retain the original BSD licensing.

Such bad faith is appalling... Look at the code resulting of the SFLC ruling, and what will you see ? That all the BSD license texts that were stripped off are back in the files. Just *read* your Holy GPL and maybe you'll understand why.

---

### Post by WishingWell on 2007-09-04
> **userundefine said:**
> No.  (And thanks for ignoring the rest of my post.)  The BSD license is not a EULA.  You as a user do not have to agree to the BSD license before you can use X program.  Same with the GPL.  I did not have to agree with the GPL in order to use X program it every day.

I'm not going to break down your analogy because I do not want this to devolve to a myopic discussion of hypothetical pursuits.  Perhaps you'd do well to stay away from them yourself.  "Fact is," the problem for you hinges on "generosity", the meaning of which changes according to which set of ethics you subscribe to.  This discussion devolves therefore to what the meaning of "generous" is, and I don't care to have a philosophical debate with you on that matter because it's quite certain to me that we disagree on what is or isn't "unethical."

However, you seem to think that because a BSD distribution cannot legally include it, then no one can use it.



Wrong!  If I was running OpenBSD, I could download the BSD-GPL dual-licensed, GPL-modified code and use it just fine!  **BSD/GPL license does not restrict users, only people who want to distribute.**  Thus, the kernel, and Theo and company, who *distribute*.  How else do you think BSD users run KDE, Gnome, all kinds of GPL'd software?

You're contradicting yourself, first you say that it's not a EULA (and you're right, it's not) but then you say that end users are the only ones who can actually use the license on it's own terms?

It's about distributing, we all get that so skip the crap and let's just get down to business, GPL based projects steal code while OpenBSD, the creator of one of the most used programs in ALL of FLOSS namely OpenSSH gets shafted because the rich kids in town (Red hat, Canonical, Novell) want to profit off of it but they don't give one buck back even when Theo specifically mentions that he needs donations to keep going.

At the same time much smaller projects DO donate to him, such as Slackware, even though Patrick had his own problems at the time he did the right thing.

I get why Theo is pissed, i would be too.

I kind of understand the sneaking around licenses to avoid license issues, but doing so to avoid having to contribute your own code to the FLOSS devs that developed the code your leeching off of?

It's kinda like how many Debian users feel about Ubuntu.

---

### Post by WishingWell on 2007-09-04
> **saulgoode said:**
> Mr De Raadt is wrong. A license *can* authorize recipients to modify the license upon redistribution. Software distributed under GPL V2 can offer the option to re-distribute under a later version, LGPL software can at any time be re-distributed as GPL software, MIT-licensed code can be "sublicensed", et cetera. The original authors of the 'ath5k' driver authorized re-distribution of their code under the GNU General Public License when they added the line:

***Alternatively, this software may be distributed under the terms of the GNU General Public License ("GPL") version 2 as published by the Free Software Foundation.***

Since GPL-licensing was offered as an "alternative", there is no requirement to retain the original BSD licensing. Removal of the BSD licensing terms was not illegal and you will notice that the resolution of the LKML discussion did not include distribution under BSD licensing terms.

Well, i didn't bother trying to interpret legal documents over google links, i just looked at the files, and indeed, the BSD license is right there now.

So you are wrong, unless you want to continue to deny reality?

---

### Post by saulgoode on 2007-09-04
> **WishingWell said:**
> Well, i didn't bother trying to interpret legal documents over google links, i just looked at the files, and indeed, the BSD license is right there now.

So you are wrong, unless you want to continue to deny reality?

I believe you may be confusing copyright notices with licensing. Or perhaps not. Could you provide a link to the files you are looking at?

---

### Post by Bachstelze on 2007-09-04
CAN YOU ACTUALLY READ, OR WHAT ??

Yes, the modified files are released under the GPL. Yes, the developper who made the final modifications had the legal right to do so. That's what everyone here has been saying from the beginning. So what are you blabbering about ?

---

### Post by Anthem on 2007-09-04
> **HymnToLife said:**
> CAN YOU ACTUALLY READ, OR WHAT ??

Yes, the modified files are released under the GPL. Yes, the developper who made the final modifications had the legal right to do so. That's what everyone here has been saying from the beginning. So what are you blabbering about ?
Helps to use the quote feature, so that people know who you're referring to.

---

### Post by Bachstelze on 2007-09-04
The message right before. The fact that the file is ultimately licensed under the GPL does not give the right to strip off all the previous BSD licences and copyright notices.

---

### Post by starcraft.man on 2007-09-04
I think people need to relax a bit in this thread, seems like it's getting unfriendly.....

---

### Post by Anthem on 2007-09-04
> **HymnToLife said:**
> The message right before. The fact that the file is ultimately licensed under the GPL does not give the right to strip off all the previous BSD licences and copyright notices.
And they've all been preserved in the patch that was accepted.  So it's not an issue.

But the guy wasn't talking to you, he was talking to WishingWell.

---

### Post by Anthem on 2007-09-04
> **starcraft.man said:**
> I think people need to relax a bit in this thread, seems like it's getting unfriendly.....
No doubt.

---

### Post by Bachstelze on 2007-09-04
> **starcraft.man said:**
> I think people need to relax a bit in this thread, seems like it's getting unfriendly.....

I must admit that having to repeat the same thing over and over again is not easy on the nerves...

---

### Post by starcraft.man on 2007-09-04
> **HymnToLife said:**
> I must admit that having to repeat the same thing over and over again is not easy on the nerves...

Both sides are repeating the same arguments/comments (some without even knowing the subject matter, that doesn't help). Yet neither side is listening, demonstrating IMO a prime failure of this discussion. I don't see a point in this continuing ad infinitum.

---

### Post by Fbot1 on 2007-09-04
> **HymnToLife said:**
> Me neither. And anyway, that imaginary license is not valid. "You must buy Fbot a hotdog", what for ? To use the code ? To redistribute it ? To re-sell it ?

Hmm, you're right. How about this:
[HTML]To own _____ you must buy Fbot a hotdog[/HTML]
Anyway, my point is that licenses don't always stick.

---

### Post by Anthem on 2007-09-04
> **HymnToLife said:**
> I must admit that having to repeat the same thing over and over again is not easy on the nerves...
You don't **have **to do anything.  Let it go, and let the thread die.

The whole thing's already been solved in the places that matter.  This is just sound and fury.

---

### Post by saulgoode on 2007-09-04
> **HymnToLife said:**
> CAN YOU ACTUALLY READ, OR WHAT ??

Yes, the modified files are released under the GPL. Yes, the developper who made the final modifications had the legal right to do so. That's what everyone here has been saying from the beginning. So what are you blabbering about ?

I am contradicting those who seem to be stating that the original module code submitted to the kernel module includes BSD licensing terms. From what I can tell, it does not. From my interpretation of the submitted patches discussed on the LKML, the BSD license is not present. If WishingWell (or anyone else) would correct me on this, I should be neither disappointed nor elated -- I am merely interested in an accurate understanding of the facts with this regard.

---

### Post by nonewmsgs on 2007-09-04
ok.  ive read all 18 pages of this and i still dont understand why bsd cannot use GPLed drivers.  as stated somewhere around page 11 it was revealed that linux's xorg is actually a MIT license.  can't bsd just stick a source code file with that license or would a drop of GPL taint their purity?

---

### Post by Bachstelze on 2007-09-04
> **saulgoode said:**
> I am contradicting those who seem to be stating that the original module code submitted to the kernel module includes BSD licensing terms. From what I can tell, it does not. From my interpretation of the submitted patches discussed on the LKML, the BSD license is not present. If WishingWell (or anyone else) would correct me on this, I should be neither disappointed nor elated -- I am merely interested in an accurate understanding of the facts with this regard.

The files were modified. The ultimate modifications are GPL-only, therefore the whole thing is GPL-only. But that does not give the right to remove the BSD licence texts, as was previously attempted. That's al.

And if the dual-licensed file hadn't been modified, redistribution under the terms of *either* license *must* keep the two licenses for further redistribution because the copyright owner of a work is the only one allowed to modify the licensing terms. As simple as that.

> **nonewmsgs said:**
> ok.  ive read all 18 pages of this and i still dont understand why bsd cannot use GPLed drivers.  as stated somewhere around page 11 it was revealed that linux's xorg is actually a MIT license.  can't bsd just stick a source code file with that license or would a drop of GPL taint their purity?

GPL code cannot be distributed as part of a non-GPL project, that's what the GPL is all about. The case of Xorg is different, as Xorg is not part of Linux. And even if it was, nothing in the MIT license Xorg uses forbids redistributing it as part of a GPL project.

---

### Post by WishingWell on 2007-09-04
> **saulgoode said:**
> I believe you may be confusing copyright notices with licensing. Or perhaps not. Could you provide a link to the files you are looking at?

I'm referring to the BSD licensed files that were "stolen" and distributed under GPL code without so much as a mention of the original license.

You can find them at an FTP source close to you if you wish, i've got them on my computer and if i REALLY need to i'll look them up on an FTP for your convenience.

Admit that you have to laugh about how others claim that Apple and MS have stolen BSD code when they STILL retain the license and the GPL distributors of the acquired code do not?

---

### Post by WishingWell on 2007-09-04
> **HymnToLife said:**
> The files were modified. The ultimate modifications are GPL-only, therefore the whole thing is GPL-only. But that does not give the right to remove the BSD licence texts, as was previously attempted. That's al.

And if the dual-licensed file hadn't been modified, redistribution under the terms of *either* license *must* keep the two licenses for further redistribution because the copyright owner of a work is the only one allowed to modify the licensing terms. As simple as that.



GPL code cannot be distributed as part of a non-GPL project, that's what the GPL is all about. The case of Xorg is different, as Xorg is not part of Linux.

Thank you, i thought that was made clear in the OP but apparently there are people who don't bother reading the OP at all, or maybe they just don't understand it, if they don't get it after this, i suggest that both you and i give this discussion up, it's not worth the aggravation. ;)

---

### Post by nonewmsgs on 2007-09-04
yeah i remember that now.  sorry for the interuption please go back to where you were.  

hymn you were complaining about people choosing not to give back and how they should and everyone else is saying it's the license they picked.  carry on.

*steps away from the flame*

---

### Post by Fbot1 on 2007-09-04
> **HymnToLife said:**
> GPL code cannot be distributed as part of a non-GPL project, that's what the GPL is all about.

It can, they use GCC in OpenBSD.

---

### Post by Anthem on 2007-09-04
> **WishingWell said:**
> I'm referring to the BSD licensed files that were "stolen" and distributed under GPL code without so much as a mention of the original license.
By the guy who wrote most of them in the first place.

And they were fixed before getting merged.  So please don't call them "stolen."

---

### Post by tbroderick on 2007-09-04
> **Fbot1 said:**
> It can, they use GCC in OpenBSD.

There's no GPL in the OpenBSD kernel.

---

### Post by Anthem on 2007-09-04
> **tbroderick said:**
> There's no GPL in the OpenBSD kernel.
He's talking about distribution of the OpenBSD "distro."

---

### Post by Fbot1 on 2007-09-04
> **tbroderick said:**
> There's no GPL in the OpenBSD kernel.

If that's what he/she meant than that's correct.

---

### Post by Bachstelze on 2007-09-04
GCC is not part of the OpenBSD operating system. It is distributed in separate packages, in full compliance with the GPL.

---

### Post by Frak on 2007-09-04
Why can't we all just get along? Its all open source and we all make mistakes. Let it go.

---

### Post by phrostbyte on 2007-09-04
HymnToLife,

Why are you attacking Linux on a Linux forum? What are you exactly trying to accomplish?

---

### Post by Fbot1 on 2007-09-04
> **HymnToLife said:**
> GCC is not part of the OpenBSD operating system. It is distributed in separate packages, in full compliance with the GPL.

I could of sworn that GCC was in there by default... What versions have you used?

> **phrostbyte said:**
> HymnToLife,

Why are you attacking Linux on a Linux forum? What are you exactly trying to accomplish?

He's not really attacking Linux.

---

### Post by Anthem on 2007-09-04
> **Frak said:**
> Why can't we all just get along? Its all open source and we all make mistakes. Let it go.
Agree.  And the whole thing has been resolved, and the Linux kernel is in full legal compliance with every known license.

All that's left is the bickering.

---

### Post by @trophy on 2007-09-04
19 pages already?  Holy crap.

I think this is where I get off.

---

### Post by Bachstelze on 2007-09-04
> **Fbot1 said:**
> I could of sworn that GCC was in there by default... What versions have you used?

Whether it is installed by default or not changes nothing to the fact that the OpenBSD system and GCC are two different entities - to quote the GPL words, OpenBSD is not "work based on the Program", "the Program" being GCC. So just distributing them together does not "trigger" the virality of the GPL. It would if GPL code was put into the OpenBSD kernel, for example.

---

### Post by Fbot1 on 2007-09-04
> **HymnToLife said:**
> Whether it is installed by default or not changes nothing to the fact that the OpenBSD system and GCC are two different entities. So just distributing them together does not "trigger" the virality of the GPL. It would if GPL code was put into the OpenBSD kernel, for example.

Well you did say non-GPL project but, what you're saying now is right.

---

### Post by WishingWell on 2007-09-04
> **Anthem said:**
> By the guy who wrote most of them in the first place.

And they were fixed before getting merged.  So please don't call them "stolen."

Doesn't matter because they were stolen since they did not include the license for the code.

What's up with people in this thread, do you just start reading one line and then stop reading?

It's been explained numerous times.

Dagnabit, i said i shouldn't respond, now look what you made me do.

---

### Post by WishingWell on 2007-09-04
> **phrostbyte said:**
> HymnToLife,

Why are you attacking Linux on a Linux forum? What are you exactly trying to accomplish?

He's not, what is right is right no matter what forum you are and what he is saying is that some of the code used in various Linux distributions don't follow the legal licensing issues they should.

Don't see things as black and white, criticizing something doesn't mean that you are attacking it.

---

### Post by Fbot1 on 2007-09-04
> **WishingWell said:**
> what is right is right no matter what forum you are
Not quite...

---

### Post by WishingWell on 2007-09-04
> **Frak said:**
> Why can't we all just get along? Its all open source and we all make mistakes. Let it go.

When you, like Theo have a project that is used by a number of high profile companies like Red hat, Novell and Canonical and they take your work, don't donate when you tell them you need money and keep using your work, then you can tell everyone that they should just get along.

The last thing Theo has is his code and his licenses and then they take that too without recognition nor respecting his code by including the license he put it under...

If i was him i'd just finish with a big exploit bang and join MS because the FLOSS community has treated him like crap. (sans IBM, Slackware (at the SAME time Patrick asked for help no less) and a whole lot of private donors).

---

### Post by WishingWell on 2007-09-04
> **Fbot1 said:**
> Not quite...

Correct, on this forum, people just make up things as they go along and then they too can be right as much as they want to, you're the perfect example.

---

### Post by Fbot1 on 2007-09-04
> **WishingWell said:**
> Correct, on this forum, people just make up things as they go along and then they too can be right as much as they want to, you're the perfect example.

A statement isn't always true in every forum.

---

### Post by Darkhack on 2007-09-04
> **WishingWell said:**
> When you, like Theo have a project that is used by a number of high profile companies like Red hat, Novell and Canonical and they take your work, don't donate when you tell them you need money and keep using your work, then you can tell everyone that they should just get along.

I agree that it would be in good faith for them to donate and to support Theo, but when he chose the BSD license, he should have realized this would happen.  He has a legitimate reason to complain when the BSD is violated.  Even though taking (not stealing) code without giving back is unethical and somewhat rude to a degree, it is perfectly acceptable under the BSD.  This is why so many open source developers prefer the GPL.  I wonder how long before OpenBSD becomes OpenGPL. 

> **Fbot1 said:**
> A statement isn't always true in every forum.

Example?  Last time I checked, something is either true, false, opinion, or unknown.  Even at that, unknown falls into one of the first three categories, we just don't happen to know which one.

---

### Post by Anthem on 2007-09-04
> **WishingWell said:**
> Doesn't matter because they were stolen since they did not include the license for the code.

What's up with people in this thread, do you just start reading one line and then stop reading?

It's been explained numerous times.

Dagnabit, i said i shouldn't respond, now look what you made me do.
I didn't say the original guy didn't strip the licenses.  I'm saying the issue has already been fixed, and was fixed before this thread was started.  The current files in the git tree have the full attribution.  So there's no "theft" going on here.

---

### Post by brentoboy on 2007-09-04
wow, and again, wow

A little bit of Open Source license info is in order here.   there is an awful lot of not knowing going on here.

GCC is actually "L" GPL 
see this site ... where it says that it is GPLv2 with exception "L" [http://directory.fsf.org/gcc.html](http://directory.fsf.org/gcc.html)

but that is neither here nor there.

all code files are copyrighted by their original authors in much the same way a book or article is copyright.  he (or she) is the sole owner of the code, and has 100% say about what happens to their work.

open source licenses are not contracts or licenses so much as they are simply a statement from the copyright holder that gives people permission to use their "artwork" in a certain way without expressly asking permission.  sort of like a textbook saying "you can photocopy the worksheet pages in this book without express permission from the author."

the bsd "license" applies to a single code file, and is generally posted at the top along with a statement as to who holds the copyright.   bsd was originally education centered permissions that were designed to allow professors and graduate students all share and work together on common projects that could ultimately benefit anyone and everyone.  It does a nice job of doing exactly that, while protecting the original auther

the gpl license works the same way, except one of the conditions is that the code file cant even be compiled in a way that includes code that is not also GPL.    All code files that are pulled together to build a program that has ANY gpl code in the whole batch must garantee the copyright holder of the GPL that the sum total of the project will remain open and available to everyone.

so, if the BSD kernel (one compiled program) had a single file that had a GPL clause, the entire BSD kernel would have to be destributed under the GPL.   

That doesnt mean that all the original copyright holders cant still use thier own stuff however they want, and it doesnt mean that a person willing to remove the GPL module cant turn around and use the whole thing under the BSD license instead.   But, they are right, linux can use BSD code because there is nothing that says you cant add the GPL restrictions on top of the BSD code.   But the reverse isnt true.

the argument sets up a very one way code stealing problem.
But it isnt linux nor the linux developers who are creating the problem (nor the BSD folks)  The copyrighters who submit their work under the GPL would not have submitted it if it weren't GPL (if someone could use it to create some proprietary close project).  

So, it isn't so much that the GPL code is "viral" and ruins other licenses, as it is that the GPL coders don't want their stuff out under a more permissive license.

The real reason that this entire discussion is so painful is that the Free Software Foundation (the GPL thugs) sit down with the authors of the different open source licenses, and they have long discussions about whether or not "stealing" code is permissable.  If it is not, the license is deamed incompatable with the GPL and is "tainted."

The authors of the BSD license talked with the GPL police many years ago and they all agreed that stealing code from BSD and putting it into Linux was perfectly within the rights granted by the BSD copyright notice, and everyone was happy with it.

That doesnt mean that everyone is happy with it today, but in terms of morality, richard stallman had the discussion a long time ago, and everyone shook hands and said "here here"

BSD's have traditionally NOT wanted contributions from outside sources becuase they were primarily developed by a handful of people. the result was excellent software, but driver support has always been slim.

Linux's push to have anyone and everyone submit modifications (driven by the GPL) makes for a whole lot more hardware support.  

Until recently, the BSDs had so much of a head start that they never expected to borrow code from other open source projects.   But Linux grows so fast, and supports so much hardware, there comes a point when you start to say "we could just borrow their code for that driver."

It seems to me that it is time to rethink the problem.

And this forum wont likely fall upon the ears of those in a position to do the rethinking.

it is immoral to steal someone else's code and claim it is yours.  It is not immoral to use someones copyrighted works in a way that they have stated is acceptable in a broad statement of "you may use this this way."   the people publishing the code are not unaware of the copyright restrictions they are applying to their code, and no one stole anything.

There is definitely an unfair advantage in Linux's favor.

The BSD type folks could have that same advantage.
The very act of choosing the BSD license instead of the GPL is a statement of allowing others to steal your stuff with little more than a notice that "this code was originally written by Joe BSD Developer."

But, yes, it is a bit rude.
And stripping copyright notices and BSD license statements is a violation of the rights of the copyright holder (akin to photocopying a book and giving away copies).

---

### Post by Anthem on 2007-09-04
> **Darkhack said:**
> I agree that it would be in good faith for them to donate and to support Theo, but when he chose the BSD license, he should have realized this would happen.
Plenty of GPL projects get used by other companies without getting donations.  That has nothing to do with GPL/BSD.

Regardless, there are lots of projects that Red Hat, Novell, and Canonical don't support, not just OpenSSH.  If RedHat owes Theo money because RH uses OpenSSH, then shouldn't Theo start donating to Canonical for all of the work on X.org that Canonical does?  Of course not; that's not the way the system works.

Canonical gets improvements to the kernel that are made by Intel developers.  Does Canonical now owe Intel money?

Again, of course not.  That's simply not the way the open-source ecosystem works.

---

### Post by Anthem on 2007-09-04
> **brentoboy said:**
> The authors of the BSD license talked with the GPL police many years ago and they all agreed that **stealing code from BSD and putting it into Linux was perfectly within the rights granted by the BSD copyright notice, **and everyone was happy with it.
Then it's not "stealing."

Please use a different word.

> Until recently, the BSDs had so much of a head start that they never expected to borrow code from other open source projects.   But Linux grows so fast, and supports so much hardware, there comes a point ...
And there's a reason for that.  It's the GPL (v2).

> There is definitely an unfair advantage in Linux's favor.
Why is it unfair?  What is it about that situation that's unfair?

---

### Post by brentoboy on 2007-09-04
> **Fbot1 said:**
> I could of sworn that GCC was in there by default... What versions have you used?


It is not about inclusion in a 'distro' by default.

each package is perfectly capable of being licensed in its own way.  The GPL viral affect only takes effect on code that is compiled together into a single unit.

It doesnt force the GPL on all programs that are distributed together or, and the GPL FAQ page puts it "mere aggregation"
[http://www.gnu.org/licenses/gpl-faq.html](http://www.gnu.org/licenses/gpl-faq.html)

---

### Post by brentoboy on 2007-09-04
> **Anthem said:**
> 
Then it's not "stealing."

Please use a different word.


Quite right, stealing is taking without permission.  This is "making use of."

-- as far as unfair, in the grand scheme of things they all have the same rights and privileges granted to them under copyright laws.

the unfairness enters the scene when Linux projects can use BSD code in their stuff, and BSD folks cant use Linux code in thier stuff.

it is an unfairness that they have chosen to impose upon themselves.  But, it is certainly a very one sided arrangement.  And my definition of unfair is a situation where an arrangement benefits one party more than another party.

(you may have missed my solution to the unfair problem back on page ... ? 4 or so)

---

### Post by Darkhack on 2007-09-04
> **Anthem said:**
> Plenty of GPL projects get used by other companies without getting donations.  That has nothing to do with GPL/BSD.

Exactly my point.  He shouldn't have expected a single penny.  Also, in my original post, I wasn't just referring to cash donations, but contributions of code back to the original project under the BSD license as well.  Same thing applies though.  He shouldn't have expected companies to just give back because it is the "nice thing to do".

Hmm... if only Theo had a license that allowed people to use and modify the code freely, but distribute it in such a way that it would guarantee that no one could close it or block them out.  Oh wait... such a license does exist.  The GPL.

> **brentoboy said:**
> the unfairness enters the scene when Linux projects can use BSD code in their stuff, and BSD folks cant use Linux code in thier stuff.

It's only unfair if you think it is.  If I put up a sign that says "free cookies" and everyone takes one, is that unfair to me?  Maybe I had extra and I didn't want to throw them away.  In which case, I actually benefit.  It's only unfair if you expected to get something back or you requested that you get something back.  The BSD license doesn't request anything back except that the original copyright notice be retained.  Theo gave away his cookies and now he is mad that no one has given any back to him.  That's not unfair.  That's just how the license works.  Unfair is when the license is violated.

> **brentoboy said:**
> it is an unfairness that they have chosen to impose upon themselves.  But, it is certainly a very one sided arrangement.  And my definition of unfair is a situation where an arrangement benefits one party more than another party.

[QUOTE=Dictionary.com's Definition of Unfair]
unfair - not conforming to approved standards, as of justice, honesty, or ethics
[/QUOTE]

It may appear to be unfair because one party benefits while another does not, but it was their choice to give away their code.  The approved standards as shown in the definition are that of the BSD and GPL licenses.  Theo is the kind of person that if he accidentally threw away an important paper he needed, he would barge down to the garbage dump and complain about how "unfair" it was that the garbage men just showed up and took his garbage from his curb.

---

### Post by Anthem on 2007-09-04
> **brentoboy said:**
> the unfairness enters the scene when Linux projects can use BSD code in their stuff, and BSD folks cant use Linux code in thier stuff.
Sure they could.  They could blend the entire Linux kernel, including all of its drivers, into their kernel if they so desired.  It's just that the resulting code wouldn't be BSD.

> it is an unfairness that they have chosen to impose upon themselves.
Then it's not unfair.

If you and I  are racing 100 meters, and halfway through the race you decide to crawl the rest of the way, then you don't get to complain at the end that I didn't finish on my hands and knees?  Bad analogy, I know, but the point is that if your only limitation is one you impose on yourself, then it's not an unfair limitation.

---

### Post by Anthem on 2007-09-04
A great email from the linux kernel mailing list:

[quote="Jeff Garzik"]NOTHING IS IN STONE, because nothing has been committed to my 
repository, much less torvalds/linux-2.6.git.

A patch was posted, people complained, corrections were made.  That's 
how adults handle mistakes.  Mistakes were made, and mistakes were 
rectified.[/quote]

So the code in question never even made it to the code repository, just the mailing list.  I don't see how that's "theft."

[http://lkml.org/lkml/2007/9/2/146](http://lkml.org/lkml/2007/9/2/146)

---

### Post by tbroderick on 2007-09-04
> **Anthem said:**
> Sure they could.  They could blend the entire Linux kernel, including all of its drivers, into their kernel if they so desired.  It's just that the resulting code wouldn't be BSD.

Not much of a choice.

---

### Post by Darkhack on 2007-09-04
> **Anthem said:**
> So the code in question never even made it to the code repository, just the mailing list.  I don't see how that's "theft."

It's copyright infringement if the code was distributed (even if it wasn't in an official repository) and it doesn't contain the BSD license and copyright notice.  So it technically [and legally] (IANAL, but I'm sure it would hold up in court) is theft.  Of course in if we are going to speak on technical (or legal) grounds, then the proper term is copyright infringement (I know what you meant though, not trying to be a grammar nazi here), but the code was distributed and therefor is liable.

---

### Post by brentoboy on 2007-09-04
yes, but copyright infringement is followed by a cease and desist letter, not litigation (unless they refuse to cease and desist).

---

### Post by tehkain on 2007-09-04
> **HymnToLife said:**
> I shouldn't have mentioned Theo, it seems some people are talking about him rather than the reall issue...

Forget about Theo, forget about the BSD and GPL, forget about everything and tell me. Do you feel, in the bottom of your hearts, that it is okay, when you're given something, to just take it and give nothing back ? If you do, well, feel free to do it, the BSD license allows this. But I really, sincerely pity you. And I hope you're not acting this way with your real-life friends, or you'll end up alone in no time.

In a perfect world.. in a perfect world there would be no gpl. Do I feel it is ok to not give code back if the license clearly allows it? Yes. Do I want my GPLed code given back? Yes, that is why I choose the gpl. The bottom line is we do not live in a perfect world so we have to preserve our code and its future(expanded by many others) by choosing a license like the gpl.

I feel fine if I treat the code the way the developer asked me too. You know I hate saying it but - by moving code from BSD to GPL you are liberating it. You are keeping the changes you make to the code Free. **Everyone has a different interpretation of Free** -  I choose to distinguish freedom from chaos. There is nothing wrong with unpredictability and very limited licensing - but it is chaos not freedom. Freedom does not allow its self the freedom to become unfree. That is chaos.

In a perfect world...

Like many above have said 'not being friendly does nt mean you are being mean or unfriendly'

---

### Post by luckyd on 2007-09-05
> The irony, however, is that while noisy Linux fanatics make a great deal out of their hatred for Microsoft (nasdaq: MSFT - news  - people ), De Raadt says their beloved program is starting to look a lot like what Microsoft puts out. "They have the same rapid development cycle, which leads to crap," he says.  wtf, microsoft rapid developement cycle?

---

### Post by saulgoode on 2007-09-05
> **brentoboy said:**
> 
...
[lots of commentary with which I agree]
...
And stripping copyright notices and BSD license statements is a violation of the rights of the copyright holder (akin to photocopying a book and giving away copies).

Retaining BSD license statements is not a requirement if you are distributing the code under the terms of the GPL. The original authors of the code in question explicitly allowed for this option when they included the statement "Alternatively, this software may be distributed under the terms of the GNU General Public License..." Offering an *alternative* between two things means you can choose one or the other; you do not have to take both. 

If you decide to distribute the code using *just* the BSD license then you are not bound by the terms of the GPL and you could, for example, mix it with GPL-incompatible code (rather the point, I should think). In addition, you are not required (according to the  [terms of the BSD license](http://en.wikipedia.org/wiki/BSD_license#Terms)) to include the aforementioned "Alternatively, ..." clause: it is not part of the copyright notice, it is not part of the warranty disclaimer, and it is not part of the list of conditions. 

By the same token, if you choose the alternative and distribute the code using *just* the GPL license, you are not obligated by the terms of BSD licensing and are not required to include the list of conditions of the BSD license -- this is only a requirement of the BSD license itself, which you are not using. Retention of the other two components, the copyright notice and the warranty disclaimer, IS an obligation under the terms of the GPL and *their* removal would constitute a violation.

---

### Post by vexorian on 2007-09-07
> 
Forget about Theo, forget about the BSD and GPL, forget about everything and tell me. Do you feel, in the bottom of your hearts, that it is okay, when you're given something, to just take it and give nothing back ? If you do, well, feel free to do it, the BSD license allows this. But I really, sincerely pity you. And I hope you're not acting this way with your real-life friends, or you'll end up alone in no time.
Although this is not the actual issue at all (The developers themselves forked the thing into GPLd and BSD code...) I think it is all right, after all that's supposedly what people that use the BSD license want to happen, I think it is a disgrace to see people explicitly  say "you can take and not give back" and then criticize "for not giving back", there are terms for that behaviour in many languages, unfortunally for English the term is "Indian giver" although it is an innacurate term history wise it is still a kind of behaviour I pity more than taking and not giving back.

---

### Post by BoyOfDestiny on 2007-09-07
> **vexorian said:**
> Although this is not the actual issue at all (The developers themselves forked the thing into GPLd and BSD code...) I think it is all right, after all that's supposedly what people that use the BSD license want to happen, I think it is a disgrace to see people explicitly  say "you can take and not give back" and then criticize "for not giving back", there are terms for that behaviour in many languages, unfortunally for English the term is "Indian giver" although it is an innacurate term history wise it is still a kind of behaviour I pity more than taking and not giving back.

++

Anyway, story on it here
[http://www.itwire.com/content/view/14361/1091/](http://www.itwire.com/content/view/14361/1091/)

I don't agree with the author completely (since I've seen the same dev release something under the GPL also release something under BSD...) I don't think everyone is like GPL vs BSD. He or she picks what they want.

And not surprisingly some of the comments in the comment section look the same. 
BSD is more free since it places less restrictions, thus the GPL isn't so free.
When the GPL defines Free
> 
    *  The freedom to run the program, for any purpose (freedom 0).
    * The freedom to study how the program works, and adapt it to your needs (freedom 1). Access to the source code is a precondition for this.
    * The freedom to redistribute copies so you can help your neighbor (freedom 2).
    * The freedom to improve the program, and release your improvements to the public, so that the whole community benefits (freedom 3). Access to the source code is a precondition for this.

[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

It is a license than ensure the code can never be closed off. For example what Apple has done with OSX and FreeBSD. That is the whole point, to prevent that. And it works, and most developers like it. Who doesn't like it? Think about that...

I argue that a BSD dev should be pleased with this state of affairs (yay my code is used everywhere) or they should have picked another license.

GPL code will always be there to use and build upon, not have a snapshot taken, with proprietary addons, then released with those changes locked off.

Think about who would be pleased with that? Only people/companies that want code without having to give back. 

Now if the GPL locks you into it, oh no a global community of developers get the four freedoms outlined above as long as everyone gets the same rights to the code (which the GPL guarantees). 

Ultimately the devs get to chose, but with the GPL you aren't their mercy either (lock it up, stop contributing, etc.) 
It's restricts the freedom to take away yours. That's a restriction I can back. It seems only those who want something for nothing complain the loudest. Works for me!

:guitar:

---

### Post by runningwithscissors on 2007-09-07
What's the point of GPL'ing your modifications if you dual licence them under a BSD licence? People who want to close your code will simply pounce on the BSD version.

The Linux devs don't want other parties to take their code and close modifications to it off. That's what the GPL is about.

Theo is just doing what he does best. Whinging.

---

### Post by Fbot1 on 2007-09-07
> **Darkhack said:**
> Example?  Last time I checked, something is either true, false, opinion, or unknown.  Even at that, unknown falls into one of the first three categories, we just don't happen to know which one.

First of all, where did you check? Your magical book of truth? A teacher? Anyway, that's definitely not true. A statement is either always true, sometimes true, false, or undecidable under a formal system. Now for an example:"I am on the Ubuntu forums".

---

### Post by Darkhack on 2007-09-07
> **Fbot1 said:**
> First of all, where did you check? Your magical book of truth? A teacher? Anyway, that's definitely not true. A statement is either always true, sometimes true, false, or undecidable under a formal system. Now for an example:"I am on the Ubuntu forums".

Numerous science books and Richard Dawkins' _The God Delusion_ all make reference to it.  Your example is true.  Unless you are going to use some weird-backwards interpretation of that statement, your example is true until the Ubuntu forums themselves, or your user account no longer exist and that statement becomes past tense or else it is false.  That statement cannot vary unless you change one or more variables.

---

### Post by WishingWell on 2007-09-07
> **Darkhack said:**
> I agree that it would be in good faith for them to donate and to support Theo, but when he chose the BSD license, he should have realized this would happen.  He has a legitimate reason to complain when the BSD is violated.  Even though taking (not stealing) code without giving back is unethical and somewhat rude to a degree, it is perfectly acceptable under the BSD.  This is why so many open source developers prefer the GPL.  I wonder how long before OpenBSD becomes OpenGPL. 

Don't cut my quotes short, i explained later why this is a big deal and you cut that out, edit the post to include that please.

OpenBSD will never become anything else, Theo holds the code in his hands and he could terminate the code any day he wants to.

OpenSSH isn't the only thing, are you enjoying your blob free drivers that were stolen from OpenBSD? 

I like guys like Theo and Patrick, people who push and shove and get things done, guys like you? What have you ever done? Ever come up with something as important as OpenSSH (which every OS uses nowdays) or disassembled drivers to see how they work and replicate them without using any of the code to make drivers for the community to enjoy?

No? Then STFU.

---

### Post by WishingWell on 2007-09-07
> **vexorian said:**
> Although this is not the actual issue at all (The developers themselves forked the thing into GPLd and BSD code...) I think it is all right, after all that's supposedly what people that use the BSD license want to happen, I think it is a disgrace to see people explicitly  say "you can take and not give back" and then criticize "for not giving back", there are terms for that behaviour in many languages, unfortunally for English the term is "Indian giver" although it is an innacurate term history wise it is still a kind of behaviour I pity more than taking and not giving back.

*snip*
The original licence has to be INCLUDED if you want to use the code.

*snip*

*snip*

---

