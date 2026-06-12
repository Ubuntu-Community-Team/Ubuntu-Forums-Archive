---
title: "I just need it to work a little BETTER!"
date: 2009-08-30
forum: Wine
---

### Post by rmp5s on 2009-08-30
Hello everyone.  Seen lots of WoW related questions on here but none seemed to apply directly to me.  If I've overlooked something, forgive me.

Anyway...I have an HP Mini 1030NR and I'm running Ubuntu NBR on it, which I love.  Before I wiped windows, I played WoW on here.  It worked amazingly well considering this is about as far from a gaming computer as you can get.  I'd average 5-15FPS (even 20+ from time to time)  usually which isn't great but it is very, very playable.

Well...I've wiped windows.  I now got WoW working using the (Wine based) Crossover Games app, which works surprisingly well!  Had very little problems with the install and all that.  The only real problem I have now is a very general one...how can I make the game PLAY better?  My avg FPS now is 1-3...not even playable.  I don't expect it to be great...not even back up to where it was necessarily...I just want it playable.  I'm using the same hardware as before so I don't see why this couldn't be possible...just dunno how to do it.  Can anyone shed some light on this situation?

---

### Post by Clopin on 2009-08-30
First of all I suggest you do _everything_ that this tutorial guides you to:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421)
The main problem with your WoW, can be that you are not running it in OpenGL. You can fix this by adding -opengl to the shortcut you've made.

Do that, and come back and tell us the FPS.
If that doesn't do the job, try to do glxgears in Terminal:
```
glxgears
```
It tests your FPS, tell us the output.

---

### Post by rmp5s on 2009-08-30
Very good! On my way.  

Yesterday, my goal was to get WoW working.  I did.  Today my goal is to get it playable.  I will.  lol

First thing the site said to do was to see if direct rendering is enabled:

```
glxinfo | grep "direct rendering"
get fences failed: -1
param: 6, val: 0
direct rendering: Yes

```"Into terminal. If it returns direct rendering: Yes, you're good to go!"  So...check that one off the list.

Now I'm to this:

" You can either edit your WTF/Config.wtf in your World of Warcraft directory to include (note that this file is only created after you have logged in once, skip to option 2 if you haven't): 
  SET gxApi "opengl"
   Or simply add -opengl to the end of your WoW launcher. (Recommended for first run after CD or download)"


Not completely sure how to go about this yet.  It's not complete jibberish to me but I am still learning the Linux ropes.  Can someone gimme a hand with this?


I did the gears thing too and here's what it spit out:

```
glxgears
get fences failed: -1
param: 6, val: 0
763 frames in 5.0 seconds = 152.518 FPS
1370 frames in 5.0 seconds = 273.983 FPS
3450 frames in 5.0 seconds = 689.938 FPS
2455 frames in 5.0 seconds = 490.901 FPS
3321 frames in 5.0 seconds = 664.102 FPS
1314 frames in 5.0 seconds = 262.481 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 6810 requests (5187 known processed) with 0 events remaining.

```It popped right up and ran smooth as silk.

"
[SIZE=2] For World of Warcraft to work properly, you need to look for an Open Source Intel Driver that gives you direct OpenGL rendering support. [/SIZE]
   [SIZE=2]-----                                                                                                                                              
[/SIZE]
   [SIZE=2]There are no known Issues with Intel Cards, apart from bad FPS on certain drivers."

Since I have onboard Intel graphics acceleration (Intel Graphics Media Acceleration 950), should I look for something like this?
[/SIZE]

---

### Post by rmp5s on 2009-08-30
So...I've done a little more digging in regards to openGL and it just made me more lost.  Is openGL a program or what?  What is it?  How do I use it?  One site said to "run WoW with a -opengl argument" (as you described)...I know what an argument is and all that...I just don't know how to launch a program from the terminal yet!  I did try running it from the "Alt+F2 Run Application" tool and nothing happened.  I opened the Run App box, checked the "Run in Terminal" box, pointed the thing to the WoW Launcher file using the "run with file..." button and put the "-opengl" argument after it.  The box goes away and nothing happens.  I tried it again with out the "-opengl" argument and got the same result.

What am I missing here?

---

### Post by NightMKoder on 2009-08-30
You have an Intel GMA card. The drivers for linux are...lacking - especially under jaunty. Don't expect good performance.

OpenGL = Open Graphics Layer. It's a programming library that accelerates graphics operations (and is somewhat tied to your specific video card).

---

### Post by rmp5s on 2009-08-30
lol...triple post for the win!

I've been messing with it and I think I figured out the commands to run the program in a terminal...but...I can't get it to go into the directory.  I have the game installed on an external hard drive.  I think the problem is that the external drive is called "TOSHIBA EXT"...I think the space is what's killin me.  I can get into all the other places in my "/media" directory, just not the external.  I went and tried to rename the drive to take the space out and can't.  If I can get into the drive where I need to be, I think I can run the program (something like "cd blah/blah/launcher.exe -opengl") with the argument...I guess...lol

Do I have to install opengl?  Is it a program?  What am I doing!?!?!  lol

---

### Post by NightMKoder on 2009-08-30
You have opengl installed, otherwise the game wouldn't even turn on.

As for your bash troubles - tab autocompletion is your friend, remember that case matters, and if you have things with spaces, either put a \ before the space, or put the whole thing in quotes (" or ').

ie:

cd "TOSHIBA EXT"

---

### Post by rmp5s on 2009-08-30
Ah yes...very well. I forgot about the quotes.  Thanks!

I'll play with it some more.

---

### Post by rmp5s on 2009-08-30
So...progess is progress, right?  I can get into the directory that contains the launcher for WoW in the terminal now...lol...hey, baby steps...

Now...how do I launch "Launcher.exe" from the terminal using the crossover games program AND using the opengl argument?

---

