---
title: "My first game in c++"
date: 2011-06-15
forum: The Cafe
---

### Post by gufide on 2011-06-15
Hi there,

I started to programming since one year, following some tutorials around  the internet. I made some utility programs (very basic like 100 lines)  or tic-tac-toe terminal like games. While playing the little game [chip's challenge]("http://en.wikipedia.org/wiki/Chip%27s_Challenge"), I got the idea to reproduce it. I take about four month of non-intensive programming, because I have to go to high school :razz:  and I finally made a playable version. I made an engine to load level  from text file, but it only load it at the launch of the game (only to  show a demo of the feature :wink:)  real level 1 can be play be reload (using 'r') and the others levels,  including the real level one, are compiled with the executable file. I know there's some un-polished   functions, I will make a little clean-up next time. In-game controls are:

[LIST]
[*]Move: WASD/arrow keys
[*]Next level: n
[*]Previous level: p
[*]Restart level: r
[/LIST]

The tar file contain source, **make file**, sprite/sounds and executable for linux :smile:

[http://www.mediafire.com/?d8b5akg36l569zt](http://www.mediafire.com/?d8b5akg36l569zt)
*I use this because I can update my project daily.*

Please send me feedback and ideas, it will help me to continue!
You can edit and redistribute the source under the terms of GPLv3 license :wink:

Of course, you can contact me at [EMAIL="gufide_g@yahoo.ca"]gufide_g@yahoo.ca[/EMAIL]

Good game :popcorn:

---

### Post by 3Miro on 2011-06-15
How do you compile this thing? You did not include a Makefile.

---

### Post by BrokenKingpin on 2011-06-15
What library are you using for the graphics... SDL?

---

### Post by timZZ on 2011-06-15
Chip's Challenge ha ha WOW! Played that on my Atari lynx.

---

### Post by mmsmc on 2011-06-15
how did you compile it?

---

### Post by gufide on 2011-06-15
yes, I am using SDL, just take a look in the source ;)

And I did not give the makefile because the one given by anjuta simply doesn't work outside the IDE. I can send you the configure file, but all function of SDL are 'not defined' when you are using the terminal, but it can be useful with anjuta...

To try it you don't need to compile it, binary is included in the archive, and I give the source because I just want to share it and show up what I did :p

---

### Post by cgroza on 2011-06-15
I would have tried it, but too bad, there is no make file.

---

### Post by collisionystm on 2011-06-15
there is nothing to compile....

---

### Post by collisionystm on 2011-06-15
lol great music in the game.

---

### Post by collisionystm on 2011-06-15
cd game folder
```
sudo apt-get install  libSDL_image1.2
```
```
sudo apt-get install libSDL_mixer1.2
```
```
./chipper

```

---

### Post by KoolPenguin on 2011-06-15
Tried it, works great.  Good job! :)

---

### Post by Simian Man on 2011-06-15
I like it, but don't have much time to play it right now, I got stuck on the 2nd level.

By the way, makefiles aren't some magical thing that lets you compile code.  Just type:
```

g++ *.cpp -lSDL -lSDL_image -lSDL_mixer -o chipper

```

To compile it.

---

### Post by gufide on 2011-06-15
[SIZE=3][COLOR=Red]***** Update *****[/COLOR][/SIZE]
[COLOR=Black]Now the folder contain configure and make file[/COLOR]

---

### Post by gufide on 2011-06-15
> **Simian Man said:**
> I like it, but don't have much time to play it right now, I got stuck on the 2nd level.

By the way, makefiles aren't some magical thing that lets you compile code.  Just type:
```

g++ *.cpp -lSDL -lSDL_image -lSDL_mixer -o chipper

```To compile it.

Thanks, I think that this will help me ;)

---

### Post by gufide on 2011-06-20
Hey, I'm about to make a level-editor, I need some idea. No one got a little mockup for me?

---

