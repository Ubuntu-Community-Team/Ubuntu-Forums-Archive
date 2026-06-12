---
title: "Propietary games for Linux/BSD - Will ye | Nil ye?"
date: 2008-05-06
forum: The Cafe
---

### Post by Xanderfoxx on 2008-05-06
I have a lot of friends who are aspiring to become game developers, as well as a brother, and I want to show my support and appreciation of Linux, but I need to know if commercial games are feasible in this market.

Would any of you buy an exclusively Linux game. I know some of you play UT2004, but I don't know if people pay for that, so I cannot make an assessment based on that.

I have been formulating good ideas for both commercial and hybrid (servers are released under GPL 2.0)

If anyone thinks either way, whether it's a bad idea or a good one, to promote Linux in the commercial or partially commercial serious computer game market please say so.

No flaming, please.

---

### Post by -gabe-noob- on 2008-05-06
I sugest making the game multi platform (it sounds as if you want  it to be linux only) 
and if the game is good gamers will play it. :D

---

### Post by klange on 2008-05-06
Exclusivity usually isn't a good thing.
Things have to move one step at a time. Once pretty much all games are multi-platform, then maybe we can start seeing some exclusivity.
Same goes for the open-sourcing, let's let the game companies port their stuff first, then slowly petition for more open code.

---

### Post by schtufbox on 2008-05-06
If there is a linux native version of a game, and I don't already own the Windows version, then I will buy native.
The problem with some developers is, they'll release a Linux version about a year (or more in some cases) after the Windows release. Call me impatient, but if it'll run in Wine, I won't wait a year.  If however, like Bioware did with NWN, they release the Linux Binaries so you can just use your old CD's and not buy the game again, then that's great :)
So yes, I'd buy native, but not if you released it a year after a windows version.

---

### Post by DeadSuperHero on 2008-05-06
I would definitely buy them!

---

### Post by Xanderfoxx on 2008-05-06
> **-gabe-noob- said:**
> I sugest making the game multi platform (it sounds as if you want  it to be linux only) 

Well, yeah, it will be multiplatform, but for the heavy-hitters, I may have to go ahead and develop separately for each platform. SDL and other libraries like it may slow down systems to much. Anyone who knows better, feel free to correct me, but multiple layers of abstraction and virtualization will slow even greatest and noblest beast of a gaming box, therefore ruining gaming experience.

> **-gabe-noob- said:**
> 
and if the game is good gamers will play it. :D

I sure hope I will have the resources to do my currently-fermenting ideas justice.

I hate to skimp on things like this, as once one gets out there with that great idea, and funding doesn't allow the best features to be implemented, there goes the venture. Poof! Where did the money go? Oh, well.

I have ideas on how to open source the games as much as possible, to promote it and gain a fan base for modules, add-ons, and the like, but just barely closed enough (portions like the main client) to make a profit (and therefore promote Linux/OpenBSD/FreeBSD to more traditional game dev markets,) before some guy wiht nothing better to do reverse engineers it. Hey, it's a free country (supposedly, and reverse-engineering is (or should be) a calculated risk. If everybody is nice, and nobody reverse-engineers any of the software I would oversee development of, I would release the software under GPL 2.0 either after it has made a 10% profit, or about 7 years after it hits the market, whatever comes first, anyway.

That is the basic idea behind trying to crossover propietary ways of doing things onto clearly superior technologies (and I'm not just saying that to stain my nose brown. I really believe that Linux, BSD, and similar platforms have vastly more potential than any propietary technology I can think of, and especially the one that everybody and their dog have a mutual hatred of).

I have some ideas, and I won't say too much, about games that I might employ in this manner.

I'm thinking of a MMORTS game, high quality graphics, OpenGL and OpenAL w/ EAX 4 support, multiple tactial display compatable, borrows the very best from well known RTS games, but adds some new and fresh ideas and proficiencies to the mix. 

I love C&C Red Alert 2, Warcraft 3, and Homeworld 2, and I intend to integrate the best of interface design and game logic into an MMORTS game engine that is developed first in Python using paid developers, then open-sourced under LGPL 2.0 for further development. Give a little, get a little, give a lot, get a lot. Isn't that how it should work?

Anyway, won't say too much.

And yes, I'm aware there are some existing open source RTS engines out there, but the ones I've seen are hardly out of the womb, no offence intended.

Good Night!:guitar:

---

### Post by Xanderfoxx on 2008-05-06
> **schtufbox said:**
> If there is a linux native version of a game, and I don't already own the Windows version, then I will buy native.
...
So yes, I'd buy native, but not if you released it a year after a windows version.

I would never do such a thing. The open source community has done a lot for me, making available great products for the best price - zip! Even better products are sometimes those open source but commercial products - I have yet to try a major one, but I sure intend to.

Therefore, I would release the native Linux (ELF) binaries, neatly packaged, a year beforehand, if it was up to me. If I sell any of my ideas, though, I may have limited negotiating power over the terms. Sorry.

---

### Post by drascus on 2008-05-06
Well As for games I would say no to a totally propritery game. However I would suggest a more hybrid approach. So I would say have the software parts Like the game engine, Networking Software and such be Free Software. While license the Artwork and music/sounds. That way people can use the Software in Freedom. Art doesn't need to be Free because its just there for appreciation and doesn't do practical work. But the Software parts of the Game should be Free otherwise it rasies ethical concerns.

---

### Post by -gabe-noob- on 2008-05-06
Remeber: 

Gameplay>Graphics


but then again, you can't sell gameplay :(

---

### Post by Phenax on 2008-05-06
> **Xanderfoxx said:**
> SDL and other libraries like it may slow down systems to much.

SDL is a very simple abstraction layer and has a very minimal (likely unnoticeable) performance hit. Games like Quake 4 and ET:QW use it for their Linux version..

AFAIK they have hand-crafted Windows versions because SDL wraps around DirectX 7, so if you want an OpenGL or DirectX 9/10 based game, I don't think that will work.

---

### Post by the yawner on 2008-05-06
I'd suggest focusing on Linux platform first and work on supporting other platforms later.

---

### Post by Xanderfoxx on 2008-05-07
> **Phenax said:**
> SDL is a very simple abstraction layer and has a very minimal (likely unnoticeable) performance hit. Games like Quake 4 and ET:QW use it for their Linux version..

AFAIK they have hand-crafted Windows versions because SDL wraps around DirectX 7, so if you want an OpenGL or DirectX 9/10 based game, I don't think that will work.

Ok. Does using SDL preclude the more advanced features, such as EAX 4 (3d sound hardware acceleration for occlusion, positional audio, and source effects, available on Creative Labs Sound Blaster Audigy cards, such as those used under Linux), and other thngs like that?

Also, what are the merits of using SDL rather than a heavily modified version of PyGame?

---

### Post by insane_alien on 2008-05-07
If games were made for linux and they were good then i would buy them proprietry or not. although that depends on if they appeal to my preferences(zombie killin, lots of zombie killin).

---

### Post by BigSilly on 2008-05-07
As a gamer and a Linux user, I would be very happy to buy games made for Linux. The only downside I see is that many Linux users have very unremarkable hardware. I know it might sound silly and a bit of a generalisation, but many use Linux because it makes the most of older and somewhat unspectacular hardware. I can't imagine it being worth any developer's time making games as demanding as something like Crysis work on Linux. 

Then again, I say that but speaking for myself I'm hoping to upgrade the old PC soon into something a bit more up to date. Since I won't be 'upgrading' to any new version of Windows, it'd be great to think that modern games could be forthcoming for Linux. 

I'm not making this any easier am I? Bottom line, yes I would buy Linux games. :D

---

### Post by super breadfish on 2008-05-07
No thanks. Considering all that malware, sorry, copy protection included with commercial PC games now you might as well be running Windows in the first place. Who wants a Linux port of a game if it comes with a Linux port of Starforce?

---

### Post by Tuna-Fish on 2008-05-07
The freedom argument simply disappears when you consider that games are basically interchangeable commodities that have no importance on individual freedoms. Having your life's work in a proprietary format only accessible by a closed application is a major problem. Spending your free time shooting bad guys in a closed app - not so much.

I'm perfectly willing to pay for quality games on any platform, and I wish more were made for linux so I could stop wasting my time with wine. (Not either having a native linux port or working in wine is a showstopper for me - I don't want to have a win partition with all it's troubles just for games.)

List of games I've bought for linux:
[Defcon]("http://www.introversion.co.uk/defcon/") - Awesome nuclear war game. Try the free demo, after that it's so cheap you just can't avoid buying it...
[Dominions 2, 3]("http://www.shrapnelgames.com/Illwinter/Dom3/1.htm") - An old-school strategy gem from sweden with a fantasy background that for once is well-researched, ridiculously deep and not just a cheap tolkien copy. Somewhat micromanagement-heavy, and kinda sucks for single player, but endless hours of pure fun in multiplayer.
UT 2004 - Half of all linux gamers have this. I wish we'd get a linux port of UT 2007 soon.

also, I play a lot of free software games, mainly [spring]("http://spring.clan-sy.com/") (it has an ubuntu [repo]("http://spring.clan-sy.com/wiki/Ubuntu_install").), [Vega strike]("http://vegastrike.sourceforge.net/") (an old version is in the ubuntu repos, a new one can be compiled with help from the wiki).

I also have my hopes up for [thousand parsec]("http://www.thousandparsec.net/tp/"), being an old-time stars! aficionado.

---

### Post by Tuna-Fish on 2008-05-07
> **super breadfish said:**
> No thanks. Considering all that malware, sorry, copy protection included with commercial PC games now you might as well be running Windows in the first place. Who wants a Linux port of a game if it comes with a Linux port of Starforce?

You cannot make a linux port of starforce - at least not one that cannot be removed easily and safely. A free kernel does give some assurances.

---

### Post by Tuxoid on 2008-05-07
The issue around FOSS games is that it doesn't facilitates parts of the creative design. I myself am an aspiring Game Designer. I have tried FOSS games for Linux and have been fairly unimpressed. I don't believe FOSS games necessarily need to be bad, they could be good. I don't think can be good under the current GPL. The GPL allows people to modify the creativity that can only exist in the game's source code. I am not talking about the technical pieces of code being creative; I'm talking any code required to make the game difficult, code used to design gameplay mechanics, and many other pieces of code that do not have just a technical advantage.

Richard Stallman stated in a talk, "Games are separated by a game engine (the technical part), and a collection of media"

I believe this is an inaccurate statement. As I mentioned, there are some creative pieces of games that can only exist in code. Allowing modification of any creative work is considered taboo in any media field.
These people (including myself) can be highly critical. Giving people the ability to modify creative parts of a game can destroy the Designer's vision and reputation.

The source code needs to be available to certain extent, modification should available to a certain extent, but when it comes to publication of modifications, players could be to believe mislead that it was the original copy from the original team. Even if there is a message in the game stating it is not the original copy, it's possible that many player will not see it.

The thing with general purpose applications is that they are not designed for stand-alone entertainment. For example, with a media player like Totem, it requires audio or video files to actually serve the function of entertainment. A game does serve as stand-alone entertainment. 

Game software therefore requires the same respect as any other form of entertainment media.

---

### Post by Xanderfoxx on 2008-05-10
> **Tuxoid said:**
> The issue around FOSS games is that it doesn't facilitates parts of the creative design. ... The GPL allows people to modify the creativity that can only exist in the game's source code. I am not talking about the technical pieces of code being creative; I'm talking any code required to make the game difficult, code used to design gameplay mechanics, and many other pieces of code that do not have just a technical advantage.

Richard Stallman stated in a talk, "Games are separated by a game engine (the technical part), and a collection of media"

I believe this is an inaccurate statement. 

...

Game software therefore requires the same respect as any other form of entertainment media.

This is a good point.

One could make this code available under a different name than the propietary product, where the name indicates the whole product, including the sprites, models, audio and video, but is clearly linked the the source code available under an open source project, or is this taboo?

My initial idea was to make the engine highly modular, so that critical components of gameplay, such as the AI and logic specific to the game, rather than the genre (the engine), as well as the multimedia, would not be released immediately.

Some components, like the game application framework (newly coded or modified by paid staff) would be released as an open source project immediately, and to a commercial mindset, like that of investors lending capital to me, I can explain that this is a promotional and loyalty-gaining gig, while truly, I believe that this should be made available, anyway.

Despite what Stallman says, I will design it so that loadable modules containing game -specific logic and AI, that would not be good to release immediately, can be released after 7 years. This way, I can release the core engine the moment it is finished.

I still have to think about what would be best for the community, and for the investors, as well. Delicate balance, indeed!

---

### Post by Luke has no name on 2008-05-10
I don't believe Proprietary is inherently evil (I just lost a friend in RMS).

While completely free is great for some applications, it is not bad to have binary only distributions of a game. It can be very expensive to produce a good game, and it takes very specific talent to make a good game. Also considering that a game is not a necessary piece of software (As opposed to spreadsheets and word editors), I believe that I would pay for a good game.

Cross-platform would be the best way, like UT2004 did. When is OGL3 coming out?

---

### Post by qazwsx on 2008-05-10
Mixed license?

I am not one of those gnu persons but engine and artwork can be separated. I think even RMS approves it.

Makes easier play with diffenrt set of distros.

---

### Post by original_jamingrit on 2008-05-10
I would.  Games for pure entertainment may as well be closed.  I'd definitely prefer open source 'edutainment' over closed, however.

As for FOSS games, mixed licensing (free engine/interface, closed 'campaign' or 'level' module) would definitely by okay in my books.

The main problems I see is there would need some form of anti-cheat to keep multiplayer clients from making modifications that would give them the advantage (eg; keeps them from seeing invisible players, influence random outcomes, etc;)

---

### Post by Xanderfoxx on 2008-05-10
Well, I would probably solve that by relying on the server to perform all logic in multiplayer games, while the client more or less simply renders what it is given from the server (like a thin client relying on a TLSP server to perform OpenGL acceleration and Compiz-Fusion compositing).

That would make a major hit on the server's performance, but minimize the potential for cheating. (What is the fun in that anyway?)

---

### Post by the yawner on 2008-05-10
How about making the engine open-source? Some fps and rpg games were based on the same engines.

---

### Post by the_darkside_986 on 2008-05-11
Speed depends mostly on code optimization, at least in native code such as C/C++. SDL+OpenGL can result in excellent performance that rivals commercial DirectX games. Sauerbraten runs nicely on GNU/Linux on my machine; on the other hand, Elder Scrolls IV: Oblivion, a DirectX game that seems like it could use optimization, is unplayable during battles with many NPC's. I don't think any serious commercial game could be written with PyGame--I mean--what sane program language creates a number array with range() just for numerical for-loops. I tried porting a C++ scrolling background demo to PyGame for fun, and the results were hopelessly terrible, too slow. (Even MiniD, a small scripting language project with only one developer, outperforms Python.)

With that being said, I don't bother too much with PC gaming unless the source code is hack-friendly such as Sauerbraten. I enjoy adding my own features such as bindings to more scripting languages (Lua, MiniD, etc.). But if I cannot do that due to a game's EULA, then I might as well play the game on my new PS3; it's an amazing system that doesn't become obsolete in two weeks after paying $100's to upgrade it (unlike the PC). Oblivion runs beautifully on the PS3, IMO. 

Even UT3 for the PS3 (claims that it) can use mods created on the PC, so I really have no serious need for closed source PC games anyway.

---

### Post by Xanderfoxx on 2008-05-11
Well, I'm glad you said that. If that is a more prevalent opinion than it seems to be now, then people like you who go ahead and say, "don't invest, it's a waste of money, " will save my bacon from malinvestment on a hopeless crusade.

That said, it seems the overwhelming majority of those who bothered to vote voted their interest in decent native or multi-platform games, with the server engine, client engine, app framework, and libraries released as open source, with the stipulation that reusable code be released in 7 years, or full ROI + 7%, whichever comes first.

---

### Post by Xanderfoxx on 2008-05-11
I have this idea, and I want to share it despite the possibility of someone running off with it.

Here it is:


The game itself consists of proprietary modules that extend the engine for game-specific functionality, as well as the media (vorbis (for gameplay music), flac (for gameplay FX), speex (for in-game voice chat, as well as the voices of NPCs), and theora (for streaming screen content to tournament audience monitors (I believe that the term is "gameboard," but I really don't know. What *does* one call the big screen the audience watches to see what is happening in a tournament?), as well as cinematic clips)).

The game engine consists of the core rendering engine, most of the client functionality specific to the genre, and core interfaces to the general game application framework I intend to replace DirectX 10 with.

The Open Game Application Framework, which I hope to code, interfaces with SDL (at least temporarily, until I can get something better, which will be difficult, OpenGL 2.1, OpenAL 1.1 with EAX 5.0 (for when the drivers for X-Fi cards finally come out), and standard a API for a broad range of input devices from controllers to touch screens to Wii remotes. (I'm determined to start a hardware company for the open source community!)

Finally, the reference hardware that I intend to develop, that has full API support, as well as full GNU/Linux, BSD, Solaris, *NIX, WinXP/Vista, Mac OS X, and other support.

I may be a small company, but if I tap into enough developing* markets, and do it right, I think I can manage, somehow.


*edit

---

### Post by macabro22 on 2009-02-14
I just bought world of goo! =]

---

### Post by dannytatom on 2009-02-14
If I ever had a computer that could run new games good, I'd pay for 'em.

---

