---
title: "Wine &amp; Team Fortress 2 &amp; My Microphone"
date: 2009-05-06
forum: Wine
---

### Post by GregMB on 2009-05-06
So, I got The Orange Box (Half-Life 2 + Episodes 1 and 2, Portal, and TF2) working perfectly under wine. The only bugs I have are being unable to view MOTDs (not big enough of a problem for me to complain about), and my microphone working sporadically, if at all.

Basically, here's how it works: I start up TF2, I connect to a server, I talk, and everyone tells me to stop talking. I put "voice_loopback 1" in the game console, and, they aren't joking, my mic is terrible. It was a sort of a staticy sound in 8.10, but now it more sounds like I'm talking under water. But after a while, I can say one sentence before it messes up again. I've tried every possible in game option, I've Googled for the answer, and I searched the forums. Some people have suggested removing PulseAudio for similar problems, but I don't know if that would help.

It's a Wine problem, my mic works fine in Skype. I'm using Ubuntu 9.04 Jaunty.

Any suggestions are greatly appreciated.

---

### Post by u235sentinel on 2009-05-07
> **GregMB said:**
> So, I got The Orange Box (Half-Life 2 + Episodes 1 and 2, Portal, and TF2) working perfectly under wine. The only bugs I have are being unable to view MOTDs (not big enough of a problem for me to complain about), and my microphone working sporadically, if at all.

Basically, here's how it works: I start up TF2, I connect to a server, I talk, and everyone tells me to stop talking. I put "voice_loopback 1" in the game console, and, they aren't joking, my mic is terrible. It was a sort of a staticy sound in 8.10, but now it more sounds like I'm talking under water. But after a while, I can say one sentence before it messes up again. I've tried every possible in game option, I've Googled for the answer, and I searched the forums. Some people have suggested removing PulseAudio for similar problems, but I don't know if that would help.

It's a Wine problem, my mic works fine in Skype. I'm using Ubuntu 9.04 Jaunty.

Any suggestions are greatly appreciated.

I haven't been able to get it working and have had the same issues you describe with the mic.

I'd be VERY interested in a solution.  any solution for this.

I've also tried killing pulseaudio, installing oss, messing with various sound cards (bought 4 of them in the last couple months.. all sound blaster) and so on.

help :D

there has got to be a way to make this work.

---

### Post by GregMB on 2009-05-07
Well, I'm glad that I'm not the only one with this problem. I haven't done anything as drastic as change sound cards, but I have changed mics, to no avail. If you do get it working, please tell me how you did it.

---

### Post by u235sentinel on 2009-05-08
> **GregMB said:**
> Well, I'm glad that I'm not the only one with this problem. I haven't done anything as drastic as change sound cards, but I have changed mics, to no avail. If you do get it working, please tell me how you did it.

I know the mic works.  I'm able to record my voice using sound recorder and can play it back just fine.  But in looking through the winehq entries I keep hearing people say there is a registery fix to make it work.  I'm looking and can't find what that change is.

If I do figure it out I'll certainly post it.

---

### Post by GregMB on 2009-05-11
Bump because I naively believe that if enough people see this it will get fixed.

---

### Post by u235sentinel on 2009-05-12
> **GregMB said:**
> Bump because I naively believe that if enough people see this it will get fixed.

I hope so.  I'm tired of getting killed while I'm typing to my team mates :D

But it's not enough motivation to go back to Windows.  I'm soooo sick of Microsoft's predatory attitude, DRM and a host of other problems (read Vista) that I decided to move my families computers over to Ubuntu.  We have some Windows XP still (we did buy it after all) but it's history.  Using it for Video Editing since Linux video editing is still really bad :/

And the mic I can live without but It's a really nice to have.

---

### Post by GregMB on 2009-06-02
Bump. I figure I'll give this thread one last chance.

---

### Post by u235sentinel on 2009-06-02
> **GregMB said:**
> Bump. I figure I'll give this thread one last chance.

I'm wondering if the Wine developers have made any progress on this problem.  I've looked around and haven't found anything that suggests they have but it would be VERY nice to hear of a solution. :D

---

### Post by sherl0k on 2009-06-03
I'll tell you right now that using Crossover Games, the mic was working for me. I never tried installing/getting it to work in Wine. But they're both based off of the same code, CX is just a bit more advanced.

The best thing I can tell you is that you should remove PulseAudio altogether, then reboot. In your sound preferences set ALSA as the default for everything. Run winecfg, and set ALSA as the default sound server there, too.

Wine/CX has zero support for Pulse, and it wasn't until I completely removed it from my system, that I got it working.

If you're worried about removing Pulse and breaking other apps, don't. Pulse is just a sound server like ESD or aRts, it works on the software level. Every app that I've come across I can set to use ALSA and I haven't had a problem yet.


Plus, if all else fails, you can just reinstall it. :)

---

### Post by u235sentinel on 2009-06-04
> **sherl0k said:**
> I'll tell you right now that using Crossover Games, the mic was working for me. I never tried installing/getting it to work in Wine. But they're both based off of the same code, CX is just a bit more advanced.

The best thing I can tell you is that you should remove PulseAudio altogether, then reboot. In your sound preferences set ALSA as the default for everything. Run winecfg, and set ALSA as the default sound server there, too.

Wine/CX has zero support for Pulse, and it wasn't until I completely removed it from my system, that I got it working.

If you're worried about removing Pulse and breaking other apps, don't. Pulse is just a sound server like ESD or aRts, it works on the software level. Every app that I've come across I can set to use ALSA and I haven't had a problem yet.


Plus, if all else fails, you can just reinstall it. :)
I've disabled pulseaudio but it comes across as screeching really bad. :/

I'm messing with 7.2.0 demo and I'm surprised how it solved several problems with Oblivion (for example).  Now that game works just great with full music and sound without crashing!!

So I'm purchasing it I guess.  At least I have CSS and TF2 mostly working under Wine.  If I can get the mic working it would be a bonus :D

---

### Post by GregMB on 2009-06-04
> **sherl0k said:**
> I'll tell you right now that using Crossover Games, the mic was working for me. I never tried installing/getting it to work in Wine. But they're both based off of the same code, CX is just a bit more advanced.

The best thing I can tell you is that you should remove PulseAudio altogether, then reboot. In your sound preferences set ALSA as the default for everything. Run winecfg, and set ALSA as the default sound server there, too.

Wine/CX has zero support for Pulse, and it wasn't until I completely removed it from my system, that I got it working.

If you're worried about removing Pulse and breaking other apps, don't. Pulse is just a sound server like ESD or aRts, it works on the software level. Every app that I've come across I can set to use ALSA and I haven't had a problem yet.


Plus, if all else fails, you can just reinstall it. :)

You know, a while ago I got a free copy of CX from a giveaway or something, and I actually tried installing TF2 under CX just so that my mic could work. And it didn't. But maybe I'll try that "removing pulse" idea.

---

### Post by fred583 on 2009-06-13
I have the same trouble : microphone works fine outside of wine in Jaunty. But with wine, no way to get it work, even with an usb microphone (and of course I have tried a microphone connected on my soundboard too).
Going to try removing pulseaudio...

And it solved the trouble !
Wine was allready configured for using alsa, I have juste removed the pulseaudio package (and ubuntu-desktop, which seems empty and here just to gather dependencies for install/update purposes, and depends on pulseaudio).
Now my microphone works under WoW, under windows TS on wine, and even simultaneously under wine TS and WoW.
Thanks sherl0k for suggesting removing pulseaudio.

---

### Post by GregMB on 2009-06-20
> **fred583 said:**
> I have the same trouble : microphone works fine outside of wine in Jaunty. But with wine, no way to get it work, even with an usb microphone (and of course I have tried a microphone connected on my soundboard too).
Going to try removing pulseaudio...

And it solved the trouble !
Wine was allready configured for using alsa, I have juste removed the pulseaudio package (and ubuntu-desktop, which seems empty and here just to gather dependencies for install/update purposes, and depends on pulseaudio).
Now my microphone works under WoW, under windows TS on wine, and even simultaneously under wine TS and WoW.
Thanks sherl0k for suggesting removing pulseaudio.

Hmm. I'll try that out. I hope it works.

---

