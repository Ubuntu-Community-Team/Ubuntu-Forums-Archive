---
title: "opengl error thing."
date: 2008-10-13
forum: Windows
---

### Post by themuddaload on 2008-10-13
i got this error message when trying to boot tremulous on my winxp comp.

GLW_StartOpenGL() - could not load OpenGL subsystem


what is wrong?

i seem to remember getting a similar problem on my win98 computer a while back, only i was trying to play star trek elite force


thanks for the help guys.

---

### Post by themuddaload on 2008-10-13
```
tremulous 1.1.0 win_mingw-x86 Feb 28 2006
----- FS_Startup -----
Current search path:

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
...detecting CPU, found generic

------- Input Initialization -------
No window for DirectInput mouse init, delaying
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'C:\WINDOWS\system32\opengl32.dll' ): succeeded
...setting mode 3: 640 480 FS
...using desktop display depth of 32
...calling CDS: ok
...registered window class
...created window@0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...35 PFDs found
...GLW_ChoosePFD failed
...GLW_ChoosePFD( 32, 24, 0 )
...35 PFDs found
...GLW_ChoosePFD failed
...failed to find an appropriate PIXELFORMAT
...restoring display settings
...WARNING: could not set the given mode (3)
...setting mode 3: 640 480 FS
...using colorsbits of 16
...calling CDS: ok
...created window@0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 16, 16, 0 )
...35 PFDs found
...GLW_ChoosePFD failed
...GLW_ChoosePFD( 16, 16, 0 )
...35 PFDs found
...GLW_ChoosePFD failed
...failed to find an appropriate PIXELFORMAT
...restoring display settings
...WARNING: could not set the given mode (3)
...shutting down QGL
...unloading OpenGL DLL
...assuming '3dfxvgl' is a standalone driver
...initializing QGL
...WARNING: missing Glide installation, assuming no 3Dfx available
...shutting down QGL
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
GLW_StartOpenGL() - could not load OpenGL subsystem
```


i deleted the search path, but that is the rest of the error printout thing.

---

### Post by MaxIBoy on 2008-10-16
Try a different OpenGL game, such as Alien Arena or Urban Terror. 

Also, what graphics card do you have?

---

### Post by themuddaload on 2008-10-17
i am running winxp.

this computer doesnt have a graphics card =/  but it still should be able to plat them, shouldnt it?

---

### Post by MaxIBoy on 2008-10-17
Depends.
[http://www.opengl.org/wiki/index.php/Getting_started](http://www.opengl.org/wiki/index.php/Getting_started)

Try going to the device manager (if I remember correctly, it's control panel, system, then something else. It's been a while.) Look at any device with a name like "display adapter." That would be your chipset. Google the name of your chipset and "drivers," that should work.

---

