---
title: "Trouble running FIFA Online under wine-swap file issue"
date: 2010-06-17
forum: Wine
---

### Post by haloony on 2010-06-17
Hey Guys,

I recently registered for EA's FIFA Online open beta and have installed it under wine. The software has a Silver rating on AppDb and the installation seemingly went smoothly but when I try to run launch.exe I get this error: ```
FIFA 03 requires at least 280MB of free swap file space. Please free the required space and re-run the game.
```
I am dual booting Ubuntu Lucid and XP and I have a 3.7 gig swap partition. I am a little unsure but I think my windows installation is using the pagefile.sys as a swap file and that my linux installation is using the swap partition. I am wondering what I can do so the game, ran under wine, will recognize my swap partition as swap space.

Any feedback will be appreciated.

Thanks,
Hal

---

### Post by asdfoo on 2010-06-17
> **haloony said:**
> Hey Guys,

I recently registered for EA's FIFA Online open beta and have installed it under wine. The software has a Silver rating on AppDb and the installation seemingly went smoothly but when I try to run launch.exe I get this error: ```
FIFA 03 requires at least 280MB of free swap file space. Please free the required space and re-run the game.
```
I am dual booting Ubuntu Lucid and XP and I have a 3.7 gig swap partition. I am a little unsure but I think my windows installation is using the pagefile.sys as a swap file and that my linux installation is using the swap partition. I am wondering what I can do so the game, ran under wine, will recognize my swap partition as swap space.

Any feedback will be appreciated.

Thanks,
Hal

Some old programs don't handle large values, maybe greater than 2048?.  Three options:

Patch the executable to skip the check (requires some assembly knowledge)
Patch Wine to report a smaller sized swap space.
Try installing in Windows then copy the files into your linux partition and try running the program. (may or may not work, depends if the game needs the registry entries)

---

### Post by haloony on 2010-06-17
Hey asdfoo,

Thanks for the response! But FIFA Online beta is a new game and if anything, based on the error I am receiving, I would think I need to get wine to report a greater swap file size. In any case, how would I go about patching wine to alter the swap space it is reporting? Is it super difficult? Going to do a little google searching now.

Thanks again,
Hal

---

### Post by asdfoo on 2010-06-17
> **haloony said:**
> Hey asdfoo,

Thanks for the response! But FIFA Online beta is a new game and if anything, based on the error I am receiving, I would think I need to get wine to report a greater swap file size. In any case, how would I go about patching wine to alter the swap space it is reporting? Is it super difficult? Going to do a little google searching now.

Thanks again,
Hal

The problem is that the value wine reports is larger than the app expects, Windows truncates the value sometimes since they interpret it as a negative or really high number I think.

The file to patch is dlls\kernel32\heap.c, the name of the function is GlobalMemoryStatus.

The best value to use I don't know, it may require some experimentation.  That is modify, compile, run.  You can run wine from the source directory when testing, so you don't have to install it system wide.

eg ~/wine-1.2-rc3/wine fifa.exe

---

### Post by huluvu on 2010-07-04
any working fixes yet? :(

---

### Post by LeoEvs on 2011-01-17
where is the heap.c ?
someone did it work?

i have 2gb of ram and 2gb swap ...
when run the application, the ram is using 40% and does not get to use the swap.

thanks for something,
sorry my english. :wink:

---

### Post by cogadh on 2011-01-17
You need to download the Wine source code to find the heap.c file, modify it with the change asdfoo suggested, then compile Wine to create a custom installation of it. However, unless the application you are running needs to use the swap, it won't. With 2GB of RAM, the swap file is not going to be needed much, certainly not as "substitute RAM".

---

