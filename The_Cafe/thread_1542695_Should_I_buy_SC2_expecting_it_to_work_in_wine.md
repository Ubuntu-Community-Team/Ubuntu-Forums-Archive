---
title: "Should I buy SC2 expecting it to work in wine?"
date: 2010-07-30
forum: The Cafe
---

### Post by Dustin2128 on 2010-07-30
I saw some SC2 screenshots and reviews and I'm intrigued. It appears to have good replay value so I'm more interested than I would be otherwise (I usually beat non-zelda games in less than 4 hours if I'm not easter-egg obsessed). I'm about to get a used computer that scrapes minimum requirements for graphics card, but exceeds in everything else. I figure linux is going to work better than the existing xp install, especially if I use lxde or fluxbox due to far lighter system requirements. I noticed it had a gold rating for 32 bit lucid and gentoo which are the two distros I'm considering putting on it. I'm just wondering- should I expect most of the features to work out of the box or with minimal editing? Being able to play the game in single and multiplayer is all that really matters, I don't care about bonuses like voice chat.

---

### Post by TheWeakSleep on 2010-07-31
If it's a game that you think you would really like to play, then I think that you should get it. I haven't played it yet, though my brother has it and he really loves it. I'm actually playing the original one now :) all the talk had me nostalgic (the old blizzard games run amazingly well!). I don't think that you should get it if you would be too disappointed if it didnt run on wine though. You could easily set up a dual-boot or a virtual machine ( I don't know how well that would work:P ) but yeah. basically what I'm saying is if you really want to play it, you should get it. but not if you're going to regret it if it doesn't run on wine.

that being said... I could try it out for you if you want.

---

### Post by Dustin2128 on 2010-07-31
> **TheWeakSleep said:**
> If it's a game that you think you would really like to play, then I think that you should get it. I haven't played it yet, though my brother has it and he really loves it. I'm actually playing the original one now :) all the talk had me nostalgic (the old blizzard games run amazingly well!). I don't think that you should get it if you would be too disappointed if it didnt run on wine though. You could easily set up a dual-boot or a virtual machine ( I don't know how well that would work:P ) but yeah. basically what I'm saying is if you really want to play it, you should get it. but not if you're going to regret it if it doesn't run on wine.

that being said... I could try it out for you if you want.
Sounds good, do you have 64 or 32 bit though? I'm thinking the computer I'm receiving is 32 bit. Also I am a big FOSS zealot and I'd *really* prefer not to setup a dual boot just for one game.

---

### Post by TheWeakSleep on 2010-07-31
I understand I'm the same way :p I'm going to try and install it on my hp laptop running kubuntu. do you think that kde would have any effect? its 32 bit.

---

### Post by Dustin2128 on 2010-07-31
> **TheWeakSleep said:**
> I understand I'm the same way :p I'm going to try and install it on my hp laptop running kubuntu. do you think that kde would have any effect? its 32 bit.
It's a little bulky.. might reduce performance. Test it out with gnome or lxde (my top two) if you don't mind.

---

### Post by TheWeakSleep on 2010-07-31
hmm okay. I'm frustrated with kubuntu right now, so i might just throw ubuntu on the laptop now instead of later and do it on a fresh install, are you in a rush? 
:p

edit: well, I'm already doing a fresh install. It'll all be done tonight, barring some crazy stuff. I'll keep you posted on anything I need to do on getting it up and running (if I can ;) )

just so you know, it's 32 bit standard ubuntu with gnome

anything you wanna know about the hardware or anything?

---

### Post by Dustin2128 on 2010-07-31
> **TheWeakSleep said:**
> hmm okay. I'm frustrated with kubuntu right now, so i might just throw ubuntu on the laptop now instead of later and do it on a fresh install, are you in a rush? 
:p

edit: well, I'm already doing a fresh install. It'll all be done tonight, barring some crazy stuff. I'll keep you posted on anything I need to do on getting it up and running (if I can ;) )

just so you know, it's 32 bit standard ubuntu with gnome

anything you wanna know about the hardware or anything?
test it out with lubuntu too (sudo apt-get install lubuntu-desktop) if it's not too much trouble. I use that DE for gaming due to extremely light resource usage. But I'd like to know how much VRAM the laptop's card has, the one I'm getting only has 256MBs iirc. No rush though, I'm not buying until the price to go down a few orders of magnitude.

EDIT: Also, how is the offline play capability? That's a major selling point for me.

---

### Post by TheWeakSleep on 2010-07-31
Okay I'll let you know hardware details when I'm done with the actual install. I will try it with lubuntu as well, hopefully this helps anyone else in the same predicament as well :p

---

### Post by TheWeakSleep on 2010-07-31
Okay so here are my first impressions after a quick install. First of all, the dvd installer didn't run, you have to mount it with an unhide option (you can check that out on appdb) but to avoid all of that, I would recommend using the digital download option at battle.net.

there were no errors during the installation and everything ran fine, though when i first started the game it crashed right away, but theres no problem with that running it in Vista/7 compatibility mode. I haven't been able to get the sound to work. in winecfg, under library, you can try to disable the mmdevapi dll (didn't work for me) or you can compile wine with openal (I didnt) other than that it runs just fine, though maybe a little slowly, with only the (very) minimal tweaks.

I tried on gnome and lxde with wine 1.2.

Still though, It doesn't run perfectly and your mileage may vary, so I'm going to stick with my original advice :p get it if you want it, but not if you'll be heartbroken if it doesn't run well in wine.

---

### Post by Spr0k3t on 2010-07-31
Seriously... there are some Linux users who work on the development of the systems at Blizzard.  If you were to contact Blizzard support asking for SC2 to work under Linux even if it were with WINE, I'm sure there would be more support efforts made to help make it work.  I've contacted Blizzard for assistance with WOW a couple times and they were quick to help... even pointing out some work arounds on appdb.

Also, make sure you tell them you are purchasing SC2 for use on a computer system that does not have Windows.  Fill out that registration card with Linux written in.

---

### Post by Matthewthegreat on 2010-07-31
It looks like it will work fine in wine

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=11123]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=11123")

---

