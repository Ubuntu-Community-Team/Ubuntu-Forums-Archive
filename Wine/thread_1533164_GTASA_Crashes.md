---
title: "GTA:SA Crashes"
date: 2010-07-17
forum: Wine
---

### Post by LuciusMare on 2010-07-17
Hi, I installed Grand Theft Auto San Andreas, it installed without a flaw, but when I tried to run it, my display screamed "Out of range" - as it happens with many other games, the game tries to set a frequency the monitor can't handle. So I turned on "desktop emulation" in wine, but then, after seeing the intro screen (NVIDIA, main picture), it crashes with the infamous "Do not send" screen. Here is the log: [http://pastebin.com/YaaCCquz](http://pastebin.com/YaaCCquz)
And as I said, my wine configuration is following:
Audio set on OSS, hardware acceleration on.
Graphics: Virtual desktop, and following a guide I found, Vertex shading off, pixel shading off (no effect)

---

### Post by asdfoo on 2010-07-18
> **LuciusMare said:**
> Hi, I installed Grand Theft Auto San Andreas, it installed without a flaw, but when I tried to run it, my display screamed "Out of range" - as it happens with many other games, the game tries to set a frequency the monitor can't handle. So I turned on "desktop emulation" in wine, but then, after seeing the intro screen (NVIDIA, main picture), it crashes with the infamous "Do not send" screen. Here is the log: [http://pastebin.com/YaaCCquz](http://pastebin.com/YaaCCquz)
And as I said, my wine configuration is following:
Audio set on OSS, hardware acceleration on.
Graphics: Virtual desktop, and following a guide I found, Vertex shading off, pixel shading off (no effect)

The out of range problem is not Wine's fault.  Your X server has a list of valid modes and refresh rates which your video driver has made available, type xrandr at a terminal to see these.

I've heard that this problem has issues with copy protection and may require a nocd patch.

---

### Post by LuciusMare on 2010-07-18
I know it's not, it's mainly my screen problem, I guess. (Anyway, you mean that I can disable the game trying to set the frequency my screen can't handle?)

I've already got nocd patch (It was in the guide, I own the game), no effect.
edit: Hm, I see it's a fairly common problem... [http://www.google.com/search?q=%23+Unhandled+exception%3A+page+fault+on+read+access+to+0x00000000+in+32-bit+code+(0x004dd5a3](http://www.google.com/search?q=%23+Unhandled+exception%3A+page+fault+on+read+access+to+0x00000000+in+32-bit+code+(0x004dd5a3)) Too bad. Anyway, if anyone finds a solution, I would be grateful.

---

### Post by LuciusMare on 2010-07-18
Catching on the "fixme:d3d:buffer_PreLoad Too many declaration changes or converting dynamic buffer, stopping converting" line right before starting debugger, I found a thread, which might be related to my problem - [http://ubuntuforums.org/showthread.php?t=1510607](http://ubuntuforums.org/showthread.php?t=1510607) - I dimly remember doing so, though now I run GTA:SA through PlayOnLinux, which even uses it's very own way to run games, it gives each game it's own drive, so I guess it does not apply. 

Next one:
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
Eliminated by removing the movies, I guess -  I don't even remember showing it up after reinstalling it through playonlinux...

The third:
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
Googling the link got me to another directx related thread, and weird enough, gta:sa related thread. The thread is located here: [http://www.daniweb.com/forums/thread105689.html](http://www.daniweb.com/forums/thread105689.html) But I don't find any valuable information here.

next result is actually from ubuntuforums, yet the advice (remove the movies) here didn't help me, as explained above: [http://ubuntuforums.org/archive/index.php/t-583733.html](http://ubuntuforums.org/archive/index.php/t-583733.html)

I continued my search but with no actual results.

And the last:
fixme:win:EnumDisplayDevicesW ((null),0,0x177f294,0x00000000), stub!
After removing the very specific parts (the adresses) and googling, I found something related to video card, but I found that people even had gta:sa running out of the box with nvidia, and my drivers are updated, so this also seems like a dead end.

Any more ideas appreciated. (wine version 1.1.42)

---

### Post by asdfoo on 2010-07-18
I suggest you use Wine-1.2, 1.1.42 was not the best release.

---

### Post by LuciusMare on 2010-07-19
Still the same, and appdb even reports more people with 1.2 failing to run gta:sa.

---

### Post by asdfoo on 2010-07-19
could be a regression then, someone may have to file a bug report if there isn't one open already

---

### Post by LuciusMare on 2010-07-20
Great new news! The problem is simply solved by applying a "no-intro" patch! You can find one on google, I won't provide a direct link. Well, I guess it's solved by now, thank you anyway :)

---

### Post by asdfoo on 2010-07-20
good work :)  you could probably put a comment on the AppDB to help other people

---

### Post by LuciusMare on 2010-07-21
Okay, even different solution: After an unfortunate mistake, I had to reinstall GTA:SA, but after applying the patches, the error showed up again! I tried to recall what did I do differently... And the real solution seems to be, to install complete GTA:SA, not to leave out the sounds, by installing "custom". I guess one should also apply the patches, I have not tried. I am going to write the comment.

---

