---
title: "Can I create 3D art in python ?"
date: 2009-12-23
forum: Ubuntu Studio
---

### Post by bobdobbs on 2009-12-23
Hi all.

I would like to create 3D art in python, and I'd like to know if this is possible, and where to start.

At the moment I know absolutely zilch about building 3D.

I've got to outcomes in mind: 3D imagery that can be modified in realtime, and abstract imagery that I can integrate into design projects.

Where should I start ?

---

### Post by cotcot on 2009-12-24
I probably do not understand your question as you mean it. Maybe some clarification with an example could help.

I guess you already found Blender (3D art and video editor) ? What I know with Blender is that you can use plugins written in Python.

---

### Post by skullmunky on 2009-12-24
There are a bunch of ways but most require you to know or learn a little bit about 3D.  

**panda3D** ([panda3d.org]("http://panda3d.org")) is a pretty powerful and easy-to-use engine in Python, though it's mostly based around modeling and animation in other packages like Blender and then creating interactive 3D and games.  it is possible to generate models from scratch but it's a little complicated.

**python-ogre** ([www.python-ogre.org]("http://python-ogre.org")) is a really powerful game engine which you can also use to generate forms from scratch but has a slightly higher learning curve.

**pyglet** ([pyglet.org]("http://www.pyglet.org")) is a lower-level python library which may be useful for you, it's essentially a way of using OpenGL from Python.

**processing** ([www.processing.org]("http://www.processing.org")) is not Python, it's Java, but it's a great tool for quickly getting started with programming 3D and other graphics things.

---

