---
title: "How does WoW perform?"
date: 2010-11-21
forum: Wine
---

### Post by Kimm on 2010-11-21
I've been using Ubuntu only since it came out, but when I got my new computer a couple of months ago, my friends managed to convince me to install Win7 on it so that I could get better performace in WoW (since, in 10.04 I got a pretty lousy framrate). I have, however, started to remember why I dislike Windows so much... SO, my question is, how does it perform in Ubuntu 10.10? I figure the new Nvidia drivers (among other things) might boost the performance, I would really like to return to my good old ubuntu :)

---

### Post by cgolson84 on 2010-11-22
> **Kimm said:**
> I've been using Ubuntu only since it came out, but when I got my new computer a couple of months ago, my friends managed to convince me to install Win7 on it so that I could get better performace in WoW (since, in 10.04 I got a pretty lousy framrate). I have, however, started to remember why I dislike Windows so much... SO, my question is, how does it perform in Ubuntu 10.10? I figure the new Nvidia drivers (among other things) might boost the performance, I would really like to return to my good old ubuntu :)

I played wow on windows for a few years, XP, Vista and 7.  In wine i get a solid 60 frames per second with about as much stuttering as i got in windows.  I had some sound issues that were fixed when i removed pulseaudio.  I am using Linux Mint but i have about the same game quality when i boot into ubuntu 10.10 x64

---

### Post by cbilljones on 2010-11-22
performance should be comparable if you are using opengl, the disadvantage is some of the new effects arnt supported in opengl, so in windows with directx you can have all the effects, but that will reduce performance; so i see it as an acceptable tradeoff. At least we have hardware curser now though;)

---

### Post by cgolson84 on 2010-11-22
Honestly I don't use opengl and i get great framerates.  When i add the opengl tag, I don't see much difference. i get a few more of the eyecandy settings without using opengl.

---

### Post by cwwilson721 on 2010-11-23
You get more eye-candy w/D3D compared to opengl, but if you have the same settings between WoW/wine and WoW/Win7, well...

Here's [THE ANSWER]("http://www.youtube.com/watch?v=xQFBK1yNIxE")

---

### Post by Hairy_Palms on 2010-11-23
i generally get reasonably close FPS on both, the kicker i find is that wine doesnt multithread, so CPU heavy addons cause an FPS hit far more than on windows, but with the default UI it seems pretty even.

---

### Post by cwwilson721 on 2010-11-23
It's NOT even...[Watch the YouTube vid]("http://www.youtube.com/watch?v=xQFBK1yNIxE"). WoW/wine outdoes WoW/Win7 in FPS and Latency.

On the setup I made the vid with was:
[LIST]
[*]AMD Athlon X2 5200+ (No overclock)
[*]2GB DDR2 PC5300 (2x1GB, Dual Channel)
[*]Nvidia 9600 GS w/768MB DDR2, PCI-X16, no overclock, latest Linux and Windows drivers from Nvidia.com
[*]Onboard NV chipset NIC
[*]Windows 7 x64 Ultimate, recorded w/FRAPS
[*]Ubuntu X64 10.10, fully updated, recorded w/gtk-mydesktop 
[*]All Addons, settings, etc, EXACTLY the same. ONLY difference was WoW/wine was started w/'-opengl' added to commandline to start WoW. Win7 was started as usual
[*]wine used XP mode
[/LIST]
As you see in the video, the FPS was significantly higher in WoW/wine than WoW/Win7.

Some of that can be attributed to the lower latency of the Linux networking stack as compared to Windows. 1/2 the lag=higher framerates. (Lower times for data to transfer back/forth to servers ALWAYS helps)

Runs were made as close to each other as possible. Only the time taken for a reboot and logon to WoW and getting recording app started was in between the two runs.

I have since doubled my RAM, and will try to do another comparison (with sound this time...lol) when the patches, etc, settle down (Maybe after Cata comes out), so stay tuned...

---

### Post by Justin_Bailey on 2010-11-23
> **cgolson84 said:**
> Honestly I don't use opengl and i get great framerates.  When i add the opengl tag, I don't see much difference. i get a few more of the eyecandy settings without using opengl.

Technically you're still using OpenGL via DX conversion. ;)

---

### Post by cwwilson721 on 2010-11-23
> **Hairy_Palms said:**
> i generally get reasonably close FPS on both, the kicker i find is that wine doesnt multithread, so CPU heavy addons cause an FPS hit far more than on windows, but with the default UI it seems pretty even.
Since wine is currently ONLY 32-bit (there is a 64bit, but not ready for public consumption), as complexity goes up, speed goes down.

So, not only not multi-threaded, it's not 32bit (As is Wow itself. Really. Still 32bit)

Until a usable 64bit wine is released, all comparisons between WoW/wine and WoW/Win7 will only be comparable at lowest settings and least amount of addons possible.

---

### Post by Kimm on 2010-11-23
Thanks everyone, I'll be reformating this weekend ;)

> **cwwilson721 said:**
> Since wine is currently ONLY 32-bit (there is a 64bit, but not ready for public consumption), as complexity goes up, speed goes down.

So, not only not multi-threaded, it's not 32bit (As is Wow itself. Really. Still 32bit)

Until a usable 64bit wine is released, all comparisons between WoW/wine and WoW/Win7 will only be comparable at lowest settings and least amount of addons possible.

No, thats not right, since WoW is a 32 bit application it makes no difference what so ever if Wine is 32 or 64 bit.

---

### Post by GeoPirate on 2010-11-25
I've been using wine 64bit for the most part since 10.04 beta, it's perfectly usable, especially for wow.  I've gotten framerates about the same and lower latency on wow with wine for some time now.  There is some tweaking involved, but detailed instructions are here and on the ubuntu wiki.

---

