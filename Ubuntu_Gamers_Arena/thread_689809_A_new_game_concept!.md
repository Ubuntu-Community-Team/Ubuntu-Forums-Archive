---
title: "A new game concept!"
date: 2008-02-06
forum: Ubuntu Gamers Arena
---

### Post by redwan on 2008-02-06
Hi everybody,

I realized a game based on the briquolo game that you might alreay have tried on ubuntu.

Usually, the game controls the music. For instance, when a player reaches the last level of a game, the music becomes louder and more stressful. My game is a controlled musically game which means that the music controls the game and this brings you new sensations.

More detailled on my website : [http://cmg.redouane.info]("http://cmg.redouane.info")

All the installation instructions are present in the install.txt file in the archive. Please do not hesitate to send an email or to let a message in this thread for more explanation.

This program is using CMake for the compilation and if you find any way to improve the CMake configuration file, please let me know. I would also like to make a .deb archive if someone can let me know how to do it.

Thanks!

Edit (02/09/08) : New version available on the website which corrects some bugs

---

### Post by ryanVickers on 2008-02-06
I am not able to try it yet, but it looks like a very nice idea... Great web page design btw :p  Perhaps too vibrant though.

---

### Post by redwan on 2008-02-08
Thanks ryanVickers!

Why you cannot try it? You do not have ubuntu on your computer :) ?

---

### Post by Jadd on 2008-02-08
Tried installing it, got this error:
```
Please set the following variables:
OPENGL_INCLUDE_DIR (ADVANCED)
SDLMIXER_INCLUDE_DIR
SDLTTF_INCLUDE_DIR
SDL_INCLUDE_DIR
```

---

### Post by redwan on 2008-02-08
My bad, I forgot to write in the install.txt file that you need to install the devel of all the libraries and you also need to install sdl_mixer.

So basically you need to install:
sdl devel
sdl ttf devel
sdl mixer devel

Hope it works

---

### Post by redwan on 2008-02-09
New version available, please check it out !
Should correct some problems you had folks

---

