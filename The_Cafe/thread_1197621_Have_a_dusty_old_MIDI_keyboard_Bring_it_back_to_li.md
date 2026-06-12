---
title: "Have a dusty old MIDI keyboard? Bring it back to life with LMMS"
date: 2009-06-26
forum: The Cafe
---

### Post by Mazza558 on 2009-06-26
[http://jamesgadsby.wordpress.com/2009/06/26/introduction-to-lmms-how-to-take-your-midi-keyboard-to-the-next-level/]("http://jamesgadsby.wordpress.com/2009/06/26/introduction-to-lmms-how-to-take-your-midi-keyboard-to-the-next-level/")

Hi all, I wrote this quick (haha) guide explaining how you can make that dusty old MIDI keyboard, lying in a corner, so much more awesome with no extra cost except a couple of hours. It basically allows you to mimic (and surpass) top-level keyboards in sound quality simply by linking your keyboard to your computer.

I only discovered this program earlier this year and I just think it's incredible what you can do for free these days.

---

### Post by Phreaker on 2009-06-26
Can lmms load vsti?

---

### Post by Mazza558 on 2009-06-26
> **Phreaker said:**
> Can lmms load vsti?

Do you mean VST plugins?

As far as I know, all plugins used are VST plugins.

---

### Post by Eisenwinter on 2009-06-26
LMMS can only load VST plugins made for Win32, and therefore it requires WINE in order to use those VSTs.

My opinion? Not worth it, I stick with Cubase SX 3 on Windows XP for music production.

---

### Post by Phreaker on 2009-06-26
I use REAPER in wine, so I was thinking of substituting it with lmms.
I need to test that

---

### Post by Mazza558 on 2009-06-29
> **Eisenwinter said:**
> LMMS can only load VST plugins made for Win32, and therefore it requires WINE in order to use those VSTs.

My opinion? Not worth it, I stick with Cubase SX 3 on Windows XP for music production.

I've been testing out VST support over the last few days and, bar a couple, they all work fine, and just as they do in Windows - especially with the very latest WINE.

---

### Post by Mazza558 on 2009-08-10
Hi all, I've created a one-command install of LMMS, which installs the dependencies, grabs lmms from its git repository, configures and compiles it for your convenience. Now it's as easy as copy and paste! 

To install LMMS 0.4.4:

> sudo aptitude update && sudo aptitude install libqt4-dev qt4-dev-tools git-core build-essential libsndfile1-dev libasound2-dev libjack0.100.0-dev libjackasyn-dev libsdl-sound1.2-dev  libsdl1.2-dev libsdl-mixer1.2-dev libvorbis-dev libvorbisfile3 libvorbisenc2 libsamplerate0-dev libstk0-dev stk libfftw3-dev libfluidsynth-dev git cmake && git clone git://lmms.git.sourceforge.net/gitroot/lmms && cd lmms && git checkout -b stable-0.4 origin/stable-0.4 && mkdir build && cd build && cmake .. -DCMAKE_INSTALL_PREFIX=/usr && make && sudo make install

...Or if you want to test out the future of LMMS (and it's looking very good), run this command:

> sudo aptitude update && sudo aptitude install libqt4-dev qt4-dev-tools git-core build-essential libsndfile1-dev libasound2-dev libjack0.100.0-dev libjackasyn-dev libsdl-sound1.2-dev  libsdl1.2-dev libsdl-mixer1.2-dev libvorbis-dev libvorbisfile3 libvorbisenc2 libsamplerate0-dev libstk0-dev stk libfftw3-dev libfluidsynth-dev git cmake && git clone git://lmms.git.sourceforge.net/gitroot/lmms && cd lmms && mkdir build && cd build && cmake .. -DCMAKE_INSTALL_PREFIX=/usr && make && sudo make install

**Note that, if you want to run the command again (either of them), you need to delete the lmms folder if your /home directory first. If you have lots of projects, just rename your existing lmms folder so you don't lose them.**

---

