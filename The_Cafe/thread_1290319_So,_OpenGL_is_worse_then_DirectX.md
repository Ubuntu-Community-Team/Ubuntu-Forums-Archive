---
title: "So, OpenGL is worse then DirectX?"
date: 2009-10-13
forum: The Cafe
---

### Post by CJ Master on 2009-10-13
I can think of no other reason companies would choose something available for one platform only instead of cross-platform. Is OpenGL slower?

---

### Post by Simian Man on 2009-10-13
OpenGL is not slower than Direct3D; they both drive the same hardware.  However because the OpenGL API is very outdated and patched up with extensions, it can be much more difficult to achieve good performance, whereas good performance is kind of the default way of doing things in Direct3D.

OpenGL code for modern hardware tends to be full of extensions which are a pain to work with and is just messier than the equivalent D3D code.  Also Direct3D is much nicer to work with because it provides support for a lot of things OpenGL doesn't like the D3DX library that provides fonts, sprites and other things.

So Direct3D is better but not because it's faster, just because the API is more up to date and better reflects the actual hardware.

---

### Post by hessiess on 2009-10-13
OpenGL is just a lib for drawing polygons, DX is a complete app dev framework. I have looked into DX breafly and it sempt to require an absolute tun of set up code just do do trivial things.

Personally I wouldn't use DX for anything as it tyes you to one(fundamentally broken) platform.

---

### Post by Simian Man on 2009-10-13
> **hessiess said:**
> OpenGL is just a lib for drawing polygons, DX is a complete app dev framework. I have looked into DX breafly and it sempt to require an absolute tun of set up code just do do trivial things.
That's not exactly true.  "Hello World" with DirectX is non-trivial, but all of that code required to setup the library is a constant overhead; it doesn't scale up for larger apps.

However doing things that are beyond hello world but still trivial like writing text to the screen in an efficient manner, or loading a simple static mesh and displaying it are MUCH easier with Direct3D than they are with OpenGL and to pretend otherwise is foolish.  That's why there are so many OpenGL helper libs on sourceforge (of widely varying quality); because OpenGL is so bare-bones to the point of being painful.

> **hessiess said:**
> Personally I wouldn't use DX for anything as it tyes you to one(fundamentally broken) platform.

I agree, and would never develop a Windows-only game (or Linux only for that manner), but DX is a great library.

---

### Post by schauerlich on 2009-10-13
> **CJ Master said:**
> I can think of no other reason companies would choose something available for one platform only instead of cross-platform. Is OpenGL slower?

Because that one platform is 90% of the desktop market, and near 100% of the PC gaming market?

---

### Post by forrestcupp on 2009-10-13
> **Simian Man said:**
> but DX is a great library.

I agree.  I worked with managed DX for a while, and it was pretty nice.  Especially since 3D sound and input device programming integrates so nicely with the graphic side of it.

But I did find that the main reason a lot of people program directly in DX is to make a game engine to make game programming easier.

But you can't compare OpenGL to the complete DirectX.

---

### Post by JDShu on 2009-10-13
> **EDavidBurg said:**
> Because that one platform is 90% of the desktop market, and near 100% of the PC gaming market?

Thats not a reason to use DX over OpenGL. The reason, like many have stated is that it is easier to use.

---

### Post by schauerlich on 2009-10-13
> **JDShu said:**
> Thats not a reason to use DX over OpenGL. The reason, like many have stated is that it is easier to use.

...Writing a game using the library that 90+% of your potential customers use ISN'T a reason to use DirectX?

---

### Post by RiceMonster on 2009-10-13
> **EDavidBurg said:**
> ...Writing a game using the library that 90+% of your potential customers use ISN'T a reason to use DirectX?

I don't see your point. Direct X and OpenGL are both available on Windows. It's not like using OpenGL is going to have any effect on Windows users using your game.

---

### Post by JDShu on 2009-10-13
> **RiceMonster said:**
> I don't see your point. Direct X and OpenGL are both available on Windows. It's not like using OpenGL is going to have any effect on Windows users using your game.

This.

---

### Post by hessiess on 2009-10-13
> **EDavidBurg said:**
> ...Writing a game using the library that 90+% of your potential customers use ISN'T a reason to use DirectX?

Writing a game on top of a good, platform independent engine lets you largly completely forget about the DX vs OGL issue. Now the only problem is HLSL vs GLSL.

---

### Post by -grubby on 2009-10-13
> **hessiess said:**
> Writing a game on top of a good, platform independent engine lets you largly completely forget about the DX vs OGL issue.

And this entire thread's purpose is debating whether OpenGL is a good engine.

---

### Post by SunnyRabbiera on 2009-10-13
> **-grubby said:**
> And this entire thread's purpose is debating whether OpenGL is a good engine.

Well it is a good engine, but maybe it is time we made a new alternative to DX.
Mainly because we need something is more easy to work with despite the matter that OpenGL can perform better then direct x

---

### Post by TheBuzzSaw on 2009-10-13
Seeing as how Blizzard builds games for both PC and Mac, methinks OpenGL is still perfectly relevant.

I do want to learn DX someday, but in the meantime, I am big on cross-platform development. Sure, Windows has massive market share, but why not hit all three platforms at once?

---

### Post by hessiess on 2009-10-13
> **-grubby said:**
> And this entire thread's purpose is debating whether OpenGL is a good engine.

OGL isnt an engine, its a library for drawing shaded an textured polygons.

[ogre](http://en.wikipedia.org/wiki/OGRE)
[Crystal space](http://en.wikipedia.org/wiki/Crystal_Space)
[Irrlicht](http://en.wikipedia.org/wiki/Irrlicht_Engine)

Are graphics/game engine which do a lot more than OGL, such as implementing scene graphs, event systems and so on.

---

### Post by starcannon on 2009-10-13
> **CJ Master said:**
> I can think of no other reason companies would choose something available for one platform only instead of cross-platform. Is OpenGL slower?
Money makes the world go around.
For a bit of side by side comparison, [http://www.winmatrix.com/forums/index.php?/topic/13647-directx-10-vs-opengl-2-1-graphics/](http://www.winmatrix.com/forums/index.php?/topic/13647-directx-10-vs-opengl-2-1-graphics/)

Here's an article from last year that I feel sums up pretty nicely. 
[http://www.tomshardware.com/reviews/opengl-directx,2019.html](http://www.tomshardware.com/reviews/opengl-directx,2019.html)

For an endless supply of articles, pundits, etc...
[http://www.google.com/search?hl=en&q=opengl+3+vs+directx+11&btnG=Search&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&q=opengl+3+vs+directx+11&btnG=Search&aq=f&oq=&aqi=)

I want OpenGL to make a comeback, but unless some serious money, and some serious organization and co-operation take place, I don't see it happening.

Here's to hope.

---

### Post by -grubby on 2009-10-13
> **hessiess said:**
> OGL isnt an engine, its a library for drawing shaded an textured polygons.

[ogre](http://en.wikipedia.org/wiki/OGRE)
[Crystal space](http://en.wikipedia.org/wiki/Crystal_Space)
[Irrlicht](http://en.wikipedia.org/wiki/Irrlicht_Engine)

Are graphics/game engine which do a lot more than OGL, such as implementing scene graphs, event systems and so on.

Ok, by 'engine' I thought you meant OpenGL, not a game engine.

---

### Post by hoppipolla on 2009-10-13
I'm not a coder, but it does always seem like DX is better which is such a shame ._.

Hopefully if Linux-based OSs get more popular OpenGL will get a bit more TLC! :)

---

### Post by aaaantoine on 2009-10-13
> **hoppipolla said:**
> Hopefully if Linux-based OSs get more popular OpenGL will get a bit more TLC! :)

OpenGL is one of a handful of open projects that benefits more from Windows losing market share than from Linux gaining market share.

---

### Post by Npl on 2009-10-13
> **hoppipolla said:**
> I'm not a coder, but it does always seem like DX is better which is such a shame ._.

Hopefully if Linux-based OSs get more popular OpenGL will get a bit more TLC! :)
I think Handhelds and consoles (some PS3 Games use subset of OpenGL, but most use the hardware directly) have a better chance of pushing OpenGL back into the minds of developers. Even if it does I dont think its a reason to rejoice unless it gets popular again because the API gets improved (or rather redone) - why is that you`re happy if a OpenGL gets more coverage because its the only choice and not based on its quality and technical merits?

But the point still is that noone uses OpenGL unless he has to, its just a damn mess both for application and driver developers. OpenGL-ES (handhelds) is a stripped down version and a much cleaner API.

---

### Post by j.bell730 on 2009-10-13
Ironically, DirectX was largely thought of as a monstrosity, compared to OpenGL in DirectX's early days. Everyone criticized Microsoft for creating it when they could have just stuck with OpenGL.

---

### Post by Npl on 2009-10-13
> **j.bell730 said:**
> Ironically, DirectX was largely thought of as a monstrosity, compared to OpenGL in DirectX's early days. Everyone criticized Microsoft for creating it when they could have just stuck with OpenGL.And early Direct3D versions often where totally incompatible with each other. eg. if you had a D3D6 Game and wanted to use (even a single) D3D7 feature you had to rewrite alot to fully change to D3D7.
With OpenGL most new features would just be a optional extension.

The end result is that after several tries, often changing basically everything, MS suceeded, while OpenGL just limbs along with decade old luggage and still wont do necessary big changes.

Guess its a win of darwinism over life-support :)

---

### Post by graabein on 2009-10-13
Microsoft just happens to make OpenGL run slow on Windows while pushing DirectX. You do the math.

---

### Post by hoppipolla on 2009-10-13
> **Npl said:**
> I think Handhelds and consoles (some PS3 Games use subset of OpenGL, but most use the hardware directly) have a better chance of pushing OpenGL back into the minds of developers. Even if it does I dont think its a reason to rejoice unless it gets popular again because the API gets improved (or rather redone) - why is that you`re happy if a OpenGL gets more coverage because its the only choice and not based on its quality and technical merits?

No I didn't mean that, I meant TLC as in "Tender, Loving Care", like, it would get more work done on it and be through and through better :)

I agree with you about the consoles and things though :)

---

### Post by Simian Man on 2009-10-13
> **graabein said:**
> Microsoft just happens to make OpenGL run slow on Windows while pushing DirectX. You do the math.

Virtually all of OpenGL is implemented in your graphics cards video drivers which aren't written by Microsoft at all...so yeah you're way off base here.

---

### Post by Tipped OuT on 2009-10-13
Do you guys even realize that OpenGL is mostly 2D (task bar, etc.) and Direct X is mostly 3D (Video Games, etc.).

How could you even compare the two?

=/

---

### Post by JDShu on 2009-10-13
> **Tipped OuT said:**
> Do you guys even realize that OpenGL is mostly 2D (task bar, etc.) and Direct X is mostly 3D (Video Games, etc.).

How could you even compare the two?

=/

lolwut

---

### Post by dcraven on 2009-10-13
> **Tipped OuT said:**
> Do you guys even realize that OpenGL is mostly 2D (task bar, etc.) and Direct X is mostly 3D (Video Games, etc.).

How could you even compare the two?

=/

Huh? You might be thinking of SDL.

---

### Post by RiceMonster on 2009-10-13
> **Tipped OuT said:**
> Do you guys even realize that OpenGL is mostly 2D (task bar, etc.) and Direct X is mostly 3D (Video Games, etc.).

How could you even compare the two?

=/

Are you serious?

---

### Post by hoppipolla on 2009-10-13
> **JDShu said:**
> lolwut

haha agreed :)

---

### Post by Tipped OuT on 2009-10-13
> **RiceMonster said:**
> Are you serious?

No. lol.

---

### Post by Xbehave on 2009-10-13
> **Tipped OuT said:**
> Do you guys even realize that OpenGL is mostly 2D (task bar, etc.) and Direct X is mostly 3D (Video Games, etc.).

How could you even compare the two?

=/
Please stop posting without a clue, or at least read the first two pages before commenting on page 3 of an insightful discussion.

so far we have coverd
[LIST]
[*]OpenGL and directX are both 3d rendering APIs/libs.
[*]Game engines allow you to avoid interactive with openGL/DX at all (I'm adding that, most engines are DX only)
[*]DX is easier to use
[/LIST]
It seams to me somebody needs to create  a lib/API around openGL that is easier to use than the DX tools (because **I think**, on a raw performance and a low level both are pretty equal). I think an advantage DX has is that the ms IDE is actually pretty good (as a python *developer* all i need is a text editor but apparently IDEs are useful), so apart from a nice openGL wrapper lib (which need to be IN openGL) openGL also needs a nice IDE.

---

### Post by hoppipolla on 2009-10-13
> **Tipped OuT said:**
> No. lol.

It seemed like you were! hehe

Ok maybe we shouldn't descend like hawks the second someone might not know something lol

If you really don't know about it Tipped OuT then someone could probably explain it! As I understand it they both go direct through the graphics card and are principally for 3D graphics rendering and effects! But I might be wrong xD

---

### Post by CJ Master on 2009-10-13
> **tipped out said:**
> no. Lol.

lies

---

### Post by Tipped OuT on 2009-10-13
> **CJ Master said:**
> lies

Lol, you posted all of that for nothing. XD

Come on, it's on freaking Wikipedia. I would have to be a complete moron.... oh wait.

---

### Post by JDShu on 2009-10-13
Anyway, heres to hoping that OpenGL becomes more popular and maybe more open source 3D games and other applications will appear :D

---

### Post by Slug71 on 2009-10-14
Im guessing for OpenGL to 'compete' or be on the same level as DX, a complete rewrite is in need.

Me just wonders if it will ever happen. :(

---

### Post by billdotson on 2009-10-14
I sure would like to see OpenGL be as good as DirectX in terms of technical merits and I would definitely like to see it become as easy to use as DirectX. I personally think it should be illegal for Microsoft to purposefully ruin OpenGL support on Vista. I have heard from multiple sources that it can only be used to 50% of its full capacity of something like that. If I had more money and time than I do now I would be trying to organize a class action. Come to think of it, I'd be chasing lots of underhanded tactics by corporations if I had the time. There is too much anti-competitive crap that goes on in the corporate world, especially with technology. Any company that does anti-competitive crap like MS does is holding the advancement of technology back, which is criminal. I won't point fingers at anyone else here but there are definitely other corporations that do this too.

I don't know much about OpenGL or DirectX, but if it really wants to compete and open up the PC gaming scene for more than just Windows users (OS X users make up ~10% of the market and some of them probably count for Windows share too, which they have just to play games) it has to be about as easy or easier. With the smaller market share for Linux, OS X, BSD, etc. OpenGL isn't worth the extra work to get working on anything other than Windows. I can't really talk because I can't contribute to the code myself (I am learning though so I can try and help with these sort of projects in the future) but if it needs a full rewrite to be competitive then I guess it needs a full rewrite to be competitive. To be competitive someone needs to find a way to make Microsoft fix the OpenGL implementation in their operating system (if I have misinformation on the subject please correct me, I would really like to know if I heard wrong).

So, when is OpenGL 3.0 coming out?

Edit that out.. OpenGL 3.2 is already out. I read on a forum somewhere that it cleaned out the API and made it easier to use. You can check wikipedia and a few other places (I guess opengl.org) to see the more technical specifications of it.

I could only hope that OpenGL will come back fighting.

---

### Post by Frak on 2009-10-14
1. It controls nearly 100% of the PC Gaming market.
2. It's cleaner in my experiences.
3. It's faster in my experiences.
4. It's newer and more up-to-date with hardware standards.
5. There's a kick-*** IDE that supports it fully.

---

### Post by hoppipolla on 2009-10-14
So, if a game was ported to Mac OSX... what's that made in? OpenGL?

Is that another reason why fewer advanced games make it on to OSX and open source OSs?

---

### Post by toupeiro on 2009-10-14
Some people have hit on it, but basically, openGL running slow on windows is Microsofts doing.  I support a lot of 64-bit linux desktop doing heavy 3d modeling and it's 100% OpenGL.  In areas where the applications are cross-platform, Linux is ALWAYS the platform of choice for performance.

---

### Post by blueturtl on 2009-10-14
OpenGL was a superior alternative for a good while before DirectX gained ground. Why did all those game developers push through the pain that was DirectX development when they could have just kept using OpenGL?

Whoever can answer that question has the answer to getting devs to use OpenGL again.

My theory is lazyness. Most developers are lazy. Windows was a poor gaming developmet platform until a unified API came into existence. DOS game coders pretty much built their games to use spesific hardware features. If you had no ATI Mach card, then no ATI Mach features for you. If you had no SoundBlaster, then no sound support for you etc.

DirectX pulls it all nicely together. No more wondering about what hardware the gamer might be running. Just write to DX features and supporting hardware will work. This is the part where lazyness comes in. OpenGL was not a part of the DirectX framework. A game developer would code most of their game in DX features, and then work separately on an OpenGL engine... or they could just forget OpenGL and build everything inside the DirectX development framework. Yes, Direct3D was a bitch in the beginning compared to OpenGL, but it was so niftly part of the package and all the target machines would run Windows anyway -- who cares about portability?

John Carmack made the case when D3D was still sucking that Microsoft should incorporate OpenGL support into DirectX so that it be called DirecGL or something. He felt that he was wasting time with D3D when OpenGL was more robust and easy to use and it was there already. But knowing Microsoft they of course refused. Why would they want to support portability when they were holding over 90% of the desktop OS market?

Eventually Direct3D came to match OpenGL in terms of features. How could we get OpenGL support today if we couldn't get it even when OpenGL was the superior alternative?

---

### Post by murderslastcrow on 2009-10-14
I think it's fair to say Wikipedia's take is fairly non-biased and objective. [http://en.wikipedia.org/wiki/Comparison_of_OpenGL_and_Direct3D](http://en.wikipedia.org/wiki/Comparison_of_OpenGL_and_Direct3D)

It would seem that the big differences are of little consequence these days. I argue that, in the big picture, they're at feature-parity, except one is closed while the other is not.

If not for the XBOX or XBOX 360, I wonder if Direct X would still be used as frequently today. The main problem is that developers get Windows SDKs, which include Direct X, rather than choosing a cross-platform SDK by default.

It's just another way to keep people tied in.

---

### Post by VertexPusher on 2009-10-14
> **Frak said:**
> 4. It's newer and more up-to-date with hardware standards.
No, it is not.

[http://en.wikipedia.org/wiki/Comparison_of_OpenGL_and_Direct3D#Extensions](http://en.wikipedia.org/wiki/Comparison_of_OpenGL_and_Direct3D#Extensions)

OpenGL is always bleeding edge. Whenever graphics card vendors implement a new feature, it is accessible through OpenGL first, long before DirectX supports it.

This has quite a few interesting side effects. For example, when the first Shader Model 4.0 graphics cards hit the market, people were told that their new features required DirectX 10 and therefore an OS upgrade to Windows Vista. Of course this was nothing but a marketing scam. Windows XP is perfectly capable of showing "DirectX 10 effects" in games, as long as the game engine uses OpenGL instead of Direct3D.

---

### Post by Kazade on 2009-10-14
Wow, there is so much confusion in this thread!

Firstly, to clarify, DirectX is a combination of APIs that do many different things (handle input, sound, graphics, 3D math, resource loading etc. etc.). Direct3D is the graphics API component. OpenGL is a graphics API. Let's compare Apples to Apples here.

Secondly, OpenGL controls the same hardware as Direct3D, differences in performance will come down to how the programmer has used the API, the quality of the drivers, and what features each API has exposed to the programmer. 

OpenGL did stagnate a little after OpenGL 2.0 (introduction of GLSL) and remaining backwards compatible did cause quite a bit of cruft to build up. This didn't make it "slower" than D3D, but it did make it a little more difficult for programmers to find the "fast path" of rendering (e.g. which API calls are slower than others). OpenGL continued to be up-to-date through extensions developed by the people making the GPUs (nvidia, ati, intel etc.), so you could always access the latest functionality.

The cruft was pretty much rectified overnight with the changes in OpenGL 3.0 which actively started deprecating features. GL 3.1 and 3.2 continued using this new deprecation model. So if you avoid the deprecated stuff, you get to use a lean, mean API for graphics. In OpenGL 3.2 you have to go out of your way to use the old, slow API calls. 

D3D and OGL are different APIs but they do the same thing. The BIG difference is that OGL is cross-platform, and D3D isn't (well, unless you include Wine's implementation, or XBox).

There are 3 main reasons that games developers aren't using OpenGL over D3D:

1.) The rest of DX gives them some neat tools to work with. Everything works together.
2.) Legacy. Games cost a lot, they have their workflows and engines. It would cost a lot to change for minimal market gain.
3.) Support. They go direct to MS when there is a problem.

This is not about performance, quality or technical merits of the API, it's just business.

OpenGL can be partnered with SDL, OpenAL, etc. to get similar functionality as the whole DX API and it will work everywhere. That's the way to go if you want to reach a bigger audience IMO.

---

### Post by Simian Man on 2009-10-14
> **toupeiro said:**
> Some people have hit on it, but basically, openGL running slow on windows is Microsofts doing.  I support a lot of 64-bit linux desktop doing heavy 3d modeling and it's 100% OpenGL.  In areas where the applications are cross-platform, Linux is ALWAYS the platform of choice for performance.

No, Microsoft hasn't done anything to slow down OpenGL on Windows.  There were a lot of rumors leading to the release of Vista that the new Windows graphics model wouldn't allow OpenGL to talk directly to the hardware, but it turned out to be completely untrue.  OpenGL is almost totally implemented directly by your graphics cards driver and by the chipset itself.  If OpenGL is slow on Windows, it's because of your graphics driver, *not* Microsoft.  The problem is that graphics drivers for Windows, especially ATI historically, have concentrated more on the D3D pipeline than the OpenGL one.

After that Microsoft defense, time for some criticism :).

> The cruft was pretty much rectified overnight with the changes in OpenGL 3.0 which actively started deprecating features. GL 3.1 and 3.2 continued using this new deprecation model. So if you avoid the deprecated stuff, you get to use a lean, mean API for graphics. In OpenGL 3.2 you have to go out of your way to use the old, slow API calls.

That is all well and good, but the Windows headers and libs do not support OpenGL 3 yet and likely won't for a long, long time (if ever).  Microsoft hasn't actively interfered with OpenGL on Windows, but they have passively let it stagnate by not updating the development libraries.

If you want to target OpenGL 3.x on Windows, you still need to go through the extension system for a good portion of the functionality.  So it is still much harder to use in an efficient way than D3D is.  Though there are libraries like glew and glee to make this doable.

Basically the problem boils down to D3D working well with a lot of features out of the box vs. OpenGL which needs a lot of work arounds or 3rd party libraries to get the same thing.  If you only cared about Windows anyway, it's an easy decision.  Really the only thing OGL really has going for it is that it's cross-platform.  I think a better OpenGL will come after Windows dominance wanes - not the other way around.

BTW if I were to write a 3D game, I would for sure use an existing graphics engine like [Ogre]("http://en.wikipedia.org/wiki/OGRE") or [Irrlicht]("http://en.wikipedia.org/wiki/Irrlicht_Engine") that support both OpenGL and Direct3D on a variety of platforms.  They have already dealt with the disparities between the two libraries.

---

### Post by Frak on 2009-10-14
> **VertexPusher said:**
> No, it is not.

[http://en.wikipedia.org/wiki/Comparison_of_OpenGL_and_Direct3D#Extensions](http://en.wikipedia.org/wiki/Comparison_of_OpenGL_and_Direct3D#Extensions)

OpenGL is always bleeding edge. Whenever graphics card vendors implement a new feature, it is accessible through OpenGL first, long before DirectX supports it.

This has quite a few interesting side effects. For example, when the first Shader Model 4.0 graphics cards hit the market, people were told that their new features required DirectX 10 and therefore an OS upgrade to Windows Vista. Of course this was nothing but a marketing scam. Windows XP is perfectly capable of showing "DirectX 10 effects" in games, as long as the game engine uses OpenGL instead of Direct3D.
They just did that recently.

Oh well, DirectX/Direct3D will lead the market for a LOOOOONG time to come. No message board will change that.

---

### Post by Slug71 on 2009-10-14
First off thanks for clearing this up.


> **Kazade said:**
> 
OpenGL can be partnered with SDL, OpenAL, etc. to get similar functionality as the whole DX API and it will work everywhere. That's the way to go if you want to reach a bigger audience IMO.

I wonder if this is how ReactX is being done? Since its open source it should be able to be ported to Linux.

Simian Man makes a good point about using Ogre and/or Irrlicht though.

---

### Post by Kazade on 2009-10-14
> **Simian Man said:**
> 
That is all well and good, but the Windows headers and libs do not support OpenGL 3 yet and likely won't for a long, long time (if ever).  Microsoft hasn't actively interfered with OpenGL on Windows, but they have passively let it stagnate by not updating the development libraries.


That is true.. but...

> 
If you want to target OpenGL 3.x on Windows, you still need to go through the extension system for a good portion of the functionality.  So it is still much harder to use in an efficient way than D3D is.  Though there are libraries like glew and glee to make this doable.


Glew and GLee make the whole thing transparent. Just include <glee.h> rather than <gl.h> and that's it. Then you have access to all the extensions. It's so easy, it's not even worth worrying about.

> 
Basically the problem boils down to D3D working well with a lot of features out of the box vs. OpenGL which needs a lot of work arounds or 3rd party libraries to get the same thing.  


You mean, including glew/glee? Hardy a *lot* of workrounds.

> 
If you only cared about Windows anyway, it's an easy decision.  Really the only thing OGL really has going for it is that it's cross-platform.  I think a better OpenGL will come after Windows dominance wanes - not the other way around.


True. If all you cared about was Windows, then use DX. But, you instantly rule out OSX and Linux distros, and their market sharing is increasing (something like 5-10% between them, so what, nearly 1 in 10 potential customers gone from the start).

> 
BTW if I were to write a 3D game, I would for sure use an existing graphics engine like [Ogre]("http://en.wikipedia.org/wiki/OGRE") or [Irrlicht]("http://en.wikipedia.org/wiki/Irrlicht_Engine") that support both OpenGL and Direct3D on a variety of platforms.  They have already dealt with the disparities between the two libraries.

+1. I'm talking more about big games developers building their own engines. Indie developers should definitely use an existing engine.

---

### Post by Slug71 on 2009-10-14
> **Kazade said:**
> 
OpenGL can be partnered with SDL, OpenAL, etc. to get similar functionality as the whole DX API and it will work everywhere. That's the way to go if you want to reach a bigger audience IMO.


This - Delta3D

[http://en.wikipedia.org/wiki/Delta3D](http://en.wikipedia.org/wiki/Delta3D)

---

### Post by Kazade on 2009-10-14
> **Slug71 said:**
> 
I wonder if this is how ReactX is being done? Since its open source it should be able to be ported to Linux.

ReactX, last I heard, has stalled. And no, it won't work using OpenGL etc. ReactX was/is going to use the underlying, low level NT kernel calls to do everything in the same way as DirectX does.

Any Direct3D implementation on Linux would be a Gallium3D state tracker (Wine already does what you said and wraps D3D to OpenGL calls, so really, WineD3D *is* a Linux implementation of Direct3D, it just goes through an extra layer).

---

### Post by Simian Man on 2009-10-14
> **Kazade said:**
> Glew and GLee make the whole thing transparent. Just include <glee.h> rather than <gl.h> and that's it. Then you have access to all the extensions. It's so easy, it's not even worth worrying about.
You are right, those libraries are awesome, that's true, but there is still the issue of what to do if the extension is not supported.  Do you bail out or create two render paths, one that uses the nice extension feature and one that doesn't?

With Direct3D it is kind of simpler because you just target a particular version of the library and any features that aren't implemented in hardware are emulated by the library.

> **Kazade said:**
> 
You mean, including glew/glee? Hardy a *lot* of workrounds.

Well there is that but there are also other issues.  Do you want to load a texture from an image file?  Then you need a library for that (SDL_image is good if you are using SDL, SOIL is good as well).  Do you want to display some text?  Then you need a library for that (I have used FTGL which worked OK).  D3D gives you these things for free.

> **Kazade said:**
> 
True. If all you cared about was Windows, then use DX. But, you instantly rule out OSX and Linux distros, and their market sharing is increasing (something like 5-10% between them, so what, nearly 1 in 10 potential customers gone from the start).
Yeah I agree with you.  *I* care about Linux a lot and would never work on a Windows only project.  But at the current time, for a big game company, a lot more than 90% of their market has a Windows machine.  A few people I work with are into hardcore games and are also Linux enthusiasts.  They play a few Linux games, but all of them have a windows machine and/or dual boot as well.

It's a shame because it's kind of a chicken and the egg situation :(.


[quote=Slug71]
This - Delta3D

[http://en.wikipedia.org/wiki/Delta3D](http://en.wikipedia.org/wiki/Delta3D)[/quote]
Wow, that actually looks pretty cool, I can't believe I've never heard of this before.

---

### Post by Kazade on 2009-10-14
> **Simian Man said:**
> 
It's a shame because it's kind of a chicken and the egg situation :(.

There are two ways out of this:

1. Wine (short term)
2. A D3D Gallium state tracker (long term)

Wine's D3D is getting bloody brilliant, and soon it will support DX 10! It won't be long before we can buy Windows games and be confident they will run to some extent under Wine.

Wine's D3D implementation is still a wrapper around GL though, but the real solution to this is to write a D3D state tracker, in combination with the test suite that Wine is building up, we could actually have a native D3D implementation on Linux in the next 5 years. 

I know that a lot of people have had bad experiences with Wine, but over the last year things have really stepped up a gear.

---

### Post by Slug71 on 2009-10-14
> **Slug71 said:**
> This - Delta3D

[http://en.wikipedia.org/wiki/Delta3D](http://en.wikipedia.org/wiki/Delta3D)

Would be nice if there was a .deb or PPA for this though. Or better yet if it were in the repos.

---

### Post by graabein on 2009-10-17
> **Simian Man said:**
> Virtually all of OpenGL is implemented in your graphics cards video drivers which aren't written by Microsoft at all...so yeah you're way off base here.

There was some noise when Microsoft released Vista that OpenGL was not fully supported or ran on top of DirectX which seriously reduced the performance... thus making developers pick DirectX over OpenGL, delivering another blow to an open industry standard, vendor lock in, blah blah same old song and dance, just google it man. Maybe they fixed it later when some damage was done.



On the chicken and egg situation - try open standards.

---

### Post by Npl on 2009-10-17
> **graabein said:**
> There was some noise when Microsoft released Vista that OpenGL was not fully supported or ran on top of DirectX which seriously reduced the performance...Only by those who fail to understand that this was only the case if you had no opengl-driver specific to your GFX-Card - then Vista will emulate it via Direct3D - and big surprise this was slower than using native D3D
> **graabein said:**
> thus making developers pick DirectX over OpenGL, delivering another blow to an open industry standard, vendor lock in, blah blah same old song and dance, just google it man. Maybe they fixed it later when some damage was done.Why don't you provide references before your conspiracy theories? How likely is it that all gamedevs are oppressed or part of the conspiracy as none of them favors OpenGL over Direct3D.

Just read what developers have to say about OpenGL: [http://www.gamedev.net/community/forums/topic.asp?topic_id=504547&PageSize=25&WhichPage=1]("http://www.gamedev.net/community/forums/topic.asp?topic_id=504547&PageSize=25&WhichPage=1")

---

### Post by blueturtl on 2009-10-17
On the lighter side:
[Hitler Not Impressed with OpenGL 3]("http://www.youtube.com/watch?v=sddv3d-w5p4")

No but thanks for the people in the above posts for explaining the situation more clearly. I actually thought OpenGL was playing feature-catch-up.

---

### Post by Xbehave on 2009-10-17
> **blueturtl said:**
> On the lighter side:
[Hitler Not Impressed with OpenGL 3]("http://www.youtube.com/watch?v=sddv3d-w5p4")
LoL, 

Having seen the depreciation stuff explained pretty well somewhere, am i the only one that thinks its a good idea? The problem with openGL was that there were so many calls it was hard to figure out which to use, now its clear, yet there is no need to break old apps. Additionally you are free to implement just part/use of the spec. I mean I see the point people make about leaving 2.2 for CAD stuff and making 3.0 forward looking and game orientated (something like 2.4 still being around while 2.6 is where new stuff goes), but I don't understand where the hate comes from because something has features you don't use (especially APIs where if you don't call a function it's like its not there).

Oh and for the record my middle name is Manuel and i know nothing (especially about game development / graphics), so i really am looking for information not an argument.

---

### Post by Simian Man on 2009-10-17
> **graabein said:**
> There was some noise when Microsoft released Vista that OpenGL was not fully supported or ran on top of DirectX which seriously reduced the performance... thus making developers pick DirectX over OpenGL, delivering another blow to an open industry standard, vendor lock in, blah blah same old song and dance, just google it man. Maybe they fixed it later when some damage was done.

It was just that, noise.  Those rumors existed prior to the release of Vista and were never based off any kind of reality.  It's funny how people can remember a rumor (over three years later) than the actual truth of the situation!

---

### Post by phrostbyte on 2009-10-17
OpenGL is a graphical API, DirectX is much bigger. You might compare OpenGL to Direct3D.

There is other libraries which are used with OpenGL like:

OpenAL - Open Audio Library
OpenCL - Open Computing Language
OpenML - Open Media Library
OpenGL ES - Open Graphics Library for Embedded Systems <-- this one is widely popular in smartphones eg, iPhone, Symbian, or Android.


OpenGL is the primary 3D graphics API for Linux and Mac OS X, but is also supported on Windows. OpenGL is created by a consortium similar to the W3C, which included Nvidia, Intel, AMD.


[URL="http://en.wikipedia.org/wiki/Gallium3D"]
Gallium3D[/URL] is a project to which will decouple  OpenGL from the video drivers in Linux. So it may be possible that Direct3D will be a native API in Linux in the future, alongside OpenGL.

Also there are high level scene graphs like [Ogre3D]("http://www.ogre3d.org") or [Open Scene Graph]("http://www.openscenegraph.org/projects/osg") which provide a very high level API to OpenGL and/or Direct3D. Using Gallium3D, these may also become first class graphics API.

---

### Post by graabein on 2009-10-18
You know the story about crying wolf huh? Being sceptical about Microsoft's doings is hardly conspiracy theories but whatever man. In this case I could have checked up on the story I heard about OpenGL and DirectX but I figured it was more of the same. Sorry about that.

---

### Post by toupeiro on 2009-10-18
> **Simian Man said:**
> No, Microsoft hasn't done anything to slow down OpenGL on Windows.  There were a lot of rumors leading to the release of Vista that the new Windows graphics model wouldn't allow OpenGL to talk directly to the hardware, but it turned out to be completely untrue.  



Actually, you are wrong.  I worked with different 3rd party vendors for a better part of a year while they re-worked the way their whole graphics engine worked for their application because the the way Vista would not allow OpenGL to talk directly to the hardware. Some applications are only just now able to release version that are supported on Vista because of how much work this took to accomplish. Its a fact that some Framebuffer addresses were completely restricted by Microsoft to appease the MPAA because those same video framebuffer addresses *could* also be used to bypass encryption to rip DVD's.  Well, they went overboard and restricted way more than they needed to.  Any application which tried to use these specific framebuffer addresses would have to completely rewrite their software. And quite honestly, it still is not as fast as Linux.  I've yet to see one instance where OpenGL on 64-bit Windows outperformed, or even matched, 64-bit Linux with identical hardware.  

I'm not saying it won't ever be done.  I am saying with the vendors I've worked with are pretty big players in the enterprise software market as it relates to graphics, and it hasn't been done there yet.

---

