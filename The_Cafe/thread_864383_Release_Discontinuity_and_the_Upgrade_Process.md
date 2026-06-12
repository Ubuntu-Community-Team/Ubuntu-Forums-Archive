---
title: "Release Discontinuity and the Upgrade Process"
date: 2008-07-19
forum: The Cafe
---

### Post by GOfree on 2008-07-19
As a newbie, I find the whole idea of serial releases and upgrading rather disconcerting. I wonder if there are experienced penguistas here who could shed light on the situation and give me some tips to make upgrading less painful.

I don't understand the discontinuity between Ubuntu releases and do not like having to reconfigure half of my system with an upgrade. I started with 7.10 (Gutsy Gibbon) and had an interesting experience getting it to work with my system (AMD 64, ATI drivers, etc.). I learned a lot about my system in the process, but I don't want to do it with every new release. Now, for whatever reason, 8.04 (Hardy Heron) does not work for me. I tried the original release and the 8.04.1 maintenance release, and ended up back with Gutsy. This meant several "upgrades" and clean installs, trying to get the new release working, then having to reconfigure everything back to the way it was. Why is this process so painful?

Am I missing something? How do the experienced users deal with release schedules and upgrades? I have figured out how to make a separate partitition for my home folder, which means that I don't have to back up my work for a clean install. I think that this is a step in the right direction, and it might be something worth implementing as a standard feature of the distribution. But that still leaves all the reinstalling and reconfiguring of packages to be done, which for a novice, can be rather painful and a daunting prospect if it has to be done with every new release, every six months.

Are there any strategies for dealing with this that you can recommend? I have read posts from people who are still using Dapper Drake and are doing just fine. Gutsy Gibbon works great for me, and I would be happy to stay with it, but cannot help thinking that there is something in the new release that I am missing. And what will happen next April when official support for 7.10 ends? Does this mean no more updates? What do I do then?

Are the Ubuntu developers working on ways to improve the upgrade process? I know that there is a button on the Update Manager GUI for "Upgrade", but it does not seem to work very well. Time and time again, people run into problems and what is recommended is a clean install. ...And if people did not expect this, had no plans to back up... . In "Ubuntu for Non-Geeks" by Rickford Grant, I read that if you try an upgrade and it does not work for you, you can return to the previous setup by selecting the older kernal in the GRUB menu. Again, this sounds like a good idea, but it does not seem to work. At present, from what I have read, there is no viable way of "downgrading" to a previous setup, once an upgrade has been attempted. Ubuntu developers seem to be working hard to attract new users (like me) away from Windows, which is very good, but I hope they will do more for us once we are here and making the upgrade process better would be a good place to start.

Now, why is there all this discontinuity between releases in the first place? It has something to do with the source code behind the packages, like a different version of Python used in Hardy that is incompatible with Gutsy packages, right? Well, I am not a programmer and have never written any code, so it would be very arrogant of me to criticise here, but this situation seems to be endemic to the way Linux is organized as a collection of more or less independent packages. But isn't there something that could be done to bridge releases and make them more continuous? I mean, right now, Gutsy and Hardy are essentially different distributions altogether, right? Ubuntu is not really a single distribution at all, is it? If I have to do a clean installation between one release of Ubuntu and the next, what is to dissuade me from going from Ubuntu to Debian or some other GNU/Linux distribution? What do Gutsy and Hardy have in common that would substantially justify calling them a single distribution in the first place?

These thoughts came into relief for me when I started reading about BSD (Berkeley Software Distribution) operating systems. Up to then, I was prepared to think of release discontinuities as just an inevitable fact of life. Windows and Linux seems to both have this problem, so maybe it is just something I must learn to live with. But then (correct me if I am wrong) BSDs like FreeBSD seem to have overcome the problem with parallel releases being mutually compatible and evolving simultaneously, based on a unified base system. Well, taken at face value, this seems to be the way to go. Can't something be done with Ubuntu to make it more like that?

(This is just a suggestion. I cannot code it, but maybe someone else could.)

---

### Post by Methuselah on 2008-07-19
I used FreeBSD and loved it.
But I did experience one upgrade process from 6->7.
I had to build the kernel which was fine.
However, it was also recommended that you rebuild all 'ports'.

Archlinux 'rolling-release' is propbably closer to what you'd like.

---

### Post by hyper_ch on 2008-07-19
well, if everything works as you want, why do you upgrade?

but the point is that between releases a lot of packages get altered... so other packages depending on it will also need to adjust and hence other configuration is needed.. that's because of the modular build of linux.

---

### Post by GOfree on 2008-07-20
Thanks for the replies.

(Maybe that's all I'm gonna get.)

Thanks for the insight into FreeBSD, Methuselah. I guess I had a misconception there. I am not sure that I would be up to rebuilding the kernal or the ports. Maybe. Thanks for the heads-up on Archlinux. This sounds more like a reasonable challenge for me. From what I have read about Arch, I may be a typical candidate for that distribution, and you have just saved me from a long, drawn-out process of distro-hopping. 

Thanks for your response, hyper_ch. That is the question, isn't it. Why upgrade if everything works already? Maybe it is all the hype that surrounds a new release. Maybe it is the sense that there must be something wrong with the old release. I don't know. What I want to know is how experienced users respond to new releases. From your response, I take it that, maybe, you have been through a few release cycles, and are not swept up by the hype and not afraid that the release you are using will become obsolete. I am reading into your response here.

Anyways, off we go. Thanks Ubuntu for weaning me off Windows. Let's see what else is out there.

(Row, row, row, your boat, gently down the stream. Merrily, merrily, merrily, merrily, life is but a dream.)

---

### Post by tiachopvutru on 2008-07-20
I can't exactly be sure that it says what I understand it to be, but maybe your problem will be gone by the next release?

Look at number 5 on the following [link]("http://fabrizioballiano.net/2008/07/19/10-2-things-youll-get-with-ubuntu-810-intrepid-ibex/").

---

### Post by Sef on 2008-07-20
moved to community cafe.

---

### Post by Yes on 2008-07-20
Did you upgrade, or do a clean install of 8.04?  When I upgraded to 7.10 I had nothing but problems, but since I had my /home folder on a seperate partition I was able to easily and painlessly do a clean install, and everything worked perfectly.

---

### Post by kko1 on 2008-07-20
> **GOfree said:**
> As a newbie, I find the whole idea of serial releases and upgrading rather disconcerting. Why is this process so painful?

If I were to get philosophical, I would say it is painful so you would learn. Now, I don't mean that it is designed so, but - as I have myself experienced - battling with unwanted technical challenges IS painful, and filled with anxiety, when you ARE inexperienced. In other words, the *painfulness* is inherent in the situation. Once you learn to navigate your way through it, the pain diminishes (though rarely goes away entirely).

Then, on the technical side - sometimes upgrades just work, sometimes they don't. People's experiences vary according to what equipment they happen to have (and what particular programs they use), and the different combinations are so numerous that the developers simply cannot test for every one of them.

> **GOfree said:**
> I have figured out how to make a separate partitition for my home folder, which means that I don't have to back up my work for a clean install.

That is a good thing, which usually lessens the burden of an upgrade significantly.

However, I would recommend keeping backups of your essential personal files at all times regardless.

> **GOfree said:**
> In "Ubuntu for Non-Geeks" by Rickford Grant, I read that if you try an upgrade and it does not work for you, you can return to the previous setup by selecting the older kernal in the GRUB menu.

This only applies to *kernel* upgrades. As you've discovered, it doesn't apply to system upgrades as a whole.

Whether or not system *downgrades* (e.g. from Hardy to Gutsy) should be possible (for when things go wrong), I won't argue. However, I will say one thing. If the developers worked hard to allow for *downgrades*, it would reduce the time they can spend on securing that the *up*grades work as smoothly as possible.

> **GOfree said:**
> I hope they will do more for us once we are here and making the upgrade process better would be a good place to start.

As said, there are so many things that can go wrong, that... well, it's a good wish, but if new versions of anything are to be introduced at any point in time, upgrades will risk breaking things. (In your word, it is *endemic* in *change* itself. If you don't upgrade, you won't have to face it.)

In fact I tried to start a discussion about a parallel theme a while ago. I suppose the discontinuity (different version of Python, rewrites of programs instead of just gradually trying to fix bugs, changing to a different sound server) just represents some of the *tradeoffs* the coders and distribution packagers and maintainers have to make between continuity and new functionality 'wanted'. (Wanted by whom?)

The dilemmas of 'progress', in other words. (Or if no progress is being made, dilemmas of 'regress' or of 'stagnation'. :p ) We, as users, have to live with that, or search for alternatives (one of which is trying to avoid it).

At this point, we may again get philosophical about whether upgrades are needed at all, and whether 'progress' in the world of free software (or elsewhere in the world) really represents progress at all, or whether it is just repeating the past in a new wrapper.

> **GOfree said:**
> I mean, right now, Gutsy and Hardy are essentially different distributions altogether, right?

Essentially yes.

> **GOfree said:**
> BSD

I don't know BSD, but "parallel releases being mutually compatible", "based on a unified base system" sounds like Kubuntu, Ubuntu & Xubuntu to me. That is, a unified base released with a different topping (that is, a different Desktop Environment).

> **GOfree said:**
> Ubuntu is not really a single distribution at all, is it?

This is actually a good question. And no, it isn't. You could define "a distribution" in various ways, but considering that there are different "sets of versions" (Warty, ... , Hardy, etc.), and within these there are defined "sets" for Ku-, U-, Xu-, Edu- and what-have-you- buntu, including the plain server version, indeed what fits into this program universe isn't a monolithic entity at all.

> **GOfree said:**
> What do Gutsy and Hardy have in common that would substantially justify calling them a single distribution in the first place?

Nothing, save the *upgrade path*, which, for some, works, for some not. (And, of course, a mostly similar choice of standard programs and custom settings to install.) If that's enough for you or not is for you to decide.

> **GOfree said:**
> If I have to do a clean installation between one release of Ubuntu and the next, what is to dissuade me from going from Ubuntu to Debian or some other GNU/Linux distribution?

Nothing whatsoever. And no lock-in of that or any other kind is necessary, either.

I hope you find my musings, if not helpful, at least amusing.

kko1

---

### Post by ssam on 2008-07-20
you don't need to put home on a separate partition. if you tell the installer to use a partition that already has a home directory on it then the installer will only delete the system folders (/etc, /bin, /usr ...). (make sure you do not have the format check box ticked.)

---

### Post by kko1 on 2008-07-21
> **ssam said:**
> if you tell **the installer** to use a partition that already has a home directory on it then the installer will only delete the system folders (/etc, /bin, /usr ...). (make sure you do not have the format check box ticked.)

Which installer are we talking about? Ubuntu Live-CD installer, Ubuntu alternate CD installer, something else?

(I will continue to keep my */home* separate nonetheless.)

---

### Post by Bachstelze on 2008-07-21
> **ssam said:**
> you don't need to put home on a separate partition. if you tell the installer to use a partition that already has a home directory on it then the installer will only delete the system folders (/etc, /bin, /usr ...). (make sure you do not have the format check box ticked.)

This is **WRONG**. When installing with an unclean root filesystem, the installer will not delete anything, it will just copy the new files, overwriting files that might be already be there, but it is a very bad idea to do so, as any corrupted, harmful, or otherwise undesirable files that were on the previous system will likely still be there.

---

### Post by GOfree on 2008-07-25
kko1,

Thanks a lot for the thoughtful reply.

I apologize for not replying sooner. I have been thinking about what to say. 

Also, I had to check myself to make sure that I was not going off on a rant. I don't want to seem like I am putting Ubuntu down. I am just trying to get my bearings in this new Gnu/Linux world and find out which way is up. I guess I have a bad tendency, when I don't understand something, to jump up and down and yell, "This doesn't make sense!"

I am probably only revealing my own ignorance here, but as an ordinary newbie, my perception is probably not uncommon. From what I have read, Ubuntu is designed with the newbie in mind, and this experience with upgrades could possibly turn a lot of people off. There has got to be a better way.

---

### Post by GOfree on 2008-07-25
kko1, you raised a lot of questions that I have been thinking about: the idea of progress, the part of progress in the free software world, tradeoffs between continuity and functionality, and the centrality of the upgrade path to the identity of a distribution. 

I have always been a little (a lot?) cynical about "upgrades". The very word "upgrade" has become a catch-phrase in marketing and advertising. As you pointed out, there is a chance of stagnation without progress (or at least perceived progress). But is it really necessary to production or simply consumption? People can still do things with older technologies (software) and learn to use them in new ways, without all the "new features". But the system of *consumption* would stop as people would eventually run out of needs. With Microsloft, it is easy to understand why they *have* to come out with upgrades and *imposed* incompatibilities--to force people to buy more software. But surely this doesn't apply to Free Software, does it? (Unless there is some egoistic gain to being the most popular distribution or something.)

Now, I guess the discontinuities are somewhat inevitable with Gnu/Linux, aren't they? I understand that distributions are loose conglomerations of many packages--created by more or less independent project teams. Without a centralized structure, I can only imagine the difficulties that must arise when putting all these packages together--with different versions of code, or whatever. Maybe this is what Mark Shuttlesworth is trying to work out by getting all the projects to work together on a common release schedule. I don't know.

I can appreciate (or imagine) the difficulties involved, but as we seem to agree, it is the upgrade path that, more than anything else, defines a distribution as a single entity across various releases. 

> Q: What do Gutsy and Hardy have in common that would substantially justify calling them a single distribution in the first place?

A: Nothing, save the upgrade path, which, for some, works, for some not. (And, of course, a mostly similar choice of standard programs and custom settings to install.) If that's enough for you or not is for you to decide.


Sure, as you say, there is a relatively consistent selection of programs and settings in Ubuntu (as far as I know). Is that enough? If it is a personal choice, I have to say no. Most of us are going to choose packages and settings ourselves anyway. What, I think, we depend on from the distribution is to make sure that these packages and settings will continue to work together from one release to the next. That's what it would mean to me to say "Ubuntu" and not just "my own Gnu/Linux configuration".

...*Ah ha!* That's it, isn't it? There is just an enormous number of contingencies to work out for every users' package selections and preferences. The distribution team that is able to best work out the dependencies will have the "best" distribution. Okay, I think I get it.

Well if it is a tradeoff, as you say, between continuity and functionality, then maybe Ubuntu should rethink their gameplan. By "functionality" I hear you saying "new features", and evidentally Ubuntu is making their market strategy to be the most cutting-edge distribution on the block. That's fine. Kudos! At the same time, Ubuntu is *supposed* to be "newbie-friendly", and maybe we cannot have it both ways. As a newbie myself, I would prefer to have a more conservative and stable environment then a lot of fancy apps that I will never use. If you are gonna have the fancy apps that require a lot of fine tuning, then it seems you've gotta market your distro as a being for more advanced users.

I am going on too long, and this has probably been said before...

---

### Post by mips on 2008-07-25
Well you are always going to have these issues. Every six months or so Ubuntu takes a snapshop of Debian Sid and then builds it's own stable packages based on that. They don't actually build on previous Ubuntu versions.

If you don't like this you might want to consider a distro that uses a rolling release cycle like Arch and some others.

---

### Post by kko1 on 2008-07-25
> **GOfree said:**
> Thanks a lot for the thoughtful reply.

I apologize for not replying sooner. I have been thinking about what to say. 

Also, I had to check myself to make sure that I was not going off on a rant.

You're welcome. I appreciate a thought out response as much as you do.

> **GOfree said:**
> I guess I have a bad tendency, when I don't understand something, to jump up and down and yell, "This doesn't make sense!"

Ah, but don't we all? ;)

As it happens, it often *doesn't* "make sense". At least not from *where we're standing*.

(In other words, when you look at things from one angle (with the accompanying experiences), they look quite different compared with someone else's viewpoint. Your viewpoint is equally legitimate here as mine or someone else's.)

> **GOfree said:**
> There has got to be a better way.

There probably is. (There *usually* is. But where? ;) )

---

### Post by kko1 on 2008-07-25
> **GOfree said:**
> kko1, you raised a lot of questions that I have been thinking about: the idea of progress, the part of progress in the free software world, tradeoffs between continuity and functionality, and the centrality of the upgrade path to the identity of a distribution.

I'm glad to have been of service. ;)

It goes both ways, I find myself enjoying pondering upon these questions, so thank you for the stimulus.

> **GOfree said:**
> I have always been a little (a lot?) cynical about "upgrades". ... People can still do things with older technologies (software) and learn to use them in new ways, without all the "new features". But the system of *consumption* would stop as people would eventually run out of needs.

Quite so.

> **GOfree said:**
> Now, I guess the discontinuities are somewhat inevitable with Gnu/Linux, aren't they? I understand that distributions are loose conglomerations of many packages--created by more or less independent project teams.

Exactly.

(Just *when* and* how often* you face these discontinuities depends on a number of things as you've noticed. Programs may become abandoned (which may not matter if you keep your environment stable), and other programs still maintained may face other choices. And how the distributions *manage* and *create* discontinuities, and how often this happens, which is what prompted your initial post. I'm sure there are other considerations as well.

I'll write down a personal example. I use *KDE*, so within the next three or so years I will probably face the choice of *when* to switch to *KDE 4.x*, which is a rather large discontinuity. *If* I so desire, or if I desire something else that may be dependent on it, that is. If you don't use *KDE*, this may not apply to you, but there will be other programs, other choices, major or minor.)

> **GOfree said:**
> Maybe this is what Mark Shuttlesworth is trying to work out by getting all the projects to work together on a common release schedule. I don't know.

Yes, that is part of it. Mr. Shuttleworth has also worked to encourage an active flow of code from the distributions *upstream* and across different distributions (for instance through interlinked bug trackers, via the Launchpad), so when an improvement (a bug fix or something else) is made in one place, the wheel doesn't need to be reinvented elsewhere. Says and hopes Mr. Shuttleworth. :)

> **GOfree said:**
> ...*Ah ha!* That's it, isn't it? There is just an enormous number of contingencies to work out for every users' package selections and preferences. The distribution team that is able to best work out the dependencies will have the "best" distribution. Okay, I think I get it.

Well said.

I'll add one thing to consider though. How about the following statement? "The distribution team that provides their users with the best means to themselves deal with setting up the system the way they like (and keeping it functional) will have the "best" distribution."

> **GOfree said:**
> (Unless there is some egoistic gain to being the most popular distribution or something.)

But isn't there always?

It is a *good* thing or it's *bad*. Different people strive to create (and market) the best option (from where they're standing, i.e. how they see things). This drives forward improvements, and sometimes gives more choice, yet at the same time it may create an *illusion* of progress.

(The multitude of distributions *may* also create an *illusion of choice*, where in reality it's just more of the same. That could be considered another facet of the illusion of progress.)

> **GOfree said:**
> evidentally Ubuntu is making their market strategy to be the most cutting-edge distribution on the block. That's fine. Kudos! At the same time, Ubuntu is *supposed* to be "newbie-friendly", and maybe we cannot have it both ways.

Maybe we can't.

I wouldn't say that Ubuntu even wants to be the *most* cutting-edge option though, simply cutting-edge "enough" (what ever that may mean), and with "enough" bling-bling. :p

(And yes, there have been voices saying "what has eyecandy to do with the spirit of *ubuntu*?" I don't want to rehash that conversation here, but they had a point. However, also those who responded with "yes, but eyecandy attracts new people and this will help spread the spirit of *ubuntu* and the ideas of free software in general" had reason. As I said though, I don't want to rehash that argument here, we "might" not be able to resolve the question in a final manner one way or the other. ;) )

> **GOfree said:**
> If it is a personal choice, I have to say no.

I'll repeat my opinion that it most definitely *is* a personal choice. Out of a limited set of options, mind you, but a choice none-the-less. (As a quasi-philosophical aside, choice out of an *un*limited set of options with limited capability to decide is a daunting thought.)

> **GOfree said:**
> As a newbie myself, I would prefer to have a more conservative and stable environment then a lot of fancy apps that I will never use. If you are gonna have the fancy apps that require a lot of fine tuning, then it seems you've gotta market your distro as a being for more advanced users.

I haven't tried a lot of different (& recent enough) distributions, so I am not one to best judge which would be the *most* newbie-friendly. (And people *will* have differing opinions on the topic. For me, Kubuntu LTS has been a reasonable option, but I wouldn't presume to speak for others' experiences.)

That said, if you choose to keep any of the ubuntu flavours, perhaps the *Long Term Support* releases would be an option - *generally speaking*. (And *specifically*, *IF* whatever the reason is that keeps Hardy/8.04 from working for you gets resolved - that's the dilemma you find yourself with in this moment.) With those, at least when you have the system up and configured, you have the option to stick with a relatively stable set for three years (and then some, if you assume you can afford to "not update" for a few months more), and then perhaps upgrade not to the next *LTS* release but the one after that.

For even more slow-paced & stable goals, the to-be-released Debian 5.0 may be an option to consider.

However, *stable* and *newbie-friendly* do not necessarily equate. (In other words, "stable" means less upgrade hassle, but *may* involve other hassles.) And further, what exactly to each signifies *newbie-friendliness* probably varies quite a lot, so I *will not even try* to probe that question any further.

(Another option is the release system that *mips* brought up. It doubtless works differently from both of the above, but as I haven't used it, I don't know what *different* compromises it may involve.)

---

### Post by Foster Grant on 2008-07-25
Not all distributions use a scheduled-release plan --- Arch Linux and Gentoo in particular use rolling-release upgrades rather than saying, "Look, we have a shiny new version which might break everything you have running right!" every year or six months. There might be others but those two are the best-known.

The downside to rolling releases is obvious: With the new-release model, every six months (in the case of Fedora and Ubuntu), you have a new chance to promote the heck out of both your distribution and Linux in general. It's a standout marketing opportunity.

---

