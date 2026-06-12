---
title: "How to get Diablo 2 to work"
date: 2010-10-18
forum: Wine
---

### Post by mastablasta on 2010-10-18
Diablo 2 is crashing

This is a re-post, since previous thread was kindly deleted by the moderators/admins of this user friendly community as it wasn't following the rules to post wine related issue in wine subforums. *Mea culpa* as i should have read the rules more carfully. 

---

I managed to install Diablo 2 using wine. I had to use the terminal, for multi CD install.

The game did a video test in the end and found out that i can use software rendering. i don't know why 3D is not available because i can run Star trek: Elite force Voyager just fine. i am using opensource drivers for ATI Radeon 9600 XT. Monitor is 24" widescreen with 1600x1200 screen resolution i believe...

Upon starting the game the screen loaded the starting blizzard logo movie and then the whole thing crashed with main screen staying frozen there. upon alt-tabing i saw that diablo setup is running in background. i ended all diablo related processes, but screen was still messed up. so i restarted the computer. 

i tried to run it again. this time logo movie was shown then screen got garbled and then went black. and that was it. computer didn't crash as i could exit this black screen by pressing escape.

i should note here i am using i believe diablo 1.00. i use a character trainer with it. i see no harm in that as i only play over LAN and one of the users is not really a gamer :-)

---

Anyway a solution was provided by a forum member.
solution was to use windowed mode instead of fullscreen.

But this gives me a very small screen on a 1680x1050 display and i can not enlarge the window.

It also runs the game but the game keeps on breaking up - stopping, diablo screen gets B&W and then continuing only to do this again. why is this happening? any solution? could it be the CD drive being accessed that stops the game? I checked wine instructions and i see a link has to be made. but when i went to wine configuration i see the drive is recognised.

--

Also since the other thread was deleted and i never got a solution for the other issue - could anyone help me understand why 3D acceleration is not available? or at least full screen with 2D?

---

### Post by Soulcage on 2010-10-19
Try running the game in glide mode with [http://www.svenswrapper.de/english/index.html]("http://www.svenswrapper.de/english/index.html").
You may also want to update the game.

---

### Post by mastablasta on 2010-10-19
interesting thing, cause Blizzard dropped openGL support. i might give it a try.
 
still i am not sure why game runs fine for a short while in software acceleration mode and then starts to have problems and stops for a long while and then moves on again. also i don't know why i can't stretch the window.
 
i tried a couple of DOS games and they perform well als also stretch fine under DOSbox. and as i said i tried Voyager also works nice in Wine.
 
 
i was also thinking about updating the game, however i can not find any character trainers for latest version of the game. which is kind of logical.

---

### Post by mastablasta on 2010-10-20
wow this wrapper actually works well. however it seems it still needs windowed mode to propperly run in linux. if i do a propper windowed mode the screen is still small (in the center of my "large" desktop).

However if i use the stretching ability of this wrapper it nicely stretches over the whole screen. now the only problem left is that the panels stay displayed on top instead of hidden in the backgorund. a funny thing is that during menu, character slection and all they stay in the back. they only come forward during the game. see attached screenshot. any solution for this?

---

### Post by mastablasta on 2010-10-24
bump - ok let's try with a different quetsion. i know how to remove these panels, but how would i get them back easilly (same as they are)? i would make a launcher with that shortcut, so i would remove the panels and when i am done i would click on shortcut that would return them as they were before.

---

### Post by buzzmandt on 2010-10-24
you could use the hide/auto hide option on the panels. right click on it select properties and then select hide or auto hide, should work.

---

### Post by mastablasta on 2010-10-25
i actually tried that with bottom panel. as it seems part of the panel is actually still "over" the running game however it doesn't show on screen. as for the upper panel i am a bit afraid as i've been told it can mess up the whole thing...
 
perhaps another option would be to create a new user with no panels. but i would prefer if it would work on current user.

---

