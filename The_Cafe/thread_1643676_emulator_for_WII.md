---
title: "emulator for WII?"
date: 2010-12-12
forum: The Cafe
---

### Post by honeybear on 2010-12-12
[http://blogs.theage.com.au/screenplay/archives/Wii.jpg](http://blogs.theage.com.au/screenplay/archives/Wii.jpg)

edit: 

An emulator for linux which can playing WII gaming nintendo

---

### Post by chriswyatt on 2010-12-12
[IMG]http://i28.photobucket.com/albums/c226/chriswyatt/clippy.png[/IMG]
Fragment (consider revising)



Do you mean an emulator that runs on Wii or a Wii emulator for Linux?

---

### Post by CharlesA on 2010-12-12
It helps to ask a specific question instead of leaving a vague remark. :)

Doesn't seem like a game, so moved to the Cafe.

---

### Post by Spice Weasel on 2010-12-12
> **chriswyatt said:**
> [IMG]http://i28.photobucket.com/albums/c226/chriswyatt/clippy.png[/IMG]

Thanks a lot... I'll be getting nightmares about 16-bit-colour office equipment tonight.

---

### Post by chriswyatt on 2010-12-12
> **Spice Weasel said:**
> Thanks a lot... I'll be getting nightmares about 16-bit-colour office equipment tonight.

[IMG]http://i28.photobucket.com/albums/c226/chriswyatt/clippy.png[/IMG]
You appear to be having a dream. ;)

---

### Post by CharlesA on 2010-12-12
Lawl.

---

### Post by zekopeko on 2010-12-12
[http://www.dolphin-emulator.com/](http://www.dolphin-emulator.com/)

Supports both Wii and Gamecube. I haven't tried it in Ubuntu but it works very nicely in Windows.

---

### Post by cchhrriiss121212 on 2010-12-12
> I haven't tried it in Ubuntu but it works very nicely in Windows
Works nicely on Ubuntu as well, there is a thread in the Gaming & Leisure section where someone nice has made a binary package available for download. 

[found it]("http://ubuntuforums.org/showthread.php?t=1565775")

I use 64 bit, and have seen reports the 32 version is a bit buggier. You will need a recent/decent cpu for most games.

---

### Post by honeybear on 2010-12-12
> **zekopeko said:**
> [http://www.dolphin-emulator.com/](http://www.dolphin-emulator.com/)

Supports both Wii and Gamecube. I haven't tried it in Ubuntu but it works very nicely in Windows.

but on the video, it looks to lag a lot , no?

[http://www.youtube.com/watch?v=n2-vm2i0h70&feature=related](http://www.youtube.com/watch?v=n2-vm2i0h70&feature=related)

---

### Post by Quadunit404 on 2010-12-12
I think you'll need a hella powerful PC in order to get playable speeds. I remember seeing this guy on YouTube playing the game in Dolphin... on a 4.2GHz Core i7.

---

### Post by JustinR on 2010-12-12
Its better to compile the program from source - its REALLY REALLY EASY.
[http://code.google.com/p/dolphin-emu/wiki/Linux_dependencies](http://code.google.com/p/dolphin-emu/wiki/Linux_dependencies)

And on my Dell Inspiron 1720, 2GHZ Dual Core, 3GBS of RAM, with Wii games I get around 30-60FPS. On the GameCube I get full speed.

If you have a newer computer with bluetooth, you can even use the Wii Remote with Dolphin.

---

### Post by cchhrriiss121212 on 2010-12-12
> **Quadunit404 said:**
> I think you'll need a hella powerful PC in order to get playable speeds. I remember seeing this guy on YouTube playing the game in Dolphin... on a 4.2GHz Core i7.
Not really necessary. I use a Athlon II 245 @ 3.3 Ghz which does nearly everything on full speed. A few more hungry games dip down to about 70%.

---

### Post by Quadunit404 on 2010-12-12
> **cchhrriiss121212 said:**
> Not really necessary. I use a Athlon II 245 @ 3.3 Ghz which does nearly everything on full speed. A few more hungry games dip down to about 70%.

I need a better computer then, because I have an AMD Athlon 64 X2 QL-62 @ 2GHz and I only got like 2FPS in Metroid Prime :lol:

Fortunately I should be getting a new one  by the time I turn 18 (which just HAPPENS to be the day after Natty Narwhal is released :wink:)

---

### Post by JustinR on 2010-12-12
> **Quadunit404 said:**
> I need a better computer then, because I have an AMD Athlon 64 X2 QL-62 @ 2GHz and I only got like 2FPS in Metroid Prime :lol:

Fortunately I should be getting a new one  by the time I turn 18 (which just HAPPENS to be the day after Natty Narwhal is released :wink:)

Your CPU is fine - but you need a more powerful GPU. Dolphin makes use of it heavily and requires at least a nVidia 8600 GT or similar ATI card.

---

### Post by cchhrriiss121212 on 2010-12-12
> AMD Athlon 64 X2 QL-62 @ 2GHz
> Your CPU is fine
That CPU will still be a bottleneck even with a new GPU. Intel outperform AMD by a small margin, and older CPUs will not compare to newer ones due to architecture.

---

### Post by Quadunit404 on 2010-12-12
My next laptop is going to have a NVIDIA GTX 310M (or maybe a GTX 330M) and will either have a Core i3 or i5... and 4GB DDR3 RAM. Will that be good enough for Dolphin?

And yeah, my GPU sucks. It's okay in TF2 but an emulated GameCube? Even though the processor is the PowerPC equivalent of... oh, I dunno, maybe a Pentium Pro and the GPU is from, like, 2001, we can't have that.

---

### Post by cchhrriiss121212 on 2010-12-12
> My next laptop is going to have a NVIDIA GTX 310M (or maybe a GTX 330M)  and will either have a Core i3 or i5... and 4GB DDR3 RAM. Will that be  good enough for Dolphin?
Google and ye shall find:
[http://forums.dolphin-emulator.com/showthread.php?tid=10769&pid=102308#pid102308](http://forums.dolphin-emulator.com/showthread.php?tid=10769&pid=102308#pid102308)

---

### Post by wewantutopia on 2010-12-13
There is a repository for Dolphin-emu

```
sudo add-apt-repository ppa:glennric/dolphin-emu
sudo apt-get update
sudo apt-get install dolphin-emu
```

---

