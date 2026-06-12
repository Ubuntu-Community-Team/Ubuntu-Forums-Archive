---
title: "Program Control Of Blender Game Engine?"
date: 2009-01-29
forum: Ubuntu Studio
---

### Post by wkulecz on 2009-01-29
I'm new to Blender, but have succeeded in making trivial use of its Game Engine to move a cube in 3D space under arrow key commands.

What I'm doing, is evaluating if Blender could be used for some of our experiments where a signal from a motion base could be used to drive a visual scene.  A simple "Lear-Singer" motion based flight simulator would be a conceptual starting point (EDIT: as would most any Virtual Reality system), but we'd want to distort the scene motion in a known way relative to the physically expected view to study visual-vestibular, head-eye-hand interactions.

In terms of building blocks what seems missing to me is some way to drive the Blender scene with program outputs from the motion base (servo) controller instead of arrow keys or joystick device inputs, short of hacking the keyboard or joystick driver and making my program pretend to move the joystick or press keys.

The GE has a "message" sensor, but this seems to only be an internal communication to allow the output of one object motion, drive other objects for interaction.  I found a Python network messaging class in the Blender docs, I don't know Python, but the docs said it only "works for local loopback connections".

Using some of the Blender supplied examples and regression tests I'm pretty confidant that we can easily get high enough frame rates for the modest scene complexity we require.  Its the detail of driving the visual scene (game) from a program output instead of a human input that I'm stuck on.

Suggestions?  Better yet sample code that does such a thing.

I'm registering for the "Blender Artists" forum and will ask there as well.

TIA,
--wally.

---

### Post by skullmunky on 2009-01-29
the network connection would be a good, easy way to do it.  local loopback means it's a socket connection, but it's just used to connect two programs on the same machine rather than actually over a network.  this is a common way to connect apps together; in one common configuration, for example, you might have a program that reads Wiimote data, sends that over a network connection to Blender to control the game engine, which then sends more data over another network connection to control a sound engine, all on the same computer. 

Another example relevant to what you're doing would be something like TrackD or VRPN, which gather sensor and tracking data and then send it over a network connection to your visual simulation program.  

You could also look at Panda3D, VTK or OpenSG too for an app like this.

---

### Post by wkulecz on 2009-01-30
Thanks,

I should have mentioned I'm looking to use Blender to avoid spending ~$5K on another copy of Vizard, which is overkill for our needs.

TrackD appears to just change the problem from "how does my servo controller talk to the Blender Game Engine" to "how does my servo controller talk to TrackD".  Furthermore, Blender is not on their supported software list.

VPRN looks more interesting since source is available, but again it carries a lot of extra overhead to support devices I will not be using and again Blender is not on its list of used in applications.

It's looking like learning a little Python to run a script inside Blender to talk to my application might be the way to go.

OTOH, I'm now taking a look at Panda3D as an alternative to Blender.

--wally.

Edit:  Panda3D is a pure Python/C++ library where everything is built by programming.  I'd need to learn far too much Python, or work in C++ (which I hate, and use only if you put a gun to my head).  Worse I'd be the one stuck building all the models,  With Blender I can farm this task to someone with artistic skill, once I've linked a trivial scene to the motion controller.

---

### Post by wkulecz on 2009-01-30
I found a Blender Game Engine Script package called BZoo, [http://www.bzooworld.org/index.php](http://www.bzooworld.org/index.php) that has Python scripts to setup network connections (server and client) for networked game play.  Its far more elaborate that what I need, but it appears to have all the Pythonisms I will need to send data from my servo controller program to the BGE over a network socket to drive the visual scene.

--wally.

---

### Post by uuwatti on 2009-02-02
The [Wiring]("http://www.wiring.org.co") microcontroller supports blender. [Here's how.]("http://www.simonblackmore.net/notes/doku.php?id=wiring_to_blender")

---

### Post by wkulecz on 2009-03-25
> **uuwatti said:**
> The [Wiring]("http://www.wiring.org.co") microcontroller supports blender. [Here's how.]("http://www.simonblackmore.net/notes/doku.php?id=wiring_to_blender")

This is fine if you want to use RS-232 and a microcontroller.  I need to use a generic PC (could be Linux, Windows or Mac) and an Ethernet connection.

I found bits and pieces of info and put it all together using UDP in a simple sample blend file at: 
[http://blenderartists.org/forum/showthread.php?t=148861](http://blenderartists.org/forum/showthread.php?t=148861)

--wally.

---

### Post by skullmunky on 2009-04-08
@kulecz: so, my early reply was only theoretical ... within the last week I've started working on something similar in practice, going the wiimote->open sound control route.  searching for resources to help me reduce lag, I stumble back on this thread :)  glad to see you got something working - keep posting updates, this is very useful stuff!

---

### Post by kayosiii on 2009-04-10
Do a search on Blender + OSC... that will be your best place to start.

---

### Post by wkulecz on 2009-04-10
Yes I'd discovered OSC and it provided a piece to the puzzle.

Posted sample *.blend and python UDP driver sample at:
[http://blenderartists.org/forum/showthread.php?t=148861](http://blenderartists.org/forum/showthread.php?t=148861)

TCP vs UDP is a seperate issue, but for my applications UDP is the way to go, if you need do anything other than ignore errors and wait for the next frame update, TCP is the way to go as all you will end up doing is re-inventing a poor version of TCP.

--wally.

---

