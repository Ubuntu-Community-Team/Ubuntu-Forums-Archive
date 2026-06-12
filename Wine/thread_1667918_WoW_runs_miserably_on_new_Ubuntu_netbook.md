---
title: "WoW runs miserably on new Ubuntu netbook"
date: 2011-01-15
forum: Wine
---

### Post by ericsimmons on 2011-01-15
I am new to Ubuntu and running 10.04.

I installed Wine and am running WOW on a brand new 1.5 ghz / 2 gig ram netbook.

FPS is sooo bad, it's like .2 fps in starting zones. It's utterly ridiculous and the specs should be able to handle it. I don't understand what could be the problem.

Any ideas?

---

### Post by I8NY on 2011-01-15
2 things: is the restricted graphics driver installed? and does it have intel sucky graphics?

---

### Post by ericsimmons on 2011-01-15
Intel GMA 3150 graphics. I don't know the answer to the other question

---

### Post by NightwishFan on 2011-01-15
World Of Warcraft is not supported by Blizzard (but generally works) on Linux/Wine platforms. The problem is Wine generally does not work well with Intel graphics, try Nvida for good results.

---

### Post by ericsimmons on 2011-01-15
Well since we have established that Wine can't work with Intel graphics, I am still left with the problem of wanting to run WOW on this netbook. What are my other options for running WOW in Ubuntu?

---

### Post by I8NY on 2011-01-15
You need the graphics card/chip driver to do 3D games to start.  You can check to see if you can install it or already of it in System>Administration>Additional Driver.  Since it is intel graphics they don't have enough power to run modern games or even some old games at a descent frame rate.  A netbook was not made for gaming so don't try too hard trying to get it to run games. (2D ones are fine)

---

### Post by Elfy on 2011-01-15
move to wine forum

---

### Post by cwwilson721 on 2011-01-15
> **ericsimmons said:**
> Well since we have established that Wine can't work with Intel graphics, I am still left with the problem of wanting to run WOW on this netbook. What are my other options for running WOW in Ubuntu?Short answer:None

Long answer: NNoonnee

---

### Post by wog on 2011-01-15
I got better frame rates after I turned off the virtual desktop. Of course, it's still a little on the slow side, and it takes over all my virtual screens when it runs (all wine apps do, apparently), but at least I can run and play it.

---

### Post by NightwishFan on 2011-01-15
Yeah, run Wine games without compiz/unity running, use fluxbox or normal Gnome without desktop effects. With Intel you will not get far I think it has something to do with the way Wine allocates GPU memory and shaders, it works best with Nvidia.

---

### Post by cwwilson721 on 2011-01-16
> **NightwishFan said:**
> Yeah, run Wine games without compiz/unity running, use fluxbox or normal Gnome without desktop effects. With Intel you will not get far I think it has something to do with the way Wine allocates GPU memory and shaders, it works best with Nvidia.It's NOT "the way wine allocates" ANYTHING.

It's the sub-par implementation of opengl in the Intel chip and the drivers.

Newest Intel graphics can run the game (The newest Intel CPUs aren't bad), but overall, Intel + WoW + wine = TERRIBLE.

Since it's a combo of hardware and drivers, you're fairly up the creek. About all you can do about it is:

[LIST]
[*]Turn off Compiz
[*]Use opengl
[*]Turn EVERYTHING as low as possible
[*]Even turn off sound.
[/LIST]
For how to do all of the above, search this forum. TONS of posts about all of it.

Even your Intel issue.

Could've saved yourself a bunch of time by searching first.

---

### Post by NightwishFan on 2011-01-16
> It's NOT "the way wine allocates" ANYTHING.

Hey why the heck are you yelling at me. I know it is Intel or it would work evenly on all drivers, hence why I recommended Nvidia. I am a full time Intel gpu user I know full well it gives me less than nothing.

I cant find the article, but I know for a fact there is only so many blocks of something on the gpu, and wine needs to allocate so many for some use, and games think all of them are free. If I find it I will tell you.

---

### Post by cwwilson721 on 2011-01-16
> **NightwishFan said:**
> [COLOR="Red"]Hey why the heck are you yelling at me.[/COLOR] I know it is Intel or it would work evenly on all drivers, hence why I recommended Nvidia. I am a full time Intel gpu user I know full well it gives me less than nothing.

I cant find the article, but I know for a fact there is only so many blocks of something on the gpu, and wine needs to allocate so many for some use, and games think all of them are free. If I find it I will tell you.
Because you're wrong. The issue is NOT wine, it is lousy opengl implementaion of the chip and driver. wine just *uses* opengl. It doesn't *control* the hardware.

---

### Post by NightwishFan on 2011-01-16
I am not wrong. Wine converts DirectX calls to OpenGL. That is not just "using opengl". When I find the article I am linking to you just to prove you wrong and for now I am blocking you before I say something rude (but I certainly will not regret). See I can be an uncultured nasty person as well. Why not PROVE your statement?

You will not go far in life spouting random nonsense and treating people like they are children. You have to give respect to receive it.

---

### Post by darkknight045 on 2011-01-17
More to the heart of the matter, a netbook running a integrated GPU will struggle with 3D accelerated games such as WoW regardless of operating system.

Intel + Wine has rarely had anything but lackluster results and Wine (or some presentation layer over it) is your only option for running WoW on Linux.

The advice given above (disable compiz/metacity, and other misc. eyecandy) will squeeze some precious fps out of the game, but your hardware is holding you back more than Wine or your OS.

tl;dr; Netbooks aren't made for gaming, be it Windows or otherwise. They can do it but don't expect high performance.

---

### Post by basotl on 2011-01-18
> **ericsimmons said:**
> Intel GMA 3150 graphics.

A Google search and check of forums tells me that similar speced machines get a max of 15 fps w/ Windows when graphics are set to absolute minimum. 

Netbooks are not an ideal platform to game on... but if you are... at least get one of the ones with an ok GPU. I hear AMD has a few in the Netbook form factor.

---

### Post by a4able on 2011-01-18
first thing i tell you a netbook is not meant for gaming
its not the problem of ubuntu
i tried to install games on windows in my netbook it sucks
1.5ghz processor and all is not enough for gaming
also you have to think of one thing you are trying to install a wiindows application in another OS
wine is not a powerful tool
it has so many errors
normally softwares wont work correctly using wine
also pls check whether you have activated the additional drivers
if not activate it and take a try

---

### Post by 3razar3 on 2011-09-06
I am running it on a netbook with the 3150 1gb of ram and ubuntu 11.04 starting zones are a bit slow but its not as bad as that.. be sure to install the absolute latest mesa and intel graphics drivers it took most the day for me to hunt down stuff i needed in order to make it run but it does run a lot better now.. here is a link to the forum that contains the stuff i needed to add :

[http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)

i think the problem is that people thing just because wine adds windows support its going to be a cut and dry windows system and it isnt. if you want to run windows software 100% like windows, run windows. otherwise you need to take the time to search search search and expect lots of trouble in the process. remember: google is your friend.

for those complaining that its a hardware issue and there is no driver support think about how you are defeating yourself.. Drivers are SOFTWARE that allows the OS to communicate with hardware.. thus its not a hardware issue its a software issue.. where there's a will there IS a way

---

### Post by cwwilson721 on 2011-09-07
Windows will run WoW "okayish" on an Intel chip using D3D.

Linux/wine/OpenGL will, on VERY RARE OCCASIONS, get to run WoW at all on an Intel chip.

As far as "integrated" goes, wait on the new AMD 'APUs'. It will run WoW great.

Bottom line:

If you have Intel Graphics, forget about a reliable, playable WoW experience in Linux/wine. It will be BARELY usable in Windows.

---

### Post by _d_ on 2011-09-07
> **cwwilson721 said:**
> Windows will run WoW "okayish" on an Intel chip using D3D.

Linux/wine/OpenGL will, on VERY RARE OCCASIONS, get to run WoW at all on an Intel chip.

As far as "integrated" goes, wait on the new AMD 'APUs'. It will run WoW great.

Bottom line:

If you have Intel Graphics, forget about a reliable, playable WoW experience in Linux/wine. It will be BARELY usable in Windows.

Couldn't agree more here. My laptop is Intel integrated graphics and when playing WoW on Windows I would get ~25 FPS on lowest possible settings.

Now I tried that on Ubuntu (I believe it was back when 10.04 first came out), WoW was pretty much unplayable with only ~5 FPS.

---

### Post by Dlambert on 2011-09-08
> **ericsimmons said:**
> Well since we have established that Wine can't work with Intel graphics, I am still left with the problem of wanting to run WOW on this netbook. What are my other options for running WOW in Ubuntu?

[OK, here is the answer. Install FreeGLut. HERE = http://ubuntuforums.org/showthread.php?t=345177]("http://ubuntuforums.org/showthread.php?t=345177")

Then, configure wow

Data/En-us/

[LIST]
[*]Open Config.wtf (**note:** if you don’t have the file yet, login to the game once then logout)
[*]Add the following and save the file:Code:

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET ffxNetherWorld "0"
SET MasterSoundEffects "0"
SET SoundBufferSize "150"
SET SoundOutputSystem "1"
[/LIST]


Now configure Wine, wine regedit

then: 

[LIST]
[*]Go to HKEY_CURRENT_USER -> Software -> Wine
[*]Right click on the folder/key ‘Wine’, select ‘New’ then ‘Key’
[*]Name the newly created folder/key OpenGL
[*]Select the ‘OpenGL’ folder/key
[*]Right click on the empty space, select ‘New’ then ‘String Value’
[*]Name the newly created string value DisabledExtensions
[*]Right click on ‘DisabledExtensions’ and select ‘Modify’
[*]Enter GL_ARB_vertex_buffer_object
[/LIST]
Hope this helps!!!

---

### Post by Dlambert on 2011-09-10
Any success?

---

### Post by Dlambert on 2011-09-12
Bump

---

### Post by Dlambert on 2011-09-16
Bump

---

### Post by _d_ on 2011-09-16
> **Dlambert said:**
> Any success?

> **Dlambert said:**
> Bump

> **Dlambert said:**
> Bump

OP of this thread:
Last Activity: April 17th, 2011

---

### Post by Dlambert on 2011-09-16
Ok, well it would be nice to know the current state of his problem.

---

