---
title: "Pay To Use Desktop Recorder"
date: 2011-03-24
forum: The Cafe
---

### Post by Lucradia on 2011-03-24
I'm looking into buying desktop recording software in the near future. However, does anyone know which of them all takes advantage of 64-bit hardware so that it doesn't slow down unbelievably when recording, and ends up showing lag when playing the video?

CamStudio doesn't work at all that well (nor does Taksi); and I can't get 2.6 or 2.0 to work with ffmpeg anymore (ffmpeg is limited to FFV1 and uncompressed now in camstudio for some reason.)

**Must be for Windows**. It can't be camstudio, as ffdshow can't send the encoders it uses completely:

[img]http://i.imgur.com/ZGOGA.png[/img]

it can't be lossless if it must be open-source; as most have a restriction to 2 GB of data, or else it will crash.

---

### Post by HermanAB on 2011-03-24
Istanbul uses ffmpeg and should be the fastest of the lot.

---

### Post by FakeOutdoorsman on 2011-03-24
You could try using FFmpeg directly:

[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026).

---

### Post by Lucradia on 2011-03-24
Has to be windows, actually. Forgot that bit.

---

### Post by NightwishFan on 2011-03-24
Perhaps try this list:
[https://secure.wikimedia.org/wikipedia/en/wiki/Comparison_of_screencasting_software](https://secure.wikimedia.org/wikipedia/en/wiki/Comparison_of_screencasting_software)

Personally I just use the ffmpeg binary not sure how to on Windows though.

Edit: Oh yeah VLC as well can, not sure of how much it can do though.

---

### Post by FakeOutdoorsman on 2011-03-24
> **Lucradia said:**
> Has to be windows, actually. Forgot that bit.

That's a fairly important piece of info, but I should have guessed with the word *CamStudio*. What about FRAPS?

---

### Post by Lucradia on 2011-03-24
> **FakeOutdoorsman said:**
> That's a fairly important piece of info, but I should have guessed with the word *CamStudio*. What about FRAPS?

Fraps isn't made to handle x64 is it, and do the games must be in full screen? Because some games look horrible at full screen.

---

### Post by NightwishFan on 2011-03-24
I am fairly sure you will find few 64-bit applications of the sort unless you compile them yourself. Also, I find it highly unlikely it will make much of a difference to be honest. Test out a few and see if they are capable. You could also prioritise them using the Windows Task Manager so they get a higher share of the cpu.

---

### Post by Lucradia on 2011-03-24
> **NightwishFan said:**
> I am fairly sure you will find few 64-bit applications of the sort unless you compile them yourself. Also, I find it highly unlikely it will make much of a difference to be honest. Test out a few and see if they are capable. You could also prioritise them using the Windows Task Manager so they get a higher share of the cpu.

I tried that with camstudio (which requires you to run it as admin), no change at all. If I set a game to low, it causes itself to be laggy. Realtime can cause (and has) my computer to crash. Yes, it's the "Main System" in my signature. If you don't remember, it has AMD Phenom II X6, all six cores at 2.6 GHz (they can't be overclocked to more than 2.8 GHz. Windows 7 will also still show them at 2.66 GHz if I overclock anyway.)

The graphics card being NVIDIA GTX 470, which, believe it or not, struggles with Dragon Age: Origins.

it's funny, because I never had this problem with Intel Core 2 Duo at 3.2 GHz for two cores, on an nvidia GTS 250 with Windows XP x64.

---

### Post by Quadunit404 on 2011-03-24
I have a Fraps license and it's a 32-bit application, but videos are pretty flawless regardless of what your architecture is. I recorded a few videos using it myself.

[http://www.youtube.com/watch?v=jNYPb81kdZ8]("http://www.youtube.com/watch?v=jNYPb81kdZ8")
[http://www.youtube.com/watch?v=f6b9gGegFkI]("http://www.youtube.com/watch?v=f6b9gGegFkI")
[http://www.youtube.com/watch?v=DS_Or0FsUZM]("http://www.youtube.com/watch?v=DS_Or0FsUZM")
[http://www.youtube.com/watch?v=oeSgHWSGGfM]("http://www.youtube.com/watch?v=oeSgHWSGGfM")
[http://www.youtube.com/watch?v=iHW7hDrLUOU]("http://www.youtube.com/watch?v=iHW7hDrLUOU")

All the above videos were recorded at 30FPS, 720p, on a Core i5 M460 @ 2.53GHz that overclocked itself to 2.80GHz (lol Intel Turbo Boost,) 4GB DDR3 RAM @ 1066MHz and Windows 7 Home Premium 64-bit, with all the games on max settings if possible. Not to brag about my PC's specs or anything, but for recording games you can't beat Fraps regardless of how good your PC is.

PS: If you're trying a Source game there's always the built-in recorder as well, which is probably the only thing capable of beating Fraps for recording as the raw video it produces **always** has a perfect frame rate.

---

### Post by Lucradia on 2011-03-24
Just a question, is a fraps license permanent? Or if there's a major version, do we have to pay a discount for the upgrade?

---

### Post by Quadunit404 on 2011-03-24
Once you buy it Fraps is yours forever. All updates are free, too.

---

