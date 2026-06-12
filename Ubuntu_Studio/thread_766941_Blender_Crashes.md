---
title: "Blender Crashes"
date: 2008-04-25
forum: Ubuntu Studio
---

### Post by techolous on 2008-04-25
When I start blender and go into edit mode with a mesh, it crashes. The problem doesn't occur when I disable ati's drivers.

Im running Hardy (installed from the beta release disk, upgraded to current) on a 64 bit laptop with an ati card. Compiz was disabled, because it was causing issues with flickering opengl windows.

---

### Post by cotcot on 2008-04-25
Maybe you get some helpful information in terminal when you start blender from terminal. If it crashes it should give an error in terminal.

---

### Post by techolous on 2008-04-25
It just segfaults, no debug messages even with the '-d' option.

EDIT:
I wonder if getting a core dump would help...

---

### Post by Senesence on 2008-05-13
I don't get a crash in edit mode, but as soon as I start the game engine it segfaults in the same manner. Very ugly stuff.

<rant>
Things always break like this after a ubuntu upgrade. It's either one thing or another. Really, I view this phenomena as *the* downside to the open source (or rather "volunteer") development model.

Not very consistent, but then again, I guess that's the price of freedom. (should have known that there's a price :))
</rant>

---

### Post by chipster123 on 2008-07-19
I am having the same exact problem.
As soon as I upgraded from Gutsy to Hardy, Blender started crashing when I go into edit mode, with the fglrx driver selected in /etc/X11/xorg.conf

    Driver      "fglrx"

Here is what I have configured:
> % glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Radeon X1200 Series

% uname -a
Linux ubuntu 2.6.24-19-server #1 SMP Fri Jul 11 21:50:43 UTC 2008 x86_64 GNU/Linux

If I switch to 
   Driver    "ati"
then I get software rendering and Blender stops crashing, but then it too slow to be useful.


Here's the 'blender -d' output:

> station1:~> blender -d
Blender 2.46 (sub 0) Build
argv[0] = blender-bin
argv[1] = -d
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Color depth r 8 g 8 b 8
Aux buffers: 0
read file
  Version 245 sub 14
read file /home/chip/.B.blend
  Version 244 sub 0

ordered
 OBCube
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/chipster123/.blender/Bpymenus

Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Segmentation fault

Not much there.:(

---

