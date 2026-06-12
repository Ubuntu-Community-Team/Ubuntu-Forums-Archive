---
title: "Ubuntu Gaming / Steam Proton / Vulkan / Etc."
date: 2019-04-05
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2019-04-05
Alright there Ubuntu peeps, let's talk gaming for a little bit.

The Linux community has been making great strides in finding new ways to assist the users who want to leave Windows, to adopting Linux (in general).

Steam and proton has made a huge step forward for Gamers.  Now... if we could only convince Adobe...

However, I have tried to run some of my titles from Steam on Kubuntu 18.10, and most of which run successfully.  However, they don't run as well as they do in Windows.  This makes for a hard adoption of Linux.  When you know all you have to do, is reboot into Windows and you get better performance.

But, my ultimate goal here, is to not use Windows at all.  So, what can be done to improve game performance in Linux?  What is Windows doing with certain titles that Linux cannot reproduce with Wine/Proton/DXVK and the like?

---

### Post by jdeca57 on 2019-04-05
The reason why people use computers are widely different. Personally I think that if gaming is a priority then  there are a lot of alternatives like an XBox that will get you a perfect performance, probably even better than a Windows experience. 

If you use an OS and want to run software that it wasn't designed to run in that OS then there can be, and probably will be glitches, like a lesser performance.

The only solution would be to have a larger paying user base on Linux but then again what Linux? Because there is Redhat/Fedora or Arch/Manjaro and a lot of others and then there is Debian/Ubuntu...

---

### Post by poorpockets-mcnewhold on 2019-04-06
OS wise, I think the best dedicated one would be the SteamOS, which can also been installed as a desktop, so you can run it from Kubuntu. The major reason for this one being it doesn’t load the desktop elements in the background, and mainly focus on loading Steam in Big Picture mode, so this should help a bit.
Kernel wise, that´s pretty useless, same thing with most distro tweaks that you might found, except the habitual installation of the latest Graphics Drivers and maybe some zram and other memory/energy management.

The main reason i would say that Wine/Proton/DXVK isn’t perfect yet, is that they’re quite a lot of things to handle, from games to others games. Different technologies to adapt, different ways to make the system works for the same processes. Quite ironically, the issue is that Linux isn't Windows, and doesn’t work the exact way as most developers expected when developing for Windows platforms.

---

### Post by Shibblet on 2019-04-08
> **poorpockets-mcnewhold said:**
> Quite ironically, the issue is that Linux isn't Windows, and doesn’t work the exact way as most developers expected when developing for Windows platforms.

It's interesting that you'd say that.

I have noticed that game performance for Native Linux games seem to not run as well as the same game in Windows.  A couple of specifics are Brutal Legend, and Witcher 2.  I have yet to give Tomb Raider a run in Kubuntu, but I will here soon just to run the in-game benchmark.

This is where I feel like I am doing something wrong...  Brutal Legend runs at 60+ fps in Windows, but can't get much over 45 in Kubuntu Linux.  I have tried disabling compositing when I run the game, but the improvement is hardly noticeable.  So, is my system configured correctly to run games?  Is this a code optimization problem that the developer failed to do?  Are my CPU and GPU running efficiently?

Inquiring minds want to know.  ;-)

---

### Post by Shibblet on 2019-04-09
So, I loaded up Tomb Raider (2013l Reboot) not Rise or Shadow.

This game performs almost identical to it's Windows counterpart.  The In-Game benchmark is reporting an average of ~90 fps (with vsync and AA turned off) on my GTX 780 ti, and i7-3770 processor.  So, what is causing other games like Brutal Legend to only run at around 30 fps in Linux?  Is there a frame-limiter or something?

---

### Post by poorpockets-mcnewhold on 2019-04-09
For Brütal Legend in itself, Yes, they’re a frame limiter (It’s not really set in purpose to limit PC game performance tho according to official reason) [https://steamcommunity.com/app/225260/discussions/0/846946588480253389/](https://steamcommunity.com/app/225260/discussions/0/846946588480253389/)
But other reasons might be the huge numbers of different parts that make the game run. The game engine, It’s dependencies, The engine technologies used for textures handling, antialliasing methods, sounds, SFX handling, physics and so on.
If I’ve remembered one particular case, the NVIDIA Hairfx technology was non-working for a long time on Linux, until updated video card drivers went to fix that issue. Sometimes, those issues need to be fixed by Proton/Wine, game modifications, diverse render engines adaptations or even fully ported open games engines.

---

### Post by mastablasta on 2019-04-10
wine is a not an emulator, but also it is also not direct windows implementation. many libraries are reverse engineered. so it would be like saying why don't linux games run as fast on windows as they do on linux. you can't really compare apples and oranges. so it would only be fair to focus here on linux games version vs windows game version. 

many things can and do go wrong in that case with linux. for example for me Battle for Wesnoth for an unknown reason decides to turn on inactive monitor when i switch to full screen. i don't even know how come it has the power to do that. but it does, and the game is opensource and practically form start runs on linux.

then there is wine which is hit or miss depending on the wine version, GPU drivers and other things. so we have wine ratings for that, but even those are quite innacurate. i installed Torchlight (Platinum rating) and it worked. i didn't even notice it is on linux. i then went to install UT2004 (platinum). well it couldn't handle resolution, it didn't capture mouse... few small tweaks and it all works. not as good as in windows (i have an very old PC) but it works. 

i felt quite good about it all so i decided to install Morrowind (Gold/Platinum) and Oblivion (platinum rating) . I installed morrowind before and i knew things worked well. but not this time. i couldn't even get it to start, so i had to use OpenMW to play it. which seems to work ok so far, but i can't use my old save games. I then wen't with oblivion. read it all on the wine website, then went for install. all goes well game doesn't start. for this i balem wine developers and maintainer of the app (who just gave the rating). wine developers are at fault here, because something that worked pretty much out of the box now doesn't work at all.

BTW Bethesda offered Morrowind for free for a limited time this or was it previous week?! and for OpenMW to work you need some original files and the engine is really nicely made with a lot of improvements over the original one.

off to linux games - i got a source bundle, got one game that was free (if i signed up to Humble bundle). all games so far work well. since i have an old PC i am not sure how different they would perform on windows. also to me if i can reach 30 FPS is more than enough for most games. i really can't see the difference between 30 or 60 or between 60 or 90. i messed around a lot with Farcry2 which should work well on my PC in windows, but didn't. in any case i noticed that difference between 23, 25 or 28 FPS is very noticeable to me, but between 30 or 60 it is not noticeable unless you have some huge FPS swings to get 30 average (eg. 50 fps and then 10 and then back to 50).
Bottom line Source engine games on my PC perform the same as on windows. Games that work well in wine also perform abot the same. 

if you check phoronix website you can get more information on the difference. sometimes (rarely though) linux performs better. this always happens when developers develop the game with linux in their mind. phoronix also has a otll you can use to compare performance in windows and linux on game engines.

finally, some games are made not only with certain OS on developers mind but also for certain GPU. so sometimes a game made for AMD gpu underperfoms on Nvidia. or nvidia had to make some tweaks to make it work just as well as on AMD. they might have made those tweaks for windows driver, but not ported it to linux. that way you would get a game that works well on windows but performs poorly on linux.

---

### Post by Shibblet on 2019-04-10
> **mastablasta said:**
> wine is a not an emulator, but also it is also not direct windows implementation. many libraries are reverse engineered. so it would be like saying why don't linux games run as fast on windows as they do on linux. you can't really compare apples and oranges. so it would only be fair to focus here on linux games version vs windows game version.

Which is what I did with Brutal Legend and Tomb Raider.  Linux version vs. Windows Version.  With Tomb Raider, it was almost exactly the same in both OS's.  Brutal Legend however, is neutered in the Linux version, and apparently has a 30fps frame rate limiter on it.  Not really sure what the reason is though...

> **mastablasta said:**
> many things can and do go wrong in that case with linux. for example for me Battle for Wesnoth for an unknown reason decides to turn on inactive monitor when i switch to full screen. i don't even know how come it has the power to do that. but it does, and the game is opensource and practically form start runs on linux.

then there is wine which is hit or miss depending on the wine version, GPU drivers and other things. so we have wine ratings for that, but even those are quite innacurate. i installed Torchlight (Platinum rating) and it worked. i didn't even notice it is on linux. i then went to install UT2004 (platinum). well it couldn't handle resolution, it didn't capture mouse... few small tweaks and it all works. not as good as in windows (i have an very old PC) but it works.

Yes.  When running Windows games on Linux, I can understand that the game will not always run properly.  This is why the title is "Ubuntu Gaming / Steam Proton / Vulkan / Etc."  Many of the Windows titles now run on Linux with Proton/DXVK/Wine and the like, but they don't always run as smoothly, and may have problems, like your Unreal Tournament 2004.  My question for you is... what did you tweak to get it working well?

> **mastablasta said:**
> i felt quite good about it all so i decided to install Morrowind (Gold/Platinum) and Oblivion (platinum rating) . I installed morrowind before and i knew things worked well. but not this time. i couldn't even get it to start, so i had to use OpenMW to play it. which seems to work ok so far, but i can't use my old save games. I then wen't with oblivion. read it all on the wine website, then went for install. all goes well game doesn't start. for this i balem wine developers and maintainer of the app (who just gave the rating). wine developers are at fault here, because something that worked pretty much out of the box now doesn't work at all.

I don't know if it's as easy as blaming the Wine developers.  It may have worked on other systems, or older versions of Wine...

> **mastablasta said:**
> BTW Bethesda offered Morrowind for free for a limited time this or was it previous week?! and for OpenMW to work you need some original files and the engine is really nicely made with a lot of improvements over the original one.

I have an embarrassing number of hours in Morrowind, Oblivion, and Skyrim.

> **mastablasta said:**
> off to linux games - i got a source bundle, got one game that was free (if i signed up to Humble bundle). all games so far work well. since i have an old PC i am not sure how different they would perform on windows. also to me if i can reach 30 FPS is more than enough for most games. i really can't see the difference between 30 or 60 or between 60 or 90. i messed around a lot with Farcry2 which should work well on my PC in windows, but didn't. in any case i noticed that difference between 23, 25 or 28 FPS is very noticeable to me, but between 30 or 60 it is not noticeable unless you have some huge FPS swings to get 30 average (eg. 50 fps and then 10 and then back to 50).
Bottom line Source engine games on my PC perform the same as on windows. Games that work well in wine also perform abot the same.

60fps is the sweet-spot / magic number.  Some people are okay with 30, and others want 120, but ultimately if games can run at 60, there will be less complaints.  Even Windows (Tweak) Gamers know that they need some hefty hardware to go over 60 on most games.  

> **mastablasta said:**
> if you check phoronix website you can get more information on the difference. sometimes (rarely though) linux performs better. this always happens when developers develop the game with linux in their mind. phoronix also has a otll you can use to compare performance in windows and linux on game engines.

Most of Phoronix's reviews tend to show Windows as the better performing OS for games. And many members of the Linux community will tell users to keep Windows if they want to play games.  That's my biggest problem.  I want to use Adobe Software, and play games...  Linux isn't really what I need.  I just really like it.

> **mastablasta said:**
> finally, some games are made not only with certain OS on developers mind but also for certain GPU. so sometimes a game made for AMD gpu underperfoms on Nvidia. or nvidia had to make some tweaks to make it work just as well as on AMD. they might have made those tweaks for windows driver, but not ported it to linux. that way you would get a game that works well on windows but performs poorly on linux.

Yep.  This was one of the largest problems from the gaming-get-go.  This is why OpenGL and DirectX were made, to help developers write for one API instead of directly for Hardware.  They say this is what ultimately killed the 3dfx cards.  Glide and such.  With Vulkan becoming more prominent, Valve has made the claim that Proton "should" be able to run all games that are made for Vulkan without issue.

My only question about Vulkan is:  If it will run on Linux without issue, than how much harder can it be to actually make a Linux port of the game?

---

### Post by mastablasta on 2019-04-11
> **Shibblet said:**
> 
Yes.  When running Windows games on Linux, I can understand that the game will not always run properly.  This is why the title is "Ubuntu Gaming / Steam Proton / Vulkan / Etc."  Many of the Windows titles now run on Linux with Proton/DXVK/Wine and the like, but they don't always run as smoothly, and may have problems, like your Unreal Tournament 2004.  My question for you is... what did you tweak to get it working well?
various wine settings (e.g. will it use the built in or native library), then game settings (e.g. change form directx rendering to opengl rendering)...

> 
I don't know if it's as easy as blaming the Wine developers.  It may have worked on other systems, or older versions of Wine...

well you can't blame the user if you rate the game platinum and then it doesn't work (even though hit did before) or need many tweaks to get it working. btw platinum was awarded on same wine version and OS that i used.

> 
Most of Phoronix's reviews tend to show Windows as the better performing OS for games. And many members of the Linux community will tell users to keep Windows if they want to play games.  That's my biggest problem.  I want to use Adobe Software, and play games...  Linux isn't really what I need.  I just really like it.

for some games the difference is really minimal. performance might still be better on windows, but aside from the exact data the user experience might be the same. i would advise windows for gaming mostly because they make games with windows in mind and for windows. even linux titles - they are not usually made at the same time.

> 
My only question about Vulkan is:  If it will run on Linux without issue, than how much harder can it be to actually make a Linux port of the game?

i don't know that much about Vulkan. i don't think my card is capable of using that tech. but in any case - if the engine is made for linux and the game uses that engine, then it is much easier to port it to linux or it might not even need any porting. you just need data. Unigine, UT4, old doom 3 engine, source and many others had or received linux version so games on those engines were mostly "ported" to linux. you can try it yourself with  Godot engine (if you feel like it). make a simple game on windows and port it.

problem is that engines like for example oblivion do not have a linux version. but often if they at least have good opengl support (later probably Vulcan) or if at least they don't use too much of the proprietary MS stuff they should work relatively well in wine.

---

