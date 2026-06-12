---
title: "3D applications won't run in Wine."
date: 2009-08-13
forum: Wine
---

### Post by constchar* on 2009-08-13
Hey,

Every time I run a 3D application in Wine it immediately exits and dumps this in console:
> 
james@jimmy:~/Downloads$ wine wglgears.exe
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  129 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  166
  Current serial number in output stream:  166


I'm using Wine 1.1.27 from the repository and I'm using the latest ATi Catalyst 9.7 driver (the card itself is a Radeon 4870 HD).
I've tried compiling Wine myself but I didn't see any difference, and it seems to do this with any application that uses OpenGL or Direct3D.

Thanks for any help.

---

### Post by hikaricore on 2009-08-13
Do any _native_ 3d applications work?
I've seen this exact X error in other threads and it was discovered to be an ATI driver issue.

---

### Post by constchar* on 2009-08-13
> **hikaricore said:**
> Do any _native_ 3d applications work?
I've seen this exact X error in other threads and it was discovered to be an ATI driver issue.

Yeah, native 3d applications work just fine, including Compiz.

---

### Post by NightMKoder on 2009-08-13
Try 1.1.25-26. (You can get them at [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) ) If it doesn't happen there, it may be due to the recent xrender patches (have been known to cause some problems)

---

### Post by constchar* on 2009-08-14
1.1.26 and earlier works, however it flickers really really bad.

---

### Post by andrea000 on 2009-08-16
you should be able to use winetricks to install
OpenGL and may be Direct3D i'm not sure about
that one download wine tricks [here]("http://wiki.winehq.org/winetricks")

---

### Post by NightMKoder on 2009-08-16
> **andrea000 said:**
> you should be able to use winetricks to install
OpenGL and may be Direct3D i'm not sure about
that one download wine tricks [here]("http://wiki.winehq.org/winetricks")

Sorry, but that's completely wrong. opengl is something handled by your operating system. as for direct3d, wine has it's own version of direct3d (written in opengl). The problems mr. C is having can't be solved by winetricks, but can be helped by latest drivers and wine 1.1.28.

---

### Post by hikaricore on 2009-08-16
Completely wrong is an understatement. >.>

---

### Post by andrea000 on 2009-08-17
sorry about that direct3d may take winetricks to install i dont know
but wine uses opengl already installed on your system i found that
out from the wine website so wine already runs openGL.So if direvt3d
written in opengl maybe you don't have openGL installed on ubuntu

look up these packages they used to install a linux version of opengl

OpenGL:
libgl1-mesa-dev

OpenGL extensions:
libglew1.4-dev

SDL:
libsdl1.2-dev

---

### Post by hikaricore on 2009-08-17
> **andrea000 said:**
> sorry about that direct3d may take winetricks to install i dont know
but wine uses opengl already installed on your system i found that
out from the wine website so wine already runs openGL

There is no circumstance where installing directx is required.
As most some users need 1 library from a dx install for very specific applications.
I think by this point even that is no longer true.

---

