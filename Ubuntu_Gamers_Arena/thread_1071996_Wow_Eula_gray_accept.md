---
title: "Wow Eula gray accept"
date: 2009-02-16
forum: Ubuntu Gamers Arena
---

### Post by pdonovan821 on 2009-02-16
I'm sure this is a question that's popped up quite a bit, but i can't seem to solve it, and honestly, im almost at the point of just wiping my hard drive completely and going back to windows (which i really dont wanna do).

So here's the deal. I'm trying to install wow, via the installer ( i dont have my original discs, still have the BC and the WOTLK ones ) and I'm having the gray accept problem. I've been trying now for four days to figure this out and I'm literally about to scream. Basically, It loads up (quite beautifully I might add) but when I get to the EULA, it shows gray. I've tried the original, BC, and Wrath installer, all of em give me the same thing. I really am at a loss here.

I've tried older version of Wine, all the way back to 1.1.8 i believe it is (currently have wine 1.1.15 in), Im using Ubuntu 8.10, on a dell with a 2.4 ghz processor, 768 mb Ram, um...yeah, i think that's about the most on my specs that I can come up with off the top of my head.  

Someone help me figure this out, pretty please. I'm really really not wanting to go back to windows...because well..its the devil.

---

### Post by JustANewb on 2009-02-17
Have you tried scrolling down through the EULA?  If I remember correctly, that's the only way to continue on...

---

### Post by pdonovan821 on 2009-02-17
yep. done that. first thing i did actually.

---

### Post by dmizer on 2009-02-17
Moved to the gaming section of the forums. You should get more help here.

Thank you.

---

### Post by tysonh on 2009-02-17
did you follow any how to or guide for installing WoW?  Did you make all the registry changes for using openGL?  Did you download the MSFonts?  Keep me updated I've installed wow a couple times on ubuntu.

---

### Post by pdonovan821 on 2009-02-17
I've found a few how-to's and what not, and tried using them. Problem is none of them address my actual problem directly, which is not having the discs for the original wow (unless there's one I haven't seen)

All the registry type fixes that I've seen have been for sound, graphics, etc, nothing for an accept button that's been possessed by satan.

I really need to get this thing back up and running though...I'm a GM for one of the top twenty raiding guilds on bronzebeard on ally side. Good knows which one of my psychotic asst GM's has taken over the reigns in my absence...

not only that...im the only one in guild right now with the 25 man maly key....

---

### Post by airtonix on 2009-04-10
[http://www.wowwiki.com/Config.wtf_defaults](http://www.wowwiki.com/Config.wtf_defaults)

> readScanning - Whether the user has accepted the system scanning terms
readTOS - Whether the user has accepted the Terms of Use
realmList - Realm list server to use (e.g. "eu.logon.worldofwarcraft.com")

---

### Post by Clydtsdk-Rivendare on 2009-04-29
Yeah, somewhere in config.wtf there should be lines about readTOS and readEULA or something like that. Make sure those are set to "1" and that should do the trick.

---

