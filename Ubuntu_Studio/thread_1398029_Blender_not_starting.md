---
title: "Blender not starting"
date: 2010-02-04
forum: Ubuntu Studio
---

### Post by Michael577 on 2010-02-04
Hey guys I'm trying to open blender but it didn't load so I did this in the command line and I got this 
                   michael@michael-desktop:~$ blender
Compiled with Python version 2.6.4.
Checking for installed Python... got it!
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  27
  Current serial number in output stream:  27
michael@michael-desktop:~$ 

I reinstalled this and I got the same thing does anyone know what's wrong?

---

### Post by LuridCinema on 2010-02-04
How did you install it? Compile it yourself , Sudo apt-get install, Synaptic or Ubuntu Software Repos ?
Might google how to best install on your version and even if anyonehad a problem w/ the same graphics card. Dounds like you have an X problem. have you tried the Fullscreen or Windowed startup ?

---

### Post by cotcot on 2010-02-04
Download blender from their website, extract the downloaded file and just run the executable in the extracted folder. No install required.

In somewhat earlier versions I had to switch off the visual effects because blender could not deal with transparency in its own windows. This seems to be solved in the latest version (2.49).

---

### Post by Michael577 on 2010-02-04
> **LuridCinema said:**
> How did you install it? Compile it yourself ,  Sudo apt-get install, Synaptic or Ubuntu Software Repos ?
Might google how to best install on your version and even if anyonehad a  problem w/ the same graphics card. Dounds like you have an X problem.  have you tried the Fullscreen or Windowed startup ?

I did a reinstall from synaptic, opened it from the downloaded file, nothing about the command line, and I originally got it though the software center. In other words I almost tried everything, the thing that I should mention is that my graphics card isn't supported by ATI anymore and i never let it look for drivers until I decided to download the ati control center then after that I started having that darn problem. EVEN when I uninstalled it completely that problem comes up. and on top of that I can't use desktop effects.

---

### Post by Michael577 on 2010-02-16
I reinstalled ubuntu and it works just fine

---

