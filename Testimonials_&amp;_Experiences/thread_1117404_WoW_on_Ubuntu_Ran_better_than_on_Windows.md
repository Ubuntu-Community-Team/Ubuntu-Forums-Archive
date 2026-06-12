---
title: "WoW on Ubuntu: Ran better than on Windows"
date: 2009-04-05
forum: Testimonials &amp; Experiences
---

### Post by jpmelos on 2009-04-05
Three days ago, I installed WoW on Ubuntu. I used to play on Windows, mainly because I thought it would be hard to install, I would have to waste days to make it run correctly, etc, etc.

Well, I am using Ubuntu 8.10, downloaded Wine 1.1.18, installed WoW and patched it up to 3.0.9. During the installation, no problem. Everything installed successfully, I didn't have a single problem.

The game didn't run. The screen was black. I typed on Google "WoW Ubuntu". This page showed up: [https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft"). I followed everything in the Configuration section. And the game ran smooth. And from three days ago until now, the game didn't crash once, didn't lag once and no errors on models or anything ever occurred.

And I got a bonus: A bug actually is gone! On Windows, everytime I typed question mark, the last word of the message would be erased, so I'd have to add a random letter at the end of the message to be erased everytime I needed to use the question mark to send the message correctly. No big deal, but on Ubuntu, I have had no bug at all, not even a small one like that.

Ubuntu scores one more point!

---

### Post by murderslastcrow on 2009-04-05
Good job! I've found this true with WINE and many programs, including games. For instance, the MMO Nostale runs much quicker with no visible lag on Linux, all of the Prince of Persia games ran out of the box for me, and support is getting better every day.

I think it's important to note, not only the tremendous success of the WINE project so far in reimplementing the API for Linux flawlessly for many programs, but also the fact that Windows programs often run faster in Linux. This isn't just because the WINE code is efficient, but because the kernel has magnificent speeds and stability. Ideal for games.

Thank you so much for sharing your experience.

---

### Post by Ms_Angel_D on 2009-04-06
Thanks for sharing this My WOW playing Brother in law is trying to switch to Ubuntu but was having a few problems with getting everything up and going, I'll be sharing this post with him

Angel

---

### Post by jbysmith on 2009-04-06
> **MetalHellsAngel said:**
> Thanks for sharing this My WOW playing Brother in law is trying to switch to Ubuntu but was having a few problems with getting everything up and going, I'll be sharing this post with him

Angel

Most certainly doesn't apply to all games, but yes WoW runs absurdly well under Wine. On my system anyway, with WoW set to OpenGL mode, the frame rate is definitely improved, so is the loading time as well.  Running from say Deeprun Tram to Stormwind is near instant, *really* fast.

---

### Post by Ms_Angel_D on 2009-04-06
> **jbysmith said:**
> Most certainly doesn't apply to all games, but yes WoW runs absurdly well under Wine. On my system anyway, with WoW set to OpenGL mode, the frame rate is definitely improved, so is the loading time as well.  Running from say Deeprun Tram to Stormwind is near instant, *really* fast.

The bigget problem is that I live in Washington state and he's in Virginia So overcoming that factor alone so I can help him switch is something else to say the least...lol. 

However I did sign up for a 10 day WOW free trial and was able to install and run it on my Ubuntu with no problem. He's dual booting with XP and I think he wanted to be able to use the same install or at least copy over the games directory and run it. Possibly because he has Mods? Do you run any mods on your game? If so do they work ok, could you possibly list them?

My Husband and I play Guild Wars on our Ubuntu Computers and they run it fantastically in wine. No problems what so ever.

Angel

---

### Post by jbysmith on 2009-04-06
If he's just curious and doesn't want to commit, there's always the Wubi installer.  Painless install and even less painless to remove.  Great way to try it out without risking anything; it'll be a tick slower as you're dealing with a "virtual partition" on NTFS, but it's identical otherwise.

I've never had any issues simply copying the WoW directory back and forth across OS installations.. can just drag it off the NTFS host and drop it on your Linux desktop.. can *probably* run it right out of the host directory without copying it but I've never tried it.  (Is it /host?  I'm not positive.. only toyed with Wubi once... it's there somewhere.)   Again, if he's just testing, I'd just copy it so as not to mess with the source data... just in case.   If it doesn't work, no harm done and nothing risked.

And yes, I use a ton of mods.  XPerl, Clique, Bagnon/Banknon, Atlas and all its goodies, a few tooltip mods, an item database mod whos name slips my mind at the moment, etc etc.  Zero issues across the board.

The only issue I've had is with Compiz, no surprise there.  Performance was fine, but if I ran the game full screen then switched to another desktop, I'd "lose" the window, forcing me to do a "wineserver --k" in a console to stop the process.  But that's easily fixed too.  Tell WoW to run in a "full screen window", and problem solved.

---

### Post by Ms_Angel_D on 2009-04-06
> **jbysmith said:**
> If he's just curious and doesn't want to commit, there's always the Wubi installer.

No he already has the dual boot set up so we're good to go there. He loves Ubuntu and really wants to use it full time, His WOW Guild and the fact that he has obligations to it were the main reasons Windows was kept because we were not sure how to get it running on Ubuntu.

> **jbysmith said:**
> And yes, I use a ton of mods.  XPerl, Clique, Bagnon/Banknon, Atlas and all its goodies, a few tooltip mods, an item database mod whos name slips my mind at the moment, etc etc.  Zero issues across the board.

That's good to know I don't know which he uses but I'm emailing this post to him so he can look over and see which you've listed.

> **jbysmith said:**
> The only issue I've had is with Compiz, no surprise there.  Performance was fine, but if I ran the game full screen then switched to another desktop, I'd "lose" the window, forcing me to do a "wineserver --k" in a console to stop the process.  But that's easily fixed too.  Tell WoW to run in a "full screen window", and problem solved.

This might be the problem he may very well need to disable compiz why playing. Look most Noobs he's been bitten by the compiz love bug...:lolflag:


Angel

---

### Post by jbysmith on 2009-04-06
> **MetalHellsAngel said:**
> This might be the problem he may very well need to disable compiz why playing. Look most Noobs he's been bitten by the compiz love bug...:lolflag:

Heh myself included, I can't live without the bling.  Not just WoW but games in general are sometimes problematic with Compiz running.  On my particular hardware the performance is fine, usually gets me if I switch desktops.  The "full screen window" seems to work for me with WoW, other games obviously can have issues.  I've occasionally lost Guild Wars as well accidentally when it was running full screen; haven't tried it lately though so not sure if corrected yet.

Chances are his addons should work just fine; they're just LUA scripts being called internally, shouldn't be an issue but yea should be ready to deal with it, just in case.

One option is to install the Fusion Icon into the tray; can enable/disable Compiz with a click as needed.

Can always also make a script to do it for you too.  Basically call "metacity --replace", run the game, then "compiz --replace" when it's done.  It'll turn itself on and off as needed so you won't need to remember to do it.

---

### Post by jpmelos on 2009-04-06
> **MetalHellsAngel said:**
> However I did sign up for a 10 day WOW free trial and was able to install and run it on my Ubuntu with no problem. He's dual booting with XP and I think he wanted to be able to use the same install or at least copy over the games directory and run it. Possibly because he has Mods? Do you run any mods on your game? If so do they work ok, could you possibly list them?

I use loads of mods. Some of them are Pawn, RatingBuster, QuestHelper, Cartographer. And I never found a problem.

Hey, I'm really glad that my testimonial was actually helpful! I hope this makes people who keeps Windows for playing to come to Ubuntu full time. Some games will definitely run better in Ubuntu.

My ping in Ubuntu is actually lower than on Windows, probably because of all the protection Windows needs due to viruses and security holes and stuff. I had anti-viruses and firewalls running at the same time as I was playing WoW.

---

### Post by binbash on 2009-04-07
I am a hard core wow player also, i tried wow on 4 different pcs and i do not agree with you.It is not good to see a crash in action.And for fpswise , xp + nlite is the best.

---

### Post by jbysmith on 2009-04-07
> **binbash said:**
> I am a hard core wow player also, i tried wow on 4 different pcs and i do not agree with you.It is not good to see a crash in action.And for fpswise , xp + nlite is the best.

That's odd. A difference in FPS I can see, but I think I've had one crash over the past year or so.  (I've gotten one or two in Windows as well, nothing unique there.)  

On my particular hardware anyway (nVidia based with current drivers) the framerate was acceptable in DirectX mode, but really took off and left XP in the dust once I switched WoW over into OpenGL.  Of course that's just my hardware.. I know some hardware vendor's drivers just aren't up to par yet on the Linux end.  Compiz can cause issues as well with some stuff, making sure it's disabled is a good failsafe just to see what's what.

Slower I can see, but if your drivers and Wine is up to date, it shouldn't be crashing on you.

---

### Post by syntheticz on 2009-04-07
I have WoW installed under WINE too with the burning crusade expansion, and it all installed and runs flawlessly and better than on windows :) Only bug is I can't turn the graphics up to high or the graphics mess up, but WoW doesn't have good graphics so that doesn't matter lol.

---

