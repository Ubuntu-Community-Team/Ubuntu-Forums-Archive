---
title: "So why don't developers make games for Linux?"
date: 2005-09-13
forum: The Cafe
---

### Post by gflores on 2005-09-13
Obviously one of the reasons is because of the small market. But is that the only reason? Is it more difficult to make the games for Linux (code-wise)? Do the graphics turn out siginificantly worse than on Windows? I'm pretty clueless about game development for *nix systems. 

I have Unreal Tournament 2004 which I've played under Windows. However, when I installed it (I'm not even sure if it installed successfully...), it would not work. The installation process definitely needs to be simpler and just work. I posted on forums, but to no avail.

---

### Post by poofyhairguy on 2005-09-13
[QUOTE=gflores]Obviously one of the reasons is because of the small market. But is that the only reason? Is it more difficult to make the games for Linux (code-wise)? Do the graphics turn out siginificantly worse than on Windows? I'm pretty clueless about game development for *nix systems. 
[/QUOTE]

The fragmentation of a small market. As you found out, its hard to make files that install in every distro because they are so different. I believe that until one distro gets way more popular than the rest, this will be the case

---

### Post by BWF89 on 2005-09-13
[QUOTE=poofyhairguy]The fragmentation of a small market. As you found out, its hard to make files that install in every distro because they are so different. I believe that until one distro gets way more popular than the rest, this will be the case[/QUOTE]
Why couldn't they just release the game as a TAR file so it would install on all Un*x type systems?

---

### Post by xequence on 2005-09-13
[QUOTE=BWF89]Why couldn't they just release the game as a TAR file so it would install on all Un*x type systems?[/QUOTE]

Not everyone knows how to compile. I sort of do, just the very basics...

And it would take awhile to compile a DVD size TAR file, wouldent it?

---

### Post by BWF89 on 2005-09-13
[QUOTE=xequence]Not everyone knows how to compile. I sort of do, just the very basics...[/QUOTE]
Even if they didn't know how to compile at all, all the game company would have to do is post a list of commands that the user is to copy and paste into terminal.

[QUOTE=xequence]And it would take awhile to compile a DVD size TAR file, wouldent it?[/QUOTE]
No clue. If it took awhile to compile I would just start compiling before I went to bed or school so when I got back it would be done.

---

### Post by endy on 2005-09-13
If a game had enough source code that it could only fit on a DVD I don't think I'd compile it, not unless I was going on holiday for a long time :P

Seriously, most game engines aren't that big. It's the artwork that fills the CDs and DVDs and you wouldn't compile them :)

---

### Post by skirkpatrick on 2005-09-13
And why do you think you need to compile the game?  If the game is statically linked, there's no need to compile it.

I installed Doom3, Enemy Territory, and Neverwinter Nights and didn't have to compile anything.

---

### Post by Muhammad on 2005-09-14
[QUOTE=gflores]Do the graphics turn out siginificantly worse than on Windows?[/QUOTE]

I'm running Doom3 in Ubuntu, and for some reason (OpenGL?) the graphics seem alot better and the constant lagging is gone.

---

### Post by npaladin2000 on 2005-09-14
Now ask yourself why any game company would sell their SOURCE code in a box on the shelf, and expect to make any money after the first copy is sold. ;)

Linux needs commonality in this case.  The best level of it is likely SDL/OpenGL, as the closest equivalent to DirectX. The problem is, these games WILL have to be statically linked and include all their own library files, to reduce problems with different software and different dependencies on different distros.

I can see commercial publishers adopting Autopackage; that would solve one problem.  But the other problem is the lack of commercial-level development tools for SDL...even though it's available for Windows also.  So Step 1 is to start pushing for SDL/OpenGL to take market share from DirectX.  That'll make any Windows SDL game easier to port to Linux. 

There's one final problem: The "FSF nazis" that insist at gunpoint of all code being open-source. They're scary for anyone who wants to make money off of their coding work, including commercial game developers who are NOT gonna initially open-source their games until they've made back their investment plus a reasonable profit.  If they have to give out source code, they won't; because everyone will just take a copy and compile it on their own system...you can't really copy-protect source code.

---

### Post by endy on 2005-09-14
[QUOTE=npaladin2000]Now ask yourself why any game company would sell their SOURCE code in a box on the shelf, and expect to make any money after the first copy is sold. ;)

Linux needs commonality in this case.  The best level of it is likely SDL/OpenGL, as the closest equivalent to DirectX. The problem is, these games WILL have to be statically linked and include all their own library files, to reduce problems with different software and different dependencies on different distros.

I can see commercial publishers adopting Autopackage; that would solve one problem.  But the other problem is the lack of commercial-level development tools for SDL...even though it's available for Windows also.  So Step 1 is to start pushing for SDL/OpenGL to take market share from DirectX.  That'll make any Windows SDL game easier to port to Linux. 

There's one final problem: The "FSF nazis" that insist at gunpoint of all code being open-source. They're scary for anyone who wants to make money off of their coding work, including commercial game developers who are NOT gonna initially open-source their games until they've made back their investment plus a reasonable profit.  If they have to give out source code, they won't; because everyone will just take a copy and compile it on their own system...you can't really copy-protect source code.[/QUOTE]


Hmmm, well lets say I'm a one man development team with no money and I think of a killer FPS game idea. I can download the GLP Quake 3 source, do my stuff and start selling what I've made provided I allow access to the modified source code. You don't have to have the source code packaged with the CD or binary download but it must be available. With this method yes, some people could compile the source code themselves but they still need the art files and extras which, lets say, are only on the CD. 

I think it can work, it's just no company has the balls. Yes the pirates would have an easy time with it but lets face it people who pirate games pirate them no matter what so nothing would change there.

Oh, and regarding the "FSF nazis" I think this swings both ways, there are plenty of people that try to tell you that you have to keep source code closed, patented and with an extra topping of DRM otherwise society will apparently collapse :)

---

### Post by npaladin2000 on 2005-09-14
[QUOTE=endy]Hmmm, well lets say I'm a one man development team with no money and I think of a killer FPS game idea.[/QUOTE]


Killer FPS idea?  Isn't that an oxymoron?  

I want to see UNIQUENESS, not 5000 cookie-cutter Quake3 clones.  FPS games have been done to DEATH.

Incidentaly, remember, you do have to make your modified source available...and before you do that you have to come up with your own textures, maps, sounds, polygon designs, player designs, interfaces and all the other stuff that ISN'T GPL...you, as a 1-person shop is going to do this, right?  And it's going to be commercial quality?

---

### Post by Knome_fan on 2005-09-14
[QUOTE=poofyhairguy]The fragmentation of a small market. As you found out, its hard to make files that install in every distro because they are so different. I believe that until one distro gets way more popular than the rest, this will be the case[/QUOTE]

Not really, after all there are several games that work on any linux distro (doom, quake, nwn, all the loki stuff), so no, this is not a problem.

[QUOTE=npaladin2000]There's one final problem: The "FSF nazis" that insist at gunpoint of all code being open-source. They're scary for anyone who wants to make money off of their coding work, including commercial game developers who are NOT gonna initially open-source their games until they've made back their investment plus a reasonable profit. If they have to give out source code, they won't; because everyone will just take a copy and compile it on their own system...you can't really copy-protect source code.[/QUOTE] 
Calling others Nazis makes you wonder who the real zealot around here is, doesn't it?
And at gunpoint? What are you smoking?
Jesus...

---

### Post by blueturtl on 2005-09-14
edit:

After reading [Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm) and giving some thought to it I'd like to rethink some of the things typed here, here is revised version of my post:

It's a vicious cycle:

The big brands do not see a big enough market and therefore do not release any games => people keep using Windows to play games => people buy games for Windows...

I know if I had the choice all my games would currently be Linux ports. I see no point in using Windows just for the sake of one thing. It's ridiculous. Of couse if MS wanted to they could remove all other functions from Windows and make it a gaming platform only...  ;-) 

I think if the companies only saw the potential and dared publish any big titles for Linux also they would get their money back fast. A lot of users like me only use Windows for gaming and would turn to Linux only gamers if it only were possible.

We've seen what Blizzard has done (which is porting their titles also to the Mac environment) and it's making a lot of people happy because at least IMO Blizzard's RTS titles are among the best in the genre. This way Blizzard has ensured that it's fans on the Mac platform will be just happy and not only that, they will draw most of Mac gamers to themselves as no serious RTS alternatives are available for the Macintosh. Most people don't even need to play *all* the games in the market, they're picky over quality. This would mean if Linux got support from a few critical game publishers such as Sierra, Valve and Blizzard the market would enlarge quite a bit, which in turn would increase interest among other publishers and so on and so on...

We need to start collecting names of Linux users willing to pay for a port of say Half-Life2 for Linux and send the list to Valve's HQ. The same could be done for native WarCraft III and StarCraft with Blizzard. I think most gamers also won't mind the disclusion of the game's source code, since they just want to be entertained...

Now.. where do I sign my name? :)

---

### Post by GeneralZod on 2005-09-14
[QUOTE=Knome_fan]Not really, after all there are several games that work on any linux distro (doom, quake, nwn, all the loki stuff), so no, this is not a problem.
[/QUOTE]

I'd add UT'04 to this, as I consider it to be pretty much the perfect Linux port.  The installation was, if I recall, identical to that of Windows.  The original install was last August under Mandrake 10, and since then the same install has survived, completely untouched, through Mandrake 10.1, Gentoo, and now Kubuntu.  As soon as 3d acceleration is running, my old UT'04 install Just Works straight away.  It's great! :)

---

### Post by agger on 2005-09-14
[QUOTE=BWF89]Even if they didn't know how to compile at all, all the game company would have to do is post a list of commands that the user is to copy and paste into terminal.


No clue. If it took awhile to compile I would just start compiling before I went to bed or school so when I got back it would be done.[/QUOTE]

Well, they wouldn't actually have to provide commands for the user - the compilation might just as well be part of the installation wizard!

But yes, it could easily take a while - *but*, most of the space taken up on 
a DVD game would actually be graphics and sound.

To achieve interoperability one might also imagine some sort of universal byte-code operated gaming engine which one had to install and which would be ported to each distro, and then the actual games might run on top of that.

---

### Post by endy on 2005-09-14
[QUOTE=npaladin2000]Killer FPS idea?  Isn't that an oxymoron?  

I want to see UNIQUENESS, not 5000 cookie-cutter Quake3 clones.  FPS games have been done to DEATH.

Incidentaly, remember, you do have to make your modified source available...and before you do that you have to come up with your own textures, maps, sounds, polygon designs, player designs, interfaces and all the other stuff that ISN'T GPL...you, as a 1-person shop is going to do this, right?  And it's going to be commercial quality?[/QUOTE]

Think about where id came from, it's basically one main guy coding and a few for art and level design. Doom was given away a shareware (almost free) and they changed the gaming world. Trust me it can and will be done via GPL, it's only a matter of time.

What about Counter Strike, the most played game on the internet. That came free from a small community effort and got sold even though you could still get it free. That's how this would work except you don't have to buy the engine as Q3 is GPL.

This is just an example as there are other free game engines that you could use for various different game genres. The point it *never say never* ;)

---

### Post by Kvark on 2005-09-14
[QUOTE=npaladin2000]Now ask yourself why any game company would sell their SOURCE code in a box on the shelf, and expect to make any money after the first copy is sold. ;)[/QUOTE]
"Now ask yourself why any game company would sell their BINARY code in a box on the shelf, and expect to make any money after the first copy is sold. ;)" Even the uncrackable half life 2 with online authentication is cracked. How can you make money after the first copy is sold, cracked, and available for download?

This problem exists regardless of if you release the binaries or the source.


About games on linux, it's all about market share, if linux had 20% of the desktop market then I bet game developers would not ignore the platform.

---

### Post by agger on 2005-09-14
[QUOTE=npaladin2000]Now ask yourself why any game company would sell their SOURCE code in a box on the shelf, and expect to make any money after the first copy is sold. ;)
[/QUOTE]

That's really very simple: They use a game engine under the GPL, and that is (of course) open source and you have the four freedoms.

The name of the game, however, plus the plot, characters, artwork and sound 
are protected by trademark and copyright law and need not to be placed under any sort of GPL or Creative Commons-license.

So you could do what you wanted with the source code, but making extra copies to sell or give to your friends or download from the Net would still be unlawful.

Plus, by pirating the game you wouldn't get the fancy box, special access
to the game's Web site, support (etc.) that they offer with many games.

I think widespread use of standardized GPL'ed gaming engines might actually save the game developers a lot of money because they would improve each other's engines. thus needing less effort to develop engines and thus be able to devote more time to the creative work (stories, characters, plots, gameplay, artwork) which will always be most important to the user experience (the engine is, of course, just that: A vehicle).

---

### Post by az on 2005-09-14
[QUOTE=npaladin2000]
There's one final problem: The "FSF nazis" that insist at gunpoint of all code being open-source. They're scary for anyone who wants to make money off of their coding work, including commercial game developers who are NOT gonna initially open-source their games until they've made back their investment plus a reasonable profit.  If they have to give out source code, they won't; because everyone will just take a copy and compile it on their own system...you can't really copy-protect source code.[/QUOTE]

I am such a FSF zealot (nazi is offensive) and I do not force anyone at gunpoint.  If this has been your experience, I suggest you move to a country where guns are discouraged, like here in Canada.

The point is my right to chose my software, and not my right to chose *your* software.  Get it straight.

If games were released as FLOSS, it would not take long for someone to package it for each distribution.  This is how upstream source to distribution's binary works.  It is not a question of people having to install from source.  Someone else will do it.

Probably what is the most feasable is to have the engine as FLOSS and the artwork and multimedia (the more costly portion of the work involved) as proprietary.  I would expect the software to be FLOSS, otherwise, why bother running it on a PC, just get a games console.  But I would not epect the multimedia stuff to be any more free-libre than a song on the radio.


Think of how much better the engines would become.  The dev costs for the engine would almost drop to zero, and their quality would sky-rocket.


***darn, posted too late!

---

### Post by getaceres on 2005-09-14
Also there's a huge problem with drivers.
NVidia drivers are known to be better, but half of the gamers have ATI cards, and ATI drivers for Linux are very very very much worse than their Windows drivers.

---

### Post by blueturtl on 2005-09-14
> Also there's a huge problem with drivers.

I think Windows users suffer from this as well. Who here doesn't remember fiddling with hardware drivers under Windows just to make a device work or better yet, to make a game run? I do.

True, ATI's drivers are really bad on Linux, but their drivers are also notorious under Windows.

---

### Post by getaceres on 2005-09-14
[QUOTE=blueturtl]I think Windows users suffer from this as well. Who here doesn't remember fiddling with hardware drivers under Windows just to make a device work or better yet, to make a game run? I do.

True, ATI's drivers are really bad on Linux, but their drivers are also notorious under Windows.[/QUOTE]
 No, ATI drivers in Windows are as good as NVidia drivers, if no better. 
I talk by myself, I have an ATI card and I don't have any problem to play whatever game I want in Windows with very good performance.
But ATI in Linux is another story. I suffer it everytime a driver comes out. They address 2 or 3 issues for every 2 months release. An now is better, because not so many time ago, with some luck, you had a release every 6 months. But performance does not get even close to the Windows drivers. Playing Doom 3 in Linux is a pain. It's slow and above all, it's extremely unstable.
The only good thing about ATI drivers is that they are working on a graphical installer. It doesn't work for me, but they are in the right direction.

---

### Post by Lord Illidan on 2005-09-14
I don't know very much about tarballs and stuff when it comes to hardcore linux, but I do know that the UT 2004 demo was a .sh file which worked perfectly on Fedora Core 1. (Haven't tried it on Ubuntu yet).. I don't think .sh files are easily crackable opposed to a bunch of source code.

And source code is worse than binary for piracy, because a rival company can download the source code, make some tweaks, and voila`, he can release his own version, thus the original producer loses money to a rival... at least with binary piracy, that doesn't happen.

A game made by 1 person is not going to be as good as a commercial game. That is a fact. That person can be a genius, but still, it is not going to be of the same quality, unless the person is skilled in everything, cg modelling, design, level design, character design, audio effects, soundtrack, programming - menu programming, 3d programming, voice acting etc.

Games like chromium, neverball, these types of games can be made by 1 person. Doom 3, Unreal 2004, Warcraft 3, WoW, these belong to the companies. Companies need to be paid, because the developers/artists/designers/voice actors, etc need to eat. They need money to live, something which FSF zealots need to consider, in my opinion. The idealogy is great, but a person working full time on OSS, unpaid, is not going to live long, and donations are not sufficient.

And why developers don't program games for Linux.

No 1. Size of the market. Windows users consist 95% of the market. Linux is a bare 3%, of which half I believe are servers...
So which developer would modify the code to put it on Linux?
Also, linux users are percieved as geeks, hackers. The kind of people you don't really want to give the source code to, right?

No. 2. Propietary technologies such as Direct X do nothing to ease the porting of games from Windows to Linux.

---

### Post by gflores on 2005-09-14
I think another issue has to do with the type of people Linux users are. Mac, which has very little market share as well, has many more commercial games than Linux. Mac is generally targetted towards the teenager, college student, and those new users. These are all potential gamers. Linux has software developers and IT type people that are probably more likely to pirate it if it were released on Linux. It hasn't really established itself as a desktop OS for the teenagers and such, which are the ones that buy the games.

---

### Post by void_false on 2005-09-14
> teenagers and such, which are the ones that buy the games. 
LOL M8. I think only in US ppl are buying games. Kazaa, bittorent, million of warez sites that release full game even before its official release. And they *are* teenages who sit in internet 25 hours a day.

---

### Post by blastus on 2005-09-14
I have an idea! Why not have a common Linux distribution that is specifically geared for games, games development, games modding? It would have to be a free distribution supported by the community that is optimized specifically for games. If it became popular enough it could become attractive to the game developers because they would only have to develop games for one distribution then.

My reasoning is that ANY OS, be it MS-Windows, Linux, Mac, or BSD are not designed for games. They all attempt to do everything and none of them are specialized just for games. They are all bloated and have a lot of things that are unecessary for running games. For example, it is not necessary for a lot of OS services and for the MS-Windows and X-Windows interfaces to be running when a game is running. With a common Linux gaming platform we could compete head on with MS-Windows and console games--we should be able to outperform MS-Windows because we should be able to get more juice out of the hardware.

What I'm proposing is a type of XBox or PS except that it is a free Linux gaming platform that runs on PCs.

---

### Post by poofyhairguy on 2005-09-14
[QUOTE=blastus]I have an idea! Why not have a common Linux distribution that is specifically geared for games, games development, games modding? It would have to be a free distribution supported by the community that is optimized specifically for games. If it became popular enough it could become attractive to the game developers because they would only have to develop games for one distribution then.
[/QUOTE]

Ok. That gets rid of the division problem. How do you solve the other big problem- MS controls the most popular game making toolkit for computers (directx)?

---

### Post by stoffe on 2005-09-14
[QUOTE=gflores]I think another issue has to do with the type of people Linux users are. Mac, which has very little market share as well, has many more commercial games than Linux. Mac is generally targetted towards the teenager, college student, and those new users. These are all potential gamers. Linux has software developers and IT type people that are probably more likely to pirate it if it were released on Linux. It hasn't really established itself as a desktop OS for the teenagers and such, which are the ones that buy the games.[/QUOTE]
 Whatever the reason, there is big difference between the two types of people - if it's only that Mac users are more willing or able to pay, I don't know. But take a company like [Garagegames](http://www.garagegames.com/pg/)  which sell indie games for Windows, Mac and Linux. Somewhere on their site they quote numbers like 65% sales on Mac, 7% Linux and the rest Windows. 

Most of their games are available for all platforms, they even have a policy about no Win-only games I think. Even if they aren't Doom3 games, they aren't your average garage game either. If you haven't tried it, I really, really recommend [Gish](http://www.garagegames.com/products/40). It's a fantastic game that manages to be both modern and classic. :)

Anyhow, I don't have any reliable figures (does anybody?) but I'd be willing to bet money that the number of Mac users don't outnumber Linux users by that much. And I don't think that Mac users are so much more the gaming type either. Of course, any x86 Linux user have the opportunity to dual boot for their games, but if you could get the game for Linux directly, wouldn't you?

So why aren't the games sold for Linux? Noone *actually* knows. Garagegames only supports Linux because they want to, not because it gives them any money, or so they say at least. I applaud that, but there is something broken about that which needs to be fixed. If it's the economic model that doesn't go well with the Linux users, then someone must come up with something else that works for all parts.

Games *are* different from other software, at least right now in that noone has found a viable business model for open source yet. Garagegames wanted to go open source and live off reselling games made with their engine, but in the end couldn't and now charge a very reasonable price of $100 instead. Any single player game needs to be paid for somehow, just like any software - there just isn't much services to be offered for those. And for multiplayer, where a service model would be just perfect, well there you have all the cheaters, pirate servers and more. Not that it has actually been tried in enough large scale, which is not so strange: with the cost of developing a commercial grade game today, there just isn't any room for such experiments, sadly.

There are lots of stuff being built that is open source, and some of it is really good, engine-wise at least. But there isn't any games that measure up just yet, and I'm doubtful if there will be in the near future. The things that people always forget is the tools. It is always about the tools - your engine can be the best ever seen, but without the tools there simply will be no games. That is why the mod community can make commercial grade games with little else than an engine and dedication - they get the tools. Crystal Space, YAKE, Nebula, Irrlicht, whatever. No tools, no game. 

Add to this that the people who makes the games are largely uninterested - even the nerdiest of the extremely talented programmers - people who can do amazing things with OpenGL - has never booted anything but Windows and just give blank stares at the very idea. Why would they? They want to make games, pure and simple.

Not that the industry can't be converted. OGG was quite quickly and broadly adapted as soon as it came on their radar. Why not? It's at least as good as MP3 and they save some cash. But that's it. Cash. Other than that, they largely don't care. PNG is another example, it's also becoming much more common, and no wonder. It's a perfect format for textures as it is lossless, supports many colors and have good compression. That kind of stuff is easy to adopt.

Now, apart from all that, it isn't hard to write games for Linux if you take it into account from the start. If you have the goal that it should run on Linux, and just pay attention, it *will* run on Linux. And it will run approximately as good as on Windows, not really a problem. It will take some extra work, which usually means some extra cost. Not much, and even less if you have an engine to build upon, that works on Linux. Surprisingly many do. 

Already there it might be hard justifying the extra cost for an amazingly small *paying* public. And here comes the kicker: Linux usually is a testing and support nightmare. Even though there are standards to keep to, and some people like the Autopackage guys claim otherwise, it's rare if it ever happens that "it just works" on two machines. Myself, I have no idea why. But I do see it happening all the time.

To me, personally, it's not very fun to have these opinions. I run Linux, and at home, it's the only OS booted since at least February when it was the last time something broke so bad I had to boot over and surf for help. =) But it's important to be honest about these situations so they can be changed.

I'm myself involved in the gaming industry. I'm involved in a gaming education, and I do know and talk to a few in the industry, although I don't know the big names of course. I've built some pretty decent demos, if no full games, and I've cross-built them on Linux "because I can". I might very well be involved in making some games in a not-so-distant future. And of course I want to make these games run on your machines - for my own moral or political ends, if nothing else. But that might be hard to accomplish. And I'll take *any* suggestions that might help. :)

In short, a *broad* generalization:
* Linux is a support nightmare
* Linux users don't buy (or pay?) for games
* The industry isn't very interested
* The traditional service model does not seem to apply
* It takes too much resources to do full quality open source games, game makers need to eat
* There's no real tools for OSS development

To those who disagree on the above points, I just want you to know that I want to be proven wrong. By all means, please do prove me wrong.

Your insights are welcome. Games is one of the big remaining puzzle pieces and I think it's high time it fell into place now, somehow. :)

---

### Post by blastus on 2005-09-14
[QUOTE=poofyhairguy]Ok. That gets rid of the division problem. How do you solve the other big problem- MS controls the most popular game making toolkit for computers (directx)?[/QUOTE]

We build our own on OpenGL (someone on these forums mentioned something about SDL/OpenGL also.) There's nothing wrong with OpenGL and I believe it existed way before DirectX did. The idea is to provide an entirely new platform--not one that is compatible with MS-Windows. Take a PS for example, do PS games run on an XBox or vice versa? I know it wouldn't be easy though, but if we had a strong united community that was really determined, it may be possible.

---

### Post by poofyhairguy on 2005-09-14
[QUOTE=stoffe]
* There's no real tools for OSS development
[/QUOTE]

This is the one I dispute. Wasn't the Quake 3 engine open sourced lately?

---

### Post by stoffe on 2005-09-14
[QUOTE=poofyhairguy]This is the one I dispute. Wasn't the Quake 3 engine open sourced lately?[/QUOTE]
 Fair enough. Though it is a game from 1999, it probably do feature "real tools" (I haven't looked at it yet).

Somewhat badly put, my main gripe is more that even though there's all these great and cool - and powerful - engines and libraries (OGRE, ODE, Irrlicht, OpenAL, CrystalSpace and what have you), noone seems to understand the need for tools, or are interested in providing them. (Actually, that might well be a business model worth looking into). For every engine and the like I evaluate, I have a simple two-question test it must pass:

1. Has it got all the tools we need?
2. Has anyone else *completed* a *real* project with it?

If it's even maybe to one of those, it's not an option. :) Torque, the engine from Garagegames is quite dated if you compare to the games of today (but see their upcoming shader engine), but they do have all the tools you need. This makes it reasonably possible to succeed in *finishing* a game before the time runs out, which IMO is much more important than all the whiz and bang in the world.

---

### Post by dv_ on 2006-03-06
Sorry for the thread necromancy, but I'm glad this thread exists and really want to state my opinion.

I'm using Ubuntu for quite a while now, and think its quite amazing. I like the look&feel and prefer it over Windows any day.

That said, I also develop games semi-professionally. I do cross-platform development, but starting to develop in Linux was a REAL shock.

Why? Coming from the Windows world, I have the DirectX SDK with its *awesome* documentation (I'll refer to this later), a top-notch IDE (Visual Studio) and tons of tons of content creation tools. There are tools popular among game developers that exist only in Windows; 3d studio max is one good example. Maya is less popular for game content creation, until now I saw it being used in the CGI business rather than for game development. Still, it is a huge powerful modeling package and fortunately available for Linux/Unix. (Although the Motif UI isnt all that pretty :) )

Well, if one goes to Linux, most of these nice tools suddenly vanish. Instead, one gets a bunch of documentation fragments, once in a while some pointers to dusty mailing lists, zero tutorials, zero tools, zero help. Yes, SDL is a start, but it is not enough. OpenGL? Yes, its a good API, but advanced stuff requires extensions, and unlike Direct3D, there is NO comprehensive documentation for newer functionality (framebuffer object anyone?). Unfortunately, OpenGL has *zero* value without the newer functionality. What we need is ONE huge SDK with a documentation on-par with the DirectX one.

As for the docs: the Direct3D docs are by far the best. Not only they do include a good reference, but also a programmer's guide filled with useful, not necessarily Direct3D-centric info (like basics about PRT). Also included are many samples and tutorial that range from very basic stuff to really fancy things like spherical harmonics and HDR lighting. Where do I get THIS for OpenGL? Well, good luck with Google. If you think the extension registry is enough, think again.

This in turn means that resorting to SDL & OpenGL implies an increased development time, which absolutely KILLS any chance of Linux game development. It doesn't stop with OpenGL. A sophisticated input system equal to DirectInput? 3-D positional audio? (Ok, this one is in Creative Labs' tight grip, but software 3D audio anyone?) Tools for creating and playing in-game movies? (Theora is awesome, but there is virtually no toolchain for it, not even stable DirectShow filters exist!) Shader debugging systems? Shader studios like Rendermonkey or FX Composer?

Of course, creating tools is not easy with the toolkit issues. GTK or Qt? Also, where is good RAD? Glade is not enough. Again, VC is a good example. One marvelous tool would be RAD in one nice IDE, which doesnt exist either (again, I'll address this later). And, GTK isn't really portable from a practical POV. It is a pain to set up GTK in Windows (and Windows devs aren't used to resolving 27 dependencies just for one lame launcher GUI), and it looks just plain ugly since it draws all stuff itself. Take that UI consistency!

And it STILL doesnt stop. One quickly encounters a really peculiar problem: building a project is not straightforward in Linux! There is make, which just isnt enough for large projects (dependency resolving is fun!). The de-facto standard is autotools, which is actually one of the WORST choices. I can guarantee you that NO Windows developer will like it. It takes quite a while to stumble upon better alternatives like scons. Unfortunately, most IDEs do not support scons. Speaking of IDEs, right now only Eclipse and KDevelop can be considered for game development. Anjuta doesnt support the workspace/project model which is absolutely ESSENTIAL. (KDevelop supports it, but in a rather strange way.) Debugger integration in KDevelop has matured, but is still dwarfed by the VC debugger, which is unmatched until now. This lone feature is the main reason why I still develop my hobby stuff in Windows (other than testing of course). gdb is a horrific nightmare compared to the VC debugger. kdbg is quite ok, but it lacks source code awareness (by that I mean a list of source code files), which is present in an IDE.

Now, there are the Linux devs. I was astonished by this huge amount of ignorance I encountered. Sorry guys, but resorting to emacs and console DOES NOT make you l33t or better than others. Forcing everyone else to this developing style is just plain stupid and one good reason to stay away. Right now, I have to resort to the console because NO IDE has good scons integration. And no, I won't try autotools again. After months of royal pains in the a*** with it I came to the conclusion that its just not worth it.

Also, there are the usual system-specific quirks, like how to load plugins (dlsym/dlopen etc.), the LD_LIBRARY_PATH issue (in Windows the app automatically loads DLLs present in the same directory) etc. but again, no docs about it! I stumbled upon them by coincidence (I wonder what I still miss).

Summarizing; what is needed:
* One coherent, well-tested game SDK incorporating OpenGL, SDL, GLEW (important for extension handling!), maybe OpenAL or Audiere, and Newton (not ODE - Newton is a free physics engine, closed source but freely available; it is FAR easier to develop with Newton than with ODE, with better results too)
* EXTREMELY well done SDK documentation
* Good toolchain WITH GOOD GUIs (good GUIs seem to be kind of lame in the Linux world - sorry guys, this just scares devs and especially content producers away)
* Good tutorials
* One good IDE with RAD support and scons integration (or its enhancement bksys or something else, just not autotools please, we don't want to waste our time debugging m4 scripts or god forbid configure scripts)
* Good tutorials for general Linux/Unix development
* Better manners; not all devs are into hardcore l33t network programming, you know ;)

Well, this is not all thats needed, but the most important stuff. You may plonk me now :)

---

### Post by Bandit on 2006-03-06
DV, been there dont that. I know exactly what you mean. I took CPT in college in 1999. I used VS6.0 back then and the MFC and DX documentation is hands down some of the best.

I belive the OP answered his own question. 
Small market = small dollars.
Big time game developer companies dont get big on small dollars.
I am glad to see ID Software tries to make some effort by releasing games that can run nativly on linux.
Cheers,
Joey

---

### Post by SSTwinrova on 2006-03-06
[QUOTE=dv_]
Summarizing; what is needed:
* One coherent, well-tested game SDK incorporating OpenGL, SDL, GLEW (important for extension handling!), maybe OpenAL or Audiere, and Newton (not ODE - Newton is a free physics engine, closed source but freely available; it is FAR easier to develop with Newton than with ODE, with better results too)
* EXTREMELY well done SDK documentation
* Good toolchain WITH GOOD GUIs (good GUIs seem to be kind of lame in the Linux world - sorry guys, this just scares devs and especially content producers away)
* Good tutorials
* One good IDE with RAD support and scons integration (or its enhancement bksys or something else, just not autotools please, we don't want to waste our time debugging m4 scripts or god forbid configure scripts)
* Good tutorials for general Linux/Unix development
* Better manners; not all devs are into hardcore l33t network programming, you know ;)[/QUOTE]

Even though I'm only a freshman in college right now I plan on getting into game development, and when I'm hopefully in charge my own development studio, I'd love to make my games natively available for Linux also (in addition to the obvious choice, Windows). If you, dv_, and anyone else would like to start work on any/all of your points above, I'd be more than willing to get involved. Because of the nature of the work it probably couldn't be labeled as a 3rd Party Project, but just the general word that this was started/being done by the Ubuntu community would only help to promote the distro more.  :)

---

### Post by YourSurrogateGod on 2006-03-06
[QUOTE=poofyhairguy]The fragmentation of a small market. As you found out, its hard to make files that install in every distro because they are so different. I believe that until one distro gets way more popular than the rest, this will be the case[/QUOTE]
[Grab a cold one.](http://www.bibacity.co.uk/shop/files/BeersofScotland/samueladams.jpg)

---

### Post by Cebonet on 2008-06-14
Well, The developers of gamers and linux distros should find a way to make linux a killer in games. I´m tired of these "flash games" looking games. And the emulators i've used to play CS doesnt have a good performance. 

The games should not be open source ( if it's possible), When I wanna go to a shop, I want to see a huge list og games, that have linux logo on it:)

It's the games that makes the operation system atractive.

---

### Post by lorderico on 2008-06-25
I think what linux needs is something that will stand out from windows.  For instance, what it people took the wii technology (along with virtual reality), and made a similar (but cheap) technology that could be connected to linux via an open source driver so that linux (and hopefully linux only) could use it to make some unique games.  I am sure that if everyone out there was allowed to create there own games with technology like the wii's, we would have much more interesting games out than we have now.  If something unique came to linux that windows users don't have, then some people would switch for the games.  Eventually, you might get enoughh people to switch that game developers would release all of their games for linux as well as windows.

Just a thougt.
Eric

---

### Post by zmjjmz on 2008-06-25
Blame DirectX.

---

### Post by LaRoza on 2008-06-25
[img]http://img181.imageshack.us/img181/8060/necromancingsv7.jpg[/img]

---

