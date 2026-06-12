---
title: "-HELP- Need a decent program like Yukon or GLC... but for non-opengl games?"
date: 2011-01-18
forum: Ubuntu Studio
---

### Post by cessusbangy on 2011-01-18
I am really desperate here.
It seems that every single goddamn thing I use, will capture either;
A) OUT OF SYNC
B) DROP FRAMES
C) CORRUPT (see: Recordmydesktop)
D) LOWFPS.

I'm running Ubuntu Linux 11.04 in Virtualbox OSE. I've tried ffmpeg, Istanbul, RecordmyDesktop, X11Cap, Xfire, Mplayer. AND NOTHING. REPEAT: NOTHING... will work.

I'm trying to make a Let's Play on Youtube. I'm running Fallout 1 & 2 in WINE (latest version).

Recordmydesktop:

Cannot capture mic + desktop audio.
Produced file will only be around 90mb... after processed harddrive freespace is 10 or so GB... even though WHILE recording my harddrive will show that there is no space, and crashes the program -.-
Kdenlive will process my ogv file... yet somehow will drop a whole lot of frames, say something is there when it's not, crash or produce terrible results.
Pitivi is even worse, strangely enough...
OpenShot is the same as Kdenlive.

Now, that's Recordmydesktop... time for Ffmpeg.

Capturing works ok, for about 30 seconds... then the video will go awry and audio go WAAAY out of sync. I try -async, -vsync, -itsoffset... and nothing works?

Now, Istanbul.

Uncustomizable, low frame rate, cannot capture mic + desktop audio. Sh*t.

X11Cap:
Same as Istanbul... except trying to capture at 30fps will only process at 13 fps (my system is easily fast enough).

What I'm looking for essentially, summed up is...

- A game recorder that supports DirectDraw games (such as Fallout), that doesn't crash, doesn't skip frames, doesn't cause desync and that records both game and mic audio.
- A video editor which will not be impossible to use, can handle .ogv files correctly and can sync audio correctly.
- An emulator (like WINE), that has Screen Capturing capabilities.

I got a reply last time saying I should provide information... well here you go:
1). Virtualbox v3.2.8_OSE r64453
2). WINE v 1.2.1
3). Ubuntu Linux 11.04
4). Kdenlive v0.7.8
5). gtk-recordmydesktop v0.3.8
6). Ffmpeg (version ?, used guide in forum)

I cannot do all of this on my original Ubuntu. As my guardian doesn't want me to install multiple programs and games. The virtualbox DOES have max cpu and memory being used.

My PC specs:
- Intel Core i7 Duo Processor (3.1Ghz)
- 6GB RAM
- Nvidia GT220 (1GB) Video Card


If I don't get a reply. I will laugh. I have asked similar questions like this before, for around a week, and have not gotten more than one reply.

Help me.... please?

---

### Post by hgernhardt on 2011-01-18
Cessusbangy—

Have you tried using the command-line version of recordmydesktop?  I've not had *any* luck whatsoever in using the GUI frontends thereto.

Here's the command line I use:

```

recordmydesktop -x 0 -y 290 --width 1280 --height 800 --device hw:2,0 --delay 5

```

A bit of explanation:
[LIST]
[*][FONT="Courier New"]**-x 0 -y 290**[/FONT]: sets the x and y coordinates of the recordmydesktop viewport.
[*][FONT="Courier New"]**--width 1280 --height 800**[/FONT]: sets the width and height of the viewport
[*][FONT="Courier New"]**--device hw:2,0**[/FONT]: The ALSA device identifier for the audio input device I will be using.  See also [FONT="Courier New"]/proc/asound/cards[/FONT].
[*][FONT="Courier New"]**--delay 5**[/FONT]: Delay 5 seconds before beginning screen capture.
[/LIST]

The recordmydesktop manual shows several other switches which may be useful, including framerate (defaults to 15), whether or not to take full screen shots every frame (necessary/default if you're using compositing).

That's about the limit of my knowledge in this area.  By ditching the GUI and going CLI, I've managed to get success in generating reasonable screencasts.

Good luck,

Henry

---

