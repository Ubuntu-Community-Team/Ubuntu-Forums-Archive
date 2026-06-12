---
title: "Game Engine for Linux?"
date: 2009-02-23
forum: Ubuntu Studio
---

### Post by morty35 on 2009-02-23
Is there a linux based game engine that is close to as good as torque for 3D space battles.  We are looking at torque because of the price. The game engine needs to be able to handle large numbers of objects. The number is more important than the graphics abilities (however, the graphics need to be descent). It would also need to handle significant data processing for the AI.  One other large requirement is that it would have to handle large amounts of networking.

These are mostly the strengths of torque, but I wanted to know if there was a game engine that works on Linux that works as well.

---

### Post by Stochastic on 2009-02-23
Hmm, a quick google search pointed me to this 2006 thread: [http://www.linuxforums.org/forum/linux-programming-scripting/57964-good-free-game-engine.html](http://www.linuxforums.org/forum/linux-programming-scripting/57964-good-free-game-engine.html) which states > It also depends on what type of game you want to make.

There are excellent 3D engines available:
[http://www.ogre3d.org/](http://www.ogre3d.org/)
[http://www.crystalspace.org/](http://www.crystalspace.org/)
[http://irrlicht.sourceforge.net/](http://irrlicht.sourceforge.net/)
[http://luxina.de/](http://luxina.de/)

Perhaps you want something simple, 2D?
[http://openlegends.sourceforge.net/](http://openlegends.sourceforge.net/)
[http://www.pygame.org/](http://www.pygame.org/)
[http://www.libsdl.org/](http://www.libsdl.org/)
[http://www.clanlib.org/](http://www.clanlib.org/)
[http://www.talula.demon.co.uk/allegro/](http://www.talula.demon.co.uk/allegro/)

Or perhaps you have an exact type of game in mind and want an engine that caters specifically for it?
[http://gemrb.sourceforge.net/](http://gemrb.sourceforge.net/) (Baldur's Gate)
[http://www.fifengine.de/](http://www.fifengine.de/) (Fallout-like)
[http://www.stratagus.org/](http://www.stratagus.org/) (2D RTS)
[http://arrakis.sourceforge.net/](http://arrakis.sourceforge.net/) (2D RTS)

You need to be specific about requirements.
as well as points to a more detailed thread: [http://www.happypenguin.org/forums/viewtopic.php?t=2055](http://www.happypenguin.org/forums/viewtopic.php?t=2055)

Keep in mind all this is from 2006, so there's a good chance things have changed since then.

But in general, you probably won't find many game programmers in this section of Ubuntu Forums.  If you head to the Development & Programming section, you'll probably find more knowledge, or even to this Linux Game Development Forum: [http://www.happypenguin.org/forums/viewforum.php?f=7](http://www.happypenguin.org/forums/viewforum.php?f=7)

I really know nothing in this area, but if you run into any really impressive engines (particularly any that handle audio really well), please post back with your results.

---

### Post by ToasterThief on 2009-02-23
Take a look at ioquake3.
[http://ioquake3.org/](http://ioquake3.org/)

---

### Post by skullmunky on 2009-02-24
> **morty35 said:**
> Is there a linux based game engine that is close to as good as torque for 3D space battles.  We are looking at torque because of the price. The game engine needs to be able to handle large numbers of objects. The number is more important than the graphics abilities (however, the graphics need to be descent). It would also need to handle significant data processing for the AI.  One other large requirement is that it would have to handle large amounts of networking.

These are mostly the strengths of torque, but I wanted to know if there was a game engine that works on Linux that works as well.

Define "large numbers".  100's?  100,000's?

Since graphic quality & detail isn't as important as quantity, almost any game engine should be able to provide you with a fair number of entities.  they all have slightly different overheads in the graphics calls which will prob. become noticeable when you get up towards the millions of entities, but you'll hit network bottleneck far sooner.  

Check out "Angels Fall First", it's made in Panda3D and is maybe similar to what you want to do:

[http://ia.affuniverse.com/](http://ia.affuniverse.com/)

Ogre is the other engine I know a little about, it's known for render quality in particular but it usually gets kudos for efficiency too.  

Coding in C++ may give you some boost over coding in python, but again it may not.  My advice is to do network tests first, that'll set the real limit on number of things you can have running, then after that focus on optimizing your AI code; my guess is the AI is something you have to write (or SHOULD write) no matter what engine it is, and efficiency will be almost entirely dependent on how good your code is, not on implementation details in the engine.  

I've only had a little bit of (very painful) experience with Torque, and I didn't see any particular advantage over the myriad FOSS engines.

---

### Post by cb951303 on 2009-02-24
quick answer: if you're looking for a complete engine including the tools,editors etc.. no. torque is your best chance (unless you want to pay for unreal engine 3 :D)

detailed answer: I wouldn't use it. Ogre, Irrlicht or Crystal Space, with external tools and plugins can do a lot. Sure, you'll have to make it work but history shows that they are all capable of making great games.

Also, you can use them commercially. Irrlicht is licensed under zlib and the other 2 is LGPL. With zlib you can prety much do anything. With LGPL there is 2 point's that you have to pay attention.
1- If you want to keep your source code closed, you have to link LGPL libraries as shared libraries (DLL/SO). No static linking.
2- If you modify the original engine code, you have to release the modified code (only the modified code not your game's source)

PS: If you're doing an open source game you can ignore the above paragraph :D

---

### Post by kayosiii on 2009-02-25
We have had some success with Unigine -- With quite large scenes.... Still in beta and not cheap though.

We are also keeping our eye on Blender game engine.

---

