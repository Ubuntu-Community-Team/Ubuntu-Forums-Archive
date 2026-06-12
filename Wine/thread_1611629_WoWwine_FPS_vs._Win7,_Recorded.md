---
title: "WoW/wine FPS vs. Win7, Recorded"
date: 2010-11-02
forum: Wine
---

### Post by cwwilson721 on 2010-11-02
I have stated for a while, on this forum and others (AND in my sig), that WoW/wine has faster FPS than Windows7.
I tend to hear alot of "wine cannot be faster, because it's not native' and 'Windows has to be slower, because of the extra overhead"

They both can't be right. But, how do I go about a test, and show the results? I thought about it for a LONG time.

Well, I finally broke down, and recorded two runs around Ironforge on my mounted 80 Hunter. First in Windows 7 Ultimate 64-bit, then once in Ubuntu 10.10 with wine 1.3. Both OSs had the LATEST drivers installed from Nvidia. (I like the new Windows install, BTW. And installing the *.run file from Nvidia is easy, too)

The ONLY difference between the 2 installs (besides the OS of course. Both are, at least, 64bit. They are EXACT copies of each other, down to the addons, WTF files, etc.) is appending '-opengl' at the end of the launcher command in Linux. Both runs have a large FPS graph from Recount, and both show the Latency graph from Recount in the lower right hand corner. 

I recorded Windows 7 first, using FRAPS. Then, after a quick reboot, logged in WoW/wine, and recorded the same trip with gtk-recordmydesktop. In both movies, you can see the FPS and Latency graph.

The results shocked me. It's clear what is going on.

What are the results? Well, check [World of Warcraft: Windows 7 vs Linux/wine....FPS: Who wins?]("http://www.youtube.com/watch?v=xQFBK1yNIxE")

In the meantime, how about YOU post what YOU think the results will be?

Will WoW/wine or WoW/Windows 7 be 'faster'?
And why?

---

### Post by cwwilson721 on 2010-11-02
Here it is:

[World of Warcraft: Windows 7 vs Linux/wine....FPS: Who wins?]("http://www.youtube.com/watch?v=xQFBK1yNIxE")

Took awhile for YouTube to process the video, but can be viewed in 720P now...

---

### Post by Refalm on 2010-11-02
In my experience, TF2 runs better in Wine than Win7, but CoD:MW2 runs worse in Wine than Win7.

I think the results are kinda like that. It depends on how many people voted for fixes in AppDB.

---

### Post by cwwilson721 on 2010-11-02
Post 2 has the link

---

### Post by cwwilson721 on 2010-11-02
> **Refalm said:**
> In my experience, TF2 runs better in Wine than Win7, but CoD:MW2 runs worse in Wine than Win7.

I think the results are kinda like that. It depends on how many people voted for fixes in AppDB.
If the game is D3D only, it will run worse in wine.

---

### Post by t.rei on 2010-11-02
They are working on that. But that was my experience as well. And it's not just the fps that is (only slightly for me) better, but the load-times on zoneing are amazingly better on linux. Guess no swapping when not needed is kindof helping. I'm not talking about a few percent here. Linux Zoning is about 1/5th of the same setup under win7. So no more booting that. (well actually I don't play anymore... who has the time?)

---

### Post by Refalm on 2010-11-02
Multiplayer games run better in Linux and Windows XP, since Windows 7 has this multimedia scheduler that put games on a lower priority, that results in massive lag and sound stutter.

One of the reasons for switching to Ubuntu was that there is way less junk like Windows 7 is full with.

---

### Post by cwwilson721 on 2010-11-02
In case you couldn't read the graphs, here's the results:

Windows 7 Ultimate 64bit/Direct 3D: 25-30 FPS, 125 Latency
Ubuntu 10.10 64bit/wine 1.3/OpenGL: 50 FPS, 75 Latency

I usually get 20-30% increase in FPS in wine/WoW, not 100%. The differences are probably due to using the screen record.

Linux/wine does, however, turn 'choppy' here and there, but usually for VERY short times. I think it may be due to WoW's opengl server-side, and wine's opengl over D3D conversion process, more than any major flaw.

The latency cannot be underestimated, though. Lower lag ALWAYS means higher framerates, no matter the game. If you're running lower lag than the other guy w/identical hardware, your FPS will be higher. This result here shows how much more efficient Linux's TCP/IP stack is as compared to Windows 7 (And I HAVE edited Windows 7 registry to maximize throughput in TCP/IP.)

Another thing is my CPU usage and ram usage (not shown in video). In Windows 7, my CPU cores are almost maxxed out (75% on one core, most of the time), and ram at 75% usage. Raids are MUCH higher, 90% and 75% +. In Linux, however, I have 50% usage on one core, and ram at 50%, with raids at 75% and 60% (I do run Windows 7 with absolute MIN programs running in background. In Linux, I ONLY disable Compiz, otherwise, all my usual programs are running, like IM clients, etc)

So, to summarize:

Windows 7: 25-30 FPS, 125 Latency, 75% CPU, 75% ram usage
Linux/wine: 50 FPS, 75 Latency, 50% CPU, 50% ram

Linux/wine wins due to: Better TCP/IP stack, better CPU and ram utilization, and overall efficiency.

So to those that say "wine is slower than native Windows", I say the proof you are wrong is at [World of Warcraft: Windows 7 vs Linux/wine....FPS: Who wins?]("http://www.youtube.com/watch?v=xQFBK1yNIxE")

And spread the word.

---

### Post by cwwilson721 on 2010-11-02
I'd like to hear from you on your opinion on why WoW/wine is running faster than WoW/Win7

---

### Post by gyussz on 2010-11-04
Can I see your config.wtf?

---

### Post by St0 on 2010-11-04
Can WoW run in openGL on Windows? that would be a better comparison. I really like Ubuntu but hate how you have to rely on Wine to make games work, this OS could be amazing if developers just supported it more. 
I bet it's because MS pay them to develop games for Windows :(

---

### Post by cwwilson721 on 2010-11-04
> **St0 said:**
> Can WoW run in openGL on Windows? that would be a better comparison. I really like Ubuntu but hate how you have to rely on Wine to make games work, this OS could be amazing if developers just supported it more. 
I bet it's because MS pay them to develop games for Windows :(Yes, you can play WoW in opengl in Windows the same way you do for Linux, either edit the config.wtf, or append '-opengl' at end of launch command), but there is a performance hit. I went with what was best for each OS, as far as opengl and D3D is concerned.

---

### Post by _outlawed_ on 2010-11-04
Just wondering if you were running on maximum graphics settings for both tests?

Also these numbers will vary taking into consideration a number of factors that are too many to name.

I get better FPS in Windows 7 on WoW than I do in Linux, considering the fact that my graphics card is intel and intel is more leaned towards Windows drivers.

---

### Post by cwwilson721 on 2010-11-05
Not just "leaned" anymore. You will be VERY lucky for WoW/wine to run at all with an Intel videochip.

As for settings, they are custom I prefer FPS to eyecandy.

While I can set everything to 'max', I would die in raids. I would MUCH rather be able to move around at 50 FPS and kill the Lich King than be at 10 FPS (or less) and say "Look at the pretty effects!" and have Raid Lead say "Rez the Hunter...AGAIN".

If you read the "Information" area on the video (or my sig), you would know my computer is NO powerhouse by any stretch of the imagination.

This was a straight-up, EXACT copy between Linux and Windows 7, settings and all, comparison. I removed all the variables by this. The ONLY difference is I appended '-opengl' at the end of the launch command in Linux. config.wtf, addons, settings, hardware, what I was wearing, and what was on my shelf in the library were IDENTICAL.

While I could have launched Windows 7 WoW in OpenGL mode also, that would not be fair. Windows does not do OpenGL as well as D3D, and there is a definite performance hit.

I LOVE the latency difference, too. 1/2 compared to Windows. THAT gives you a FPS boost right there.

---

### Post by cwwilson721 on 2010-11-05
> **gyussz said:**
> Can I see your config.wtf?This is the config.wtf I used when making the movies:
```
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET patchlist "enUS.patch.battle.net:1119/patch"
SET hwDetect "0"
SET gxResolution "1280x720"
SET gxRefresh "53"
SET gxVSync "0"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "4"
SET mouseSpeed "1"
SET Gamma "0.900000"
SET accounttype "LK"
SET VoiceActivationSensitivity "0.39999997615814"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "507"
SET particleDensity "40"
SET environmentDetail "75"
SET weatherDensity "1"
SET ffxGlow "0"
SET ffxDeath "0"
SET realmName "Caelestrasz"
SET gameTip "70"
SET uiScale "0.78999996185303"
SET gxWindow "1"
SET Sound_OutputQuality "2"
SET Sound_NumChannels "64"
SET Sound_EnableHardware "1"
SET Sound_EnableMusic "0"
SET Sound_EnableDSPEffects "0"
SET Sound_EnableSoftwareHRTF "1"
SET Sound_EnableEmoteSounds "0"
SET Sound_EnablePetSounds "0"
SET showChatIcons "1"
SET Sound_EnableAllSound "0"
SET accountName "cwwilson721@gmail.com"
SET g_accountUsesToken "1"
SET playIntroMovie "4"
SET reflectionMode "0"
SET groundEffectDensity "40"
SET groundEffectDist "110"
SET maxFPS "0"
SET maxFPSBk "0"
SET textureFilteringMode "0"
```

Had to do window mode to be sure I could access the recorders...lol

---

### Post by _outlawed_ on 2010-11-05
> **cwwilson721 said:**
> ...

That couldn't be farther from the truth. lol

While I can get WoW to work with Wine, and get some *decent* FPS when like starting a new character and such...I have never really tested going through Orgrimmar at peak times....or hell even Dalaran during peak times.

But I have to admit, at least I could get WoW going....I couldn't play ANY games back on Karmic whatsoever. Lucid made that possible, and it got even better with Maverick.

I get like 25-35 FPS on lowest settings on Windows 7 (stock Gateway laptop ;p) and will have to post here my FPS on linux (currently copying WoW files over from my backup dvd).

And as far as your comp specs go, your computer is a powerhouse compared to mine.

[http://support.gateway.com/s/Mobile/2008/OasisSR/1015480R/1015480Rsp2.shtml](http://support.gateway.com/s/Mobile/2008/OasisSR/1015480R/1015480Rsp2.shtml)

---

