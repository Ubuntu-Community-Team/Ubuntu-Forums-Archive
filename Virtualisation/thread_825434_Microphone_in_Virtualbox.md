---
title: "Microphone in Virtualbox??"
date: 2008-06-11
forum: Virtualisation
---

### Post by KingTermite on 2008-06-11
I did a search and found another similar thread that didn't appear to get an answer. :(
[http://ubuntuforums.org/showthread.php?t=732839&highlight=virtualbox+microphone](http://ubuntuforums.org/showthread.php?t=732839&highlight=virtualbox+microphone)

But I'll try anyway.

I finally got sound working. Didn't realize you had to specifically enable it. Then had to fiddle with which driver to use before I got it working. Sound now works, but not microphone.

I plug in my head set with the intention of having a voice conversation on Yahoo messenger. My mic isn't detected. I fiddle around in control panel, but my mic is not detected there either.

Any ideas on how I can get the mic working?

Yahoo Messenger with voice is the ONLY reason I even have Virtualbox installed. If it won't work, then its useless to me. :(

---

### Post by sonicb00m on 2008-06-11
Don't know about your problem but doesn't it work with Wine. Does the Linux version support voice?

Virtual box with an entire XP installation to run a single program like that sounds insane :D

---

### Post by KingTermite on 2008-06-11
> **sonicb00m said:**
> Don't know about your problem but doesn't it work with Wine. Does the Linux version support voice?

Virtual box with an entire XP installation to run a single program like that sounds insane :D

I've tried it in wine. There are two major flaws.

You can use voice, but text that you type doesn't show up, therefore you have no typing capability. Also it doesn't show/use the "games" which is the other primary feature.

This is primarily how my g/f and I communicate nightly until she's here in a few months. After that I don't need it. But I was trying Virutalbox because it didn't work in Wine.

Besides....there may be a few other programs I end up using that I'll use it for.

---

### Post by chessmani on 2008-07-05
I'd like to know the answer as well. It worked for me out of the box and one day it suddenly stopped working.

---

### Post by chessmani on 2008-07-13
I got it working. It turned out that I had the microphone enabled in Kmix, but surprisingly it was muted in alsamixer.

I suggest you check alsamixer and see if the capture settings are correct. I need around 74% in 'capture' to hear my voice.

---

