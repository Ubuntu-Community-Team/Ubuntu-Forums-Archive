---
title: "Is openGL dead ?"
date: 2008-12-19
forum: The Cafe
---

### Post by emshains on 2008-12-19
Well, I have seen a lot of people on the web talking about opengl and how it kicks directX's ***. They often talk about h/w usage and other stuff like that, but then again, check the mainstream games ? Can you name a title that uses opengl, other than second life and WoW, and they use it because they needed the games to work on macs. 

Check these games: Fallout 3, GTA IV, whole source engine, Crysis, Gears of War2 etc.
All of them use directX, which means they are not going to work well with linux. 
Is this the influence  of Bill ?

I mean, it would still live on consoles, like PS3, or portable h/w, like iPhone, but as far as I can see, there is no game made for PC, that targets a big market, and uses opengl.

---

### Post by SunnyRabbiera on 2008-12-19
Actually there is a lot of stuff that uses open GL, its far from dead.

---

### Post by WaeV on 2008-12-19
Halo PC for macs uses OpenGL, but the windows version uses DirectX.

---

### Post by emshains on 2008-12-19
> **WaeV said:**
> Halo PC for macs uses OpenGL, but the windows version uses DirectX.

All of the Halos are ported to macs, or just the first one ? 


And, please, give me a name of a game, that is manufactured in 2007-2008, that uses openGL.

---

### Post by zmjjmz on 2008-12-19
DirectX and OpenGL are not equivalents. The game devs use DirectX is because DirectX includes a whole lot more like sound, net code, etc.
OpenGL is far from dying out to Direct3D though. Maybe it is when it comes to games (not really true), but it will live on.

---

### Post by eragon100 on 2008-12-19
Enemy Territory: Quake Wars uses OpenGL

---

### Post by Npl on 2008-12-19
The only reason its not dead is because theres no crossplattform alternative. Whenever you have **choice** you go for the alternative... like Direct3D.

Its years behind Direct3D, and would need a huge cleanup and restructuring.

---

### Post by emshains on 2008-12-19
But how can it then be used to make a port of HL2 to the ps3, if it is years behind the original rendering system?

---

### Post by zmjjmz on 2008-12-19
> **emshains said:**
> But how can it then be used to make a port of HL2 to the ps3, if it is years behind the original rendering system?

It isn't necessarily "years behind".
It's just harder to make things look more realistic.

---

### Post by Npl on 2008-12-19
> **emshains said:**
> But how can it then be used to make a port of HL2 to the ps3, if it is years behind the original rendering system?"OpenGL" for the PS3 is a based on OpenGL-ES with extensions and a fixed platform (and even then most games DONT use it). If you plan to use OpenGL can expect different graphicscards you
*) Dont know which operations run in hardware and which fallback to software. This can even differ between drivers on the same hardware. Have fun testing tons of cards.
*) typically need 2-3 ways to do everything as alot of functionality that Direct3D offers universally is an extension.

---

### Post by Delever on 2008-12-19
> **emshains said:**
> 

Check these games: Fallout 3, GTA IV, whole source engine, Crysis, Gears of War2 etc.
All of them use directX...

Any of them work on PS3 by any chance? You know, PS3 has no DirectX...

---

### Post by SunnyRabbiera on 2008-12-19
> **Npl said:**
> The only reason its not dead is because theres no crossplattform alternative. Whenever you have **choice** you go for the alternative... like Direct3D.

Its years behind Direct3D, and would need a huge cleanup and restructuring.

Bah to heck with direct3d as at least opengl is cross platform and linux friendly.
MS only apps= even more behind in my opinion

---

### Post by mangar on 2008-12-19
I happen to work in a related field.

In the gaming market, the only major company that still uses OpenGL is id, with their various engines (quake 1,2,3,4, id5). 

Just about everyone else uses DirectX.

Many Mac games are written using DirectX, and than ported using Cider, so no luck there either.

[http://www.transgaming.com/products/cider/](http://www.transgaming.com/products/cider/)

On Windows, OpenGL is considered a legacy system, with the only active development happening in the professional space (cad, etc), and even that is transitioning to directX:

[http://www.mcadforums.com/forums/files/autodesk_inventor_opengl_to_directx_evolution.pdf](http://www.mcadforums.com/forums/files/autodesk_inventor_opengl_to_directx_evolution.pdf)

In short, OpenGl is not dead, but it's certainly not well.

---

### Post by Delever on 2008-12-19
For me saying that OpenGL is dead is like saying that Linux is dead. Measuring OpenGL "deadness" status with Windows market share seems very wrong. Unless there is another library that GPU manufacturers are going to implement in every card model, I don't think it is going to be dead very soon.

---

### Post by cb951303 on 2008-12-19
> **Npl said:**
> The only reason its not dead is because theres no crossplattform alternative. Whenever you have **choice** you go for the alternative... like Direct3D.

Its years behind Direct3D, and would need a huge cleanup and restructuring.

It's not years behind. But you're absolutely right about cleanup and restructuring. I was so disappointed when OpenGL 3.0  came up and it was the same old s***y state machine design ...

---

### Post by cb951303 on 2008-12-19
> **mangar said:**
> I happen to work in a related field.

In the gaming market, the only major company that still uses OpenGL is id, with their various engines (quake 1,2,3,4, id5). 


add blizzard (remember the opengl argument in WoW) and bioware (never winter nights) to that list...

edit: maxis and crytek uses opengl too

---

### Post by mangar on 2008-12-19
@cb951303
If you'll read the attached pdf, you'll notice that Autodesk's developer are pushing toward directX since the hardware manufacturers provides very inconsistent support for OpenGL (in short, they are more or less dropping support for OGL as well).

OpenGL is dying in the same fashion that photo films, tape cassettes and floppies had died - the support is slowly dwindling, the quality of the remaining products gets worse over time, and in the end nobody uses it anymore. Ogl is still not completely gone, but it is on the way out (with the ogl 3.0 fiasco more or less putting the last nail in the coffin).

---

### Post by Delever on 2008-12-19
> **cb951303 said:**
> add blizzard (remember the opengl argument in WoW) and bioware (never winter nights) to that list...

Add Unreal engine, although game developers are free not to support OpenGL in their release, and that makes sense.

There are also rumors about OpenGL support in source engine.

---

### Post by Delever on 2008-12-19
> **mangar said:**
> @cb951303
If you'll read the attached pdf, you'll notice that Autodesk's developer are pushing toward directX since the hardware manufacturers provides very inconsistent support for OpenGL (in short, they are more or less dropping support for OGL as well).


Not suprising, since such product like AutoCAD is destined for one system. It has such things like COM and .NET framework heavily mixed inside it's codebase, porting that would be just hard.

I agree that OpenGL indeed needs more work. I just arguing about definition of "dead"...

---

### Post by eragon100 on 2008-12-19
> **Delever said:**
> Add Unreal engine, although game developers are free not to support OpenGL in their release, and that makes sense.

There are also rumors about OpenGL support in source engine.

That not just a rumor. It's confirmed. Postal 3 is confirmed to both run oh the source engine and to get a native linux client. Offcourse this means the source engine *must* get OpenGL support, or they have to do what EVE Online did and port their game with Cider/Cedega for mac/linux respectively, but then they would have to pay two extra licenses to transgaming.

---

### Post by cb951303 on 2008-12-19
> **mangar said:**
> @cb951303
If you'll read the attached pdf, you'll notice that Autodesk's developer are pushing toward directX since the hardware manufacturers provides very inconsistent support for OpenGL (in short, they are more or less dropping support for OGL as well).

OpenGL is dying in the same fashion that photo films, tape cassettes and floppies had died - the support is slowly dwindling, the quality of the remaining products gets worse over time, and in the end nobody uses it anymore. Ogl is still not completely gone, but it is on the way out (with the ogl 3.0 fiasco more or less putting the last nail in the coffin).

No, there is simply no other cross platform alternative. So as long as macos exists (who needs hardware acceleration for lots of things) opengl won't die.
I also want to add linux in front of macos but I know we're not too many to make a difference on this subject yet.

---

### Post by mangar on 2008-12-19
NWN1 was out in 2002. NWN2's Aurora Engine is DirectX based. 
Thanks for the correction. Blizzard is using ogl as well.

---

### Post by Delever on 2008-12-19
I would look at it this way: games are simply using API which is recommended and supported by system manufacturer. DirectX is chosen for Windows because support for OpenGL in future is not certain; it is lucky that Microsoft implemented support for OpenGL in Aero, and this is again one more argument against "dead".

---

### Post by cb951303 on 2008-12-19
> **Delever said:**
> I would look at it this way: games are simply using API which is recommended and supported by system manufacturer. DirectX is chosen for Windows because support for OpenGL in future is not certain; it is lucky that Microsoft implemented support for OpenGL in Aero, and this is again one more argument against "dead".

The most important reason of DirectX choice over OpenGL is because DirectX is a whole package. With DirectX you get 3d graphics, network, audio, video, user interface(via win32 inheritance). If you were a developer which one you would choose considering that OpenGL has only 3D graphics capability?

---

### Post by Delever on 2008-12-19
> **cb951303 said:**
> The most important reason of DirectX choice over OpenGL is because DirectX is a whole package. With DirectX you get 3d graphics, network, audio, video, user interface(via win32 inheritance). If you were a developer which one you would choose considering that OpenGL has only 3D graphics capability?

This has several answers, depending of scope of different things.

For example, last game I made used OpenGL with SDL, and my own networking layer. But this game was very small and experimental, and I have chosen to use OpenGL to make it portable, and that was easy to do.

If I were developer big enough to write my own game engine (so I could even begin to think about selecting API), and my market would certainly be PC/XBOX, I would choose DirectX. If my game would be destined to PS3, I would have to use OpenGL (that special version).

If I were medium developer with appropriate resources, I would select existing engine. When deciding which one, I would value possibility to run it on different platforms.

---

### Post by Npl on 2008-12-19
> **cb951303 said:**
> The most important reason of DirectX choice over OpenGL is because DirectX is a whole package. With DirectX you get 3d graphics, network, audio, video, user interface(via win32 inheritance). If you were a developer which one you would choose considering that OpenGL has only 3D graphics capability?Noone is stopping you from using OpenGL with DirectX (sans graphics). The reason not to use OpenGL is because its grown to a bloated mess, both for Application developers and Driver writers.

To quote John Carmack on OpenGL3:> "Yeah, so that's a little bit sad, the way that whole situation has gone. I understand the way it all happened and I can't be too upset about it, but there was a move going to modernize the OpenGL API. It really has a lot of cruft on it right now. I'm quite frank in saying that the DX9+ class Microsoft APIs are a lot better thought out and more consistent than the current state of OpenGL, which has selectors and all these extensions and things that just aren't really clean and nice, and there was a move to go ahead and bring it up to par... [inaudible, loud squeaking door] some directions were perhaps mis-steps, but some things were looking pretty good on there. But, as I understand, what happened was some of the companies on the ARB made the justifiable statement that the major codebases for CAD developers, the 10 million line codebases, the 20 years of ancient history, they're never going to convert to a radically new API. Making a new OpenGL that's not remotely backwards compatible just isn't going to fly, isn't worth doing. And, I disagree with that stance, but not enough to make a scene about it. I do think that there is a need for a non-Microsoft, open, cross platform API that's modern-- we can still do everything we need to with the current OpenGL, it's just kind of a mess. That's not the argument you want to be making. You want to say 'We're using this because it's clean and elegant, and it's better than the alternative,' and that's not really the case..."

Its an excerpt [from a quite long audiolog]("http://www.enemyterritory.tv/audio/data/qcon2008_et.tv_keynote.mp3") in case someones questioning the source.

---

### Post by cb951303 on 2008-12-19
> **Npl said:**
> Noone is stopping you from using OpenGL with DirectX (sans graphics). The reason not to use OpenGL is because its grown to a bloated mess, both for Application developers and Driver writers.


why use opengl if you're going to use directx anyway? I know opengl is bloated but frankly opengl was always underdog when it came to games. And I think the reason behind this is the one I explained earlier.

---

### Post by etnlIcarus on 2008-12-20
> **cb951303 said:**
> The most important reason of DirectX choice over OpenGL is because DirectX is a whole package. With DirectX you get 3d graphics, network, audio, video, user interface(via win32 inheritance). If you were a developer which one you would choose considering that OpenGL has only 3D graphics capability?

Not sure your argument stands up to much scrutiny. The only components of DirectX that are reliably used these days is Direct3D and DirectDraw. [http://en.wikipedia.org/wiki/Directx#Components](http://en.wikipedia.org/wiki/Directx#Components) Most professional game devs, if they're building an original engine and not simply licensing one, are first going to figure out what APIs they want to use, depending on budget, platform, technical aspirations etc. The only commercial games likely to use DirectX exclusively are the ones which are introduced as budget titles from release and eventually end up as free-full games on your favourite computer magazine's front cover.

I'm going to echo what many others in this thread have already said: Direct3D is clean, stable, capable and the only reliable standard on the dominant OS platform. That's more than enough of an explanation for it's dominance in the PC-gaming market, despite portability.

---

### Post by emshains on 2008-12-20
> **Delever said:**
> Any of them work on PS3 by any chance? You know, PS3 has no DirectX...

I am talking about PC's, and if the devs can port their code to PS3, then they ar e just plain lazy, if they can't port it to linux.

---

### Post by Delever on 2008-12-20
> **emshains said:**
> I am talking about PC's, and if the devs can port their code to PS3, then they ar e just plain lazy, if they can't port it to linux.

I think the main reason is that once game is released for target platform/os, it needs to be supported, and currently companies don't expect investment in that to return from Linux customers.

If however, Linux had serious user percentage, they would port it without another thought.

---

### Post by Erunno on 2008-12-20
> **cb951303 said:**
> edit: maxis and crytek uses opengl too

CryEngine 2 currently does not support OpenGL in the renderer but is supposedly worked on. Sims 2 was ported to OS X by Asypr.

---

### Post by emshains on 2008-12-20
So why, if it is so behind the modern world and is bloated etc., do we, linux dudes, aren't helping it ?
I mean, openGL is the only good renderer, besides ogre, which is really slow on my 7300gt. If weren't for openGL, we couldn't do compiz or any gaming. If I could, I'd take part in it's development, but since I am lacking the knowledge and time I just can't do it.

---

### Post by zmjjmz on 2008-12-20
> **emshains said:**
> So why, if it is so behind the modern world and is bloated etc., do we, linux dudes, aren't helping it ?
Not sure what you mean by that, but it is under active development so it's not like nobody's working on it.

---

### Post by Frak on 2008-12-20
Thanks to Ryan "Icculus" Gordon, Prey (2006 video game) now works on Linux under OpenGL.

[http://icculus.org/prey/](http://icculus.org/prey/)

Anyways, OpenGL is far from dead, just look at every Mac app out there with a heavy graphical interface. It's rendered under OpenGL.

---

### Post by WaeV on 2008-12-20
What about EVE online?  They have a linux version which I'm pretty certain doesn't use DirectX.

---

### Post by Erunno on 2008-12-20
> **WaeV said:**
> What about EVE online?  They have a linux version which I'm pretty certain doesn't use DirectX.

Actually, it does. The engine was recently ported from DirectX 8 to 9. The updated engine was released with the Trinity expansion pack. Cadega/Cider are used on Linxu and Mac OS X [1].

[1] [New EVE Online Client Offers Official Linux and OS X Support]("http://www.escapistmagazine.com/news/view/78605-New-EVE-Online-Client-Offers-Official-Linux-and-OS-X-Support")

---

### Post by Erunno on 2008-12-20
> **emshains said:**
> So why, if it is so behind the modern world and is bloated etc., do we, linux dudes, aren't helping it ?

The OpenGL standard is currently maintained by the Khronos group and many stakeholders are actually part of this organisation including graphic card vendors as well as heavy users of OpenGL (including companies developing CAD applications). The "Linux dudes" can't just waltz in and take over development. It woud result in a fork which no hardware vendor would support. OpenGL was the disappointment that it is due to companies with huge code basis depending on old versions of OpenGL and prevented from 3.0 becoming incompatible with former versions.

---

### Post by emshains on 2008-12-20
> **Erunno said:**
> The OpenGL standard is currently maintained by the Khronos group and many stakeholders are actually part of this organisation including graphic card vendors as well as heavy users of OpenGL (including companies developing CAD applications). The "Linux dudes" can't just waltz in and take over development. It woud result in a fork which no hardware vendor would support. OpenGL was the disappointment that it is due to companies with huge code basis depending on old versions of OpenGL and prevented from 3.0 becoming incompatible with former versions.

It still is an open-source project, it's not like they don't need any help. I mean, we can't/won't take over the project, but we can still try to help them.

---

### Post by Erunno on 2008-12-20
> **emshains said:**
> It still is an open-source project, it's not like they don't need any help. I mean, we can't/won't take over the project, but we can still try to help them.

OpenGL is a specification, not an actual application. And the biggest problem is getting all stakeholders to agree upon a new OpenGL architecture when there are code bases covering several millions of lines which would break with a new, incompatible version which is very much needed if OpenGL is to move forward.

---

### Post by toupeiro on 2008-12-20
OpenGL is so far from dead...  Increase your range beyond games or Vendors which almost solely cater to a windows model (AutoDesk) and you will see this...

---

### Post by MikeTheC on 2008-12-20
For my part I would hope OpenGL either doesn't die, or if it dies that it gets replaced with a worthy successor. We always need competition, especially where proprietary standards exist.

---

### Post by emshains on 2008-12-22
> **toupeiro said:**
> OpenGL is so far from dead...  Increase your range beyond games or Vendors which almost solely cater to a windows model (AutoDesk) and you will see this...

Well, the thing is, it's hard for me to see it in work.

---

### Post by Frak on 2008-12-22
> **emshains said:**
> Well, the thing is, it's hard for me to see it in work.
If OpenGL dies, Apple Quartz dies, Apple Aqua dies, Apple gaming (mostly) dies, Autodesk dies, Bonelab dies, EMotion dies, SenseAble dies...

There are many companies (and governments) that rely on OpenGL for various purposes.

---

### Post by Listen2TheTruth on 2008-12-22
Read this post before it gets deleted and my account suspended.

I guess there will always be people who can look at gold and throw it away and think its "fake" or "can't be" or "im an ignorant moron". Pick one of the above im pretty sure you are right up there with any of the above described. 

Ok to clarify. I've build and been using an HHO system in my car for the past 6 months. If anyone can tell you about results, its not a oil lobbied PhD holder, a fake scientist or a opinionated freak who is so paraniod thinking his birth is a conspiracy, no..but someone like me- a regular consumer who has used it and loves it to death!

I drive a volvo that gets 31 MPG HWY with my HHO system off, 53MPG HWY with it on. Any questions? Didnt think so! 

Besides some of you (removed by moderator) forgot that Hydrogen can be extracted from water using electroalysis with solar panels, windenergy etc. so although the extraction process may not be 100% efficient, it sure as hell can be "FREE" if we choose to. 

Oil requires a hell lot of energy to obtain too. Researching, Drilling, Extracting, destilling etc...look at all the processes that it has to go through before it can be made available as a combustable gas. Do some research before you post your ignorant, nonsensical opinions on a topic you have no idea about! 

Do a google search on zero point energy or zero field energy, a guy in kansas invented a device that produces more energy (output)than the energy put into the system to extract it (input). Thats the future of energy "creation" and if you are one of those misleading, good-for-nothing opinionated pinheads thinking "oh matter can neither be created nor distroyed - i learned that in High School...waahhh waahhhh cryyy cryyy" then all i have to say is "you have been living on the moon" for science and technology is a dynamic world and it changes every nanosecond of your existence! So get with the plan and stop being ignorant and crying about a solution that really works!

Lastly, watch ZEITGEIST 1 + 2 and be changed forever.

---

### Post by ZarathustraDK on 2009-03-16
I don't think there should be any fear concerning the impact on Linux in regards to games/linux angle. Even if OpenGL went bottom-up games has always been a minor tip on the scale in regards to Linux-adoption (which is a good thing too).

I can better imagine linux-adoption soar as a result of its quality and tip the scales in favor of OpenGL (more users, more demand for OpenGL for leisurely pursuits), than I can imagine OpenGL punch a hole Linux' boat.

---

### Post by Simian Man on 2009-03-16
OpenGL is very outdated in terms of the API.  It reflected the way the hardware worked years ago, but not any more.  Now to make something performant, you have to rely on the extension mechanism and avoid a whole slew of functionality in the API proper.  Anything done with Dircet3D can be done with OpenGL: it's the same hardware underneath after all.

Basically Direct3D just makes the programmer's life way nicer.  That is why it is being used for most games nowadays.  The Khronos Group was supposed to publish a new OGL specification, but it faltered.

OpenGL won't die, it just needs some TLC.

---

### Post by Shea7993 on 2009-07-19
> **Npl said:**
> "OpenGL" for the PS3 is a based on OpenGL-ES with extensions and a fixed platform (and even then most games DONT use it). If you plan to use OpenGL can expect different graphicscards you
*) Dont know which operations run in hardware and which fallback to software. This can even differ between drivers on the same hardware. Have fun testing tons of cards.
*) typically need 2-3 ways to do everything as alot of functionality that Direct3D offers universally is an extension.

Point to note here... PS3 uses openGL

So howcome the PC versions of PS3 games dont support openGL??? like UT3, ive tried to get info on OpenGL support for the Unreal Engine 3 and could only find that its not completed and probably wont be either, however UT3 is out on PS3 and other unreal engine 3 based games? like WTF? OpenGL games work rather well with wine, and developers could make Linux native clients for their games to support us Linux gamers

---

### Post by Sef on 2009-07-19
Necromancing.  Start a new thread and link to this one if you like.

---

