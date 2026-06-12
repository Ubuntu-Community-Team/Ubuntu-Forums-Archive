---
title: "Spore for Linux?"
date: 2007-10-02
forum: Ubuntu Gamers Arena
---

### Post by rudeboyskunk on 2007-10-02
I know it hasn't been announced, but the makers say they want to make a Mac port, so what are the chances of making a Linux port?

---

### Post by Perfect Storm on 2007-10-03
Doubtful, the publisher is EA.

---

### Post by socomoddjob on 2007-10-07
This game may make me partition some space for XP. Ive been waiting for this one a LONG time now.....

---

### Post by Hooloovooloo on 2007-10-10
I would have to say that it's not impossible. If they don't make one it will most likely be possible to play through Wine or Cedega.
EA have said that they will port their games to Mac using Cedega. So they would have to adapt the game and Cedega to work nicely togeather. If Cedega get the necessary changes to run Spore they may be implemented in Wine, if not you can use Cedega to play it. (All this based on that they port all changes on the Mac version of Cedega to the Linux version)

---

### Post by Paqman on 2007-10-10
We can only hope. I'm really looking forward to Spore.

---

### Post by Herisson on 2008-02-26
Transgaming anounced Spore for the Mac ([http://www.transgaming.com/news/?id=80](http://www.transgaming.com/news/?id=80)) . If they'll merge cedega and cider code, I think it will work on Linux =))

---

### Post by compiledkernel on 2008-02-26
Sadly unlilkely.

---

### Post by doorknob60 on 2008-03-13
Man I REALLY hope Spore works with Wine or something, because it looks like a really awesome game! If not, I still have a Windows 2000 partition though, assuming it would be compatible....hope I don't have to upgrade to Vista...eeew. Wouldn't be even worth it :P Well let's just hope for the best until the release date of September 7th (incase you didn't know that).

---

### Post by OllyNewport on 2008-03-17
I would say that this game would take a long time to port over, and even then it won't be the real developers porting it, it would be the guys at EA, and they are widely know for doing bad ports "Orange Box Anyone?", the Mac port will probally take a while to come to see the light of day, and as for Linux, the problem is that there are so many different flavors that it's hard to develop for this OS in retrospect, but that doesnt mean that WINE wouldn't be able to run it.

---

### Post by zerix01 on 2008-05-23
> the Mac port will probably take a while to come to see the light of day, and as for Linux,

EA will have a Mac version using Cider from Transgaming. [http://www.spore.com/press_011508.php]("http://www.spore.com/press_011508.php")

This should mean that Transgaming has the ability to make spore work on Linux using Cedega but just needs to port the code. If you read this thread [http://www.cedega.com/forum/viewtopic.php?t=9430]("http://www.cedega.com/forum/viewtopic.php?t=9430") they basically are saying they need to discuss when the port can happen. Something tells me the WINE project or Codeweavers will have it working first given Transgamings' history.

> 
the problem is that there are so many different flavors that it's hard to develop for this OS in retrospect, but that doesnt mean that WINE wouldn't be able to run it.

I'm not sure why so many people say this. I see a lot of games for Linux that have only one version. I never see Debian, Ubuntu, Redhat, SUSE, Mandriva versions, that one version runs on them all. Most distros at this point are pretty much the same at the lower level. Most differences now are in the GUI and what drivers come installed, and non app related things like different control panels, OS installers, or the way the system boots. All of those things help make one distro different from the other but none will stop a game from running.

---

### Post by cogadh on 2008-05-24
> **zerix01 said:**
> EA will have a Mac version using Cider from Transgaming. [http://www.spore.com/press_011508.php]("http://www.spore.com/press_011508.php")

This should mean that Transgaming has the ability to make spore work on Linux using Cedega but just needs to port the code. If you read this thread [http://www.cedega.com/forum/viewtopic.php?t=9430]("http://www.cedega.com/forum/viewtopic.php?t=9430") they basically are saying they need to discuss when the port can happen. Something tells me the WINE project or Codeweavers will have it working first given Transgamings' history.



I'm not sure why so many people say this. I see a lot of games for Linux that have only one version. I never see Debian, Ubuntu, Redhat, SUSE, Mandriva versions, that one version runs on them all. Most distros at this point are pretty much the same at the lower level. Most differences now are in the GUI and what drivers come installed, and non app related things like different control panels, OS installers, or the way the system boots. All of those things help make one distro different from the other but none will stop a game from running.
Cider and Cedega are not equivalent, so the fact that they are able to use the Cider wrapper to make a game work on Mac is absolutely no indication that it will work with Cedega. Not to mention, the whole point of Cedega and Wine is that you don't need to port any code to make Windows software work in Linux. That being said, I wouldn't expect Spore to work anytime soon in Cedega or Wine, due to the new SecuROM copy protection that they are using on it. It is the same version of SecuROM that BioShock uses, and that game still doesn't work in Wine or Cedega due to that.

The "distro-specific" version fallacy is due to the fact that different distros use different package management software. For some reason, people assume that having the installer package distro-specific means the game or app is distro-specific. That is just not true. The software itself is actually the same across all distros, the method of installation is just different.

---

### Post by Sammi on 2008-05-25
> **cogadh said:**
> Cider and Cedega are not equivalent, so the fact that they are able to use the Cider wrapper to make a game work on Mac is absolutely no indication that it will work with Cedega. Not to mention, the whole point of Cedega and Wine is that you don't need to port any code to make Windows software work in Linux. That being said, I wouldn't expect Spore to work anytime soon in Cedega or Wine, due to the new SecuROM copy protection that they are using on it. It is the same version of SecuROM that BioShock uses, and that game still doesn't work in Wine or Cedega due to that.

Ok the new SecuROM will be a significant problem. But other than that, if Transgaming manage to get Spore running, then I'm very confident that the Wine developers can too. I really have more faith in their coding abilities, because Cedega just isn't the same quality as Wine IMHO.

---

### Post by cogadh on 2008-05-25
You missed the point. The fact that they can wrap the Spore executable with Cider to run the game on a Mac does not mean that the Windows version will ever work in Cedega or Wine on Linux. Transgaming doesn't actually have to do any extra coding to make Cider run a game:
> Cider is a sophisticated portability engine that allows Windows games to be run on Intel Macs without any modifications to the original game source code. Cider works by directly loading a Windows program into memory on an Intel-Mac and linking it to an optimized version of the Win32 APIs. Games are "wrapped" with the Cider engine and they simply run on the Mac. This means developers have only one code base to maintain while enjoying the flexibility of targeting multiple platforms and, therefore, multiple revenue streams. Cider powered games use the same copy protection, lobbies, game matching and connectivity as the original Windows game. All this means less effort and lower costs. Cider is targeted to game developers and publishers. 
The odds that it will work in Cedega are actually much better than it is for Wine, since Transgaming already licenses the SecuROM technology, which Wine will never have. I'm not sure if the SecuROM licensing they use for Cider extends fully to Cedega, but odds are it does.

---

### Post by Sammi on 2008-05-25
Come on. Cider is nothing more than the Cedega engine for mac. Where are they supposed to get a Win32 API implementation from? Develop another one from the ground up? That's silly.

You've still got a good point about the SecuROM licensing problem.

---

### Post by cogadh on 2008-05-25
Cider is based on the technology used in Cedega, but it is not the same thing at all. It has been modified and optimized to be used on a Mac for a very specific purpose, unlike Cedega, which is made for more general use on Linux. The differences may seem subtle, but they are very significant. Just look at the games that already use Cider compared to how they work in Cedega:
[list]
[*]Madden NFL '08 - not rated, which either means no one has ever tried to play it on Cedega, or it doesn't work at all.
[*]Tiger Woods '08 - not even listed by Cedega, which is never a good sign
[*]Myst Online - unplayable (0 star rating)
[*]Eve Online - playable (4 star rating)
[*]GameTap - see Tiger Woods '08
[*]Command & Conquer 3 - unplayable (1 star rating)
[*]Battlefield 2142 - playable (3 star rating)
[*]Harry Potter & The Order of the Phoenix - see Tiger Woods '08
[*]Need For Speed: Carbon - playable (3 star rating and officially supported by Cedega)
[*]X3: Reunion - barely playable (2 star rating)
[*]Heroes of Might & Magic 5 - playable (3 star rating)[/list]
Obviously, the fact that all these games can be run on a Mac because of Cider is no indication of how well they will work with Cedega at all. Of the ones that do actually work, they don't work perfectly (Eve Online comes the closest) and most don't work at all.

---

### Post by Sammi on 2008-05-26
Now that's actually very interesting. Good job on compiling that list! :KS

---

### Post by gardengxc on 2008-06-06
well we will have a the engine a week from Monday. so three months before the game is released. so we have three months to get it working.

---

### Post by rudeboyskunk on 2008-06-08
I posted a plea to the makers of Spore to make a Linux port.  Go there and comment on it and digg it too, so more people on Digg can see it and maybe the makers will pay a little more attention to the Linux gaming crowd.

[http://www.jasonthepinko.com/?p=42](http://www.jasonthepinko.com/?p=42)

---

### Post by darklegion on 2008-06-11
> **cogadh said:**
> Cider is based on the technology used in Cedega, but it is not the same thing at all. It has been modified and optimized to be used on a Mac for a very specific purpose, unlike Cedega, which is made for more general use on Linux. The differences may seem subtle, but they are very significant. Just look at the games that already use Cider compared to how they work in Cedega:
[list]
[*]Madden NFL '08 - not rated, which either means no one has ever tried to play it on Cedega, or it doesn't work at all.
[*]Tiger Woods '08 - not even listed by Cedega, which is never a good sign
[*]Myst Online - unplayable (0 star rating)
[*]Eve Online - playable (4 star rating)
[*]GameTap - see Tiger Woods '08
[*]Command & Conquer 3 - unplayable (1 star rating)
[*]Battlefield 2142 - playable (3 star rating)
[*]Harry Potter & The Order of the Phoenix - see Tiger Woods '08
[*]Need For Speed: Carbon - playable (3 star rating and officially supported by Cedega)
[*]X3: Reunion - barely playable (2 star rating)
[*]Heroes of Might & Magic 5 - playable (3 star rating)[/list]
Obviously, the fact that all these games can be run on a Mac because of Cider is no indication of how well they will work with Cedega at all. Of the ones that do actually work, they don't work perfectly (Eve Online comes the closest) and most don't work at all.

I believe that most of the Cider engine improvements have been or will be ported to cedega 6.1.This suggests that Cider is just a version of Cedega with modifications to work on OSX correctly, that is given more priority than Cedega.C&C 3 works on 6.1beta.I don't own any of the other games listed but there's a good change that they'll work with Cedega 6.1.
Also Cedega itself could be considered to be for a "specific purpose" as it's compatibility is awful compared to Wine, and is more aimed at getting a handful of games to work well.Which is much the same aim as Cider.
That being said, if there are any code changes on the Windows code side for getting games to work well under Cider, then it's a different story.

---

### Post by Wikzo on 2008-06-16
The demo of Spore is leaked. I'd tried to install it with Wine (default), but can't run it because I haven't got DirectX. What should I do?

I'm running Ubuntu 8.04 with the latest version of Wine.

---

### Post by mrjnoobles on 2008-06-16
I have the latest DirectX installed in Wine but I get this error: "Sorry, your graphics card is below our min spec, the game will not run."

I have an Intel GMA 950 and I can play it in Windows just fine though.

If you want to try installing DirectX anyway here's the guide I used: [http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html](http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html)

(That is the second result in a google search for "directx wine")

---

### Post by Sammi on 2008-06-16
Installing DirectX will most likely just make things worse.

Wine isn't developed to be a platform you install DirectX on, it's supposed to be a direct replacement for DirectX. Wine is in fact supposed to be a complete reimplementation of all the core Windows API's, DirectX included. But it's not done yet. Some things are virtually finished, while other stuff is only half implemented or not implemented at all. Only real advice is this: be patient.

---

### Post by Wikzo on 2008-06-16
> **mrjnoobles said:**
> I have the latest DirectX installed in Wine but I get this error: "Sorry, your graphics card is below our min spec, the game will not run."

I have an Intel GMA 950 and I can play it in Windows just fine though.

Same here. I have a Intel® GMA X3100. Thanks for the link, but I think I won't install DirectX yet.

---

### Post by lockerhaxor on 2008-06-17
Considering how much I'm looking forward to spore, and that I'd prefer to use it on my Ubuntu machine, I hope it'll run on Wine. 

The only other hope is the Mac version somehow working. But yeah. I can't wait for this game.

---

### Post by CydeSwype on 2008-06-17
Got the creature creator but it demands that ActiveX be installed.  Tried running it under my virtualized windows as well, but no love there...some security issue.  I think there's some wrapper on the app that knows it's running under emulation somehow...

Wine 1.0 is supposed to come out today.  Not sure what effect that will have on all this.

---

### Post by Vil on 2008-06-17
No joy using Windows 2000 emulated through qemu. The process starts and just dies on its own, no messages or anything. =(

I haven't had any luck with wine so far, either, getting the same results as others on the Creature Creator's appdb page. Of course, the creature creator and the game will be somewhat different, and while one may work the other may not. =/

---

### Post by Frem on 2008-06-17
> **Vil said:**
> Of course, the creature creator and the game will be somewhat different, and while one may work the other may not. =/

Seeing as the creature creator and sporepedia are used within the game, any problems you experience with this demo will also be in the full version.

---

### Post by Sammi on 2008-06-17
Read the Wine application database entry for Spore to see how well Wine runs it atm: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=7588](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7588)

---

### Post by graabein on 2008-06-18
Spore for Linux would be great but I've heard it's coming for the Wii so I'm good with that. I wonder how a strategy/simulation like this will work on consoles... It will be interesting to see...

---

### Post by Magnes on 2008-06-18
> **Wikzo said:**
> Thanks for the link, but I think I won't install DirectX yet.

You don't have to install full DirectX (is it even posibble on WINE?), just the additional dlls which work fine with the WINE implementation of DirectX.

---

### Post by Billy_McBong on 2008-06-18
i managed to get spore installed. but it complained about Direct X for me too after the install finished and it tried to run.

i ran it again which caused my screen to go all black, it crashed after a few seconds, then i was left in some horrible resolution and did a control-alt-backspace

any help to get it working would be greatly appreciated. if i figure out anything useful ill post it

---

### Post by EricBetts on 2008-06-18
I had the same symptoms until I upgraded to the latest wine ([http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)), now its able to load, but most of the UI elements arent visible (as covered in appdb entry, [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12558](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12558))

Also, if you come out of an application with the wrong resolution, try running "xrandr -s 0" on the command line, it sets your screen back to the default resolution X was using.

---

### Post by Billy_McBong on 2008-06-18
i upgraded to the newest version of wine and can get a little farther now. i get to the screen where it tells you are running the trial version spore creature creator, has places to click on to upgrade and to reserve the full game (but they do nothing). can't seem to get past this screen.


thanks for the command, it fixes the resolution.

---

### Post by EricBetts on 2008-06-19
If you click in the upper left of that box, it'll close and a registration box will come up, you'll see some of the UI along the bottom of the screen while its open.  After closing it you can get to the editor via the hidden buttons that are talked about on the appdb link I posted before.  There are even some screenshots

---

### Post by Bartje on 2008-06-19
If spore is so popular, perhaps it would be interesting to see an open source variation on the game.. :-), if there isn't any yet at least.

---

### Post by Billy_McBong on 2008-06-19
im not at my computer but ill try that when i get home. thanks for the help Eric

it would be amazing if someone made an open source version of spore. but spore took a really long time to make, so we probably wont see an open source clone anytime soon

---

### Post by nicesocks on 2008-06-19
if you have the newest version of WINE, and want to fiddle around with the creature creator, then keep this one notice in mind:
currently the UI doesn't load right.  it's invisible, loading the graphics of both the UI and 3d elements so that background likes to appear in the foreground, covering over foreground objects and UI.

you still can use the software, but you won't see most of what you are doing.

to get beyond the initial add, click the top right where you imagine an [x] would be on a window.  then you will get to a registration screen, register if you'd like to.  you don't have to.
once you are done with that, you will have a spiraling galaxy before you.  you might have to hit [esc] to ensure you are working with the galaxy and not some invisible window that would be getting in your way.
just to the right of the galaxy will be another invisible button.  it makes a different sound as you mouse over it, this is the creature creator button.  click it, and have fun.

i'd recommend studying screen shots or movies of the creature creator to familiarize yourself with the whereabouts of buttons and knobs.  best of luck, and have fun!

---

### Post by TheConqueror on 2008-06-19
I got the full version of the Creature Creator installed (after installing directX).  But it complains that it can't find the Internet when it starts up, and then terminates.  Doesn't Wine give Internet access at startup?  When I run Dark Crusade through Wine I can happily connect to the online gaming, so I know there is a network connection available through Wine.

Oh well, keep on trying!

Allen

---

### Post by EricBetts on 2008-06-19
The full creature creator's inability to contact its license server is covered by a winehq bugzilla entry [http://bugs.winehq.org/show_bug.cgi?id=13990](http://bugs.winehq.org/show_bug.cgi?id=13990)  It might be worthwhile to keep an eye on it and see when it gets fixed.

> **Bartje said:**
> If spore is so popular, perhaps it would be interesting to see an open source variation on the game.. :-), if there isn't any yet at least.

Actually at a talk for The Long Now Foundation on June 26, 2006, Will Wright talked about how many of the Sim games, specifically referencing simcity, are based on simple rules as seen in [Conway's Game of Life]("http://en.wikipedia.org/wiki/Conway's_Game_of_Life").  Although the complexity is significantly increased, I would assume Spore follows many of the same concepts.

---

### Post by Skerit on 2008-06-20
I haven't bought any new game in years, why would I if I'm not sutre it can even run under Linux? But I would love to give Spore a go.

Anyhow, I can't believe it's impossible for Transgaming to make Spore run under Linux if it runs under Mac OS X. Making all these games work on OS X and not Linux, kind of feels like they're betraying us.

---

### Post by EricBetts on 2008-06-20
I think betraying us is a little strong, but Cedega isn't that far from Cider, so its possible it will be supported and they just haven't announced it yet.  Or, as often the case in business, they'll add support when they believe enough people want it.  I, for one, am hopeful and would be willing to pay for cedega if it supported Spore.

---

### Post by Billy_McBong on 2008-06-20
I got it working, now i just have to memorize where all the buttons are. 

it will be a while before the full version is out so im hoping Wine will be able to run it better by then. if not there is still cedega

---

### Post by lingnoi on 2008-06-20
If you copy all your windows fonts to drive_c/windows/fonts it should show the menu apparently, haven't tried it yet.

---

### Post by EricBetts on 2008-06-20
I saw the message in the bug report about that and gave it a try, but my results are the same as before; the person who added that comment to the bug report also added a screenshot of sporepedia within Spore, but didn't provide any other menus or context about how he got to it (I've also gotten to it via random clicking, but it looks deformed).

If anyone else tries this, please post your results so we can get a consensus on if its a viable fix (or if you don't have an account, email me at [email]bettse@onid.orst.edu[/email] and I can proxy-post the results.)

---

### Post by Yfrwlf on 2008-06-27
> **Skerit said:**
> I haven't bought any new game in years, why would I if I'm not sutre it can even run under Linux? But I would love to give Spore a go.

Anyhow, I can't believe it's impossible for Transgaming to make Spore run under Linux if it runs under Mac OS X. Making all these games work on OS X and not Linux, kind of feels like they're betraying us.

EA is a nightmare to try to contact, but I also asked them if they were going to port to Linux since they are OS X, but no response yet and I don't expect one due to how corporations are with not being honest and direct.  Would be nice to know if they had any such intentions though, and I agree with you that it's pretty stupid not to have one *nix (Linux) port when you have another (Mac).

Many will try to say it's simply user demand, and that very much could be the case and is at least part of it, however it is well known that licenses/contracts between companies can be discriminatory, hence why "exclusive" game titles and other things like that are made.  So, have the Spore developers signed exclusivity contracts with Apple, Microsoft, and Nintendo and that is one reason is no Linux port?  It's very possible, but probably something that's impossible to ever find out without spy equipment. :)

And if anyone feels like responding with a "Why would they do that??  It should be all about teh monies!" then ask yourself the same question about other exclusive titles, same deal.  In exchange, the developers may get direct payment or perhaps access to the company's special software development kit or development programs, who knows, but they do do it, so there is some kind of reason for it.  Why would they make Metal Gear Solid 4 for the PS3 only and not the 360 as well which has a larger market share right now?  Surely all those 360 gamers would easily pay for money required to port it.  The whole point is that porting from Mac to Linux is a pretty tiny step and should warrant a Linux port due to the 10-20% of Linux market share worldwide.  (Yeah, I know most sites try to say it's smaller than that, but I don't believe they take into account the adoption in Europe and non-American countries in general since they are mostly all US-based websites and mostly in English, but that's JMO.)

---

### Post by UltraSonicSite on 2008-06-27
> **Bartje said:**
> If spore is so popular, perhaps it would be interesting to see an open source variation on the game.. :-), if there isn't any yet at least.

If we have any hope of seeing it any time soon we should probably start working on it now. I know I've thought about making a spore-like game =D

---

### Post by Yfrwlf on 2008-06-27
> **UltraSonicSite said:**
> If we have any hope of seeing it any time soon we should probably start working on it now. I know I've thought about making a spore-like game =D

Since Spore is simply an MMO simulator essentially, there are several projects out there trying to make open source MMOs, so I guess it's a matter of finding one that could be used for a Spore-like purpose which is the closest to that goal, and try to help them out with the groundwork.

I've been looking into game engines lately and I've run into two.  One is a game engine that uses Crystal Space called CEL.  Another is Blender, though I know less about that.  I just know that the open game Apricot's goal is to not only make a game, but to help develop a game engine that will either be a separate package to Blender but integrated with it, or will be bundled with the normal Blender version.  If I had to guess, I'd guess CEL was closer to being user-ready but I'm not sure.  Blender is compatible with both Ogre3D and Crystal Space from what I read.

In any case, that's what I'm most anxious for and interested in, is making a solid game engine that can be used to pump out games and game content.  If you can make making games easy for the masses, think about how that would effect the game industry and the number of games out there.  The more that progresses, the easier making a MMOSim will be.

---

### Post by Bartje on 2008-06-28
> **UltraSonicSite said:**
> If we have any hope of seeing it any time soon we should probably start working on it now. I know I've thought about making a spore-like game =D

:idea:I am using Blender for some years now, Maya and 3ds max before, so I think I can call myself being, or at least at the beginning of an experienced 3D modeler. If you'd need models, I can help making them if you'd start on making that kind of game..

> **Yfrwlf said:**
> 
I've been looking into game engines lately and I've run into two.  One is a game engine that uses Crystal Space called CEL.  Another is Blender, though I know less about that.  I just know that the open game Apricot's goal is to not only make a game, but to help develop a game engine that will either be a separate package to Blender but integrated with it, or will be bundled with the normal Blender version.  If I had to guess, I'd guess CEL was closer to being user-ready but I'm not sure.  Blender is compatible with both Ogre3D and Crystal Space from what I read.

The game engine of Blender already is completely integrated in the package. For some aspects, the game engine is even used for certain things used for animation. The Apricot project is not to integrate it, but to improve it. They even use Crystal Space as well. Perhaps they'll use it's code inside Blender too, I don't know, or it is to learn to improve its own engine. But I am convinced Blender would be an essential tool for making a spore like game.

---

### Post by Yfrwlf on 2008-06-28
> **Bartje said:**
> :idea:I am using Blender for some years now, Maya and 3ds max before, so I think I can call myself being, or at least at the beginning of an experienced 3D modeler. If you'd need models, I can help making them if you'd start on making that kind of game..

The game engine of Blender already is completely integrated in the package. For some aspects, the game engine is even used for certain things used for animation. The Apricot project is not to integrate it, but to improve it. They even use Crystal Space as well. Perhaps they'll use it's code inside Blender too, I don't know, or it is to learn to improve its own engine. But I am convinced Blender would be an essential tool for making a spore like game.

In any case Blender would probably be used to create the models, so if it can be used for the game engine too, that's good I suppose, if it's one of the best things out there at the moment.  No matter which you choose though, of course there will be coding involved, the only difference being how much coding it takes depending on what the particular game engine can or cannot do.  I'd certainly be nice to have a game creation environment that had options to pretty much easily create anything you'd want, and then have modules to add new features.  I'm pretty sure this is the way Blender is set up to some degree, so perhaps it's a good platform for that.  Still need to check them out in depth.

A big part of making a Spore-like game though would be the AI since it'd use a very complicated system of values and calculations.

I think a good goal of any project like that would be to also help the Apricot project in making the game engine capable of allowing the fairly easy creation of the game itself.  Help craft the tools to build the game while in the process of making it.

One gripe I have about some projects is that, while I understand taking small steps sometimes, the bar is often set so low for open source games.  It shouldn't be a project's goal to make a "generic knock-off" of a game, it should be the goal to make a *better* game.  Use an engine which allows easy upgrading for new graphics features to be easily added later.  Use an engine which allows amazing graphical effects, too, to actually *use* the hardware power of the new AMD/ATI HD 4870 graphics cards that came out with a penguin on the box, otherwise Linux gamers can't even take advantage of it really.  Don't try to be as good as Spore, try to be better, and hopefully in the process it will help allow the possibility of different games with different rules to easily offshoot from the project, too, so that it won't just be accomplishing a single goal, but can help lots of other good games to come out of it.  Ogre3D, Crystal Space, and others are already used in some pretty amazing games, now all you need is a game engine which can easily help produce them, and open source will take over. ;)

---

### Post by Bartje on 2008-06-28
My idea exactly... just wanted to say that if there are modelers needed...

---

### Post by Xbehave on 2008-07-02
I think the problem is the creature stage of the game, it doesnt seam like a standard FPS so somebody will need to make an engine for it the rest is already done and just needs some reconfiguration
first stage seams simple to create
create monsters => blender scripts
creature stage => quake engine + some work
tribal stage => widelands/0.a.d
civilisation stage => freeciv/freecol 
space stage => freeorion? freeciv mod?

this will obviously lack the graphical edge of spore but has the advantage that it could eventually outshine it. it will have 4/5*the development base of a normal game so as each of the games improved the improvements can be ported over, and hopefully put a bit of life into the development of any games that have dried up.

after playing ufo:alein invation (an RTS? with a turn based stratagy shooter inside it that uses the quake engine) i really hope somebody 'just' sticks the various engines needed for a spore clone together.

---

### Post by Yfrwlf on 2008-07-02
> **Xbehave said:**
> I think the problem is the creature stage of the game, it doesnt seam like a standard FPS so somebody will need to make an engine for it the rest is already done and just needs some reconfiguration
first stage seams simple to create
create monsters => blender scripts
creature stage => quake engine + some work
tribal stage => widelands/0.a.d
civilisation stage => freeciv/freecol 
space stage => freeorion? freeciv mod?

this will obviously lack the graphical edge of spore but has the advantage that it could eventually outshine it. it will have 4/5*the development base of a normal game so as each of the games improved the improvements can be ported over, and hopefully put a bit of life into the development of any games that have dried up.

after playing ufo:alein invation (an RTS? with a turn based stratagy shooter inside it that uses the quake engine) i really hope somebody 'just' sticks the various engines needed for a spore clone together.

I don't know a whole lot about game development yet, but my guess is that would be a very bad idea if you want a game that doesn't look like it's pieced together from all those games.  Using an open source 3D engine you should be able to create any of the views, either 2D or 3D, it's just a matter of camera placement.  Then you just need the mechanics in each game type, and the interface.  FreeCiv, for example, could never transform into what you'd like, because it doesn't use a 3D engine with normal meshes and models and such like you need.

I think the only way to create a quality, seamless, polished game is to stick with one graphics engine that can do a lot.  But, it just depends on the quality you're happy with of course.  I'd like something that had the potential to be more impressive than Spore from the getgo. :)

---

### Post by zerix01 on 2008-07-14
[http://forums.ea.com/mboards/thread.jspa?threadID=390670&tstart=0]("http://forums.ea.com/mboards/thread.jspa?threadID=390670&tstart=0")

I have started a petition on the Spore forums. Maybe we can get EA's attention.

---

### Post by Yfrwlf on 2008-07-14
> **zerix01 said:**
> [http://forums.ea.com/mboards/thread.jspa?threadID=390670&tstart=0]("http://forums.ea.com/mboards/thread.jspa?threadID=390670&tstart=0")

I have started a petition on the Spore forums. Maybe we can get EA's attention.

I can't post because it says my "persona" is wrong or some crap.  I've tried creating both "classic" and newer "personas" and neither ever work.

---

### Post by iamcims on 2008-07-29
> **Yfrwlf said:**
> I can't post because it says my "persona" is wrong or some crap.  I've tried creating both "classic" and newer "personas" and neither ever work.

Same here, I tried using both my persona, bf2 and classic and it still blocks me out from posting on this thread.. HMMMM

---

### Post by Yfrwlf on 2008-07-30
> **iamcims said:**
> Same here, I tried using both my persona, bf2 and classic and it still blocks me out from posting on this thread.. HMMMM

I think they just don't want feedback.  Lots of companies just don't care lol.

Then there's the companies that actually realize all the benefits that being nice to their own CUSTOMERS can give them and are much nicer and more open.

---

### Post by ceduriki on 2008-08-01
I have faith in Wine. By the time the game is out, we'll be set to game. I hope...

---

### Post by EricBetts on 2008-08-10
Back on the original thread topic:
It works!(Spore on Linux)


They've got a patch out that can be applied against the current git tree and everything will work, the intro screens with logo, the full UI, everything! (For the demo version, haven't rested the retail version since I don't have a copy)

---

### Post by Yfrwlf on 2008-08-10
> **EricBetts said:**
> Back on the original thread topic:
It works!(Spore on Linux)
[http://ericbetts.org/node/91](http://ericbetts.org/node/91)

They've got a patch out that can be applied against the current git tree and everything will work, the intro screens with logo, the full UI, everything! (For the demo version, haven't rested the retail version since I don't have a copy)

The retail version isn't out yet, would be why ;)

That's cool, I hope they slap these improvements into the next Wine version so the CLI-impaired can also have easy access to Spore on Linux.  Great news, thanks for sharing. ^^

---

### Post by EricBetts on 2008-08-10
> **Yfrwlf said:**
> The retail version isn't out yet, would be why ;)

That's cool, I hope they slap these improvements into the next Wine version so the CLI-impaired can also have easy access to Spore on Linux.  Great news, thanks for sharing. ^^

I'm sorry that I wasn't clearer, when I said "retail" I meant the retail version of the Creature Creator.

---

### Post by Yfrwlf on 2008-08-10
> **EricBetts said:**
> I'm sorry that I wasn't clearer, when I said "retail" I meant the retail version of the Creature Creator.

My fault, I didn't know one existed.  I expected that the Creature Creator would be completely free to help hype up Spore more for them.

---

### Post by legolas_w on 2008-09-08
What if I:

- install virtual box
- Install windwos xp inside it
- install Spore inside the windows

will it works?

Thanks

---

### Post by Yfrwlf on 2008-09-08
> **legolas_w said:**
> What if I:

- install virtual box
- Install windwos xp inside it
- install Spore inside the windows

will it works?

Thanks

Yeah, but slowly since I don't think Virtual Box has hardware 3D support.  Since the hardware in Virtual Box for the virtual OS is emulated, you need a virtual driver that supports 3D hardware acceleration, otherwise your virtual OS will be running in software video mode just like it would if it was installed for real and you hadn't installed your Nvidia or ATI drivers.

---

### Post by Yfrwlf on 2008-09-09
Wow, so far, unless you crack the game, it doesn't look very enticing at all:

[http://arstechnica.com/news.ars/post/20080908-gamers-fight-back-against-lackluster-spore-gameplay-bad-drm.html](http://arstechnica.com/news.ars/post/20080908-gamers-fight-back-against-lackluster-spore-gameplay-bad-drm.html)

12 years to develop a lackluster RTS with a few side games.  Yay.

---

### Post by croxis on 2008-09-12
Maxis "games" arnt really games, they should be thought of as software toys.

---

### Post by Yfrwlf on 2008-09-13
> **croxis said:**
> Maxis "games" arnt really games, they should be thought of as software toys.

Sometimes the AI can be pretty fun to interact with, too, but with Spore perhaps not as much as other titles.  I can't believe Amazon removed all the negative comments from gamers about it.

---

### Post by jackcy on 2008-09-13
I was able to install and play spore with wine.
It works pretty well with my nvidia card.
By now it crashes during the step to land.

Here a link on how it could be done. [http://www.holarse-linuxgaming.de/wiki/spore](http://www.holarse-linuxgaming.de/wiki/spore)

---

### Post by willz06jw on 2008-09-14
BTW guys -- Cedega announced full Spore support

Later,
Will

---

### Post by Bios Element on 2008-09-15
> **Yfrwlf said:**
> Sometimes the AI can be pretty fun to interact with, too, but with Spore perhaps not as much as other titles.  I can't believe Amazon removed all the negative comments from gamers about it.

They didn't. It was a database glitch. Spore had more comments then almost any other item they had and their database choked on it. All the lost comments are back though. Google is your friend.

---

### Post by legolas_w on 2008-09-15
> **jackcy said:**
> I was able to install and play spore with wine.
It works pretty well with my nvidia card.
By now it crashes during the step to land.

Here a link on how it could be done. [http://www.holarse-linuxgaming.de/wiki/spore](http://www.holarse-linuxgaming.de/wiki/spore)

Hi
Can you please explain how we can apply the patch into wine?

Thanks

---

### Post by Yfrwlf on 2008-09-16
Wine probably plays Spore nearly perfectly because the "Mac version" is actually just the Windows version wrapped inside Wine/Cider.  If you look inside the program directories you will see the typical Wine folders.  Apparently Wine is becoming one of the major tools to use to make cross-platform programs since the Windows libraries/API is now a cross-platform one.

---

### Post by legolas_w on 2008-09-16
Hi
I just installed the game using winE 1.1.4 without any patch and it looks to work? but in the cell age things looks to be shown incorrectly, can someone please take a look at the screenshot and let me know whether the game is like this screenshot or problem is with Wine?

Why everything has a trail? is it from the game or WinE / installation problem?
[IMG]http://tinypic.info/files/1pjex3xvqa4vnt3olwmq.jpg[/IMG]
Thanks

---

### Post by MasterNetra on 2008-09-16
Did you try droping the graphics stuff to a minimal? Also there are water currents in the cell stage i've played spore on windows.

---

### Post by DownTown22 on 2008-09-17
I have Spore on my laptop running Vista...and no, the trails aren't from the game.  I'm gonna say it's a Wine thing.

---

### Post by xefialtis on 2008-09-21
It is interesting, this thread...it started out by someone asking if Spore might ever get a Linux port, and ended up being mostly an argument of what is better, this or that, and who did what to whom...

I propose a solution...
What we really want is some action to get games that play on Linux. How many people are using Linux these days? 1, 10, 100, 100,000? If they all bought a copy of Spore, and then returned that copy because it doesn't run on their operating system...do you thing the gaming industry would take notice?

If we really want to get games that run natively on Linux, we need to ask for it by using our $$ not our 'patch' or our 'band-aid' (wine)...

---

### Post by acalafra on 2008-09-21
> **legolas_w said:**
> What if I:

- install virtual box
- Install windwos xp inside it
- install Spore inside the windows

will it works?

Thanks

Spore will install but it will not play because directx3d is not supported in virtualbox.

---

### Post by MasterNetra on 2008-09-21
> **acalafra said:**
> Spore will install but it will not play because directx3d is not supported in virtualbox.

Actually if you read up its does play. Just not with perfect looks and takes some fiddling i guess. I however won't install it on my Ubuntu machine. I played it out on Vista. The only real good stage is the creature stage. Cell stage is alright i guess. But Tribal stage & civilization stage doesn't have much to them really. Space Stage would be alright if you weren't fending off pirates every 5 minutes or less and if their were other ships of your kind traveling around that you could add to your fleet or send to handle the pirates and other attacks at least. After all I could be out near the middle of the galaxy and a colony comes under attack. What can you do currently? Nothing by the time you get there the event is over. I think the game should of been worked on for another year or so -.-

---

### Post by schmidtbag on 2008-09-23
i don't ever expect the game to be ported to linux BUT, as far as i know, every other maxis game works in wine to some degree.  i have simcity 4 and that has some visual glitches here and there but works perfectly fine.  also, wine and crossover developers focus on what people WANT, and this game is fairly high demand

---

### Post by jessekaboom on 2008-09-26
I'm relatively new to the whole linux scene, but I know how to do most basic functions. Gaming on linux is pretty new to me, however.

I downloaded a torrent for Spore that worked fine on my Windows machine, but I want to get it for my linux machine, also. I'm downloading the same torrent, and I'm planning on using Wine and seeing if I can get it to work, but I see a lot of people talking about the Mac OS X version - would it be easier / more compatible if I used the Mac version of the game as opposed to Windows?

---

### Post by Yfrwlf on 2008-09-27
> **jessekaboom said:**
> I'm relatively new to the whole linux scene, but I know how to do most basic functions. Gaming on linux is pretty new to me, however.

I downloaded a torrent for Spore that worked fine on my Windows machine, but I want to get it for my linux machine, also. I'm downloading the same torrent, and I'm planning on using Wine and seeing if I can get it to work, but I see a lot of people talking about the Mac OS X version - would it be easier / more compatible if I used the Mac version of the game as opposed to Windows?

The Mac version **IS** the Windows version. ^^  It runs "Cider" which is Wine for Mac OS X and then runs the Windows version through it.  Cider on Linux, however, probably wouldn't work because they probably tied it in with OS X somehow, and of course Wine isn't an implementation of the OS X API, it doesn't allow you to run OS X programs.  So, no, I'm pretty sure you want the Windows version even though you may be able to run the Windows version (the EXE file) that is inside the OS X version, but I wouldn't bother.

---

### Post by Micro-soft_WIn_Dos_SuCkS on 2008-10-08
There's a way to play Spore in Linux.
ofcourse you need to make some sacrifices, like Craking the DRM in Spore and this will cause You to play without Internet verification and also the Ligthing Graphis and stuff would be out, but is not that bad.

Here is some proof:
[IMG]http://i376.photobucket.com/albums/oo205/spaxpam/SporeonUbuntuLinux.png[/IMG]

But I'm not sure if posting here the Steps to have Spore in Ubuntu 8.04 with Wine/source, since that would be rude for the author.

O well All you need is a good PC with High or Medium Performance to play.
Wine Source(look for the last Source at WineHQ)

Thanks

---

### Post by Twitch6000 on 2008-10-08
> **Yfrwlf said:**
> The Mac version **IS** the Windows version. ^^  It runs "Cider" which is Wine for Mac OS X and then runs the Windows version through it.  Cider on Linux, however, probably wouldn't work because they probably tied it in with OS X somehow, and of course Wine isn't an implementation of the OS X API, it doesn't allow you to run OS X programs.  So, no, I'm pretty sure you want the Windows version even though you may be able to run the Windows version (the EXE file) that is inside the OS X version, but I wouldn't bother.

Incorrect darwine is wine for mac :).
Cider is Cedega for MAC and Cedega is cider for Linux.

They both are are heavily edited wine projects and normally have hacked .dll's and such to make the game work 100%.

Like Cedega will have starcraft working 100% no bugs what so ever on normal wine however you have about 4 major bugs.

---

### Post by Micro-soft_WIn_Dos_SuCkS on 2008-10-09
Hey what about my post? 
PAY ATTENTION TO MY POST! 
Please! 
Thanks!

---

### Post by Sef on 2008-10-09
> Hey what about my post? 
PAY ATTENTION TO MY POST! 
Please! 
Thanks!

Please have patience.   It takes some time somtimes for a post to be answered.

---

### Post by Micro-soft_WIn_Dos_SuCkS on 2008-10-09
> **Sef said:**
> Please have patience.   It takes some time somtimes for a post to be answered.

Hey I know but I mad because he answered the post before mine even without looking at last post!!

What gives!?

o WELL NVR MIND!
Thanks

---

