---
title: "How do commercial 3D videogames work?"
date: 2005-11-04
forum: The Cafe
---

### Post by Zensunni on 2005-11-04
I never really thought about it, but I'm curious, how do 3d videogames work with your system? I know C+ is good for programming, but I don't see any commands like "display 3D environment". Most of the homemade programs I've seen just have if-then and print outputs. How do commercial applications do things like having their own windows and run complicated 3D invironments? I'm sure they might use C+ for the game's logic and variables...but what do they use to turn out such environments?

The only thing I can come up with is that that the program might actually just manually send color commands to each pixel, based on the running program's variables....but that seems a bit too manual.

There's gotta be some sort of smart hardware-to-software interface that a program exchanges with.

---

### Post by GeneralZod on 2005-11-04
Look into OpenGL, a cross-platform library that is very useful for 3D graphics.  DirectX is the other most-often used one, but is proprietary.

OpenGL has bindings to lots of languages; for example, TuxKart(?) is a 3D hardware-accelerated racing-game written in Python! :)

---

### Post by mpettitt on 2005-11-04
All C++. Honestly. The "hardware-to-software interface" is the graphics card driver, which takes polygons and turns them into pixels, using the GPU.
The trick, really, is to use a toolkit like OpenGL/Mesa which can take simple commands and convert them into the polygons that the GPU can handle. If you're interested in the details, take a look at some of the OpenGL text books that are around - "Interactive Computer Graphics with OpenGL" by Angel is my one of choice, but they are all pretty much covering the same ground.
A lot of commercial games use a custom developed engine which does the same basic task, along with wrapping it in an even more abstract layer, so you can do things like "if collide(x, y)" which is shorthand for "check what x is, and where all the components of it are, do the same for y, and see if any of them are in the same place".

But overall, it is just the same code. Sorry :-)

---

### Post by Zensunni on 2005-11-06
Ah, that makes more sense. Open GL (or other hardware-to-programs interfaces) handle commands thrown at them from programs that are coded in C++ (or python, etc).

I'd kind of like to try programming, but I know that I'd have to learn a full language before I tried making it interface with something like open GL. Still, I should look into it.

---

### Post by TravisNewman on 2005-11-06
Yeah I'd suggest not jumping into a game right away ;)

---

### Post by maruchan on 2005-11-06
> I'd kind of like to try programming, but I know that I'd have to learn a full language before I tried making it interface with something like open GL. Still, I should look into it.

[http://blender3d.org/cms/Features.155.0.html](http://blender3d.org/cms/Features.155.0.html)

You can make 3D games or other interactive stuff with Blender while you learn how to program. This would probably require some scripting, but there are tutorials and books available for this.

If you want to dive right in, go for OGRE: [http://www.ogre3d.org/](http://www.ogre3d.org/)  ...see this page for tutorials and such: [http://www.ogre3d.org/wiki/index.php/Main_Page](http://www.ogre3d.org/wiki/index.php/Main_Page)

Hope that helps.

---

### Post by Zensunni on 2005-11-09
Eh, wow, maruchan!

Ogre seems really cool. This is the side of development I like..... 'tis why I opted for web-development instead of harder stuff like C++.

I've played around with UT editor a little bit. Does the 3d rendering development work the same way?

---

### Post by Azriphale on 2005-11-18
C++? Hard? HAH!

Once you start playing with it a little (I recommend taking a short course or getting a book or something), it is actually a really really simple language. It makes sense. Provided the code you right conforms to the sense it makes. And, it is insanely powerful, as you get to know it more.

OpenGL is not terribly difficult either. Although that is not something I have used much at all, and not for a while. If you want to get into drawing stuff on the screen, I think OGRE is a very friendly API to work with. It also makes sense. Except I am still very much learning to use it. And I still need to get it to compile in Ubuntu.

---

