---
title: "Portal 2: low resolution, choppy sound"
date: 2011-06-20
forum: Wine
---

### Post by prshah on 2011-06-20
Hello,

I am facing some problems with Portal 2 in wine.

After I start playing the game, the sound cuts out altogether (after about 3-5 seconds of play starting). I also am not able to play smoothly at higher resolutions (Eg, can only play at 9xx X 5xx widescreen 16:9 resolution).

My System specs: Pentium Dual Core 1.6GHz / 2GB RAM / "01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)" / Proprietary drivers 260.19.06 / Intel HiDef onboard audio.

I installed off DVD, and it went very smoothly. I tried to play with the above problems. I then used winetricks to install d3dx9_36, directmusic and directsound.

Now sound/music stays throughout the game, but it is choppy. The game continues to be "laggy" at higher resolutions. Multicore rendering is active.

My system is no speed demon, but it should be able to handle this with ease.

I have also installed it in it's own WINEPREFIX, since I did not want to mess up existing settings; so it's as virgin an install as it's going to get. 

Maybe I need to install some other components? Should I install the entire directx9 (winetricks says "overkill").

Any tips and pointers appreciated.

Tech level: Intermediate-high.

---

### Post by Firezap on 2011-11-20
I know I may be really late to reply but this might help people in the future so yea.:)
Okay, I am assuming that you already have the game started and running. And most likely you have sound for the menu correct? The reason the sound cuts out is do to the sound driver. You need to change it to the ALSA sound driver. Just use winetricks. Select the change settings then select "sound=alsa". This should fix the audio. In the start of the game though around when you first see GlaDos again the audio usually cuts out again. Just set the subtitles on and get past that part and save. Then restart the game. You should now have smooth audio for the rest of the game. As for the low resolution part I really do not know what to tell you. Although this is a advanced game so this might just be your system. I have a Nvidia GT 240 and a over-clocked AMD Phenom II CPU that is running around 4 GHz and I still have bad framerates once in a while. Wine is great but it is not perfect. I also found a way to stop the stupid flashing mouse that a lot of people have but I forget what I did exactly, trying to remember...I will reply If I figure out what I did.:confused: Oh, I am using Wine 1.3.28.

---

