---
title: "o no not another WoW thread!"
date: 2009-06-30
forum: Wine
---

### Post by PuddingKnife on 2009-06-30
Oh, but it is.  And you've all been so helpful so far, thank you for your patience.

So. I have WoW installed on an XP partition, works like a breeze.  I copied the entire WoW folder from XP to an external hdd, and from the external hdd to my Ubuntu partition.

I have installed Wine, and I can view the WoW folder from Wine and even start it from the Wow.exe file.

I can start it, connect, log in, and the game begins. The only problem is that Im getting perhaps 1 frame every 15 seconds, completely unplayable.

Ive tried using OpenGL, but that gives me black rectangles everywhere. 

Please help, I'd love to ditch Windows forever, and this is the only thing holding me back.

---

### Post by BenAshton24 on 2009-06-30
Just a few Questions...

Do you know what graphics card you have?

Have you installed the proprietary restricted drivers for you Graphics card?

I've not had any problems with NVIDIA cards but with ATI theres always something that needs a bit of extra tweaking..

Only thing that I can suggest really is that you make sure that your drivers are installed and disable screen glow effect and the lighting effect.

Also, there are tons of helpful tips on the wine appdb page for words of warcraft... [http://appdb.winehq.org/objectManager.php?sClass=version&iId=16459](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16459)

Hope this helps you :D
Ben.

---

### Post by PuddingKnife on 2009-07-01
> **BenAshton24 said:**
> Just a few Questions...

Do you know what graphics card you have?

Have you installed the proprietary restricted drivers for you Graphics card?

I've not had any problems with NVIDIA cards but with ATI theres always something that needs a bit of extra tweaking..

Only thing that I can suggest really is that you make sure that your drivers are installed and disable screen glow effect and the lighting effect.

Also, there are tons of helpful tips on the wine appdb page for words of warcraft... [http://appdb.winehq.org/objectManager.php?sClass=version&iId=16459](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16459)

Hope this helps you :D
Ben.

Thanks for the reply! This is my computer:

[http://support.gateway.com/s/Mobile/Q106/BladeC/1014033Rsp2.shtml](http://support.gateway.com/s/Mobile/Q106/BladeC/1014033Rsp2.shtml)

I have installed restricted extras. To disable screen glow and lighting effects you must edit the config.wtf file, correct? I'll give that a try and see if it improves the framerate any.

---

### Post by PuddingKnife on 2009-07-07
Ive applied the proper changes, and even tried running it under OpenGL.  With OpenGL, I get a much worse framerate on the login screen than I do when its not activated.

I would really like to ditch Windows and get this up and running.. Everything works except for the unplayable framerate.  Help!


EDIT: Just found this quote on the WineHQ page:
> INTEL issues

 Unfortunately, Intel does not make its own drivers for their cards for Linux. Their Windows drivers aren't even that good to start with.

For World of Warcraft to work properly, you need to look for an Open Source Intel Driver that gives you direct OpenGL rendering support.

-----

There are no known Issues with Intel Cards, apart from bad FPS on certain drivers.

So could anyone point me in the right direction to get a working driver for my Intel chipset?

---

