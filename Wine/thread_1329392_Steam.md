---
title: "Steam ?"
date: 2009-11-17
forum: Wine
---

### Post by wsamh on 2009-11-17
What steps do I need to take to make sure that Steam runs and the games can run also?

---

### Post by Dude-PWB- on 2009-11-17
Check out [http://winehq.org]("http://www.winehq.org") and search for steam, and the games you want to use in steam. Members there have posted lots of information to get steam, and their games up and running properly in wine.

---

### Post by beastrace91 on 2009-11-17
Be sure to be running the latest Wine version for starters - also your millage will vary depending on what games you plan to run and what your hardware setup is - if you run into any issues along the way feel free to post them here and myself or a number of other people will be sure to lend suggestions where we can :)

Also check the link in my signature for other suggestions on performance optimizations.

~Jeff

---

### Post by Alatar1 on 2009-11-17
The winehq thing is a good idea, but my best luck with steam came with using OPENGL for graphics, i use an NVIDA video card, I hear ATI has issues with alot of things in Wine.
    Also it helped me pumping up the resolution real high (in counter-strike at least) helped improve rendering and framerates somehow. It seems my particular machine and my vid card like when i turn the game resolution up pretty high in pretty much any game, dont ask me why but it helps...

---

### Post by beastrace91 on 2009-11-17
> **Alatar1 said:**
> It seems my particular machine and my vid card like when i turn the game resolution up pretty high in pretty much any game, dont ask me why but it helps...

Its not just your system: [quote="http://jeffhoogland.blogspot.com/2009/11/wine-cedega-and-cxgames-benchmark.html"]The Results:
Counter Strike - Source
Resolution: 1680x1050
- Wine: 72.29 fps
- CXGames: 153.03 fps
- Cedega: 113.83 fps
Resolution: 1024x768
- Wine: 49.33 fps
- CXGames: 163.03 fps
- Cedega: 119.22 fps
Resolution: 640x480
- Wine: 63.23 fps
- CXGames: 179.94 fps
- Cedega: n/a[/quote]

As you can see Wine for some reason seems to run certain games better at higher resolutions.

~Jeff

---

### Post by wsamh on 2009-11-17
How do I make sure that I am using openGL and that I use high resolution for to work properly, just clarifying? just to let you know that I am a novice user in linux.

---

### Post by Alatar1 on 2009-11-17
You can set the game to use OPENGL graphics in the games video options. as well as the resolution settings in the same place.
If you cant get to it that way im not sure.

---

### Post by beastrace91 on 2009-11-17
Depends on your game. For instance CSS only runs in DirectX but Wine converts those calls into OpenGL (so it runs on Linux) - as for getting the best performance there are a few standard things that help on all systems (such as using the latest drivers) but for the most part just play with your graphics settings to see which ones yield the best results.

Regards,
~Jeff

---

### Post by xuCGC002 on 2009-11-17
I've got a question. I was running Steam just fine the other day, playing all my games as normal. Then it told me (on any game I click) that the games are not available, please try again. Going into offline mode and playing them works, multiplayer (on CS 1.6 and Team Fortress Classic) works for about 5 minutes before kicking me off. I tried what's listed in the Steam help, is there a WINE problem to this?

---

### Post by beastrace91 on 2009-11-17
Odds are its just a Steam issue. Try closing Steam & the deleting your clientregistry.blob file and reloading Steam - this solves alot of various Steam woes.

Regards,
~Jeff

---

### Post by xuCGC002 on 2009-11-17
> **beastrace91 said:**
> Odds are its just a Steam issue. Try closing Steam & the deleting your clientregistry.blob file and reloading Steam - this solves alot of various Steam woes.

Regards,
~Jeff

I had already tried that. I really want to play online longer than 5 minutes, and chat too!

---

### Post by Alatar1 on 2009-11-17
Try reinstalling, not steam itself but you can remove local game files and re-download them, if that doesnt work try reinstalling steam as well, cant gurantee it will work, but reinstalling is always an option.

---

### Post by wsamh on 2009-11-17
After I installed steam. I installed a game and when I tried to play it, Steam says that I have an outdated nvidia driver. How do I fix that?

---

### Post by beastrace91 on 2009-11-17
Just check the "ignore this message" in the future - it is un-important so long as you have the proper driver installed on Ubuntu for your graphics card.

Also I am decently sure the latest version of Wine no longer displays this message - what Wine version are you using?

Regards,
~Jeff

---

### Post by Alatar1 on 2009-11-17
so you can still run the game with this error popping up? then ya i'd ignore it...
updating wine is your friend, it fixes so many things, very good idea keeping it up to date.

---

### Post by wsamh on 2009-11-17
I'm using 1.1.33. And no, It does not run properly when I ignore it. I'm trying to play left 4 dead. Even though I heard it is really hard to try to get to run on wine.

---

### Post by wsamh on 2009-11-17
I have a geforce 8400gs

---

### Post by beastrace91 on 2009-11-17
That driver message has nothing to do with your game not working - ignore it (it is saying you do not have a proper *Windows* graphics driver installed - which is fine, cause well we are using Ubuntu).

That being said - what abouts on Left 4 Dead is not working for you? Also what video driver do you have installed? Also just as a fair warning odds are you are going to see horrid performance on L4D under Wine (Check the benchmarks link in my sig for exact performance specs) - it is barely playable on my 260m which is has over twice as much power behind it that you card does.

Regards,
~Jeff

---

### Post by wsamh on 2009-11-18
I only get sound but not even the intro. not event the intro. I'm using the nvidia v185 driver. Any specific settings that I should try. I'm just trying to learn how to get the most out of wine on my computer.

---

### Post by beastrace91 on 2009-11-18
Try different Wine version - I know personally I've gotten it working decently under 1.1.28, 1.1.29, and 1.1.32 - have yet to sit down and try the latest.

Regards,
~Jeff

---

