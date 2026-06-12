---
title: "DLL File Troubles With Bryce 5.5"
date: 2009-07-03
forum: Wine
---

### Post by kshane on 2009-07-03
Hi all!

 I have installed Bryce 5.5, the free version, with ALMOST complete success.  The only problem I've come up with is that I have been unable to find a file that is missing.  I discovered the glitch when I stated the program in terminal.  It said two files were missing and named them.  One I found by Googling the file name.  The other I have been unable to locate.  The remaining missing file is BR55Axiam.dll.  It, apparently, involves the ability to rotate objects.  Obviously the program is of little use without that capability. 

I have done a file search on my own computer in the XP partition as I have Bryce installed there.  I could not find it.  I have Googled the file name in whole and part and have had no success there.  Since, I assume, this file is installed normally during the installation process, I am wondering if it is somehow possible to extract it from the installation file itself.  This is not a pirating thing, as the program is offered freely.  Can any one tell me how I might get this file?

This program runs fantastic under Ubuntu, with the exception of not being able to rotate objects. Thanks so much for any help!

Kevin

P.S.:  DAZ (the owners of Bryce) offer no direct support for the free version.  I have also been unable to find any other complaints of this nature either on their site or on the Wine home page.

---

### Post by kshane on 2009-07-04
bump...

---

### Post by cogadh on 2009-07-04
It sounds like that is a DLL that would normally be found in the application's installation directory after an install. If that is the case and it somehow can't be found when you run the app with Wine, then all you should (usually) need to do is change directories to the application's install directory before you run it:
```
cd ~/.wine/drive_c/Program\ Files/path/to/app
wine app.exe
```
With Windows applications, they sometimes need to be run "in" their installation directory in order for the executable to find all of the files it needs, otherwise it tries to find the files in Windows normal DLL directory, system32, where it won't find anything it needs.

---

### Post by kshane on 2009-07-09
Thanks, cogadh.  I tried what you suggested and had the same problem.  No ability to rotate objects.  

Is it possible to get inside the installation exe to find this file?

Thanks again!

Kevin

---

### Post by cogadh on 2009-07-09
I'm not sure if you could do that (depends on the installer used), but I just tried installing Bryce and was able to get it working fully (rotation and all) with no errors about missing DLLs. After the install I do have the B55Axiom.dll file in the Bryce installation directory as it should be. All I did use winetricks to install Visual C++ 6 and Visual C++ 2005 runtimes before running the Bryce install. It is possible that without those two runtimes installed, the installer was unable to properly register the DLL and skipped it. I would recommend you try the same and then re-install Bryce to see what happens.

---

### Post by kshane on 2009-07-10
Okay...  I uninstalled (apt-get purge...) all the wine stuff, including Bryce.  Then I reinstalled the most recent Wine (...25).  Next I installed the stuff you recommended using winetricks.  Then I installed Bryce.  Finally, in terminal, I navigated to the directory bryce is installed in and ran it from the command line.

Same thing!  Absolutely EVERYTHING works, but I am still unable to rotate the objects.  And, I also noted that the file I thought was responsible for that process that was missing before IS in the Bryce directory (B55Axiom.dll).

Any other suggestions?

***Thanks very, very much for your help so far.***  

Kevin

---

### Post by kshane on 2009-07-10
I also just found out - while trying to test some more - that I cannot "stretch" objects, not can I change the angle/direction of the sunlight, relative to the object....

---

### Post by cogadh on 2009-07-10
This is really odd. Are you getting any unusual error messages in the terminal when you run it? No offense intended, but is it possible this could be a PEBKAC situation, i.e. are you sure you are using the app correctly?

---

### Post by kshane on 2009-07-10
Hi again!

Yeah...  I'm using it correctly.  I have been using Bryce for about 6 years.  Always with Windows, though.  I'm not a "pro", but I've been cranking out art at about 1 to 12 scenes per day.

I don't have the best machine, but it works perfectly in Windows - so it SURELY should work in Ubuntu with Wine.  It's a little slow doing the final rendering in Windows (up to an hour with hi-res, large scenes).

Kevin

---

### Post by kshane on 2009-07-11
Uh...  I'm sorry - yes there are two new error messages:

```

libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering

```

Sorry again...

---

### Post by Th3_uN1Qu3 on 2009-07-11
> **kshane said:**
> Uh...  I'm sorry - yes there are two new error messages:

```

libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering

```

Sorry again...

You don't have your video drivers installed right.

---

### Post by kshane on 2009-07-12
> **Th3_uN1Qu3 said:**
> You don't have your video drivers installed right.

I have had no other issues with anything.  I am using the the ATI FGLRX driver.  All other apps work flawlessly, including Compiz, when I load it.  

Am I missing something?  What other drivers do I need? Mesa does not work for me at all.  Can't do anything that requires accelerated graphics under Mesa.

_Thanks_, by the way...

Kevin

---

### Post by kshane on 2009-07-12
If any one can help:

Here's the output for fglrxinfo:
```

kevin@Fulcrum:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.8087 Release

```

And the output from glxgears:

```

kevin@Fulcrum:~$ glxgears
7873 frames in 5.0 seconds = 1574.574 FPS
7825 frames in 5.0 seconds = 1564.555 FPS
7824 frames in 5.0 seconds = 1564.752 FPS
7803 frames in 5.0 seconds = 1560.544 FPS
7818 frames in 5.0 seconds = 1563.567 FPS
7819 frames in 5.0 seconds = 1563.758 FPS
7826 frames in 5.0 seconds = 1565.196 FPS

```

I don't understand what drivers are not installed properly.  Everything appears to be correct...

I just looked through info at winehq (FAQ, wiki, various searches) and found nothing to help with this error code:

```

libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering

```

Not asking for anyone to hold my hand - I would appreciate just a pointer in the right direction.

Thanks...

Kevin

---

### Post by kshane on 2009-07-13
No takers, eh?

---

### Post by kshane on 2009-09-09
Well, I finally found the solution.  I am going back to Windblows.  Been watching to see if ANY ONE would help out, but, apparently once the moniker of "PEBKAC" is used, no one gives a damn.  At least I don't have to weather insults from self righteous, prepubescent jerks of the likes of cogadh.  

I give...](*,)

Oh, and Mr Moderator, after deleting my post, you can delete my account.

---

