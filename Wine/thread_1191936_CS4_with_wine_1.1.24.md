---
title: "CS4 with wine 1.1.24"
date: 2009-06-19
forum: Wine
---

### Post by alex.rayu on 2009-06-19
New wine is out (1.1.24) that has a series of bugs fixed, that prevented CS4 from installation and running. Anybody tried? Anybody succeeded?

---

### Post by paradigm2 on 2009-06-19
1.1.24 isn't being pulled from the special PPA I set up as per the announcement?  I guess it needs a day or two for the maintainer to get things set up.

---

### Post by alex.rayu on 2009-06-20
Oh Ok. I got so excited when I received "bugs closed" emails and then went and saw 1.1.24 there with the buds in the list of fixed! Can't imagine I will run CS4 in wine now!

---

### Post by alex.rayu on 2009-06-22
Any update?

---

### Post by TheBuzzSaw on 2009-06-22
I would be fairly shocked if CS4 ran in WINE.

---

### Post by alex.rayu on 2009-06-23
Has anybody tried it? I have tried on my wife's laptop, and install failed. But it could be due to the fact that she already had lots of things installed there from the past. Anybody with a fresh WINE ?

---

### Post by TheBuzzSaw on 2009-06-23
I guess I can give it a try one of these days. The discs are sitting right there on my desk, and I have the latest WINE installed.

I'll report back as soon as I can.

---

### Post by Nugar on 2009-06-23
Just to let you know, a Photoshop CS4 "portable" copy will run in Wine 1.1.24. Just click on it, no tweaks. (Ubuntu 9.04)

It does just what I need, and that is edit my photographs, from RAW on. Loads faster than when running in XP.

The problem is that when you try to activate the text tool, the program crashes. I don't use the text tool for my photos, so it is ok with me.

This weekend, if I have some time, I'll try to get Dreamweaver and Flash working. They won't work just clicking the exe like PS.

Cheers,

Nugar

---

### Post by NightMKoder on 2009-06-23
> **Nugar said:**
> Just to let you know, a Photoshop CS4 "portable" copy will run in Wine 1.1.24. Just click on it, no tweaks. (Ubuntu 9.04)

It does just what I need, and that is edit my photographs, from RAW on. Loads faster than when running in XP.

The problem is that when you try to activate the text tool, the program crashes. I don't use the text tool for my photos, so it is ok with me.

This weekend, if I have some time, I'll try to get Dreamweaver and Flash working. They won't work just clicking the exe like PS.

Cheers,

Nugar

I remember there is a fix for the text tool by overriding some dll.

---

### Post by alex.rayu on 2009-06-24
Thank you for trying it. I thought the text tool got fixed? Evidently not. I use text tool a lot. I do web design and get lots of layered PNGs that only FireWorks can open, and lots of PSDs that often have a newer blending method that CS2 does not support. So, I am very bound to a functional CS4. I am sitting in Win7 right now. Very good and polished. But I am still missing the font rendering of Ubuntu, and many small useful little things that Ubuntu has. As son as I hear that it works in a way that CS2 works, I will switch back.

---

### Post by phyreanjel on 2009-06-25
> **NightMKoder said:**
> I remember there is a fix for the text tool by overriding some dll.

  [http://ninetynine.be/blog/2009/04/photoshop-cs4-on-ubuntu-904/](http://ninetynine.be/blog/2009/04/photoshop-cs4-on-ubuntu-904/)

Until I hear it works I'm running it on 1.1.19 :)

---

### Post by alex.rayu on 2009-06-26
So... Is there anybody who would say something like "I have installed it via the installer, and it runs well including the text tool"?

---

### Post by CK05 on 2009-06-26
I can run Photoshop CS4 fine without any problems, text works. But the only problem is that it has problems saving some formats but other than that everything is good. 

 I used my download from Adobe. Installed it using the installer and followed the instructions on the Wine APP database. (winetricks, a few dll's from the net can't remember but it's all listed there in one of the posts).

---

### Post by alex.rayu on 2009-06-26
Are you tricking me? :D Hmm... Looks sweet. Anybody else succeeded?

---

### Post by CK05 on 2009-06-26
I'm not tricking you. It is difficult to get it to work however all the information I got to get it to work is on the Wine App Database page for Photoshop CS4

---

### Post by alex.rayu on 2009-06-27
No offense pal. I was not really saying you tricked me. It's just that the news is unbelievalble =)

---

### Post by alex.rayu on 2009-06-27
And I have strange spots in CS4 - some panels and design elements are missing. And only Wine built-in gdi32.dll works. Native hangs.

---

### Post by alex.rayu on 2009-06-27
If someone has similar problem as me with only wine gdiplua working and parts of interface not showing, do this:

1. Install ie6
2. In WINE drive settings, delete the / mapping to z://
3. Set gdiplus to Windows version (native)
4. Turn off compiz =(

And it works!

:( Flash CS4 does not work.
:( FireWorks CS4 does not work.
:) DreamWeaver works

---

### Post by CK05 on 2009-07-03
good to hear you got it working. you can't however save many formats in PS CS4, hope that'll be fixed soon.

---

### Post by artik1024 on 2009-10-19
> **phyreanjel said:**
> [http://ninetynine.be/blog/2009/04/photoshop-cs4-on-ubuntu-904/](http://ninetynine.be/blog/2009/04/photoshop-cs4-on-ubuntu-904/)

Until I hear it works I'm running it on 1.1.19 :)

phyreanjel many thanks !!!! You saved meeeeeeeeeeeee !! everything work so nice now !
thx !!!! :D

---

### Post by Kreative_Station on 2009-10-20
> **artik1024 said:**
> phyreanjel many thanks !!!! You saved meeeeeeeeeeeee !! everything work so nice now !
thx !!!! :D


So you mean to tell me, a 64-bit version of CS4 Photoshop was successfully installed and properly working in 


[LIST]
[*]Ubuntu 9.04
[*]Ubuntu 9.10 beta
[*] AMD Phenom 9600 64-bit
[/LIST]

Wonderful news either way!:guitar:

---

