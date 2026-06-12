---
title: "Why can Linux run Unreal 2007?"
date: 2007-01-03
forum: The Cafe
---

### Post by RussianVodka on 2007-01-03
I recently learned that all the Shader Model mumbo jumbo is owned by MS. And I started thinking about it again. All the new games are being built "for DX10 and Shader Model 4". But with all these constant "improvements" done by Microsoft, and only for Windows, Linux games are still of the same quality (sure you can point out the lack of Linux games, but I can just as easily point out all the lack-luster games that have only recently been released for Windows. That's not the point.)

Take for example the Unreal engines. From what I understand they've been supporting Linux since Unreal 1. Supposedly Unreal Engine 3 was built to use DX10, Shader Model 4, and so on. Yet it runs on Linux in OpenGL. Why is this? Is it because OpenGL 2.0 is capable of everything that DX10 is (from what I understand, DX10 is just a heavily optimized version of DX9)?

Same thing with Id Software's games.

Is DX nothing but hype? And if it's so revolutionary, why is OpenGL also capable of doing all that stuff?

---

### Post by Klaidas on 2007-01-03
> Linux games are still of the same quality
Bwahahaha! :mrgreen: 
Are we comparing tuxkart to NeedForSpeed?

---

### Post by _simon_ on 2007-01-03
I think they mean that UT under Windows is the same quality as UT under Linux.

---

### Post by blueturtl on 2007-01-03
The abilities of hardware under Linux are only restricted by lack of driver support and device spesifications. All the same things that DirectX can do can at least in theory be accomplished under Linux. DirectX is simply a layer that enables programmers to easily access these features. What we need is better support from video- and soundcard vendors so that we can leverage the features their hardware provide.

DooM3 requires DirectX under Windows but runs just fine under Linux without it AND with all the good stuff enabled.

---

### Post by RussianVodka on 2007-01-03
> **blueturtl said:**
> 
DooM3 requires DirectX under Windows but runs just fine under Linux without it AND with all the good stuff enabled.

Kind of a stupid question, but does that mean I would be able to run D3 with DX9 effects on a DX8 card? Not that it'll run fast, but will they look the same on both cards?

---

### Post by Pathfinder_ on 2007-01-03
i think that doom 3 uses opengl under windows.

@russinavodka
if u have a dx8 card then you will not be able to run dx9 effects at all.

---

### Post by RussianVodka on 2007-01-03
> **Pathfinder_ said:**
> i think that doom 3 uses opengl under windows.

@russinavodka
if u have a dx8 card then you will not be able to run dx9 effects at all.

When in Windows, DX acts as the middleman between OGL and the GPU. In Linux, OGL directly interacts with the video card. From what I understand.

My question was why is it that games that require Direct X 9 or 10 under windows, run just as well in Linux. Is it because OGL has it's own versions of Shader Model and what not, which are just emulated when they are run in Windows?

And as far as running DX9 on DX8 cards, I just remembered that card specifications usualy say something like:  DirectX9 / OpenGL 2.0

Now, would this mean that if I had a card which didn't support DirectX, but did support OpenGL 2.0, Doom 3 would run in Linux but now Windows?

---

### Post by Donshyoku on 2007-01-03
It isn't so much that OpenGL emulates Direct3D features with the same hardware as much as OGL uses that same hardware for a different function.  OpenGL doesn't use the shaders in the same way that Direct3D does.  Comparitively, OpenGL can only "emulate" shaders (I use that term losely) up to version 1.4 while D3D is on 4.0 now with Vista.  But using different technologies in OpenGL, they can produce similar effects.

---

### Post by macogw on 2007-01-03
UT2003 worked better on Win95 than on WinXP, according to one of my gamer friends :D  Those guys like making their games work on EVERYTHING, and it makes sense.  If you cut chunks of the population out based on their OS being old or a minority, you lose potential sales.

---

### Post by bastiegast on 2007-01-03
> **RussianVodka said:**
> I recently learned that all the Shader Model mumbo jumbo is owned by MS. And I started thinking about it again. All the new games are being built "for DX10 and Shader Model 4". But with all these constant "improvements" done by Microsoft, and only for Windows, Linux games are still of the same quality (sure you can point out the lack of Linux games, but I can just as easily point out all the lack-luster games that have only recently been released for Windows. That's not the point.)

Take for example the Unreal engines. From what I understand they've been supporting Linux since Unreal 1. Supposedly Unreal Engine 3 was built to use DX10, Shader Model 4, and so on. Yet it runs on Linux in OpenGL. Why is this? Is it because OpenGL 2.0 is capable of everything that DX10 is (from what I understand, DX10 is just a heavily optimized version of DX9)?

Same thing with Id Software's games.

Is DX nothing but hype? And if it's so revolutionary, why is OpenGL also capable of doing all that stuff?

I am far from an expert on this, but I thought id share my thoughts(they're more like questions though). So everyone's saying DX is so incredibly great. The might  not be particularly wrong about that but it maybe is not in those cool effects they advertise with. I think its might be just a great tool/framework for programming games but the effects can in fact be produced by opengl just as well.

Well it was not really an answer to your question and im curious what others have to say about it.

---

### Post by Burgresso on 2007-01-03
Um, you can setup Unreal on Linux?

---

### Post by macogw on 2007-01-03
> **Burgresso said:**
> Um, you can setup Unreal on Linux?

Yep, the same install disc works on Linux and Windows, and I think it works on Mac and all other Unixes too.

---

### Post by MetalMusicAddict on 2007-01-03
UT2004 and Quake4 installed native here. Eagerly awaiting UT2007. :)

---

### Post by WinterWeaver on 2007-01-03
All ID games, as far as I understand, also have Linux Native installations.

---

### Post by rolando2424 on 2007-01-03
Too bad my old GeForce MX 400 can't render a type of shaders that I forgot the name, so I can't play Quake 4... :( (at least in Windows I couldn't, so I assume it also don't work in Linux...).

Well, got to stick around with Unreal Tournament 2004 Demo :D

---

### Post by Burgresso on 2007-01-03
> **macogw said:**
> Yep, the same install disc works on Linux and Windows, and I think it works on Mac and all other Unixes too.

I can't believe I didn't know that.

This is huge - this is a huge victory for Linux. It should deserve its own thread it's so cool. But since I'm the only one who didnt know about this, I'm sure it's been discussed plenty. :)

---

### Post by delfick on 2007-01-03
i recently found this out too :D

so i natively installed quake 3, quake 4 and doom3 on my linux install....and they work fantastically :D

i even think doom3 works better in linux than in windows :D

EDIT :: i just realised i can play these games while beryl is still running, with no noticable side effects :D (on the same display :D)

---

### Post by Erunno on 2007-01-03
As far as I know Doom 3 used OpenGL for rendering and DirectSound / Input for the things the names suggest ;)

There was a nice article by someone who obviously had done work in that field and explained why game programming for linux is inferior to windows programming. Basically it was about lack of documentation and lack of tools. I'll post it if I can find it.

---

### Post by Lord Illidan on 2007-01-03
> **Erunno said:**
> As far as I know Doom 3 used OpenGL for rendering and DirectSound / Input for the things the names suggest ;)

There was a nice article by someone who obviously had done work in that field and explained why game programming for linux is inferior to windows programming. Basically it was about lack of documentation and lack of tools. I'll post it if I can find it.

I definitely agree. We do need better documentation when it comes to opengl, cairo, basically everything out there. And as for lack of tools, well, better IDEs would be a bonus. The days of using vi/emacs/gedit for everything are past.

---

### Post by macogw on 2007-01-03
> **Lord Illidan said:**
> I definitely agree. We do need better documentation when it comes to opengl, cairo, basically everything out there. And as for lack of tools, well, better IDEs would be a bonus. The days of using vi/emacs/gedit for everything are past.

Hey! I like vi.  Now, Eclipse, THAT is a program that should die.  It makes writing Java code feel like VB *shudder*

---

### Post by pmj on 2007-01-04
DirectX has more features than OpenGL. Often when games have both a DirectX and a OpenGL renderer, the DirectX one will look better. This is sometimes due to laziness (less time is spent on the OpenGL version), but you can't get away from the fact that OpenGL is moving pretty slow while DirectX is gaining new features at a much more rapid pace.

Doom 3, while being a very pretty game, isn't doing anything special that cards couldn't do many years ago. This is why you can play the game on a now almost ancient GeForce 3 card, and while it won't run fast it'll look identical to the game running on the best card on the market.

There are of course many benefits of choosing OpenGL over DirectX, I just felt I had to be the guy defending DirectX here. It really isn't such a bad product anymore.

---

### Post by Mathiasdm on 2007-01-04
> **macogw said:**
> Hey! I like vi.  Now, Eclipse, THAT is a program that should die.  It makes writing Java code feel like VB *shudder*

What are you talking about?
Eclipse is a great program!

I can't really comment about the VB stuff, since I've never coded VB, but I really like using Eclipse.

---

### Post by Lord Illidan on 2007-01-04
> **macogw said:**
> Hey! I like vi.  Now, Eclipse, THAT is a program that should die.  It makes writing Java code feel like VB *shudder*

I am **not** dissing vi. What I am saying is that when projects increase in size, vi gets very inefficient.

We need better IDEs like Eclipse, Anjuta, etc.

---

### Post by deepwave on 2007-03-25
> **pmj said:**
> DirectX has more features than OpenGL. Often when games have both a DirectX and a OpenGL renderer, the DirectX one will look better. This is sometimes due to laziness (less time is spent on the OpenGL version), but you can't get away from the fact that OpenGL is moving pretty slow while DirectX is gaining new features at a much more rapid pace.

Doom 3, while being a very pretty game, isn't doing anything special that cards couldn't do many years ago. This is why you can play the game on a now almost ancient GeForce 3 card, and while it won't run fast it'll look identical to the game running on the best card on the market.

There are of course many benefits of choosing OpenGL over DirectX, I just felt I had to be the guy defending DirectX here. It really isn't such a bad product anymore.

Err... I don't think its a question of whether OpenGL is older/has slower development than DirectX.  DirectX and OpenGL are just two different APIs to do graphics calculations and access the videocards.  It more of thing, that writing code in DirectX is easier.  If there is one thing MS can do it is writing decent APIs (some of the time) for developers.  DirectX also does all the whizbang shader stuff, while in OpenGL you would have to write your own shader.

As for DirectX 10 being all that great... well even John Carmack does not see any reason to upgrade from DirectX 9.  Other studios are of the same opinion.  (Sorry, I can't find the link to interview with John Carmack).

---

### Post by Lord Illidan on 2007-03-25
Sorry, was just playing UT 04..I noticed that under Linux I could not select shadows further than the blur option..there just aint any more..under Windows there were more.

---

### Post by aidanr on 2007-03-25
[http://www.thehaus.net/Tips/UT/ut2004icculusfaq.shtml](http://www.thehaus.net/Tips/UT/ut2004icculusfaq.shtml)

> Q: Why won't render-to-texture or realistic shadows work?
A: They do now! All you need is the 3369 patch, an NVIDIA card, and the latest NVIDIA drivers. To get render-to-texture (for the Hellbender license plate, etc.) add UseRenderTargets=True in the [OpenGLDrv.OpenGLRenderDevice] section of your UT2004.ini. To get realistic shadows add bPlayerShadows=True and bBlobShadow=False in the [UnrealGame.UnrealPawn] section of your User.ini.

:)

---

### Post by XVampireX on 2007-03-25
What the **** is wrong with you people? OpenGL is far more capable than pitty ol' Direct3D.

It's not a matter of API it's a matter of devs not caring for other platforms. And also in college most people learn direct3d, not opengl.

---

### Post by tehhaxorr on 2007-03-25
It hasn't been called UT2007 for about 9 months, it;s UT3 now.

[http://www.unrealtournament3.com/](http://www.unrealtournament3.com/)

---

### Post by Tomosaur on 2007-03-26
DX is not 'hype'. It is just more focused on game tech than OpenGL. The two APIs can do pretty much exactly the same stuff, it's just that, for creating games, DX makes it easier. It is entirely possible for someone to come along and create a DX-Like wrapper for OpenGL. However - whereas OpenGL is essentially just graphics, DX also incorporates sound and such.

---

### Post by Spr0k3t on 2007-03-26
While it may be easier to develop games in DirectX, you have a better feature set in OpenGL.  Even though the code for the same program in OpenGL will be a little longer, and a little more confusing to a beginner in the programming field, the OpenGL application will be more effecient.

Developing in DirectX is like slapping a VTOL on a Pinto.

---

### Post by cowlip on 2007-03-26
> **Tomosaur said:**
> DX is not 'hype'. It is just more focused on game tech than OpenGL. The two APIs can do pretty much exactly the same stuff, it's just that, for creating games, DX makes it easier. It is entirely possible for someone to come along and create a DX-Like wrapper for OpenGL. However - whereas OpenGL is essentially just graphics, DX also incorporates sound and such.

But so do SDL and OpenGL + OpenAL, all cross-platform and used in gaming consoles other than the directxbox :)

[http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer](http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer)
[http://en.wikipedia.org/wiki/OpenAL](http://en.wikipedia.org/wiki/OpenAL)
[http://en.wikipedia.org/wiki/OpenGL](http://en.wikipedia.org/wiki/OpenGL)

---

### Post by deepwave on 2007-03-26
> **Spr0k3t said:**
> 
Developing in DirectX is like slapping a VTOL on a Pinto.

Great.  Now I wouldn't be able to get rid of the image of a chicken strapped to a variable lift turboprop wing from a V-22 Osprey.

---

