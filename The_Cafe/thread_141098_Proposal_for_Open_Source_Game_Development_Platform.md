---
title: "Proposal for Open Source Game Development Platform"
date: 2006-03-07
forum: The Cafe
---

### Post by SSTwinrova on 2006-03-07
Someone posted yesterday in an old thread about why Linux is generally lacking in the commercial game department and gave a lot of what I felt were very good reasons why studios stick with DirectX/Windows. Here's an excerpt from the post ([http://ubuntuforums.org/showpost.php?p=799128&postcount=32](http://ubuntuforums.org/showpost.php?p=799128&postcount=32)) outlining what he suggested is needed:

[QUOTE=_dv]Summarizing; what is needed:
* One coherent, well-tested game SDK incorporating OpenGL, SDL, GLEW (important for extension handling!), maybe OpenAL or Audiere, and Newton (not ODE - Newton is a free physics engine, closed source but freely available; it is FAR easier to develop with Newton than with ODE, with better results too)
* EXTREMELY well done SDK documentation
* Good toolchain WITH GOOD GUIs (good GUIs seem to be kind of lame in the Linux world - sorry guys, this just scares devs and especially content producers away)
* Good tutorials
* One good IDE with RAD support and scons integration (or its enhancement bksys or something else, just not autotools please, we don't want to waste our time debugging m4 scripts or god forbid configure scripts)
* Good tutorials for general Linux/Unix development
* Better manners; not all devs are into hardcore l33t network programming, you know [/QUOTE]

I replied to the thread and posted in the (K)Ubuntu Gaming sections with a link to this, but since this is buried a few pages, I thought I would create this thread as a way to see if anyone from the Ubuntu community would be interested in starting to work on some of his points. This of course wouldn't be considered a 3rd Party Project as it does not *directly* benefit Ubuntu in anyway, but my take is that if the Ubuntu community gets recognition for being the ones that start something like this, it will help promote the distro as the OS for developing Linux games on. So, here's my proposal:

I'd like to work with others to create the **Open Source Game Development Platform** (note I'm not using the term Linux, as commerical games for the forseeable future will almost all be developed for Windows, but providing open source alternatives comparable to DX that work on both Windows and Linux will allow porting games to be much easier on the developers). I think that if we could initially get 8-10 people from the community here to start working on some of the following things in their spare time (or maybe just 5+ truly dedicated people), this could get off the ground. Based on _dv's post, I propose this project be broken up into the following three stages:

[LIST=1]
[*]**Software Decision**: Decide exactly what scope this platform would cover. _dv mentions lots of pieces of software, some of which are redundant, so choosing what we want to use is an important first step. (Later on other options could be included, but I think an initial goal of one thing for each job would be plenty).
[*]**Information Collection:** This would be creating the documentation that in the full post is mentioned as being completely fragmented. Completing full, easy to read use documentation for all of the software decided on will be key in getting existing DX developers to switch and lowering the bar as much as possible to new developers. Getting the help of the people in charge of each of the projects would be a plus, so if two different pieces fo software are similar, maybe use this as a guide for what to initially include.
[*]**Platform Creation**: This covers the bulk of the work, getting everything chosen together and making it presentable and look as professional as possible. Also, maybe take an existing IDE and integrate it or write a plugin to work with the platform and try to reach the level that VS is at.
[/LIST]

I'm sure there's stuff I left out and this idea would need tweaking, but that's why I'm posting this: to get feedback. If it appears enough people are interested, I'll register a domain, set up a Wiki (probably the best way to collaborate for this project), and do any of the other backend work necessary that's within my skill range. Of course people familiar with code would be necessary, but I think that **anyone can help**, especially for the documentation section in scouring the web looking for anything which may be of use. I'll post in the Programming Help forums with a link to this thread, but please post your thoughts (even if it's "This is the stupidest idea I've ever heard"  :) ).

---

### Post by Master Shake on 2006-03-07
I think this is a GREAT idea, but methinks (second time I've used that word today!) you'll need a LOT more people involved.

But then again, I'm no programmer.

---

### Post by colo on 2006-03-07
I don't want proprietary games. I don want games needing $THIS_EXACT_VERSION of $SHARED_LIB. Just keep them for yourselves, thanks.

---

### Post by Brunellus on 2006-03-07
What makes this any different from the myriad engines/frameworks/platforms already out there for Linux?  

If you want actual, commercial games, then you need to show that there is an actual market for them.

---

### Post by SSTwinrova on 2006-03-07
[QUOTE=Master Shake]I think this is a GREAT idea, but methinks (second time I've used that word today!) you'll need a LOT more people involved.[/QUOTE]

Oh, I absolutely agree. I'm just saying that if the Ubuntu community could get something off the ground, then we would hopefully start bringing in more volunteers to make this more than *just* an Ubuntu effort.

[QUOTE=colo]I don't want proprietary games. I don want games needing $THIS_EXACT_VERSION of $SHARED_LIB. Just keep them for yourselves, thanks.[/QUOTE]

I fall on the side of the fence that believes Linux can exist just fine with proprietary software being thrown into the mix, but I respect and can see where people who share your opinions are coming from. This platform, however, wouldn't solely benefit proprietary games as having a nice, unified open source platform would allow smaller developers to write games with Linux in mind. And perhaps I just don't know enough about the inner workings of game development, but is the static linking thing absolutely necessary or just common practice? If the latter, I'd think that somewhere along the lines of making this, that issue could be addressed.

---

### Post by SSTwinrova on 2006-03-07
[QUOTE=Brunellus]What makes this any different from the myriad engines/frameworks/platforms already out there for Linux?[/QUOTE]

What this project would be focused on wouldn't be so much about writing anything new as it would be taking all the existing efforts and attempting to integrate them as nicely as possible and provide a cohesive set of documentation. Yes, there's OpenGL/AL, numerous toolkits, etc. all available and these would absolutely be used, but getting everything into a single download and saying "This is what you need and here's how to interface with it" would be a great improvement over what already exists. If there is something as complete as I'm referring to, please post with a link to it, as I'm simply assuming most of what _dv said in his post was true.

[QUOTE=Brunellus]If you want actual, commercial games, then you need to show that there is an actual market for them.[/QUOTE]

I agree, but wouldn't you agree that games developed with DX in mind have a slim to none chance of being natively ported to Linux? This is more of a way to allow for games to be ported if the developer wishes to do so (think of it as trying to create a bridge in the catch-22 situation we're in right now).

---

### Post by Bandit on 2006-03-07
I have always wanted my own MMORPG, I also would be very willing to help develop one also.  If we had our own Ubuntu MMORPG that would be so kewl..

---

### Post by Zeroedout on 2006-03-08
[quote=Bandit]I have always wanted my own MMORPG, I also would be very willing to help develop one also. If we had our own Ubuntu MMORPG that would be so kewl..[/quote]
There is atleast one FOSS MMORPG being developed. I can't remember the name of it off hand, (i'de google for it, but i get so little free time now days) but i'm sure they could use another hand :)

As for the project getting everything into one download, that sounds really interesting, and as far as i know hasn't been done. Is it something that can be done though? I mean it would be a hell of alot of work to create tools (assuming they do not already exist). Perhaps the way games are coded in linux as a opposed to windows is just a matter of using a different style. I admit i'm arguing out of ignorance here, so feel free to bash what i said. Either way I was discussing the problem of game development in linux with a friend today, and he pointed me to [http://lgdc.sunsite.dk/index.html](http://lgdc.sunsite.dk/index.html) . If you look under the articles, there are quite a few tutorials on how to do things, though i am not a programmer and I can not say weather they are adequet.

---

### Post by GameGod on 2006-03-08
SSTwinrova, check your private messages...

---

### Post by ZylGadis on 2006-03-09
I strongly agree on the need for a unified game development environment in linux. I develop a MMOS in my free time, and I have mostly went on to pure server-side development for several reasons - one of them is that I absolutely refuse to make a windows-only client. We'll see where I go with that decision; most probably at some point I'll have a complete server, and a pseudo-client in a browser.

---

### Post by SSTwinrova on 2006-03-10
Oooooohhhh, I feel so special now that my thread has 5 of those flowers/boxing gloves (or whatever the rating picture is) off to the side, lol  :)

---

### Post by xanas3712 on 2006-03-10
Newton may be better, but if it's closed source it doesn't seem to match up with the rest of the toolkit going there.  Why not invest in making ODE or another open alternative better?  I don't see why we have to accept what is available now.

I have no issue whatsoever with commercial software.  That should be encouraged.  But I want commercial free software, not commercial proprietary software.

I don't believe all software has to be supported/made available for free(in terms of price), but I do believe that all software should be open.

How does it benefit anyone other than the developer for software to be closed?  It doesn't.  In the long run open software will ALWAYS be better than closed software for everyone.  It maximizes the potential benefits of software for this to be so.  

Everyone has to be able to support themselves with their work, and I understand commercial software.  But proprietary software is about control, and though it may be the way to make the most money off a piece of software it is not the best way to maximize benefit.

---

### Post by SSTwinrova on 2006-03-12
I agree that if this is going to be associated with open source, ODE should definitely be considered over Newton. I've even been talking with one of the leaders of the Crystal Space engine, and he mentioned something about ODE working with their software, so that might have just been the opinion of _dv.

---

### Post by timas on 2006-03-14
First off, I've gota say that I'm neither a Linux guru, a game/app developer or anything else that might prove valuable, just another simple joe that prefers the idea of OS over Microsoft's Windows..

I think, from an outside view that the biggest reason games aren't developed for linux in general are:
  - Its too bothersome to find all the right tools and lib's and dependacies, while for windows there's a few solid IDE's out there and just one basic system in which all is clear and documented.

  - Because its so hard to decide on the right tools, it takes time.. time costs money and eventually its just too small of a public to attract to turn it into a cost-efficient game that way.

  - The revenue gathered from the windows game/client is high enough to just not bother, at all

As you might notice, this initiative to provide a good solid documented download, or even an IDE (that'd rock) really works into the first thing I mentioned.. If it works out to be able to supply game developers with the before mentioned download/IDE it might just suddenly become more interesting to adress the linux folks too and through that eventually create a market big enough to get the investing parties interested in taking on that market..

While I'm uncertain as to what kind of help I might be able to offer, I think its a great idea and would love to contribute to it

-Tim

---

### Post by SSTwinrova on 2006-03-19
I posted about this idea on some forums more specifically geared to game development, and this one sparked the longest discussion with some interesting points being brought up: [http://www.ogre3d.org/phpBB2/viewtopic.php?t=18313](http://www.ogre3d.org/phpBB2/viewtopic.php?t=18313)

As I've (attempted) to make clear: this was not an idea I originally came up with, so all I have to go on for motivation is the original post behind this idea. If you read through that topic I just linked to, I'd appreciate any feedback regarding the points mentioned there.

---

### Post by Virogenesis on 2006-03-20
The thing about this idea is the fact that it would not only be cross platform with mac and windows but will be the fact that this would work with consoles aswell.
eg: <insert console> uses linux so <insert console> now because powered by linux it could make good use of the framework that would convince more to port over to this framework. 
Not only that but arcade machines could also use this alot look at how namco teamed up with nvidia to produce arcade machines using linux.
Its a fantasic idea but would require many man/woman  hours it would take years to produce a proper platform but like the linux kernel it would be used and embraced by many.

---

### Post by timas on 2006-03-20
hrm.. I read the stuff on ogre3d.org and most of the folks on there are saying "Linux support is too hard!" and "There's no sense behind glueing a bunch of apps together on a single framework!"..

Linux support -is- hard, but I do believe that if you make your game run with its own local libs you don't have any issues with all of these dependencies they are talking about.. I could be wrong, its up for argument!

And if there's no use in linking apps on a framework.. why in heavens name did MS ever make the Visual Studio IDE? Again, I could be mistaken, I've never used Visual Studio, nor have I ever coded a game in anything else as PHP.

My thoughts on this is that we need to consider these things:
- We need a IDE that can interface with a framework that can be used to build a game upon
- This framework should be platform-independant, it aught to be somewhat like DirectX, but better.. perhaps Ogre as they seemed to be rather pleased with its capabilities?
- The IDE should be able to utalize all the functions/calls/methods/classes/objects the framework offers to offer a superbly integrated development client.
- The framework should be built to use the things that are always available, the hardware. Perhaps on Windows by routing itself through DX but thats for them to consider.

The idea should be that developing in this IDE, with this framework is just as easy, or better yet, easier as the IDE(s) they use now.. And most important, that if they build a game, its automatically platform-independant.

I like the idea that consoles could use this too, and its true.. a light-weight linux with an optimized use of the engine could do really well..

And yes, I agree with Virogenesis that it'll take a lot of time.. but a huge community of people that are interested in Linux are the younger folks but they just don't switch because of the lacking support on games.. the rest is pertty much taken care off..

---

### Post by MojoX on 2006-04-14
SSTwinrova,the Mono project is working on a framework to facilitate game development: [http://www.mono-project.com/Tao](http://www.mono-project.com/Tao)

You also may want to follow the Axiom engine: [http://axiomengine.sourceforge.net/wiki/index.php/Main_Page](http://axiomengine.sourceforge.net/wiki/index.php/Main_Page)

Oh, and Crystal Space is worth watching as the Crystal Blend project should be a boon when the Blender integration is further along.

---

### Post by dv_ on 2006-04-16
Yes, Tao looks quite good, and is Mono-based, which is both a good and a bad thing.
Good: Mono takes care of all system-specific weirdness, making the whole thing much more homogenous and straightforward. Also, porting is much easier. And there is the MonoDevelop IDE (I don't know how good it is though).
Bad: GC can be the source of much trouble in a game, when it suddenly decides to clean up things (the network ping won't love this). I do not know how fine the GC can be configured (for example, cleaning up immediately would be fine). Also, in spite of this famous email hosted on the mono site, the whole legal situation is STILL uncertain (this email has zero legal value, unfortunately).

I think the Ogre guys miss the point. Its NOT about Yet Another Gameengine. Its about the layer *below* the engine (the DirectX SDK isn't an engine).

In fact, Microsoft is targeting something bigger called XNA. XNA is the next logical step - the SDK + a CMS for game-development consisting of dependency chains not only for code, but also for artwork, version control systems for code AND gameart etc. I don't know if XNA succeeds in this, but the demonstrations are very impressive. One homogenous, well-documented game development environment would be REALLY nice. Which brings me to the question: does a version control system for game artwork (with this I include 2D/3D-graphics, movies, music, sounds, scripts etc.) exist?

Anyway, we should get the basics right first, shouldn't we? :)

---

### Post by SSTwinrova on 2006-04-17
[QUOTE=dv_]I think the Ogre guys miss the point. Its NOT about Yet Another Gameengine. Its about the layer *below* the engine (the DirectX SDK isn't an engine).[/quote]
That was probably partially my fault and not thinking about your original post enough before I came up with my idea. I don't really believe "platform" is the right word to use for a project like this, as it does imply something along the lines of Ogre, Yake, etc. (maybe just "project" instead?)

[QUOTE=dv_]In fact, Microsoft is targeting something bigger called XNA. XNA is the next logical step - the SDK + a CMS for game-development consisting of dependency chains not only for code, but also for artwork, version control systems for code AND gameart etc. I don't know if XNA succeeds in this, but the demonstrations are very impressive. One homogenous, well-documented game development environment would be REALLY nice. Which brings me to the question: does a version control system for game artwork (with this I include 2D/3D-graphics, movies, music, sounds, scripts etc.) exist?

Anyway, we should get the basics right first, shouldn't we? :)[/QUOTE]
Now that I've had a chance to re-read the original post multiple times, I think I get more of what you're after, _dv. This really is more of a direct DX equivalent instead of trying to go any "higher up" (which is what I think my mind was was coming up with: a nice cross platform, Unreal engine type thing). It's not about abstracting any of the existing technologies necessarily, but instead just getting choice things together under a single documentation effort and combining all of those into a single download (points 1 and 2). The documentation and tutorials could/should be in a wiki for easy updating and contribution.

Anyway, a question: The first "good tutorials" point I assume is with reference to the SDK being constructed, so would the second be more like how to use the Linux/Unix equivalent of the Win32 API?? Also, the toolkit stuff I really need to wrap my head around some more, as I always tend to associate that with the IDE/compiler for the code (which I know is wrong, I just need to make more exposure to the terminology).

Also, perhaps there should also be something we look at before undertaking this project. In one of the Ubuntu wiki pages, it talks about how to go about converting users to Ubuntu, and that making it easy for those already converted is the first step with encouraging others to come over being at the end. Maybe as a part of this a "standard" should be developed so that developers will know on any certified distro where libraries will be located, etc. (if all necessary stuff would be covered under LSB, then this doesn't matter, but I don't know enough about it). Then, by the time this project matures to the point where developers could really consider using it, they'll be assured that anything they make will work on all supporting distros.

This really is just a big braindump to an extent, but hopefully others can come in and comment on parts of it to further define this idea.

---

### Post by MojoX on 2006-04-17
[QUOTE=dv_]Yes, Tao looks quite good, and is Mono-based, which is both a good and a bad thing.
Good: Mono takes care of all system-specific weirdness, making the whole thing much more homogenous and straightforward. Also, porting is much easier. And there is the MonoDevelop IDE (I don't know how good it is though).
Bad: GC can be the source of much trouble in a game, when it suddenly decides to clean up things (the network ping won't love this). I do not know how fine the GC can be configured (for example, cleaning up immediately would be fine). Also, in spite of this famous email hosted on the mono site, the whole legal situation is STILL uncertain (this email has zero legal value, unfortunately).[/QUOTE]

Not throw the game thread offtopic.  But, what exactly about Mono is on weak legal ground apart form the Windows compatibility stack, which, by not falling under the standards and RAND provisions, is on shaky ground?  Isn't the CLI implementation and C# in combination with the GNOME libraries safe?  I've been looking through Google, but I can't find much that (in 2006) establishes that it is not safe to follow the EMCA CLI and C# specs.

I've been learning to program in Python and am really attracted to fiddling with Boo and Mono, but the whole legal thing seems too influenced by misinformation, assumptions, and FUD on top of the more reasonable objections.  Noone makes leagal claims about DotGNU.  Why is the FSF effort that much different than Mono?

---

### Post by sutech on 2006-04-28
This idea is very interesting.
I'm currently making a game and it's quite difficult because I'm not quite sure what to use (currently I'm deciding between Crystal Space and Ogre). And some good tutorials and documentations would be helpful.
And a complete set of tools and framework would be awesome.
It's really annoying to get those tools on my own and tune it so it actually works.
I'll be glad to help in any way I'm able.

It would be nice if the package would contain also some content authoring tools (Blender, Gimp,etc...).

---

### Post by mostwanted on 2006-04-28
[QUOTE=colo]I don't want proprietary games. I don want games needing $THIS_EXACT_VERSION of $SHARED_LIB. Just keep them for yourselves, thanks.[/QUOTE]

It's possible for developers to release their game engines as open source software where only the data format will have a restricted license. Since the data format isn't architecture-specific, it would be possible to sell "hybrid" games with open source engines that could run on any system without library issues and other binary complications as well as retaining the ability to sell it to make the developers money.

I like that ID software already do this, I just hate the fact that they don't release the source until the game has been out for several years; I guess this is because they also make money of selling the engine too (to other game developers) while it's hot stuff.

---

### Post by Raavea on 2006-04-28
I have been looking into making my own games for a long time now - I always wanted my own MUD or other style of MMORPG. When I switched over to Ubuntu for good, I didn't realise how much I'd miss my little Roleplay Game Maker 2000 program. :lol: Luckily rm2k doesn't do multiplayer games, or I'd not be here at all!
 If you need any help, ideas, suggestions, or anything, do give me a PM. I should like to help.

---

### Post by Sanne on 2006-05-30
Hi all

I just found [SSTwinrova's post]("http://community.crystalspace3d.org/forum/index.php/topic,909.0.html") on the Crystal Space forum and I would like to add a bit in favour of this engine.

There's already a nice workflow possible like this:
- [Crystal Space]("http://crystalspace3d.org") (CS), the 3D engine
- [Cel]("http://crystalspace3d.org/tikiwiki/tiki-index.php?page=Cel"), Crystal Entity Layer, higher level layer above Crystal Space
- [Blender]("http://www.blender.org/") for content creation
- [blender2crystal]("http://b2cs.delcorp.org") export script for Blender
- Game logic is scriptable in Python (!)

The blender2crystal script makes it possible to export a level for Crystal Space, start the engine and load the level, with only one click from inside Blender (provided everything is set up correctly).

Since the stable versions of CS and Cel are a bit dated, cvs versions or the last pseudo stable versions should be used. Until now it was necessary to compile those on breezy, but I just saw an unofficial repository on the blender2crystal site that provides all of those, and also the latest Blender for breezy, since the official version gives problems.

There's a [blender2crystal wiki]("http://b2cs.delcorp.org") that has all the information, and a [repositories page]("http://b2cs.delcorp.org/index.php/Debian_Packages") explaining how to get all the necessary packages.

I didn't test the packages out yet myself so I don't know how they work (I still use my self compiled versions), but I plan to do as soon as I can.

In case of questions and getting it all set up there is the [Crystal Community Forum]("http://community.crystalspace3d.org/forum/index.php") and the #crystalspace channel on irc.freenode.net, and there's also a [wiki]("http://community.crystalspace3d.org").

So, in my opinion most of what's needed is already there and much fun to work with. What's still needed are more tutorials and howtos for beginners, especially those who don't want to program in C++, but use Python for game scripting. While it's already possible to do that, you have to figure out how to do things in Python by reading the C++ api docs, which is (for me, at least) not trivial to do.

Sanne

---

### Post by squinter on 2006-07-29
Hi, I'm a new Linux user, I installed Ubuntu 6.06 in one of my old machines. I enjoy using Ubuntu, but so far I haven't been able to find any good lite (e.g.: 2D) game for it. I'm looking for a game like Harvest Moon (PSX game) for my wife, perhaps someone here can tell me such a game that is available in Linux. I installed Pcsx (PSX emulator) but Harvest Moon just wouldn't play.

Anyway, I think if there is a game IDE like [http://www.gamemaker.nl](http://www.gamemaker.nl) for Ubuntu. Lots of games will start popping up. I used to create few games using it, its fun and *very* easy to use. You can practically create games without coding! And it used to be free, now you have to pay $50 (I think) for a lifetime registration to download the full featured IDE. May be there already such similar program for Ubuntu?

Thats just my 2c worth. Peace!

---

### Post by Lord Illidan on 2006-07-29
> **squinter said:**
> Hi, I'm a new Linux user, I installed Ubuntu 6.06 in one of my old machines. I enjoy using Ubuntu, but so far I haven't been able to find any good lite (e.g.: 2D) game for it. I'm looking for a game like Harvest Moon (PSX game) for my wife, perhaps someone here can tell me such a game that is available in Linux. I installed Pcsx (PSX emulator) but Harvest Moon just wouldn't play.

Anyway, I think if there is a game IDE like [http://www.gamemaker.nl](http://www.gamemaker.nl) for Ubuntu. Lots of games will start popping up. I used to create few games using it, its fun and *very* easy to use. You can practically create games without coding! And it used to be free, now you have to pay $50 (I think) for a lifetime registration to download the full featured IDE. May be there already such similar program for Ubuntu?

Thats just my 2c worth. Peace!

Not a bad idea..but we are talking about serious games here, not platform games...serious games as in MMORPGS, FPS, etc.

I tried my hand at SDL, trying to make a game...and I failed miserably.

1. I cannot find a centralised repository of tutorials etc. There are tutorials for SDL but they are scattered all over the internet.

2. The few game sources I downloaded are very ill commented.

3. The IDE and whatever are fine already. Anjuta is very good. But, for heaven's sake..those makefiles nearly drove me crazy.

---

### Post by G Morgan on 2006-07-29
As somebody who is currently attempting to learn SDL to develop games I'd like to add my 2p.

Like Lord Illidan mentioned there is a stack of SDL material out there but much of it is of varying quality and it is fully scattered. I think an important early job would be hunting down the various tutorials and author/license permitting either copy them into a central location and maintain them or at least link to their location. Obviously full technical documentation for any libraries would be required as well.

The advantage this has is that it provides use now so fits naturally into the OSS way of doing things. The main stated aim of this project is huge and won't reach a critical mass for some time. Other examples of this are projects like the HURD, a large ambitious project which has stagnated due to a lack of current usefulness. By centralising a lot of literature you create something which has use and would grow a community to help push the main project. Keep current usefulness close at heart and it would evolve into the objective over a period.

Somebody would need to create small sections of good quality code for tuition type purposes, the sort of thing I'm talking about is similar to the Minix source, while its far too heavily commented for normal use for a complete newbie it gives enough insight to get on board. Fortunately I think this would be quite simple in this situation.

I think there would need to be some centralisation of a few things. People are obviously able to code as they like but I think establishing a coding style and standards for stuff like makefiles etc would make the entire code base of everything done more transparent even if only used as a guideline. It certainly helps for the Linux kernel (the CodingStyle file in the kernel source/Documentation/ directory is worth a read even if only for quotes from Linus). Obviously doing this would make things much easier to debug as well.

Anyway I'm sure I could think of more but for now I'll leave it at that.

//edit - also a repository of artwork would be useful as well obviously.//

---

### Post by forrestcupp on 2006-08-01
I really don't understand what the original idea is all about.  Do you want a replacement for directx, or do you want a new game engine?  They are not the same thing.  Game engines use directx or opengl or whatever.  I think there is probably already the ability to do what you are suggesting; it's just not as well publicized as the mainstream stuff.

---

### Post by RAV TUX on 2006-08-01
> **SSTwinrova said:**
> Someone posted yesterday in an old thread about why Linux is generally lacking in the commercial game department and gave a lot of what I felt were very good reasons why studios stick with DirectX/Windows. Here's an excerpt from the post ([http://ubuntuforums.org/showpost.php?p=799128&postcount=32](http://ubuntuforums.org/showpost.php?p=799128&postcount=32)) outlining what he suggested is needed:



I replied to the thread and posted in the (K)Ubuntu Gaming sections with a link to this, but since this is buried a few pages, I thought I would create this thread as a way to see if anyone from the Ubuntu community would be interested in starting to work on some of his points. This of course wouldn't be considered a 3rd Party Project as it does not *directly* benefit Ubuntu in anyway, but my take is that if the Ubuntu community gets recognition for being the ones that start something like this, it will help promote the distro as the OS for developing Linux games on. So, here's my proposal:

I'd like to work with others to create the **Open Source Game Development Platform** (note I'm not using the term Linux, as commerical games for the forseeable future will almost all be developed for Windows, but providing open source alternatives comparable to DX that work on both Windows and Linux will allow porting games to be much easier on the developers). I think that if we could initially get 8-10 people from the community here to start working on some of the following things in their spare time (or maybe just 5+ truly dedicated people), this could get off the ground. Based on _dv's post, I propose this project be broken up into the following three stages:[LIST=1]
[*]**Software Decision**: Decide exactly what scope this platform would cover. _dv mentions lots of pieces of software, some of which are redundant, so choosing what we want to use is an important first step. (Later on other options could be included, but I think an initial goal of one thing for each job would be plenty).
[*]**Information Collection:** This would be creating the documentation that in the full post is mentioned as being completely fragmented. Completing full, easy to read use documentation for all of the software decided on will be key in getting existing DX developers to switch and lowering the bar as much as possible to new developers. Getting the help of the people in charge of each of the projects would be a plus, so if two different pieces fo software are similar, maybe use this as a guide for what to initially include.
[*]**Platform Creation**: This covers the bulk of the work, getting everything chosen together and making it presentable and look as professional as possible. Also, maybe take an existing IDE and integrate it or write a plugin to work with the platform and try to reach the level that VS is at.[/LIST]I'm sure there's stuff I left out and this idea would need tweaking, but that's why I'm posting this: to get feedback. If it appears enough people are interested, I'll register a domain, set up a Wiki (probably the best way to collaborate for this project), and do any of the other backend work necessary that's within my skill range. Of course people familiar with code would be necessary, but I think that **anyone can help**, especially for the documentation section in scouring the web looking for anything which may be of use. I'll post in the Programming Help forums with a link to this thread, but please post your thoughts (even if it's "This is the stupidest idea I've ever heard"  :) ).


Just a thought but perhaps the America McGee developer could help since he is now a Ubuntu user, refer to this thread:

[http://www.ubuntuforums.org/showthread.php?t=227299](http://www.ubuntuforums.org/showthread.php?t=227299)

and his blog post here:

[http://www.americanmcgee.com/wordpress/?p=171](http://www.americanmcgee.com/wordpress/?p=171)

---

### Post by squinter on 2006-08-02
Hmm ... may be a good way to start is to create a list of the best breed of components for developing games in Ubuntu? So for example, if someone is thinking about creating a FPS game, they would know what the best library(ies) to use. This is quite a big job, we need few people to hunt down those components, try them, and decide which is best of each category.

---

### Post by GuitarHero on 2006-08-02
I think it would take a lot more than 8-10 devs.

---

### Post by G Morgan on 2006-08-02
> **GuitarHero said:**
> I think it would take a lot more than 8-10 devs.

I'd agree which is why I suggested getting the project some momentum via related things early on. A centralised OSS games development site with the tool kit being the eventual holy grail seems the solution.

WRT current developers, at least you can find what exactly it is that makes them choose DX (techincally rather than politically obviously).

---

### Post by nihilocrat on 2006-08-09
> **G Morgan said:**
> A centralised OSS games development site 

Anyone know of such a place, whose main goal is to just have a place to hang out and collaborate?

Also, I'm currently working on a space shooter which I want to eventually be a sort of Battlfield-like game in space. I want it to be a sort of shooter / RTS hybrid, but avoid a lot of the resource management and central control seen in most of these hybrid games. It will use cross-platform (meaning Big Three cross-platform: windows, linux, mac) libraries and hopefully open-source ones (though I'm willing to use free-as-in-beer libraries if they are significantly better than OSS equivalents).

I'm having a huge amount of difficulty working with ODE, and I had tried Newton before but couldn't quite get thinks to link properly. Trying to find a physics engine to do collision detection and such really killed my passion to continue on. It was really depressing, so I gave up several months ago but I'm striving to find the motivation to start again. I think I'm going to just copy-and-paste together a minimal physics system and abstract it properly so I can easily replace it later.

Anyways, I think everyone should kneel down and kiss John Carmack's and Tim Sweeney's feet for making linux versions of major game titles. They're probably about 80% of the reason that there are up-to-date graphics drivers for Linux at all. However, that's probably the biggest roadblock to more widespread acceptance of linux for gaming: the way the kernel is developed requires all hardware drivers to be open source if they are to work optimally, and that's never going to happen thanks to software patents.

In general, though, linux gaming has a humongous ways to go. Contrary to popular belief, I don't think that the end user market has much to do with this: just about all hardcore gamers are at least powerusers, and thus would just suck it up and not subject publishers to the support nightmares involved with marketing proprietary linux apps. I think the big thing here is making Linux an attractive platform for game developers: it means making the entire build toolchain just as high-quality and efficient as the proprietary solutions. Probably the best way of doing this is to make high-quality open-source libraries and tools which developers concerned about Windows/console portability would use. Once porting to consoles becomes trivial (as said before, in some cases it has) it will be much more trivial to port games to linux.

---

### Post by LeChuck on 2006-08-14
Well, I don't think any game company is interested in creating games for Linux, because there is simply no market. Also I think the existing gamedev libs are not too bad.

But I miss a better organized open source game development community, and not only coders. Something like a melting point for all of them to get news, help, publicity, scene talk, and whatsoever you think of.

I think a board/wiki/blog would be good start, but not easy to manage.

---

### Post by bruce89 on 2006-08-14
There are already ones - [LIST=1]
[*][PlayStation 3]("http://en.wikipedia.org/wiki/PlayStation_3#Software_development")
[*][PS2 Linux]("http://en.wikipedia.org/wiki/PS2_Linux").
[/LIST]

---

### Post by beniwtv on 2006-08-14
As for my 2 cents...


I'm creating a cross-platform game developement environment. The basic idea is to code your game once, and have 3 interpreters - one for winblows, one for Linux and one for MAC OSX so that you can use the game in all of the three OS. It's open source. Check my signature for the link.

Unfortunately, I am very busy at this time and developement is not going much on as I would like to. :(

But I hope I can find time soon to throw out something to play. :D

NOTE: It's great you think about a framework for games, that's what linux really needs.

Cheers,

---

### Post by rnodal on 2006-08-28
I think what will be best is to create a game development kit that will hide all the platforms differences to the programmer that way what he codes just needs to be compiled on the targer OS or platform and that's it. Also eliminate the need of having to hunt down dependencies by creating a installer that will provide the user all he needs that way he just double clicks on the game and boom he is good to go.

-r

---

### Post by linuxgamingworld on 2006-12-17
> **LeChuck said:**
> Well, I don't think any game company is interested in creating games for Linux, because there is simply no market. Also I think the existing gamedev libs are not too bad.

But I miss a better organized open source game development community, and not only coders. Something like a melting point for all of them to get news, help, publicity, scene talk, and whatsoever you think of.

I think a board/wiki/blog would be good start, but not easy to manage.
:KS 
We were thinking along the same lines when we put [[COLOR="Red"]LGW[/COLOR]]("http://www.linuxgamingworld.com") together.

Saw a senior game developer's forum post say, 'no one makes commercial games for Linux because the users are fundamentally opposed to buying software.'  I felt compelled to reverse the misconceptions that have come up in the last few years.

Interesting project you are discussing.  High-level documentation and standardization of game engines could really bridge the divide to bring Winbloz devs over.  Hope the momentum for the project has not gone away.  If [[COLOR="Red"]LGW[/COLOR]]("http://www.linuxgamingworld.com") can offer any services on the site, please let us know... Even just publicizing your efforts to get more help.  We're very into collaboration with Linux game developers.
:-D

---

### Post by The Noble on 2006-12-17
Many people have pointed out that there is not a market for games in linux; and while that is true, it's not a reason to not go through with this. Linux and its apps are almost all GPL, why can't the games for it be the same? Also, how does that work exactly? Using GPL tools, can you create for other licenses (thus allowing the maker of a game to make a proprietary game  or otherwise)?

---

### Post by RAV TUX on 2006-12-17
> **SSTwinrova said:**
> Someone posted yesterday in an old thread about why Linux is generally lacking in the commercial game department and gave a lot of what I felt were very good reasons why studios stick with DirectX/Windows. Here's an excerpt from the post ([http://ubuntuforums.org/showpost.php?p=799128&postcount=32](http://ubuntuforums.org/showpost.php?p=799128&postcount=32)) outlining what he suggested is needed:



I replied to the thread and posted in the (K)Ubuntu Gaming sections with a link to this, but since this is buried a few pages, I thought I would create this thread as a way to see if anyone from the Ubuntu community would be interested in starting to work on some of his points. This of course wouldn't be considered a 3rd Party Project as it does not *directly* benefit Ubuntu in anyway, but my take is that if the Ubuntu community gets recognition for being the ones that start something like this, it will help promote the distro as the OS for developing Linux games on. So, here's my proposal:

I'd like to work with others to create the **Open Source Game Development Platform** (note I'm not using the term Linux, as commerical games for the forseeable future will almost all be developed for Windows, but providing open source alternatives comparable to DX that work on both Windows and Linux will allow porting games to be much easier on the developers). I think that if we could initially get 8-10 people from the community here to start working on some of the following things in their spare time (or maybe just 5+ truly dedicated people), this could get off the ground. Based on _dv's post, I propose this project be broken up into the following three stages:
[LIST=1]
[*]**Software Decision**: Decide exactly what scope this platform would cover. _dv mentions lots of pieces of software, some of which are redundant, so choosing what we want to use is an important first step. (Later on other options could be included, but I think an initial goal of one thing for each job would be plenty).
[*]**Information Collection:** This would be creating the documentation that in the full post is mentioned as being completely fragmented. Completing full, easy to read use documentation for all of the software decided on will be key in getting existing DX developers to switch and lowering the bar as much as possible to new developers. Getting the help of the people in charge of each of the projects would be a plus, so if two different pieces fo software are similar, maybe use this as a guide for what to initially include.
[*]**Platform Creation**: This covers the bulk of the work, getting everything chosen together and making it presentable and look as professional as possible. Also, maybe take an existing IDE and integrate it or write a plugin to work with the platform and try to reach the level that VS is at.[/LIST]
I'm sure there's stuff I left out and this idea would need tweaking, but that's why I'm posting this: to get feedback. If it appears enough people are interested, I'll register a domain, set up a Wiki (probably the best way to collaborate for this project), and do any of the other backend work necessary that's within my skill range. Of course people familiar with code would be necessary, but I think that **anyone can help**, especially for the documentation section in scouring the web looking for anything which may be of use. I'll post in the Programming Help forums with a link to this thread, but please post your thoughts (even if it's "This is the stupidest idea I've ever heard"  :) ).

I propose you donate your resources,....time, energy,...money to this project that is already well developed....

** 	The Free Ryzom Campaign -> donate to make Ryzom GPL  **
[http://www.ubuntuforums.org/showthread.php?t=308113](http://www.ubuntuforums.org/showthread.php?t=308113)

---

### Post by v8YKxgHe on 2006-12-17
> Linux and its apps are almost all GPL, why can't the games for it be the same?

Games can be, and companies _can_ make a profit from it by selling the game. What they would be selling is not the code, but the artwork, storyline etc etc.

I think this OSS Game dev platorm is a great idea and if I knew any system programming languages I would help! ( I'm a web-dev and know mostly PHP/MySQL/Javascript/xHTML )

---

### Post by kripkenstein on 2006-12-17
This is an interesting topic, and an interesting thread. My thoughts:

The IDE goal should be to create a single integrated environment for all or most parts of game development. Perhaps plugins for Eclipse could do this. Regardless of how it is done, there should be a SINGLE development environment, and it should be easy to use - GUI tools and all that. I suggest Eclipse because it is already in wide use, and supports extensibility via plugins.

The output code should be platform-independent. This would be the major selling point: if a game can be developed on this system once and then run on Windows, Linux or Mac, that would be a huge incentive to use the system. This is of course something that Microsoft will never do, which means that the FOSS community should go right ahead. In practical terms this could be done in the easiest way by using a platform-independent base, such as Python or Mono, connected to platform-independent libraries such as OpenGL. Personally I would suggest a mix of Python and C++; nearly an entire game can be coded in Python, leaving only a few CPU-intensive areas for C++ (this is how I currently develop, btw). Practically-speaking if there are enough supporting libraries that are in C++, then the entire game could be written in Python, since all the CPU-intensive things like physics etc. would be done by external libraries anyhow (and perhaps on the GPU, in the near future). Alternatively Mono would be ok, and it seems faster than Python (the legal issues should not be ignored, but I think they can be handled).

---

### Post by RAV TUX on 2006-12-17
Please see the Sticky at the top of the cafe forum:

[http://www.ubuntuforums.org/showthread.php?t=320338](http://www.ubuntuforums.org/showthread.php?t=320338)

---

### Post by linuxgamingworld on 2006-12-17
> **RAV TUX said:**
> I propose you donate your resources,....time, energy,...money to this project that is already well developed....

** 	The Free Ryzom Campaign -> donate to make Ryzom GPL  **

How are these not two different projects?  This one appears to be for standards, the other for producing a specific MMORPG.  Both important, but can the two not exist together, in your opinion?

---

### Post by MetalMusicAddict on 2006-12-17
For me, Id like to see a open gaming console in the spirit of the [Neuros OSD]("http://www.neurosaudio.com/osd/osd.asp").

---

### Post by phoenix116 on 2009-03-01
I know the last post here was a long time ago,
but I would be interested what has happened to the project.

I have recently tried to get into ubuntu gamedev( OGL ) but it's really hard to find GOOD tutorials, documentation etc, so I would be VERY interested in that kind of project.

Does anyone know what happened to the project? Or is there something like that out there somewhere?

---

### Post by G Morgan on 2009-03-02
> **phoenix116 said:**
> I know the last post here was a long time ago,
but I would be interested what has happened to the project.

I have recently tried to get into ubuntu gamedev( OGL ) but it's really hard to find GOOD tutorials, documentation etc, so I would be VERY interested in that kind of project.

Does anyone know what happened to the project? Or is there something like that out there somewhere?

Have a look at SDL programming first of all.

[http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index](http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index)

Then have a look at using it with OpenGL. It is designed to integrate with OpenGL on Linux, OSX and Windows.

---

