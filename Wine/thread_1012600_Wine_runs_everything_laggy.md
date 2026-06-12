---
title: "Wine runs everything laggy"
date: 2008-12-16
forum: Wine
---

### Post by coolethan on 2008-12-16
every windows program i run using Wine runs very slowly,could it be that windows programs inherently use more ram than ubuntu programs? i only have 500 Mb of ram in my computer which runs ubuntu 8.10 just fine but starcraft and programs like Mixcraft 4 are very laggy, i'm wondering if i should just get more ram, will this even solve the problem or is there another way?

---

### Post by masteryurez on 2008-12-16
> **coolethan said:**
> every windows program i run using Wine runs very slowly,could it be that windows programs inherently use more ram than ubuntu programs? i only have 500 Mb of ram in my computer which runs ubuntu 8.10 just fine but starcraft and programs like Mixcraft 4 are very laggy, i'm wondering if i should just get more ram, will this even solve the problem or is there another way?

If you have 512 Mb in RAM in your computer you really should get some more RAM. 512 MB is not very much at all. That´s the main reason that every game in WINE is lagging. 

The other reason that WINE is lagging is that you may have the wrong videodriver for your graphic-card. 
Open a terminal/console and write: 
```
glxgears
```and wait a few secounds. If the "movie" lagging you have the wrong driver for your graphic card. You will see your FPS (Frames per secound) in the terminal. 

I hope it will help a bit. 512 MB ram cost about $10 or something. 

//Yurez

---

### Post by donkyhotay on 2008-12-16
A program running with wine usually takes more ram then running natively in windows. Remember that you have an extra compatiblity layer running between linux and the windows program which is taking up some of your resources. Usually this isn't too bad but if you're low on RAM to begin with it can create lagging issues. I run starcraft on my system which runs 8.04 with 1gb of RAM and I don't have any lagging issues when playing.

---

### Post by doobiest on 2008-12-16
Re: glxgears.

When replying back also issue a glxinfo to see what's going on there, you should see something like this depending on what card you have.

display: :0  screen: 1
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:

Ram's a must too, also what type of proc is it? Might be worth checking out winehq.org or crossover's forums to see what people have to say about starcraft and wine.

---

### Post by coolethan on 2008-12-16
so the computer i have is basically a Frankenstein I built by rummaging and mooching all the stuff and the ram is just harvested from different old computers, it's running intel celeron III i think. glxgears did not lag whatsoever i got 400 fps and sometimes more. glx info looks like this

isplay: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
 
i will definately buy some more ram then i've been aware of how little i've had for a while and i've been meaning to do something about it but i didn't think it was such a huge deal till now. thanks a lot guys.

---

### Post by doobiest on 2008-12-16
I wouldnt expect glxgears to lag as long as you have direct rendering.

Me thinks that graphics card sucks though.  have you run any 3d accelerated linux games and what was the result like?   Perhaps install armagedtron or one of those games

---

### Post by YokoZar on 2008-12-16
> **donkyhotay said:**
> A program running with wine usually takes more ram then running natively in windows. Remember that you have an extra compatiblity layer running between linux and the windows program which is taking up some of your resources. Usually this isn't too bad but if you're low on RAM to begin with it can create lagging issues. I run starcraft on my system which runs 8.04 with 1gb of RAM and I don't have any lagging issues when playing.Wine itself has very little memory overhead - the entire program is only about 20 megabytes or so - far more important are things like the desktop environment, the window manager, and any other programs running.

There've already been a few benchmarks showing some memory-intensive nongraphical Ubuntu+Wine programs performing faster than Windows itself - this wouldn't be possible if there were an inherent bottleneck to using Wine.

---

### Post by coolethan on 2008-12-16
i have run open arena and it ran great. i'm using the graphics card that used to run dave mirra bmx and sims theme park and stuff so 3D graphics are not an issue.

---

### Post by doobiest on 2008-12-16
and starcraft is 2d right so that's wild.  

I dunno man have you checked over at winehq or crossover forums, they might have some notes on optimizing startcraft to play through wine.

It could be ram.. but starcraft is old school so I doubt it.

You could always run it, and while running it run top, vmstat, and iostat to collect info on system load.  Those three commands should give you the mem usage that wine/starcraft is using, the cpu load at the time and IO usage.

---

### Post by hikaricore on 2008-12-16
Unless I missed it you're not providing much info.
We need to know more about your system to assess the situation.

Just because your card performed well in Windows doesn't mean that your hardware
manufacturer even bothered making/making decent drivers for Linux.  What type of
video card are you using?  Which driver are you running?  Does the card/driver
have good OpenGL support?  Glxgears isn't really a great benchmark, but if you're
only getting 400fps I'm willing to be your video hardware is very lacking in what
it's capable of in the Linux environment.

Please provide as much info as possible and don't just assume.

---

### Post by doobiest on 2008-12-16
True True, But hey if he says open arena is running fine I assumed that meant on Linux.  And that's good enough for me, Openarena takes at least some power to run.

The other side is that since starcraft is not a 3d accelled game it's not really a good indicator, That's why I'm worried about mem/cpu usage.

Lastly instead of using wine you might want to see how well Stratagus works with starcraft.  Stratagus is an RTS engine that can import graphics/maps from warcraft and other games.  I'm pretty sure starcraft is supported but I dont have time to do much other than mention it

---

### Post by coolethan on 2008-12-16
> **hikaricore said:**
> Unless I missed it you're not providing much info.
We need to know more about your system to assess the situation.

Just because your card performed well in Windows doesn't mean that your hardware
manufacturer even bothered making/making decent drivers for Linux.  What type of
video card are you using?  Which driver are you running?  Does the card/driver
have good OpenGL support?  Glxgears isn't really a great benchmark, but if you're
only getting 400fps I'm willing to be your video hardware is very lacking in what
it's capable of in the Linux environment.

Please provide as much info as possible and don't just assume.
my vid card is a rage 128 and i'm not running any drivers I've never needed too. what is OpenGL?

---

### Post by doobiest on 2008-12-17
His GLX info shows SGI?  is that normal for a rage128?

---

### Post by coolethan on 2008-12-18
> **doobiest said:**
> I wouldn't expect glxgears to lag as long as you have direct rendering.

Me thinks that graphics card sucks though.  have you run any 3d accelerated linux games and what was the result like?   Perhaps install armagedtron or one of those games

well armagetron doesn't even want to work at all. i go to game then choose local and then the screen goes black and then it dissapears and i'm left looking at the desktop again unfulfilled and disappointed.

---

### Post by birddog165 on 2009-01-23
When I ran glxgears, this is what I got:
> XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 36 requests (36 known processed) with 0 events remaining.


What's going on here?

---

### Post by dardack on 2009-01-23
> **masteryurez said:**
> snip
I hope it will help a bit. 512 MB ram cost about $10 or something. 

//Yurez

I just picked up 2gigsx2 for $15 each on newegg.  Woot for 4gigs in a laptop.

---

### Post by hikaricore on 2009-01-23
> **birddog165 said:**
> When I ran glxgears, this is what I got:


What's going on here?

Something is wrong with your video drivers or they are not installed.

---

### Post by TyLLy_4 on 2011-03-06
> **coolethan said:**
> so the computer i have is basically a Frankenstein I built by rummaging and mooching all the stuff and the ram is just harvested from different old computers, it's running intel celeron III i think. glxgears did not lag whatsoever i got 400 fps and sometimes more. glx info looks like this

isplay: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
 
i will definately buy some more ram then i've been aware of how little i've had for a while and i've been meaning to do something about it but i didn't think it was such a huge deal till now. thanks a lot guys.

u Probably meant 400 frames per 5 seconds (if u look at the terminal) 
that translates into around 75 FPS .... withs its acceptable. 

My advice would be to check the MHZ of your ram. If you have ram sticks from several machines, you might have one of very low frequency (measured in MHZ) this low MHZ memory will make your whole system perform at that speed, so you would probably be better off .... anyways .... its always good to check. 

the sticks themselves should have some kind of sticker that says speed otherwise you can open terminal and type 
```
sudo lshw
```

and then look for the memory portion of your system info. 
witch should look like this. 
```
     *-memory:0
          description: System Memory
          physical id: 1
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR Synchronous **[COLOR="Red"]667 MHz [/COLOR]**(1.5 ns)
             physical id: 0
             slot: M1
             [COLOR="Red"]**size: 1GiB**[/COLOR]
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR Synchronous [COLOR="Red"]**667 MHz**[/COLOR] (1.5 ns)
             physical id: 1
             slot: M2
             [COLOR="Red"]**size: 1GiB**[/COLOR]
             width: 32 bits
             [COLOR="Red"]**clock: 667MHz**[/COLOR] (1.5ns)
```

Mine says that i have 2 sticks of 1 Gb each running at 667Mhz .... wich its actually a bad thing because my system uns at 800Mhz :( 

CRAP! i just realized too!

---

