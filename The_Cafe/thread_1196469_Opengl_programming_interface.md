---
title: "Opengl programming interface"
date: 2009-06-25
forum: The Cafe
---

### Post by Aramil Moonmist on 2009-06-25
I wasn't sure where to put this, so feel free to move it if its in the wrong place. Also, ubuntu forums is the friendliest board I've been on, so I thought of asking here first.

The story starts about a month ago with me and my roommate trying to learn a bit of 3D programming. We started with opengl, tried direct3d and then we decided that opengl is just easier to comprehend. I'm using glut in c++ trying to figure it out. I have decent experience in c++, and oop, but had never done anything with graphics programming before. Unfortunately, there are a million and one horrendous tutorials out there (for both opengl and direct3d), but I managed to find a decent one. Most example code out there seems to be broken, versioned wrong, and some of them I'm sure I'm implementing wrong.

Skip forward a month. I haven't learned anything substantial (other than making a sweet spinning triforce). I haven't even figured out how to import a 3D object despite the 20 or so tutorials I've tried. I'd pretty much given up on the whole thing. Then I saw an article about clutter being an interface for programming 2D with opengl. I've looked around, but a few google searches hasn't turned up anything obvious. My question is; is there some 3D programming interface for opengl (or direct3d, I'm not picky) like clutter (but more powerful) that would make it a bit easier. I can usually figure most things out on my own, so complexity isn't a terribly large issue, but I'm just having a heck of a time with this.

---

### Post by DeadSuperHero on 2009-06-25
Well, it depends what you're looking for. There are many programming languages out there that have bindings for OpenGL. (For example, Python). Try looking for a good Python OpenGL engine, and set it up with an IDE (I have yet to find a particular favorite IDE yet, but Dr. Python and Codeblocks are both pretty decent)

Finally, have you considered building on top of existing engines with source code? I know the [OGRE project]("http://www.ogre3d.org/") lets you do something along those lines.

---

### Post by sim-value on 2009-06-25
SDL  is probably what you are looking for ..

there is a good tutorial at wikibooks

---

### Post by Kazade on 2009-06-25
Hi,

I believe Clutter is simply a 2D GUI interface that runs on top of OpenGL (although I may be wrong), so I don't think that is what you are looking for.

The OpenGL API isn't that difficult, it's the general concepts of graphics programming which are hard and they are going to take you some time to learn.

The first stage to using OpenGL is to create a "context". An OpenGL context stores the current state of everything in OpenGL (e.g. how the camera is set up, the textures that are loaded, where to find the vertex data etc.). Each platform (Windows, X11 etc.) has a specific way of setting up a context, but once the context is created all the OpenGL code (e.g. every function called beginning with "gl") acts in the same way.

Setting up an OpenGL window on your platform of choice is normally quite complicated. That is why people tend to use GLUT (for REALLY simple apps) or SDL for more complicated ones. I personally think you should go right for SDL, it's not that difficult.

Take a look at the "new lessons"[1] section on NeHe[2]. We are actually writing a whole new series (for OpenGL 3.1), but it will be a while before they are online. There aren't many "new" lessons, but they will get you started. If you have any questions, post in the NeHe forum, both myself and the other NeHe maintainer (Caste) visit it regularly and answer any questions we can.

A few things you will need to learn/brush up on to really get going with 3D graphics (no matter the API) are:

 1. Vectors (positions, velocities etc.)
 2. Matrices (multiplication mainly)

Hope that's of some help,

Luke.

[1] [http://nehe.gamedev.net/wiki/NewLessons.ashx](http://nehe.gamedev.net/wiki/NewLessons.ashx)
[2] [http://nehe.gamedev.net/](http://nehe.gamedev.net/)

---

### Post by Delever on 2009-06-25
This helped a lot:

[http://www.falloutsoftware.com/tutorials/gl/gl0.htm](http://www.falloutsoftware.com/tutorials/gl/gl0.htm)

And yeah, SDL is what finally helped to get hold of things.

---

### Post by jespdj on 2009-06-25
> **Aramil Moonmist said:**
> I wasn't sure where to put this, ...
The [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum would have been a better place than the Community Cafe.

---

### Post by cb951303 on 2009-06-25
If I understand you correctly you are looking for a 3d engine/framework?

[http://www.horde3d.org/](http://www.horde3d.org/)
[http://www.ogre3d.org/](http://www.ogre3d.org/)
[http://www.crystalspace3d.org/](http://www.crystalspace3d.org/)

---

### Post by Aramil Moonmist on 2009-06-25
> The Programming Talk forum would have been a better place than the Community Cafe.
My bad, I must have completely missed that one ><

Thank you all for the quick, helpful replies. I'll look into all of it, especially SDL because so many people mentioned it. I'll let you all know how it goes

---

### Post by Delever on 2009-06-26
> **Aramil Moonmist said:**
> My bad, I must have completely missed that one ><

Thank you all for the quick, helpful replies. I'll look into all of it, especially SDL because so many people mentioned it. I'll let you all know how it goes

We mention it because it huge portability problem already solved - [you can even use it with DirectX if you want]("http://www.gamedev.net/reference/articles/article2249.asp").

---

