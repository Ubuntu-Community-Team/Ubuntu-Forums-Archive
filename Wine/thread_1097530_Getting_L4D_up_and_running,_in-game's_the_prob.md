---
title: "Getting L4D up and running, in-game's the prob"
date: 2009-03-16
forum: Wine
---

### Post by myromance123 on 2009-03-16
Hey there.
  I'm running Ubuntu 8.04. Wine 1.1.17. L4D is updated and so is Steam.
Got 1.5GB DDr1 RAM, 2.3 Pentium 4, Radeon x1650.
Wine is running as XP. I'm using the drivers that are available in the repos.

I managed to get L4D to run using these commands I found on this youtube video (its in the description of the video) 
Link : [http://www.youtube.com/watch?v=far0jjAlg24]("http://www.youtube.com/watch?v=far0jjAlg24")

Commands : 
```
env WINEPREFIX="/home/xxxx/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 500 +mat_hdr_level 0 -novid -height 900 -width 1440 -windowed
```

Now, when I ran those commands using Wine 1.0, the game would run and I would get to the menu screen. BUT, there was no sound, at all.
  Plus, it would crash or maybe shutdown when I tried to go in game (single player multiplayer etc)

Running it in Wine 1.1.17 gives me sound, and loads the game so much faster, BUT!!!!   Theres no image, I can't see the screen (its just pitch black, although I can hear the menu selections taking place as I move the mouse up and down). So I can't very well test whether or not I can go in-game with this version of Wine.

Does anybody know what the problem is?
There's also some (maybe) error messages that appear in the terminal when
the games starting up. Should I post those possible error messages?
 Theres a lot of repetition in the terminal, which is why I don't post all that appears there, in here.

Can anyone guide me? Has anyone reached success and can get me playing L4D on my machine?

 Dual booting is not an option since i don't own a legal version of Windows and I can't afford one right now (its in the thousands over here..)
Searched the net and couldn't find any how-to's. Plus the search in ubuntu forums doesnt work for me (don't know why..)

Oh, it also warns me that my video card drivers are outdated. Should I go and get the binaries from Ati and install the latest one for my card?

---

### Post by myromance123 on 2009-03-16
Okeh after fiddling and finally getting the ati binary installer to work, I got back image in L4D.

 AND!!!!  There is sound. Pretty sweet~

Sadly everytime I'm just about to get in game, it crashes. OH THE SADNESS!!

It's like it's teasing me, it'll show a second's worth of in game and then just disappear, leaving me with this in the terminal:

```
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #93: "Fragment shader was successfully compiled to run on hardware.\nWARNING: 0:2: extension 'GL_ARB_draw_buffers' is not supporte"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #90: "Fragment shader(s) linked, vertex shader(s) linked. \nWARNING: 0:2: extension 'GL_ARB_draw_buffers' is not supportedWARNING: built-in varying gl_TexCoord [1] has mismatched access semantics between the vertex and fragment shader\nWARNING: built-in varying gl_TexCoord [3] has mismatched access semanti"...
```

Heck I do not know what that means... I turned all my settings to low a second time and only a fraction of a second more of in game did I see.

From the videos I've seen they all seem to use Nvidia cards, some of the latest to boot!
  I know that Linux handles Nvidia better because of Nvidia support, but I would think that the binaries released on Ati's site would give me equal abilities...
  Right now I'm at a loss, I have the ati x1600 9.2 driver installed from their website, using Wine 1.1.17 and the above hardware specs.

That second's worth of in-game means I can play!! There's just something stopping me. Before this I couldn't even enter the menu let alone fathom the ability to see in-game.

 I know I'm so close to getting it to work, if only I knew what that last problem was...

---

### Post by asdfoo on 2009-03-19
> **myromance123 said:**
> Okeh after fiddling and finally getting the ati binary installer to work, I got back image in L4D.

 AND!!!!  There is sound. Pretty sweet~

Sadly everytime I'm just about to get in game, it crashes. OH THE SADNESS!!

It's like it's teasing me, it'll show a second's worth of in game and then just disappear, leaving me with this in the terminal:

```
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #93: "Fragment shader was successfully compiled to run on hardware.\nWARNING: 0:2: extension 'GL_ARB_draw_buffers' is not supporte"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #90: "Fragment shader(s) linked, vertex shader(s) linked. \nWARNING: 0:2: extension 'GL_ARB_draw_buffers' is not supportedWARNING: built-in varying gl_TexCoord [1] has mismatched access semantics between the vertex and fragment shader\nWARNING: built-in varying gl_TexCoord [3] has mismatched access semanti"...
```

Heck I do not know what that means... I turned all my settings to low a second time and only a fraction of a second more of in game did I see.

From the videos I've seen they all seem to use Nvidia cards, some of the latest to boot!
  I know that Linux handles Nvidia better because of Nvidia support, but I would think that the binaries released on Ati's site would give me equal abilities...
  Right now I'm at a loss, I have the ati x1600 9.2 driver installed from their website, using Wine 1.1.17 and the above hardware specs.

That second's worth of in-game means I can play!! There's just something stopping me. Before this I couldn't even enter the menu let alone fathom the ability to see in-game.

 I know I'm so close to getting it to work, if only I knew what that last problem was...

sounds like a bug in Wine, maybe the generated shader code needs to be tweaked for it to work both on ATI and nvidia.  I would try reposting at [http://forum.winehq.org](http://forum.winehq.org) since some of the d3d people read the threads there.


The warning about outdated video drivers is a red herring, it's just steam/the game failing to detect which driver version you have.

---

### Post by myromance123 on 2009-03-22
Hey thanks for the reply :D
 
 Okeh I'm going to give that a try, wish me success!
  :P

---

