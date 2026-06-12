---
title: "Publish a Developers' Hardware List"
date: 2008-07-11
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2008-07-11
Has anyone else had this experience?

* Something weird happens (CPU spike, kernel panic, Grub error, weird menu behavior, etc.). 
* You post on the forums. 
* People try to help you with the problem and come up with some kind of workaround. 
* You still don't know what the problem is. 
* Someone suggests it might be a bug and you should file a bug report. 
* You file a bug report on Launchpad.
* A developer asks you some questions and maybe the output of a particular command or log file.
* The developer then tells you the bug cannot be reproduced, so it can't be fixed.

What I'm imagining is that people experience certain non-reproducible bugs because they do not have the exact same hardware the developers have. You'd like to think at least theoretically (even though non-developers do some alpha and beta testing before release, too) every single Ubuntu release worked flawlessly on every developer's computer, right?

Would it make sense, then, to ask developers to make public what hardware they're using?

If so, I could see several potential benefits: [list][*]It would behoove those who do not have that hardware but who feel fairly comfortable in their troubleshooting skills to definitely do alpha and beta testing for new releases, since the developers do not have direct access to the same hardware. [*]New users who are trying to get especially Ubuntu-friendly (not just Linux-friendly) hardware would know exactly what hardware to get to have a flawless (not just excellent) experience. [*]When developers aren't able to reproduce a bug or error, it would be immediately obvious to the tester whether it had something to do with differing hardware or a different software setup problem.[/list] What do you all think?

Here's the Brainstorm idea if you want to vote on it:
[Idea #15067: Publish and publicize a developers' hardware list](http://brainstorm.ubuntu.com/idea/15067/)

---

### Post by chris4585 on 2008-07-11
That would be a great idea.  I was just thinking, wouldn't it be 10x harder but 10x better if everyone used the same type of computer/hardware?  I mean Apple had that much right...

---

### Post by aysiu on 2008-07-11
> **chris4585 said:**
> That would be a great idea.  I was just thinking, wouldn't it be 10x harder but 10x better if everyone used the same type of computer/hardware?  I mean Apple had that much right...
I agree. Ubuntu could learn a lot from Apple. Except, instead of trying to *bind* people to certain hardware configurations through *restricting licensing agreements*, Ubuntu would simply encourage people to use recommended hardware. Other hardware would entail your mileage varying.

---

### Post by LaRoza on 2008-07-11
I disagree in general.

I have four computers on which I program (an old Sony, a Compaq, an iBook and a Thinkpad), and it would be useless to post that information.

The only time I think developers pay attention to hardware is when it directly concerns them (a webcam app, etc).

For hardware support, the most important thing is that hardware manufactures follow standards (when they exist).

---

### Post by aysiu on 2008-07-31
I don't think the two are mutually exclusive. Vendors should follow standards, but that doesn't mean there are no bugs. And usually there are bugs the developers don't know about until after the release, because they don't necessarily have the same hardware as other users.

---

### Post by kko1 on 2008-08-01
I think it would generally be a good idea. That way you could at least confirm your suspicions that no-one uses the same videocard as you do. :p

However, I disagree completely on the follow-up. In my opinion there should be no such thing as "recommended hardware". Sure, a list of what works best with linux, what manufacturers use open standards, etc., is useful, but to elaborate that into "use this video card, not that one" runs completely against the idea of the user controlling their own computing experience.

(I won't argue in length with anyone who thinks differently, but for numerous reasons I just wouldn't appreciate such "recommendations" given to me. To give one theoretical example: if we assume that the majority of devs use relatively new hardware, does that mean I "should" (or even "should be told to, i.e. recommended to") get new hardware too, if I don't want or need to "upgrade"? No. But I might still appreciate *knowing* that none of the devs use the same hardware as I do.)

As to releases working "flawlessly" on developers' computers, you did mean that purely as a theoretical figure of thought, right?

The absence of show-stopper bugs (like the machine not booting at all) on developers' machines is one thing, but the list of such bugs is short. The majority of bugs exist on developers' machines as well, however they may not bother them equally, depending on different computer using habits etc. Unless you hire someone to fix a particular bug, or are capable of doing so yourself, it's just a question of luck if there's someone else who is bothered by the same bug AND willing and able to fix it.

So, even if this were a good idea, I think the benefits would be limited. However, for the information value, I'd appreciate it as a gesture if a developer wishes to make public their hardware (and, in the case of *ubuntu, if they're using a standard Ubuntu / Kubuntu setup or not, and e.g. for Kubuntu, whether they're using KDE 3 or 4) on e.g. their Launchpad or Ubuntu wiki page. *I'm betting some do already, alongside telling what kind of bugs they're mostly working on.* If this information were compiled somewhere as a centralised list (possibly automatically updated), that would be a bonus.

All that said, I wouldn't want this *enforced* in any way on the developers (just like anyone else), but if SABDFL wants to *encourage* developers to do this, I won't object. ;)

---

### Post by aysiu on 2008-08-01
I guess I should clarify what is meant by "recommended." It is not to say that other hardware will not work or isn't supported. It is to say "If you want to make sure you have no trouble, use this." When I was looking for a good wireless card to get for my laptop, I asked people on these forums what they would *recommend*, and the overwhelming majority recommended the Intel Pro Wireless 2200, which I got and loved. It doesn't mean you *have* to get the IPW 2200 in order to have your wireless work in Ubuntu, but it was a recommendation, and I'm glad I got it.

For people who don't want to spend hours researching hardware compatibility lists, it's nice to have *recommended* hardware to know you can get and have work. It doesn't mean you have to *replace* the hardware you already have, but it's a nice resource to have when you are in a position to buy new hardware.

And, yes, of course, it's only theoretically that everything is ironed out for the developers, but I highly doubt the developers would release a version of Ubuntu that is causing kernel panics on all their rigs.

---

### Post by kko1 on 2008-08-01
> **aysiu said:**
> I guess I should clarify what is meant by "recommended."

Thank you. (You know, I was going to write "It may only be a question of wording, but..." ;) )

---

