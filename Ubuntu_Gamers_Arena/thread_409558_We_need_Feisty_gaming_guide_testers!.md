---
title: "We need Feisty gaming guide testers!"
date: 2007-04-14
forum: Ubuntu Gamers Arena
---

### Post by Perfect Storm on 2007-04-14
Greetings fellow gamers!


Soon Feisty will hit its official release date and some people might already have migrated to it.
What we need is (if you use our guides), to see if they needs any changes and/or working or not. 
So if you tried any our guides just post back here, like this in short;

eg.

wesnoth guide works on Feisty x86

or if they guides works on other arch than x86 we really like to hear from you.


regards
UGA Team.

---

### Post by dthomasdigital on 2007-04-14
Use the guides, there fantastic!

UFO: Alien Invasion Guide works with Feisty x86
Zelda 2D Guide works with Feisty x86
Warzone 2100 Guide works with Feisty x86
Astromenace Guide works with Feisty x86 - game review in the works

---

### Post by dthomasdigital on 2007-04-14
World of Padman guide almost works I had to move the file to the home directory.
Other than that is works. Feisty x86 and what a game.

---

### Post by hind3nburg on 2007-04-15
sorry, could you link to your guides for me?

---

### Post by Perfect Storm on 2007-04-15
On our game guides/documentation: 

[http://gaming.gwos.org/e107_plugins/content/content.php?cat.4](http://gaming.gwos.org/e107_plugins/content/content.php?cat.4)

---

### Post by MaximB on 2007-04-15
could you remind me please when feisty will be finally released ?

---

### Post by Perfect Storm on 2007-04-15
The 19th this month.

---

### Post by MaximB on 2007-04-15
wow - this is real close.
but I think I will wait for a few more days perior to downloading and installing.

---

### Post by compiledkernel on 2007-04-16
There are probably only minor changes between now and then. But I have to side with Maxim here, something could possibly drastically change from this point forward.

---

### Post by Steve H on 2007-04-16
I downloaded and installed Feisty last night, and I have been using Wine which is running Steam and Counter Strike online. I have had no problems at all. In fact I had more problems with the latest Wine update under Edgy.

---

### Post by mrazster on 2007-04-17
Xubuntu Fiesty 7.04.

*_Linux Native:_*
*"Urban Terror"* guide works on Feisty x86
*"World of Padman"* guide works on Feisty x86
*"Frozen Bubble"* guide works on Feisty x86
*"Unreal Tournament 2004 DVD"* guide works on Feisty x86

*_Wine Games:_*
*"Day of Defeate"* guide works on Feisty x86
*"Call of Duty"* guide works on Feisty x86

*_Game Applications:_*
*"GL O.B.S"* guide works on Feisty x86


Only thing I had to do different with some games...was when adding them to my menu. It's a slight difference i procedure.
Other than that everything works as should...atleast to me.

---

### Post by Perfect Storm on 2007-04-18
Thanks for the input. Added [Feisty x86] tags to those games.
Keep them comming :guitar:

---

### Post by fakie_flip on 2007-04-22
I tested instructions for two games, and they both don't work in Feisty. Look at the error I got from running make below. For the Secret Maryo Chronicles game, I downloaded CEGUI-DOCS-0.5.0.zip. I unzipped it. There was no configure file to run in it.

```
root@ubuntu:~# apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libatk1.0-dev libglib2.0-dev x11proto-xinerama-dev
  x11proto-render-dev libxi-dev libxrender-dev libpcrecpp0 libxcursor-dev
  x11proto-randr-dev libfreetype6-dev x11proto-fixes-dev libxrandr-dev
  x11proto-xf86vidmode-dev libxfixes-dev libxinerama-dev libdevil1c2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgl1-mesa-dev libglu1-mesa-dev libglu1-xorg-dev libsmpeg-dev
Recommended packages:
  libxt-dev libasound2-dev libaa1-dev libaudio-dev libartsc0-dev libesd0-dev
  libdirectfb-dev libcaca-dev libcucul-dev
The following NEW packages will be installed:
  libgl1-mesa-dev libglu1-mesa-dev libglu1-xorg-dev libsdl-image1.2-dev
  libsdl-mixer1.2-dev libsdl1.2-dev libsmpeg-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.6kB/1487kB of archives.
After unpacking 5612kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com feisty/main libglu1-xorg-dev 1:7.2-0ubuntu11 [25.6kB]
Fetched 25.6kB in 2s (12.1kB/s)         
Selecting previously deselected package libgl1-mesa-dev.
(Reading database ... 238046 files and directories currently installed.)
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb) ...
Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_6.5.2-3ubuntu7_i386.deb) ...
Selecting previously deselected package libglu1-xorg-dev.
Unpacking libglu1-xorg-dev (from .../libglu1-xorg-dev_1%3a7.2-0ubuntu11_all.deb) ...
Selecting previously deselected package libsdl1.2-dev.
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.11-7ubuntu1_i386.deb) ...
Selecting previously deselected package libsdl-image1.2-dev.
Unpacking libsdl-image1.2-dev (from .../libsdl-image1.2-dev_1.2.5-2_i386.deb) ...
Selecting previously deselected package libsmpeg-dev.
Unpacking libsmpeg-dev (from .../libsmpeg-dev_0.4.5+cvs20030824-1.9build1_i386.deb) ...
Selecting previously deselected package libsdl-mixer1.2-dev.
Unpacking libsdl-mixer1.2-dev (from .../libsdl-mixer1.2-dev_1.2.6-1.1build1_i386.deb) ...
Setting up libgl1-mesa-dev (6.5.2-3ubuntu7) ...
Setting up libglu1-mesa-dev (6.5.2-3ubuntu7) ...
Setting up libglu1-xorg-dev (7.2-0ubuntu11) ...
Setting up libsdl1.2-dev (1.2.11-7ubuntu1) ...

Setting up libsdl-image1.2-dev (1.2.5-2) ...
Setting up libsmpeg-dev (0.4.5+cvs20030824-1.9build1) ...
Setting up libsdl-mixer1.2-dev (1.2.6-1.1build1) ...
Saving new apt-history status...
root@ubuntu:~# logout
chris@ubuntu:~/MY GAMES$ mv goonies_r1-0-1/build/linux/Makefile -t goonies_r1-0-1/src
chris@ubuntu:~/MY GAMES$ cd goonies_r1-0-1/src/
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ make
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c debug.cpp -o debug.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c 2DCMC.cpp -o 2DCMC.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c ranrotb.cpp -o ranrotb.o
ranrotb.cpp:117: warning: this decimal constant is unsigned only in ISO C90
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c geometrics.cpp -o geometrics.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c auxiliar.cpp -o auxiliar.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c font_extractor.cpp -o font_extractor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c keyboardstate.cpp -o keyboardstate.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c sound.cpp -o sound.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c SFXManager.cpp -o SFXManager.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c SDL_glutaux.cpp -o SDL_glutaux.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c Symbol.cpp -o Symbol.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c Vector.cpp -o Vector.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GObject.cpp -o GObject.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GLTile.cpp -o GLTile.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GLTManager.cpp -o GLTManager.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c PlacedGLTile.cpp -o PlacedGLTile.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GMap.cpp -o GMap.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GMapLayer.cpp -o GMapLayer.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GooniesScript.cpp -o GooniesScript.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_skull.cpp -o GO_skull.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_rope.cpp -o GO_rope.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_skulldoor.cpp -o GO_skulldoor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_water.cpp -o GO_water.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_wateropening.cpp -o GO_wateropening.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_cagedoor.cpp -o GO_cagedoor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_character.cpp -o GO_character.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_drop.cpp -o GO_drop.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_dropgenerator.cpp -o GO_dropgenerator.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_enemy.cpp -o GO_enemy.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_entrydoor.cpp -o GO_entrydoor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_fallingrock.cpp -o GO_fallingrock.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_jumpingskull.cpp -o GO_jumpingskull.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_key.cpp -o GO_key.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GObjectCreator.cpp -o GObjectCreator.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_bigrock.cpp -o GO_bigrock.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_skeleton.cpp -o GO_skeleton.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_bat.cpp -o GO_bat.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_fratelli.cpp -o GO_fratelli.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_bullet.cpp -o GO_bullet.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_pipe_water.cpp -o GO_pipe_water.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_item.cpp -o GO_item.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_trickyskull.cpp -o GO_trickyskull.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_bone.cpp -o GO_bone.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_exitdoor.cpp -o GO_exitdoor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_lava.cpp -o GO_lava.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_closingwall.cpp -o GO_closingwall.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_fallingwater.cpp -o GO_fallingwater.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_watersplash.cpp -o GO_watersplash.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_coin.cpp -o GO_coin.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_flame.cpp -o GO_flame.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_ghost.cpp -o GO_ghost.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_musicalnote.cpp -o GO_musicalnote.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_splash.cpp -o state_splash.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_konami.cpp -o state_konami.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_gameover.cpp -o state_gameover.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_disclaimer.cpp -o state_disclaimer.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_endsequence.cpp -o state_endsequence.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_game.cpp -o state_game.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_gamestart.cpp -o state_gamestart.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_interlevel.cpp -o state_interlevel.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_title.cpp -o state_title.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_titleanimation.cpp -o state_titleanimation.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_credits.cpp -o state_credits.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_howtoplay.cpp -o state_howtoplay.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_msx.cpp -o state_msx.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c TheGoonies.cpp -o TheGoonies.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c TheGooniesApp.cpp -o TheGooniesApp.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c main.cpp -o main.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include `sdl-config --libs` -L/usr/X11R6/lib/ -lSDL_image -lSDL_mixer -lSDL_sound -lGL -lGLU debug.o 2DCMC.o ranrotb.o geometrics.o auxiliar.o font_extractor.o keyboardstate.o sound.o SFXManager.o SDL_glutaux.o Symbol.o Vector.o GObject.o GLTile.o GLTManager.o PlacedGLTile.o GMap.o GMapLayer.o GooniesScript.o GO_skull.o GO_rope.o GO_skulldoor.o GO_water.o GO_wateropening.o GO_cagedoor.o GO_character.o GO_drop.o GO_dropgenerator.o GO_enemy.o GO_entrydoor.o GO_fallingrock.o GO_jumpingskull.o GO_key.o GObjectCreator.o GO_bigrock.o GO_skeleton.o GO_bat.o GO_fratelli.o GO_bullet.o GO_pipe_water.o GO_item.o GO_trickyskull.o GO_bone.o GO_exitdoor.o GO_lava.o GO_closingwall.o GO_fallingwater.o GO_watersplash.o GO_coin.o GO_flame.o GO_ghost.o GO_musicalnote.o state_splash.o state_konami.o state_gameover.o state_disclaimer.o state_endsequence.o state_game.o state_gamestart.o state_interlevel.o state_title.o state_titleanimation.o state_credits.o state_howtoplay.o state_msx.o TheGoonies.o TheGooniesApp.o main.o -o goonies
/usr/bin/ld: cannot find -lSDL_sound
collect2: ld returned 1 exit status
make: *** [goonies] Error 1
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ 
```

---

### Post by fakie_flip on 2007-04-22
I tried to compile Goonies again, and this is what I got.

```
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ sudo apt-get install libsdl-sound1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libflac-dev libmikmod2-dev libsdl-sound1.2 libspeex-dev
The following NEW packages will be installed:
  libflac-dev libmikmod2-dev libsdl-sound1.2 libsdl-sound1.2-dev libspeex-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 741kB of archives.
After unpacking 2413kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com feisty/main libflac-dev 1.1.2-5ubuntu2 [196kB]
Get:2 http://us.archive.ubuntu.com feisty/main libmikmod2-dev 3.1.11-a-6ubuntu3 [243kB]
Get:3 http://us.archive.ubuntu.com feisty/universe libsdl-sound1.2 1.0.1-12build1 [95.2kB]
Get:4 http://us.archive.ubuntu.com feisty/main libspeex-dev 1.1.12-3 [93.0kB]
Get:5 http://us.archive.ubuntu.com feisty/universe libsdl-sound1.2-dev 1.0.1-12build1 [114kB]
Fetched 741kB in 6s (120kB/s)                                                  
Selecting previously deselected package libflac-dev.
(Reading database ... 239742 files and directories currently installed.)
Unpacking libflac-dev (from .../libflac-dev_1.1.2-5ubuntu2_i386.deb) ...
Selecting previously deselected package libmikmod2-dev.
Unpacking libmikmod2-dev (from .../libmikmod2-dev_3.1.11-a-6ubuntu3_i386.deb) ...
Selecting previously deselected package libsdl-sound1.2.
Unpacking libsdl-sound1.2 (from .../libsdl-sound1.2_1.0.1-12build1_i386.deb) ...
Selecting previously deselected package libspeex-dev.
Unpacking libspeex-dev (from .../libspeex-dev_1.1.12-3_i386.deb) ...
Selecting previously deselected package libsdl-sound1.2-dev.
Unpacking libsdl-sound1.2-dev (from .../libsdl-sound1.2-dev_1.0.1-12build1_i386.deb) ...
Setting up libflac-dev (1.1.2-5ubuntu2) ...
Setting up libmikmod2-dev (3.1.11-a-6ubuntu3) ...

Setting up libsdl-sound1.2 (1.0.1-12build1) ...

Setting up libspeex-dev (1.1.12-3) ...
Setting up libsdl-sound1.2-dev (1.0.1-12build1) ...
Saving new apt-history status...
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ makec++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include `sdl-config --libs` -L/usr/X11R6/lib/ -lSDL_image -lSDL_mixer -lSDL_sound -lGL -lGLU debug.o 2DCMC.o ranrotb.o geometrics.o auxiliar.o font_extractor.o keyboardstate.o sound.o SFXManager.o SDL_glutaux.o Symbol.o Vector.o GObject.o GLTile.o GLTManager.o PlacedGLTile.o GMap.o GMapLayer.o GooniesScript.o GO_skull.o GO_rope.o GO_skulldoor.o GO_water.o GO_wateropening.o GO_cagedoor.o GO_character.o GO_drop.o GO_dropgenerator.o GO_enemy.o GO_entrydoor.o GO_fallingrock.o GO_jumpingskull.o GO_key.o GObjectCreator.o GO_bigrock.o GO_skeleton.o GO_bat.o GO_fratelli.o GO_bullet.o GO_pipe_water.o GO_item.o GO_trickyskull.o GO_bone.o GO_exitdoor.o GO_lava.o GO_closingwall.o GO_fallingwater.o GO_watersplash.o GO_coin.o GO_flame.o GO_ghost.o GO_musicalnote.o state_splash.o state_konami.o state_gameover.o state_disclaimer.o state_endsequence.o state_game.o state_gamestart.o state_interlevel.o state_title.o state_titleanimation.o state_credits.o state_howtoplay.o state_msx.o TheGoonies.o TheGooniesApp.o main.o -o goonies
-e  o If there are no errors, the game compiled succesfully
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ sudo make install
-e  o Creating install directory /usr/local/games/goonies
-e  o Installing game and data to /usr/local/games/goonies
-e  o Creating startup script /usr/local/bin/goonies
-e 
-e Type 'goonies' (no quotes) to start the game
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ goo
googleearth  goonies      
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ goo
googleearth  goonies      
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ goonies 
/usr/local/bin/goonies: line 1: -e: command not found
goonies: font_extractor.cpp:36: void font_extract(char*, char*, int, char*): Assertion `sfc!=0' failed.
/usr/local/bin/goonies: line 1: 18868 Aborted                 (core dumped) ./goonies
/usr/local/bin/goonies: line 1: cd: OLDPWD not set
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ 
```

---

### Post by fakie_flip on 2007-04-22
Zelda2d will not compile with the directions from here.

[http://gaming.gwos.org/e107_plugins/content/content.php?content.31](http://gaming.gwos.org/e107_plugins/content/content.php?content.31)

```
chris@ubuntu:~/Desktop/zelda2d-0.2.3$ sudo apt-get update && sudo ap-get upgradeGet:1 http://archive.ubuntu.com feisty-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US    
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US          
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US    
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US      
Get:3 http://archive.ubuntu.com feisty-proposed Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-proposed/restricted Translation-en_US     
Ign http://archive.ubuntu.com feisty-proposed/main Translation-en_US           
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://download.skype.com stable Release.gpg                               
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://ftp.osuosl.org edgy/ Release.gpg                                    
Ign http://ftp.osuosl.org edgy/ Translation-en_US                              
Ign http://archive.ubuntu.com feisty-proposed/multiverse Translation-en_US     
Ign http://archive.ubuntu.com feisty-proposed/universe Translation-en_US       
Get:5 http://archive.ubuntu.com feisty Release.gpg [191B]                      
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://archive.ubuntu.com feisty-proposed Release                          
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:6 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Ign http://ftp.osuosl.org edgy/ Release                                        
Hit http://archive.ubuntu.com feisty Release                                   
Hit http://security.ubuntu.com feisty-security Release                         
Ign http://download.skype.com stable Release                                   
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Get:7 http://archive.ubuntu.com feisty-proposed Release [32.4kB]               
Ign http://ftp.osuosl.org edgy/ Packages                                       
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security/main Packages                   
Ign http://download.skype.com stable/non-free Packages                         
Get:8 http://ftp.osuosl.org edgy/ Packages [1054B]                             
Hit http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://us.archive.ubuntu.com feisty/restricted Packages                    
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://us.archive.ubuntu.com feisty/universe Packages                      
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://download.skype.com stable/non-free Packages                         
Hit http://archive.ubuntu.com feisty/main Packages                             
Hit http://archive.ubuntu.com feisty-proposed/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-proposed/main Packages
Hit http://archive.ubuntu.com feisty-proposed/multiverse Packages
Hit http://archive.ubuntu.com feisty-proposed/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Fetched 33.7kB in 2s (12.0kB/s)
Reading package lists... Done
sudo: ap-get: command not found
chris@ubuntu:~/Desktop/zelda2d-0.2.3$ sudo apt-get install build-essential bcp libsdl1.2-dev libsdl-image1.2-dev libsdl-gfx1.2-dev libsdl-mixer1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
bcp is already the newest version.
libsdl1.2-dev is already the newest version.
libsdl-image1.2-dev is already the newest version.
libsdl-gfx1.2-dev is already the newest version.
libsdl-mixer1.2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@ubuntu:~/Desktop/zelda2d-0.2.3$ make engine
make -C tinyxml
make[1]: Entering directory `/home/chris/Desktop/zelda2d-0.2.3/tinyxml'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chris/Desktop/zelda2d-0.2.3/tinyxml'
make linux -C lua
make[1]: Entering directory `/home/chris/Desktop/zelda2d-0.2.3/lua'
make all MYCFLAGS=-DLUA_USE_LINUX MYLIBS="-Wl,-E -ldl -lreadline -lhistory -lncurses"
make[2]: Entering directory `/home/chris/Desktop/zelda2d-0.2.3/lua'
gcc -O2 -Wall -DLUA_USE_LINUX   -c -o lua.o lua.c
In file included from lua.h:16,
                 from lua.c:15:
luaconf.h:275:31: error: readline/readline.h: No such file or directory
luaconf.h:276:30: error: readline/history.h: No such file or directory
lua.c: In function &#8216;pushline&#8217;:
lua.c:180: warning: implicit declaration of function &#8216;readline&#8217;
lua.c:180: warning: assignment makes pointer from integer without a cast
lua.c: In function &#8216;loadline&#8217;:
lua.c:208: warning: implicit declaration of function &#8216;add_history&#8217;
make[2]: *** [lua.o] Error 1
make[2]: Leaving directory `/home/chris/Desktop/zelda2d-0.2.3/lua'
make[1]: *** [linux] Error 2
make[1]: Leaving directory `/home/chris/Desktop/zelda2d-0.2.3/lua'
make: *** [engine] Error 2
chris@ubuntu:~/Desktop/zelda2d-0.2.3$ 
```

---

### Post by fakie_flip on 2007-04-22
I found yet another game that does not work. It would be very nice if these games were in Universe. Then they would have been tested already.

```
chris@ubuntu:~/MY GAMES$ tar -xvzf ysflight20070410.tar.gz 
ysflight
chris@ubuntu:~/MY GAMES$ ./ysflight 
YSFLIGHT
VERSION 20070107
YFSVERSION 20070107
NETVERSION 20070318
Move CWD to .
Floating point exception (core dumped)
chris@ubuntu:~/MY GAMES$ ./ysflight 
YSFLIGHT
VERSION 20070107
YFSVERSION 20070107
NETVERSION 20070318
Move CWD to .
Segmentation fault (core dumped)
chris@ubuntu:~/MY GAMES$
```

I found this error file.

```
chris@ubuntu:~/MY GAMES$ cat fserr.txt 
Cannot read AIM-9 pattern
chris@ubuntu:~/MY GAMES$
```

---

### Post by clooch on 2007-04-22
warsow, world of padman work in feisty amd64

---

### Post by Perfect Storm on 2007-04-23
> **fakie_flip said:**
> I tested instructions for two games, and they both don't work in Feisty. Look at the error I got from running make below. For the Secret Maryo Chronicles game, I downloaded CEGUI-DOCS-0.5.0.zip. I unzipped it. There was no configure file to run in it.

```
root@ubuntu:~# apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libatk1.0-dev libglib2.0-dev x11proto-xinerama-dev
  x11proto-render-dev libxi-dev libxrender-dev libpcrecpp0 libxcursor-dev
  x11proto-randr-dev libfreetype6-dev x11proto-fixes-dev libxrandr-dev
  x11proto-xf86vidmode-dev libxfixes-dev libxinerama-dev libdevil1c2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgl1-mesa-dev libglu1-mesa-dev libglu1-xorg-dev libsmpeg-dev
Recommended packages:
  libxt-dev libasound2-dev libaa1-dev libaudio-dev libartsc0-dev libesd0-dev
  libdirectfb-dev libcaca-dev libcucul-dev
The following NEW packages will be installed:
  libgl1-mesa-dev libglu1-mesa-dev libglu1-xorg-dev libsdl-image1.2-dev
  libsdl-mixer1.2-dev libsdl1.2-dev libsmpeg-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.6kB/1487kB of archives.
After unpacking 5612kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com feisty/main libglu1-xorg-dev 1:7.2-0ubuntu11 [25.6kB]
Fetched 25.6kB in 2s (12.1kB/s)         
Selecting previously deselected package libgl1-mesa-dev.
(Reading database ... 238046 files and directories currently installed.)
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb) ...
Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_6.5.2-3ubuntu7_i386.deb) ...
Selecting previously deselected package libglu1-xorg-dev.
Unpacking libglu1-xorg-dev (from .../libglu1-xorg-dev_1%3a7.2-0ubuntu11_all.deb) ...
Selecting previously deselected package libsdl1.2-dev.
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.11-7ubuntu1_i386.deb) ...
Selecting previously deselected package libsdl-image1.2-dev.
Unpacking libsdl-image1.2-dev (from .../libsdl-image1.2-dev_1.2.5-2_i386.deb) ...
Selecting previously deselected package libsmpeg-dev.
Unpacking libsmpeg-dev (from .../libsmpeg-dev_0.4.5+cvs20030824-1.9build1_i386.deb) ...
Selecting previously deselected package libsdl-mixer1.2-dev.
Unpacking libsdl-mixer1.2-dev (from .../libsdl-mixer1.2-dev_1.2.6-1.1build1_i386.deb) ...
Setting up libgl1-mesa-dev (6.5.2-3ubuntu7) ...
Setting up libglu1-mesa-dev (6.5.2-3ubuntu7) ...
Setting up libglu1-xorg-dev (7.2-0ubuntu11) ...
Setting up libsdl1.2-dev (1.2.11-7ubuntu1) ...

Setting up libsdl-image1.2-dev (1.2.5-2) ...
Setting up libsmpeg-dev (0.4.5+cvs20030824-1.9build1) ...
Setting up libsdl-mixer1.2-dev (1.2.6-1.1build1) ...
Saving new apt-history status...
root@ubuntu:~# logout
chris@ubuntu:~/MY GAMES$ mv goonies_r1-0-1/build/linux/Makefile -t goonies_r1-0-1/src
chris@ubuntu:~/MY GAMES$ cd goonies_r1-0-1/src/
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ make
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c debug.cpp -o debug.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c 2DCMC.cpp -o 2DCMC.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c ranrotb.cpp -o ranrotb.o
ranrotb.cpp:117: warning: this decimal constant is unsigned only in ISO C90
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c geometrics.cpp -o geometrics.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c auxiliar.cpp -o auxiliar.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c font_extractor.cpp -o font_extractor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c keyboardstate.cpp -o keyboardstate.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c sound.cpp -o sound.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c SFXManager.cpp -o SFXManager.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c SDL_glutaux.cpp -o SDL_glutaux.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c Symbol.cpp -o Symbol.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c Vector.cpp -o Vector.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GObject.cpp -o GObject.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GLTile.cpp -o GLTile.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GLTManager.cpp -o GLTManager.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c PlacedGLTile.cpp -o PlacedGLTile.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GMap.cpp -o GMap.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GMapLayer.cpp -o GMapLayer.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GooniesScript.cpp -o GooniesScript.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_skull.cpp -o GO_skull.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_rope.cpp -o GO_rope.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_skulldoor.cpp -o GO_skulldoor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_water.cpp -o GO_water.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_wateropening.cpp -o GO_wateropening.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_cagedoor.cpp -o GO_cagedoor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_character.cpp -o GO_character.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_drop.cpp -o GO_drop.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_dropgenerator.cpp -o GO_dropgenerator.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_enemy.cpp -o GO_enemy.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_entrydoor.cpp -o GO_entrydoor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_fallingrock.cpp -o GO_fallingrock.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_jumpingskull.cpp -o GO_jumpingskull.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_key.cpp -o GO_key.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GObjectCreator.cpp -o GObjectCreator.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_bigrock.cpp -o GO_bigrock.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_skeleton.cpp -o GO_skeleton.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_bat.cpp -o GO_bat.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_fratelli.cpp -o GO_fratelli.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_bullet.cpp -o GO_bullet.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_pipe_water.cpp -o GO_pipe_water.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_item.cpp -o GO_item.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_trickyskull.cpp -o GO_trickyskull.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_bone.cpp -o GO_bone.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_exitdoor.cpp -o GO_exitdoor.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_lava.cpp -o GO_lava.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_closingwall.cpp -o GO_closingwall.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_fallingwater.cpp -o GO_fallingwater.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_watersplash.cpp -o GO_watersplash.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_coin.cpp -o GO_coin.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_flame.cpp -o GO_flame.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_ghost.cpp -o GO_ghost.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c GO_musicalnote.cpp -o GO_musicalnote.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_splash.cpp -o state_splash.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_konami.cpp -o state_konami.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_gameover.cpp -o state_gameover.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_disclaimer.cpp -o state_disclaimer.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_endsequence.cpp -o state_endsequence.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_game.cpp -o state_game.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_gamestart.cpp -o state_gamestart.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_interlevel.cpp -o state_interlevel.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_title.cpp -o state_title.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_titleanimation.cpp -o state_titleanimation.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_credits.cpp -o state_credits.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_howtoplay.cpp -o state_howtoplay.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c state_msx.cpp -o state_msx.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c TheGoonies.cpp -o TheGoonies.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c TheGooniesApp.cpp -o TheGooniesApp.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include -c main.cpp -o main.o
c++ -g3 -O3 -Wall `sdl-config --cflags` -I/usr/local/include/SDL -I/usr/X11R6/include `sdl-config --libs` -L/usr/X11R6/lib/ -lSDL_image -lSDL_mixer -lSDL_sound -lGL -lGLU debug.o 2DCMC.o ranrotb.o geometrics.o auxiliar.o font_extractor.o keyboardstate.o sound.o SFXManager.o SDL_glutaux.o Symbol.o Vector.o GObject.o GLTile.o GLTManager.o PlacedGLTile.o GMap.o GMapLayer.o GooniesScript.o GO_skull.o GO_rope.o GO_skulldoor.o GO_water.o GO_wateropening.o GO_cagedoor.o GO_character.o GO_drop.o GO_dropgenerator.o GO_enemy.o GO_entrydoor.o GO_fallingrock.o GO_jumpingskull.o GO_key.o GObjectCreator.o GO_bigrock.o GO_skeleton.o GO_bat.o GO_fratelli.o GO_bullet.o GO_pipe_water.o GO_item.o GO_trickyskull.o GO_bone.o GO_exitdoor.o GO_lava.o GO_closingwall.o GO_fallingwater.o GO_watersplash.o GO_coin.o GO_flame.o GO_ghost.o GO_musicalnote.o state_splash.o state_konami.o state_gameover.o state_disclaimer.o state_endsequence.o state_game.o state_gamestart.o state_interlevel.o state_title.o state_titleanimation.o state_credits.o state_howtoplay.o state_msx.o TheGoonies.o TheGooniesApp.o main.o -o goonies
/usr/bin/ld: cannot find -lSDL_sound
collect2: ld returned 1 exit status
make: *** [goonies] Error 1
chris@ubuntu:~/MY GAMES/goonies_r1-0-1/src$ 
```

Fixed

---

### Post by Madwolf on 2007-04-23
I've been playing America's Army 2.5 on Feisty x64 with no problems untill now :)

---

### Post by Perfect Storm on 2007-04-23
> **fakie_flip said:**
> Zelda2d will not compile with the directions from here.

[http://gaming.gwos.org/e107_plugins/content/content.php?content.31](http://gaming.gwos.org/e107_plugins/content/content.php?content.31)

```
chris@ubuntu:~/Desktop/zelda2d-0.2.3$ sudo apt-get update && sudo ap-get upgradeGet:1 http://archive.ubuntu.com feisty-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US    
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US          
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US    
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US      
Get:3 http://archive.ubuntu.com feisty-proposed Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-proposed/restricted Translation-en_US     
Ign http://archive.ubuntu.com feisty-proposed/main Translation-en_US           
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://download.skype.com stable Release.gpg                               
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://ftp.osuosl.org edgy/ Release.gpg                                    
Ign http://ftp.osuosl.org edgy/ Translation-en_US                              
Ign http://archive.ubuntu.com feisty-proposed/multiverse Translation-en_US     
Ign http://archive.ubuntu.com feisty-proposed/universe Translation-en_US       
Get:5 http://archive.ubuntu.com feisty Release.gpg [191B]                      
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://archive.ubuntu.com feisty-proposed Release                          
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:6 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Ign http://ftp.osuosl.org edgy/ Release                                        
Hit http://archive.ubuntu.com feisty Release                                   
Hit http://security.ubuntu.com feisty-security Release                         
Ign http://download.skype.com stable Release                                   
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Get:7 http://archive.ubuntu.com feisty-proposed Release [32.4kB]               
Ign http://ftp.osuosl.org edgy/ Packages                                       
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security/main Packages                   
Ign http://download.skype.com stable/non-free Packages                         
Get:8 http://ftp.osuosl.org edgy/ Packages [1054B]                             
Hit http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://us.archive.ubuntu.com feisty/restricted Packages                    
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://us.archive.ubuntu.com feisty/universe Packages                      
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://download.skype.com stable/non-free Packages                         
Hit http://archive.ubuntu.com feisty/main Packages                             
Hit http://archive.ubuntu.com feisty-proposed/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-proposed/main Packages
Hit http://archive.ubuntu.com feisty-proposed/multiverse Packages
Hit http://archive.ubuntu.com feisty-proposed/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Fetched 33.7kB in 2s (12.0kB/s)
Reading package lists... Done
sudo: ap-get: command not found
chris@ubuntu:~/Desktop/zelda2d-0.2.3$ sudo apt-get install build-essential bcp libsdl1.2-dev libsdl-image1.2-dev libsdl-gfx1.2-dev libsdl-mixer1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
bcp is already the newest version.
libsdl1.2-dev is already the newest version.
libsdl-image1.2-dev is already the newest version.
libsdl-gfx1.2-dev is already the newest version.
libsdl-mixer1.2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@ubuntu:~/Desktop/zelda2d-0.2.3$ make engine
make -C tinyxml
make[1]: Entering directory `/home/chris/Desktop/zelda2d-0.2.3/tinyxml'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chris/Desktop/zelda2d-0.2.3/tinyxml'
make linux -C lua
make[1]: Entering directory `/home/chris/Desktop/zelda2d-0.2.3/lua'
make all MYCFLAGS=-DLUA_USE_LINUX MYLIBS="-Wl,-E -ldl -lreadline -lhistory -lncurses"
make[2]: Entering directory `/home/chris/Desktop/zelda2d-0.2.3/lua'
gcc -O2 -Wall -DLUA_USE_LINUX   -c -o lua.o lua.c
In file included from lua.h:16,
                 from lua.c:15:
luaconf.h:275:31: error: readline/readline.h: No such file or directory
luaconf.h:276:30: error: readline/history.h: No such file or directory
lua.c: In function ‘pushline’:
lua.c:180: warning: implicit declaration of function ‘readline’
lua.c:180: warning: assignment makes pointer from integer without a cast
lua.c: In function ‘loadline’:
lua.c:208: warning: implicit declaration of function ‘add_history’
make[2]: *** [lua.o] Error 1
make[2]: Leaving directory `/home/chris/Desktop/zelda2d-0.2.3/lua'
make[1]: *** [linux] Error 2
make[1]: Leaving directory `/home/chris/Desktop/zelda2d-0.2.3/lua'
make: *** [engine] Error 2
chris@ubuntu:~/Desktop/zelda2d-0.2.3$ 
```


Fixed.

---

### Post by Clay_Banger on 2007-04-23
astromenace doesnt work?

```
AstroMenace 1.0 70414

/usr/share/astromenace/game_launcher: line 98:  8398 Segmentation fault      ./${GAME_BINARY} ${CMD_ARGS} "$@"
```

---

### Post by Perfect Storm on 2007-04-24
Works fine here, another member also tested it.

---

### Post by arfink on 2007-04-26
Wesnoth works great in Fiesty 64 bit. No problems whatsoever. Don't know about the guide though, all I did was download and install the debian packages in this order- Data, Program, Music, and then Campaigns. Make sure you pick the 64 bit versions where they are available.

---

### Post by Gen2ly on 2007-05-17
> **Clay_Banger said:**
> astromenace doesnt work?

```
AstroMenace 1.0 70414

/usr/share/astromenace/game_launcher: line 98:  8398 Segmentation fault      ./${GAME_BINARY} ${CMD_ARGS} "$@"
```

Did you use a Loki Installer?  I've seen that before.

---

### Post by Clay_Banger on 2007-05-17
> **Dirk.R.Gently said:**
> Did you use a Loki Installer?  I've seen that before.No, i fixed it, by using this to load the game:
```
./AstroMenace --noAA.
```This was suggested by retrorob in Ubuntu Gamers Arena > Astromenance Problem.

---

