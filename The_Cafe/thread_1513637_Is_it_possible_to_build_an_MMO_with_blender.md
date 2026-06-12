---
title: "Is it possible to build an MMO with blender?"
date: 2010-06-19
forum: The Cafe
---

### Post by Dustin2128 on 2010-06-19
I'm working on an open source mmo for linux users, and before I can start any of the actual computer design phase (I've got back-stories for everything and a nice plot) I need to make a choice. I'd like nice, 3D graphics and I know blender is an *excellent *3D modeling program, and better, it has a game engine. My question is, obviously, would it be possible to build an MMO with it? And if so, is a converted intel core 2 duo desktop with 100 Mb/s ethernet  and 1GB of ram sufficient for a 25-50 player server?

---

### Post by MarcusW on 2010-06-19
Sorry for making this post while not at all answering your question, but for a 3D engine I recommend ogre3d. Not at all hard to make the models in blender and exporting them to ogre either. :)

---

### Post by Dustin2128 on 2010-06-19
> **MarcusW said:**
> Sorry for making this post while not at all answering your question, but for a 3D engine I recommend ogre3d. Not at all hard to make the models in blender and exporting them to ogre either. :)
tell me more; how good a game engine is it? I want something with quality bordering warcraft or regnum.
EDIT: I looked at the website and I like it; but how customizable is the interface?

---

### Post by juancarlospaco on 2010-06-19
Blender, good, that can be the most beutifull **2-20F.P.S. **MMO.

*Also see Panda3D, python+psyco, fast coding, extremmely fast coding, easy migration to C++, should be faster than Blender*

---

### Post by Dustin2128 on 2010-06-20
> **juancarlospaco said:**
> Blender, good, that can be the most beutifull **2-20F.P.S. **MMO.

*Also see Panda3D, python+psyco, fast coding, extremmely fast coding, easy migration to C++, should be faster than Blender*
thanks for the recommendations. But why would blender produce a low framerate game?

---

### Post by juancarlospaco on 2010-06-20
*See YoFankie!*
I Dunno, but if these game, made by Blender Expert seems slow, 
i think its something with F.P.S., 
anyways is not designed for high performance games, is like an Engine,
there are projects to build an AutoCAD*-Like* app from Blender too.

---

### Post by Hman242 on 2010-06-20
I've heard Crystal Space(the engine) is really good.

---

### Post by MarcusW on 2010-06-20
> **Dustin2128 said:**
> tell me more; how good a game engine is it? I want something with quality bordering warcraft or regnum.
EDIT: I looked at the website and I like it; but how customizable is the interface?

It's not a game engine, it's a graphics engine (although I guesss it's really mostly used for games). It's really flexible, I think you can customize it basically however you want. I think the website is a better source of information than me, I can just say I really liked using it. :)

[http://www.ogre3d.org/about](http://www.ogre3d.org/about)

---

### Post by del_diablo on 2010-06-20
> **Dustin2128 said:**
> thanks for the recommendations. But why would blender produce a low framerate game?

Because its not a game engine.
Its more of a render engine, for testing.
I don't recommend OGRE, because setting up the export from blender is a pain.

---

### Post by mickie.kext on 2010-06-20
I guess you are talking about MMO RPG? 

Than it is best to look at Ryzom:

[http://www.ryzom.com/en/mmorpg-rpg-mmo-index.html](http://www.ryzom.com/en/mmorpg-rpg-mmo-index.html)
[http://dev.ryzom.com/news/13](http://dev.ryzom.com/news/13)
[http://dev.ryzom.com/](http://dev.ryzom.com/)

It have been opensourced under AGPLv3, but maps and data files are still proprietary. They could use help making new maps and story, so you could use Ryzom engine as a base. You didn't really mean to make everything from scratch, did you? It is a lot of work.

As for Blender, sure. It can be used. It is one of the best 3D programs out there and only non-standard UI is keeping it from getting more users. 

As for server... I think you could put one more 1GB stick of RAM. Otherwise it is ok.

---

### Post by kesten on 2011-11-15
This is a slightly old thread, but I have just started developing an MMORPG called Journey using Blender and Panda3d as the game engine.  Although it might be possible to build a blender game, the engine seems a bit weak right now.  So Panda3d or Ogre are good choices.
Panda3d uses the Bullet Physics engine, just like blender, so that's nice.
The game was originally developed by Douglas Knapp.  I'm now assisting.  If anyone is interested in learning MMORPG programming (servers, game engine), join the team.

kesten

---

### Post by BrokenKingpin on 2011-11-16
I would not recommend the blender game engine, but it would be a good fit for doing the 3d modeling.

What is your programming experience? If it is none, you might want to spend a decade or so learning how to code before moving onto something like an MMO. You will also need a **** ton of cash for the server infrastructure once the game is developed.

Seems like every kid who plays an MMO like WoW thinks they can make their own these days.

---

### Post by DangerOnTheRanger on 2011-11-16
> **BrokenKingpin said:**
> 
Seems like every kid who plays an MMO like WoW thinks they can make their own these days.

+1 to this, especially those who haven't programmed before.

---

### Post by JDShu on 2011-11-16
It should also be noted that MMORPG is probably the most difficult genre of game to make. The reason being that it's not just art and code, but requires a running infrastructure for people to use.

---

