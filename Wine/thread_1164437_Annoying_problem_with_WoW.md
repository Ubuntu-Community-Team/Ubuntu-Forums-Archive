---
title: "Annoying problem with WoW"
date: 2009-05-19
forum: Wine
---

### Post by Jooster on 2009-05-19
Hi
I'm new to Ubuntu, and Linux in general, but I'm doing pretty well so far. However, I have come across a problem in World of Warcraft. I've searched the forums, but it doesn't seem anyone else is having this problem. It goes like this: When I play WoW, and something happens outside the program, such as someone writing to me on pidgin, or rythmbox switching song, the desktop-background shows up for a brief moment, all over the screen, and then WoW comes back. 

To me it looks like WoW is somehow unable to "suppress" all other programs. My guess is that it's not supposed to either. But it is pretty annoying, and I would be very happy if someone could lend me a hand here.

And by the way. There is another problem. When my character moves, he kind of stutters. I've searched the forums and found a thread. But it seems to be more or less dead. The answer that came up was to disable "repeating keys" under keyboard preferences. But this causes other problems, such as having to tap the backspace button multiple times if I want to delete a sentence. Did anyone ever find a reasonable solution to this problem?

Thanks in advance everyone.

---

### Post by asdfoo on 2009-05-19
Wine version? Video card? driver version?

wine --version
glxinfo | grep version
glxinfo | grep render

---

### Post by hikaricore on 2009-05-19
Have you turned off desktop effects also?

---

### Post by Jooster on 2009-05-20
Hi, this is what I get when running those commands.

wine 1.0.1

server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 3.0.0 NVIDIA 180.44
OpenGL shading language version string: 1.30 NVIDIA via Cg compiler

OpenGL renderer string: GeForce 8800 GTS/PCI/SSE2
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap,

Also, when I check the visual effects (I believe that's the same thing as desktop effects...?) none of the alternatives are checked. However, I know that some effects are enabled, since my windows bends and "flows" when I move them. Could these effects have an effect on my problem?

Thanks for the answers guys, it's really appreciated.

---

### Post by Frostsniper on 2009-05-20
I've read a little here or there I'll keep searching see if i find anything but atm i have no clue. Your drivers do look up-to-date, i don't think there bad or anything, but how to make wow able to suppress other applications is beyond my reach.  Maybe another program is out there able to surpress them for you? and allows you to set order of importance? or something? try looking for that.  sorry for being vague =/

---

### Post by Clopin on 2009-05-20
The walking stuttering, is because that Ubuntu "keeps pressing a button" until you stop holding it down.
You can disable this (which will fix it), by going to
System -> Preferences -> Keyboard
and disable the repeating keys.

---

### Post by Jooster on 2009-05-20
Thanks for your help. I've got an update though. It seems this has nothing to do with WoW really, but more with maximized windows in general. When I watch a video on youtube in maximized window, and something happens in the background, like getting a message on pidgin, song change etc, it aborts the maximize and goes back to the standard, small, picture.

I hope that's the clue you guys need for a solution. Thanks everyone :)

---

### Post by Elviswind on 2009-05-20
> **Clopin said:**
> The walking stuttering, is because that Ubuntu "keeps pressing a button" until you stop holding it down.
You can disable this (which will fix it), by going to
System -> Preferences -> Keyboard
and disable the repeating keys.

Thanks for this solution.  Since I never had this problem before a couple weeks ago and always had repeating keys turned on, I am wondering what has changed.  Is it something with the way WINE works in passing the keystrokes on to WoW?  Is it worth rolling back to an older version of  WINE to test this?

---

### Post by Clopin on 2009-05-20
> **Elviswind said:**
> Thanks for this solution.  Since I never had this problem before a couple weeks ago and always had repeating keys turned on, I am wondering what has changed.  Is it something with the way WINE works in passing the keystrokes on to WoW?  Is it worth rolling back to an older version of  WINE to test this?

Afraid I havent got any idea about that. I've only had the same issue, and fixed it by reading on the AppDB.

---

### Post by khelben1979 on 2009-05-20
To get the best performance with WoW on Ubuntu I think you should add the recommended repository which is recommended on the WineHQ homepage.

Also, make sure to run the game in a window instead of fullscreen mode. I've heard that it works better in this mode and don't forget the -opengl parameter.

---

### Post by Duskao on 2009-05-21
To make sure that you aren't using the background effects there are two ways. 
One is to go into System-Prefrences-Appearance Then the "Visual Effects" tab on the right, then choose "none". This will kill the visual effects and have you run in metacity. However, when you want to use visual effects again it will search for the driver again, and it can be a pain in the butt. 
Two is to add/remove compiz fusion. With this app you can choose metacity or compiz with two clicks from the mouse without any driver stuff. My only problem with it is that I often don't use any effects with my computer so I would leave it on metacity, but when I would reboot compiz would be on but it would show metacity selected so I would need to reselect it. 

Guess it depends how much you like your funkadelic desktop, or how much you like your games and media. Either way, it's pretty easy to switch back and forth.

---

### Post by Elviswind on 2009-05-21
> **Clopin said:**
> Afraid I havent got any idea about that. I've only had the same issue, and fixed it by reading on the AppDB.

Weird.  Not sure if you have seen it, but others here as well may be looking for a better work around than unchecking the repeating keys option in the GUI:

```
#!/bin/bash
xset -r 24
xset -r 25
xset -r 26
xset -r 38
xset -r 39
xset -r 40
wine /home/myname/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe
xset r 24
xset r 25
xset r 26
xset r 38
xset r 39
xset r 40

```

Make this shell script executable and use it to run WoW.  Of course, the wine line should be edited to be whatever you use to start Wow.  The xset commands with -r turn off key repeating in X for just the QWEASD keys and then the r option turns key repeating back on after you quit WoW.

---

