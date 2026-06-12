---
title: "How to get more games on Linux... (any programmers out there?)"
date: 2006-11-29
forum: The Cafe
---

### Post by michaeljt on 2006-11-29
Here is something which has been going through my head for a while.  One of the reasons often given for the low Linux uptake (see bug #1) is the lack of commercial games available.  However, it seems to me that these days, nearly all of the effort which goes into producing a game is for the non-coding aspects, and free software game programmers have all the expertise needed for the coding part.

Therefore, a way to remedy this situation might be for free game programmers to write engines to play commercial games.  Linux distros could package those engines, which would solve the problems that game editors have always had to get their games working on different Linux systems.

I realise that this has been done in the past with unhappy results, but I think it could succeed if they stick to the following:

1) Only write the engine, and require the original DVD for all the game data.
2) Make sure that they don't break any copy protection or make it easy to break it.
3) Talk to the game publishers first.

I would have thought that there must be publishers out there who would go along with that, and even help a bit - after all, it increases their market with no additional effort on their part.  And if one or two such engines are implemented, I think that a lot of others would follow.  

Obviously, it would be easiest if existing "clones" of commercial games were adapted to the purpose.  So if you have written one of those, why not give it a try?  Or if there is a clone of some commercial game you like, why not ask the author if they could try adapting it?

I must admit that I have not been a gamer for a long time, one reason why I don't try something like that myself - does it sound very silly?

---

### Post by jleemc44 on 2006-11-29
> **michaeljt said:**
>  - does it sound very silly?

Just a little.....

I should start using that line for my signatures. 

Example:

does it sound very silly?
- michaeljt

---

### Post by Tomosaur on 2006-11-29
I don't really understand your proposal. You want people to write an open-source version of a game engine and then just use the propietary data such as models, sounds etc? This has been done before, for example with 'Open Transport Tycoon'. The underlying code is open-sourced, but you need the original data (or free equivalents of them) to play the game. 

I also think you're misrepresenting just how much effort coding a game engine is. Yes, it's possible for an individual or a small team to create an engine, but for the more complex stuff, you need insane man-hours of coding. Added to that, a game may use more than one propietary engine within it, which effectively doubles the time required. Half Life 2, for example, uses Valve's own Source Engine, but the physics is handled by the Havok Engine. Creating an open-source equivalent of this would be extremely complicated. By the time it'd be workable, in the sense that Half Life 2 would be playable at the same standard as it is on Windows, then Half Life 2 would be seen as Old-Skool, and this just wouldn't attract new users. The most effective way of getting Windows/Commercial games running on Linux is through Wine/Cedega, or the developer itself creating a Linux compatible engine. It's just unworkable, unless the developer has close ties with the OSS community and lets them in on their plans and dev cycles so that the OSS devs can get working on an open engine prior to the game's release.

---

### Post by rowanparker on 2006-11-29
I like the idea.

The most annoying thing is having to boot up into Windows just to play a wretched game!

---

### Post by aysiu on 2006-11-29
Any connection between lack of PC gaming support and Bug #1 would be indirect if existent at all:
[http://www.psychocats.net/essays/gamingperspective](http://www.psychocats.net/essays/gamingperspective)

---

### Post by jleemc44 on 2006-11-29
I think this came up before but, one way to make this happen is to convince developers to work with more multi platform friendly engines such as OpenGL versus Direct X.

---

### Post by Zyphrexi on 2006-11-29
when will game companies learn that I'm the most important person to me?

I demand game companies satisfy my every whim!

I think it's time for some good old-fashioned corporate warfare... deathmatch style.

---

### Post by michaeljt on 2006-11-29
> **Tomosaur said:**
> I don't really understand your proposal. You want people to write an open-source version of a game engine and then just use the propietary data such as models, sounds etc? This has been done before, for example with 'Open Transport Tycoon'. The underlying code is open-sourced, but you need the original data (or free equivalents of them) to play the game.

Yes, basically.

> I also think you're misrepresenting just how much effort coding a game engine is. Yes, it's possible for an individual or a small team to create an engine, but for the more complex stuff, you need insane man-hours of coding. Added to that, a game may use more than one propietary engine within it, which effectively doubles the time required. Half Life 2, for example, uses Valve's own Source Engine, but the physics is handled by the Havok Engine.

I'm afraid I'm a bit out of contact with the gaming scene, as I said (doesn't stop me having silly ideas...)  Would you say that that is a typical level of complexity, and that most (all?) current games could not be adapted from existing engines?

---

### Post by Tomosaur on 2006-11-29
I wouldn't say it's 'typical', but it is certainly a barrier. What I meant, but didn't actually say, was that given the current divide between OSS and commercial developers, the OSS 'conversion' process can only begin once the game is released. The fast pace of technical improvement in the games industry, and computing industry in general, means that by the time the OSS engine is ready for release, the game is no longer current, and people just aren't interested. It can certainly be done, but for big, popular games: HL2, F.E.A.R etc etc etc, the OSS development time probably isn't worth it.

---

### Post by jan on 2006-11-29
Well, I guess everyone would appreciate more quality games for linux... or - better said - easier game installation & accessibility.

---

### Post by michaeljt on 2006-11-30
> **Tomosaur said:**
> What I meant, but didn't actually say, was that given the current divide between OSS and commercial developers, the OSS 'conversion' process can only begin once the game is released. The fast pace of technical improvement in the games industry, and computing industry in general, means that by the time the OSS engine is ready for release, the game is no longer current, and people just aren't interested.

Do game pubishers still release demo versions before the actual game is ready?  It might be possible to work on those first to have a head start.

You are certainly right that writing free engines would not be a general solution.  Perhaps though, it could be done for a few games - for the easier nuts to crack (and again, it should definitely be done working with, not against the publishers, if only to prevent legal problems) and well publicised by getting the engines included in various distributions in a timely manner.  Then other publishers might become interested and offer support to people wanting to write engines - or start producing them themselves.

What do you think?

---

### Post by Magnes on 2006-11-30
Help with WINE development, then more games will be working and it's easier than writing own version of whole game engine.

---

### Post by Kittie Rose on 2006-11-30
For reference, MMF2 now works just fine on Wine, according to WineHQ.

Of course I haven't tried it since the support base for Wine is piss poor.

> Help with WINE development, 

The problem with WINE is that when something goes wrong, nobody knows how to or wants to help you fix it.

I don't think games should be "free software", at least not "big ones". Games like Shenmue or Metal Gear Solid would never have come about that way... I think there should be more simple free games though, and old SNES/NES/MD/MS games should be finally considered abandonware(damn you Wii).

---

### Post by michaeljt on 2006-11-30
> **Kittie Rose said:**
> I don't think games should be "free software", at least not "big ones". Games like Shenmue or Metal Gear Solid would never have come about that way... I think there should be more simple free games though, and old SNES/NES/MD/MS games should be finally considered abandonware(damn you Wii).

But they might be open source.  Whether a free engine to play a game which can't be freely redistributed counts as free software I don't know.  But if the engines are free/open source, each Linux distributor can package the engine so that it works on their distribution.  That way you just do emerge/rpm/apt-get metalgear and stick in the (non-free) DVD and away you go.

And it might be more reliable than Wine, although Wine is making progress.  The other way would be if game publishers specifically tested under Wine, but I think that that would still end up more fiddly than if they could say "This game works natively on (say) Ubuntu Feisty, Fedora 7 and Mandriva (whatever)" because those distros package the free engine and save them the effort of making sure it works on each.

---

