---
title: "IDEs/applications for making games?"
date: 2007-06-26
forum: The Cafe
---

### Post by Extreme Coder on 2007-06-26
Hi, I have two things to ask:

- I used to code C/C++ sometime ago, but I almost forgot about it till now. 
I want to make games again, I want to know is there any IDE available for Linux specialized in game making? Or should I just use KDevelop, since I use KDE?
Also, what language do you recommend I use to develop games? One of the reasons I left C/C++ was frustration ;)

- A friend of mine wants to go Linux 100$, but on Windows he uses a program named Game Maker : [http://www.yoyogames.com/make](http://www.yoyogames.com/make)
It looks interesting, with all image/sound/map/level tools built-in and some coding support. But unfortunately, it's not available for Linux, and I looked on the web, and I couldn't find anything similar. Learning how to program is too much for him :/ Do you know of any similar program?


Thanks!

---

### Post by Extreme Coder on 2007-06-27
*bump*
Anyone?

---

### Post by Extreme Coder on 2007-06-27
*bumps again*

---

### Post by steven8 on 2007-06-27
This is not an IDE, but the Cube Engine is good and has a Linux port:

[http://www.cubeengine.com/cube.php4]("http://www.cubeengine.com/cube.php4")

---

### Post by Alterax on 2007-06-27
Well, I took a game programming class this past semester.  All of my work was done using the Anjuta IDE (Most of the class used Visual Studio except for the other linux geek that used KDevelop).  We all used the Irrlicht game engine API, which is available on Sourceforge.  It's not the best API, not good for a beginner in my opinion, but in its favor it is definitely powerful.  If you are doing 3d graphics, you may want to install Blender too (it's in the Ubuntu repositories)

Happy gaming!

--Alterax

---

### Post by Extreme Coder on 2007-06-27
While the Cube or Irrlicht engines sound nice, I was thinking of doing a 2D platformer or RPG at first. I guess I will use KDevelop and look for some tools for maps and such..
I read a bit, and people recommend Python or Ruby. Are they good for game dev?
And I still haven't found an alternative program to the one my friend uses :(

---

### Post by forrestcupp on 2007-06-27
IDEs are what you type the code in.  What you want is some kind of game engine.

For 3D I was starting to use Ogre.  It's multiplatform, and I can't back this up, but I think it is more powerful than Cube.  It seems to have a bigger backing anyway.

For 2D stuff, if you could learn Python, there is PyGame.  If you knew C++, Python will be a breeze.  It's an interpreted language, but I think with PyGame, you can still have a pretty good 2D game.

---

### Post by forrestcupp on 2007-06-27
> **Alterax said:**
> Well, I took a game programming class this past semester.  All of my work was done using the Anjuta IDE (Most of the class used Visual Studio except for the other linux geek that used KDevelop).  We all used the Irrlicht game engine API, which is available on Sourceforge.  It's not the best API, not good for a beginner in my opinion, but in its favor it is definitely powerful.  If you are doing 3d graphics, you may want to install Blender too (it's in the Ubuntu repositories)

Happy gaming!

--Alterax

Boy, are you serious?  I guess you're right that Irrlicht isn't good for a beginner *programmer*, but Irrlicht is the easiest 3D game engine I have ever seen.  It takes a very minimal amount of code to get a working environment with gravity and everything.  The reason I switched to Ogre is because Irrlicht isn't very customizable without actually changing their code and recompiling.  

By the way, I was using Irrlicht in Windows.  Is it cross-platform?

While Blender's built-in game engine isn't great, Blender is a must for creating 3D models.

---

### Post by Extreme Coder on 2007-06-27
> **forrestcupp said:**
> IDEs are what you type the code in.  What you want is some kind of game engine.

For 3D I was starting to use Ogre.  It's multiplatform, and I can't back this up, but I think it is more powerful than Cube.  It seems to have a bigger backing anyway.

For 2D stuff, if you could learn Python, there is PyGame.  If you knew C++, Python will be a breeze.  It's an interpreted language, but I think with PyGame, you can still have a pretty good 2D game.
Yes, I think I maybe meant a game engine, but with its own map editors and such. PyGame looks very interesting, I'll have a look. Do you know of any Python or PyGame tutorials?

I'll keep the 3D off my mind for sometime now.

---

### Post by forrestcupp on 2007-06-27
Just go to PyGame's website [here](http://www.pygame.org/news.html).  They have tutorials.  You'll need to learn Python first.  Just google python tutorial, and you'll find what you need.

If you use a game engine, 3D stuff isn't as hard as you would think.  In some cases it can actually be easier than programming some 2D stuff.  When I was using Windows, for a while I was learning to program 3D stuff using straight DirectX.  Now that's hard.  You have to do *everything* manually, and you pretty much have to brush up on all of your math and physics.  I think now-a-days the only reason people program with straight DirectX is to make game engine to make it easier on the people who want to make games in a reasonable amount of time.  I'd say it's probably the same with opengl, too.

---

### Post by Extreme Coder on 2007-06-27
Thanks! Just one more question though:
Are there are any tools for making maps or making game gfx?

Still no sign of an alternative to Game Maker..  I guess I will have to use VirtualBox or dual-boot him... :/

---

### Post by rksk16it on 2007-06-27
Do want to design a level and store it in a file and then load it up through a program or...design a level in some 'game-ide' like stuff ?

1. if former is the case, use **OGRE-3D** engine. It's scene-managers are **very** flexible and with the help of the ogre scripts you can easily load levels without recompiling your program. (I am not an ogre3d pro...but that is what they say on their website)

2. If latter is the case then go with Blender3D, its all-in-one (almost) kit where u can design, test and play...but i am afraid you have to read a few tutorials for that.

Good luck :popcorn:

---

### Post by Extreme Coder on 2007-06-27
> **rksk16it said:**
> Do want to design a level and store it in a file and then load it up through a program or...design a level in some 'game-ide' like stuff ?

1. if former is the case, use **OGRE-3D** engine. It's scene-managers are **very** flexible and with the help of the ogre scripts you can easily load levels without recompiling your program. (I am not an ogre3d pro...but that is what they say on their website)

2. If latter is the case then go with Blender3D, its all-in-one (almost) kit where u can design, test and play...but i am afraid you have to read a few tutorials for that.

Good luck :popcorn:
Thanks, but what I'm looking for is something similar but for 2D. I'd be really happy if I found something like Blender but for 2D.

---

### Post by steven8 on 2007-06-27
Java is good for 2d games.  Get NETBeans.  It's in the repository, and comes with a number of good example programs.

---

### Post by Extreme Coder on 2007-06-27
> **steven8 said:**
> Java is good for 2d games.  Get NETBeans.  It's in the repository, and comes with a number of good example programs.
But isn't Java harder to learn than C++?

---

### Post by forrestcupp on 2007-06-28
> **Extreme Coder said:**
> But isn't Java harder to learn than C++?

No.  I don't think you'll run into any modern language that's *harder* than C++, unless you try assembly.

My wife was dabbling in Java a while back, and it appeared to be pretty similar to C++ or C# (which is much easier than C++).

I guess the benefit of using Java over Python is that more people have Java installed.  Python is probably slightly easier to learn, though.

---

### Post by ebharv on 2008-02-11
> **Alterax said:**
> Well, I took a game programming class this past semester.  All of my work was done using the Anjuta IDE (Most of the class used Visual Studio except for the other linux geek that used KDevelop).  We all used the Irrlicht game engine API, which is available on Sourceforge.  It's not the best API, not good for a beginner in my opinion, but in its favor it is definitely powerful.  If you are doing 3d graphics, you may want to install Blender too (it's in the Ubuntu repositories)

Happy gaming!

--Alterax

How exactly did you set up Anjuta  to  user Irrlicht.  I did some of the Irrlicht tutorials when I was a Windows user :-(, and was able to set up a number of IDEs to use Irrlicht, but for some reason I can't set up Anjuta to use Irrlicht. I want to use Anjuta because it seems like a very powerful IDE.

---

### Post by Sslaxx on 2008-02-11
For whatever it'd be worth now, I am surprised nobody had mentioned [http://www.blitzmax.com/Products/blitzmax.php](http://www.blitzmax.com/Products/blitzmax.php) before...

---

### Post by Tobi-fp on 2008-02-11
Well, you could use blender.. It is a 3d animator.. but it has support for pythom programming

---

### Post by lobo-tuerto on 2008-05-10
Well, Irrlicht is perfect for beginners that want to start with game development. It's easy to use and has a very nice architecture.

I have put up a tutorial on setting up Ubuntu 8.04 + NetBeans 6.1 + Last version of Irrlicht from Subversion repository. I like NetBeans better than Anjuta. What might put you off is that the tutorials are written in spanish. But I bet you can follow the instructions pretty well.

[Irrlicht Tutorial #1: Hot to compile and install Irrlicht in Ubuntu 8.04]("http://lobotuerto.com/blog/2008/05/03/tutorial-1-de-irrlicht-como-compilar-e-instalar-irrlicht-en-ubuntu-804/")
[URL="http://lobotuerto.com/blog/2008/05/10/tutorial-2-de-irrlicht-como-configurar-netbeans-61-y-hacer-un-hola-mundo/"]
Irrlicht Tutorial #2: How to setup NetBeans 6.1 and our first Hello World Irrlicht application[/URL]

---

