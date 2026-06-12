---
title: "Game Development on Linux"
date: 2010-03-30
forum: The Cafe
---

### Post by MCVenom on 2010-03-30
Hey guys, I'd like to get a discussion going on *cross-platform* (Windows and Linux at the very least :p) game development on Linux. 

I was looking at game engines, and had pretty much settled on Torque3D. After all, I was planning to get into Torque long before I ever heard of Ubuntu, and it touts its cross-platform-ness pretty well, right? Well, it may be cross platform if you plan to develop your Linux game on Windows. Right now, there is no precompiled binary for Torque3D on Linux. And I'm trying to limit contact with my Vista partition as much as possible. :|
**/rant**

So I've decided to seek out, a capable, preferably FOSS and cross-platform set of tools for game development. Right now the clear winner to me seems to be putting together my own suite of tools around the OGRE rendering engine, maybe using Python-OGRE as a wrapper. I know I've chosen a rather more complex path than using an all-in-one solution like Torque, (especially for a beginner in game development) but I've decided its a path I definitely want to pursue. I think I'll start out in the Blender Game Engine though. ;)

What do you all think of OGRE? Of Blender? Of Linux game development in general? Inquiring minds want to know :P

---

### Post by Austin25 on 2010-03-30
I like games. I like linux. I therefore like linux games.

---

### Post by DeadSuperHero on 2010-03-30
I would recommend taking a look at [Syntensity]("http://www.syntensity.com/"). It's natively available for Linux, MacOS, and Windows, and is based on the Sauerbraten (Cube2) engine, with the exception that it focuses more on JavaScript (and is powered by the V8 engine in Google Chrome). 

You can create objects and models with Blender and import it right in (with some work), and it also ships with a built-in map editor. It's rapidly developing, and I think it's the perfect candidate for what you want to do.

Oh yeah, and it's all Free Software, so that should do it for you.

---

### Post by MCVenom on 2010-03-30
> **Mr. Psychopath said:**
> I would recommend taking a look at [Syntensity]("http://www.syntensity.com/"). It's natively available for Linux, MacOS, and Windows, and is based on the Sauerbraten (Cube2) engine, with the exception that it focuses more on JavaScript (and is powered by the V8 engine in Google Chrome). 

You can create objects and models with Blender and import it right in (with some work), and it also ships with a built-in map editor. It's rapidly developing, and I think it's the perfect candidate for what you want to do.

Oh yeah, and it's all Free Software, so that should do it for you.
Niiice.... I definitely liked what I saw. :D
Does anyone here have any experience with Syntensity? Other game engines?

---

### Post by MCVenom on 2010-03-30
Looks like the core Intensity engine is of more interest to me; its FOSS also of course and is better suited for single player games :D

---

### Post by Letrazzrot on 2010-03-30
Just to throw out some others that I know are cross-platform:

Irrlicht
Allegro
SDL
OpenAL

What kind of games are you interested in developing?

Also, if you are more of a beginner, then I wouldn't dwell too hard on this particular  decision, anyway. ;)  Use whatever seems to have the most documentation/tutorials.

---

### Post by DeadSuperHero on 2010-03-30
> **BlackOtaku said:**
> Looks like the core Intensity engine is of more interest to me; its FOSS also of course and is better suited for single player games :D
Actually, its original purpose was multiplayer, but it's becoming more and more possible to create single player games with it. According to a new development, it is possible to run in a sort of "standalone" mode, meaning the client no longer needs to connect to the Internet to run maps. Bundle everything together (models, objects, scripting, and whatnot), and you've got yourself a single-player game.

---

### Post by madjr on 2010-03-30
few other engines

[http://www.astahost.com/info.php/Top-Open-Source-3d-Engines_t19897.html](http://www.astahost.com/info.php/Top-Open-Source-3d-Engines_t19897.html)


well it's suggested that you program in 2d first and get comfortable  before hoping to 3d. At least if you want to become a real game developer you need to start from bottom up. From simple to complicated. i say this cuz lots of people just like to hop into editors and get stucked when it wont let them do certain things

you made any 2d or 2.5d games yet?

2d games don't get old anymore, just become classics

try to use cartoony style graphics and models for your first games, that way you dont need to have every detail perfect 

you may be interested in Rachel's tutorials (LusikkaMage)
[http://www.youtube.com/user/LusikkaMage](http://www.youtube.com/user/LusikkaMage)

shes really cool

have fun dude

---

### Post by MCVenom on 2010-03-30
> **Letrazzrot said:**
> Just to throw out some others that I know are cross-platform:

Irrlicht
Allegro
SDL
OpenAL

What kind of games are you interested in developing?

Also, if you are more of a beginner, then I wouldn't dwell too hard on this particular  decision, anyway. ;)  Use whatever seems to have the most documentation/tutorials.
Mostly third person platformers at this point. :D

And I have a rather well developed vision for a game I want to make, and I want it to be as perfect as possible; (much of this vision involves art, so the engine needs to be able to handle advanced graphics techniques as gracefully as possible) so I want to pick a development enviroment and engine that I can dig in and try to master it, knowing that it will have the capabilities that I need when I ultimately do get around to starting my 'masterpiece' :p

If its powerful, great with graphics, has at least somewhat mid-sized community and documentation, and a good chance of it still being around in the next few years, I'd like to look into it. ;)

---

### Post by DeadSuperHero on 2010-03-30
> **BlackOtaku said:**
> 
If its powerful, great with graphics, has at least somewhat mid-sized community and documentation, and a good chance of it still being around in the next few years, I'd like to look into it. ;)

The documentation on the [wiki]("http://wiki.syntensity.com/") is fairly robust.

---

### Post by MCVenom on 2010-03-30
> **madjr said:**
> well it's suggested that you program in 2d first and get comfortable  before hoping to 3d

you made any 2d or 2.5d games yet?

2d games don't get old anymore, just become classics

Yeah, a couple.

> try to use cartoony style graphics and models for your first games, that way you dont need to have every detail perfect 

...have fun dude
 That's the plan, thanks! :D

---

### Post by MCVenom on 2010-03-30
So far I'm split between the Intensity Engine and Irrlicht, any suggestions? :p

---

### Post by JDShu on 2010-03-30
Irrlicht looks like it has awesome documentation, so I personally would go for that. Then again, I'm still trying to make simple 2D games, so what do I know :P

---

### Post by madjr on 2010-03-30
> **BlackOtaku said:**
> So far I'm split between the Intensity Engine and Irrlicht, any suggestions? :p

you could get a feeling of both engines, like try them out for a few days, check out tutorials, vids , etc

then see which fits in better with your style

if not then you might miss a "killer feature" u may need

---

### Post by kripkenstein on 2010-04-01
> **BlackOtaku said:**
> So far I'm split between the Intensity Engine and Irrlicht, any suggestions? :p

Very different engines, useful for different things. Some points:
[LIST]
[*]Irrlicht is more general purpose
[*]Irrlicht has sound etc. modules, but they aren't FOSS
[*]The Intensity Engine specializes in fast-paced **multiplayer** games. Development is also optionally in multiplayer.
[*]Irrlicht doesn't have built-in scripting support (correct me if I'm wrong?), the Intensity Engine lets you script games in JavaScript and write plugins in Python.
[/LIST]

Disclaimer: I'm a dev on the Intensity Engine ;)

---

### Post by DeadSuperHero on 2010-04-01
> **kripkenstein said:**
> 
[LIST]
[*]The Intensity Engine specializes in fast-paced **multiplayer** games. Development is also optionally in multiplayer.
[/LIST]
 True, but I believe that the Intensity Engine is just as capable of doing a single-player standalone game. It's a very flexible engine, after all.

The only thing I dislike about the built-in map editor is that I still have to make object models in another program, rather than just being able to draw them in the editor itself. This is negligible though.

---

### Post by kripkenstein on 2010-04-02
> **Mr. Psychopath said:**
> [/LIST]
 True, but I believe that the Intensity Engine is just as capable of doing a single-player standalone game. It's a very flexible engine, after all.

Yeah, it certainly can. It might take a little setting up though, for that, but nothing serious.

---

