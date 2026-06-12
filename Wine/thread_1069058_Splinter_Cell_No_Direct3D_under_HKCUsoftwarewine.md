---
title: "Splinter Cell: No Direct3D under HKCU/software/wine??"
date: 2009-02-13
forum: Wine
---

### Post by LastWho on 2009-02-13
Hi,
i m trying to get "Splinter Cell Pandora Tomorrow" running with wine1.1.14
Installation succeded but the game is so buggy 
So i checked the wine AppDB to find [this comment]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4076"): 
> What works
Demo installation, gameplay. I had to set the registry key "OffscreenRenderingMode"="fbo" in order to avoid graphical corruption though. After that it played well. 

What does not
Graphics are buggy until you set the registry key "OffscreenRenderingmode"="fbo".

My question is about that registry key, i googled to find [this answer]("http://ubuntuforums.org/showpost.php?p=5239106&postcount=6") on ubuntuforum: 
> HKEY_CurrentUser>Software>Wine>Direct3D. Now I had to add a new string to enable Off screen rendering. I right clicked New>String and entered:
>OffscreenRenderingMode
To set the value, I right clicked on OffscreenRenderingMode and clicked Modify. For Value Data, I put in:
>fbo

but when i opened regedit i found that Direct3D and many other directories are missing under HKCU/software/wine

1- I suppose that i should find my wine registry like [this one]("http://wiki.winehq.org/UsefulRegistryKeys") ?? no?

2- I created a Direct3D then the string Offscreen and its value.. but the game is still buggy?


Other informations: 
- running Ubuntu 8.04 
- CPU 2.4 GHz
- Graphic card: Nvidia 128 Mb
- Memory sticks: 778 Mb

---

### Post by hikaricore on 2009-02-13
> - Graphic card: Nvidia 128 Mb

You'll need to be a bit more specific than that on the videocard front.
Plenty of old nvidia cards had 128mb of ram, they may or may not be supported by the latest nvidia driver.

---

### Post by Dizzle7677 on 2009-02-13
> **LastWho said:**
> 
but when i opened regedit i found that Direct3D and many other directories are missing under HKCU/software/wine

1- I suppose that i should find my wine registry like [this one]("http://wiki.winehq.org/UsefulRegistryKeys") ?? no?

- Graphic card: Nvidia 128 Mb 

Some Direct3d settings are default for Wine like 'offscreenrenderingmode'->'backbuffer'. You create the key to override the default behaviors. What Model of nvidia card/driver is it?

---

### Post by LastWho on 2009-02-13
sorry for taking that time, 
My graphic card is nvidia geforce fx 5200 and i m using it native driver i downloaded and installed from nvidia.com

---

### Post by Dizzle7677 on 2009-02-13
It's one of the first DX9/SM2 cards ... What was the question again? Why is Splinter Cell so buggy? Since I've never played it I can't give you any advice about it.[ Wikipedia]("http://en.wikipedia.org/wiki/GeForce_FX_Series#Shaders") has an interesting read about the FX series. Splurge a little and upgrade the card is my only advice.

---

### Post by Psyphre on 2009-06-18
The question wasnt why its so buggy. Its why he doesnt have a Direct3d entry in his software/wine/ section of registry editor. For that matter neither do I, it makes no sense. I need to change it to make mass effect work.

---

### Post by Xubuntnoob on 2009-06-21
Same here, but for oblivion, been looking at (following verbatim  :D ) this guide : [http://ubuntuforums.org/showthread.php?t=349764](http://ubuntuforums.org/showthread.php?t=349764)



Built an Xubuntu server - been playing around with that, now i've taken the headlong plunge into making my main comp *nix. Goodbye windows! I'm loving 9.04, very pretty desktop, but you gotta love that "gets friendlier with every use" command line. 

Looking forward to browsing the forums for all my noobie questions.
Thanks for the community.

---

### Post by cogadh on 2009-06-21
There is no Direct3D key by default, you need to manually create in order to add the extra Direct3D registry options you want to set.

---

### Post by Psyphre on 2009-06-22
> **cogadh said:**
> There is no Direct3D key by default, you need to manually create in order to add the extra Direct3D registry options you want to set.

Thanks, thats what i needed to hear. I've done it and it works.
Thanks again.

---

### Post by lightstream on 2009-06-22
I don't know if it will help for this version of the game, but for Splinter Cell: Chaos Theory, a few oddities remain even with offscreen rendering set. Telling it to use 'Shader Model 3.0' from the in-game graphics options makes the graphics perfect.

---

### Post by NightMKoder on 2009-06-22
Starting wine 1.1.23 fbo is the default so you dont need to do this on the newer versions.

---

### Post by Xubuntnoob on 2009-06-23
> **Psyphre said:**
> Thanks, thats what i needed to hear. I've done it and it works.
Thanks again.

Yup, exactly. Thanks

---

