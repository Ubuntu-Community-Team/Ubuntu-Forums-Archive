---
title: "Problem getting Sims2 to start"
date: 2010-06-02
forum: Wine
---

### Post by Axolotl9250 on 2010-06-02
Hi, I have a problem with getting sims2 to start in Wine, it comes up with 3 windows in the bottom bar in gnome and makes the screen look distended, but it won't actually load anything. I've tried to have a look at the app database wine have and apparantly there is a way to get it to work here: [HTML]http://appdb.winehq.org/objectManager.php?sClass=version&iId=2633[/HTML] but that post was in January and I now have Wine version 1.2-rc2 so I'm a little unsure of how to proceed. Does anybody more used to Wine and more savvy know anything regarding this game and it's functionality (or lack of)? Cheers :)

---

### Post by cogadh on 2010-06-02
I think you need to re-read that. The game doesn't actually work, that hack just addresses one minor problem with it enough to get it started, but it is still basically unplayable. The bugs listed on the AppDB page are still unresolved, so even though you are using a much more recent version of Wine, those problems still exist.

However, if you want to give that hack a try, you'll need to remove your currently installed version of Wine, download the Wine source code, apply the hack, compile Wine and install it. There are instructions on the Wine website for that, if you really want to try it.

---

### Post by Axolotl9250 on 2010-06-02
O.k. thanks, I managed to get dawn of war soulstorm up and running in a window but the keyboard and sound doesn't seem to work. I'm trying it with most of my games to see which ones will work and which ones will not. Is there something that can be done to tweak things like keyboard or controls? It wasn't too evident in the config panel.

---

### Post by cogadh on 2010-06-02
Rather than randomly trying games, you should probably just check AppDB first and only try the games that already have a Gold or higher rating. Sometimes Silver rated games work well enough to play, but they are often hard to get to that point. Additionally, AppDB will often have info on what you might need to do to get a game running its best, so you can save yourself a lot of frustration.

As for your problem with DoW, sound issues are usually caused by PulseAudio, and can often be fixed by running "killall pulseaudio" in the terminal before launching the game in Wine. The keyboard focus issue is one that seems to come and go with Wine, but at one time it was clearly caused by having desktop effects enabled while running Wine. Since the desktop effects also tend to break OpenGL functionality from Wine's perspective, you should check to make sure they are set to "none" before running a game.

---

### Post by Axolotl9250 on 2010-06-02
Hey, thanks for the tip, the keyboard controls work now :) I had a look at the database, for my version of Ubuntu it has a gold status, tried killing pulseaudio but the sound still didn't work and tried running it each time with the different audio drivers in the config menu but still no joy even though nobody's mentioned sound on the database :S. I'm new to Wine and its pretty much an out of the box, fresh install from synaptic. I intend to post a comment on there, In config I have all the Window settings options unchecked (if that makes a difference) and have tried it with ALSA, OSS JACK and NAS sound drivers, no theme on desktop integration, no libraries, and the default drives it was set up with when I first used Wine. Should I re-enable pulseaudio when I'm done or do I not really need it? All my other sound stuff seems to be working fine.

{EDIT} O.k. I've been doing some reading and I used ```
cat /dev/urandom >> /dev/dsp
``` which was supposed to see if my hardware  was locked by another application and I got the following error ```
Device or resource busy

``` which I read suggests that it is, I tried killing pulse audio again to see if that did anything but I still got the same error. I tried running from the terminal to see if I got any obvious errors to do with sound but got nothing. I've read through the manual and it talks about altering DLL's for programs and messing with the config files but thats quite enough above my head for now until I'm used to it. I wonder is there a way to find out exactly what (if the error message is true) is using my sound hardware and how I can kill it to let the game give me sound?

---

