---
title: "Wine direct3d crashes, can't start"
date: 2010-12-30
forum: Wine
---

### Post by El Potro on 2010-12-30
Hello folks,

I'm trying to play some old DOS games on wine, in a fresh 10.04 ubuntu install. Whenever I try to start a game that requires direct x, direct3d, it crashes. The message I get is this:

```
fixme:d3d_caps:wined3d_guess_card_vendor Received unrecognized GL_VENDOR "VIA Technology". Returning HW_VENDOR_NVIDIA.
fixme:d3d_caps:select_card_nvidia_mesa Card selection not handled for Mesa Nouveau driver
fixme:win:EnumDisplayDevicesW ((null),0,0x139dfa8,0x00000000), stub!
m Files\Bullfrog\Hospital\Hospital.exe: main/renderbuffer.c:2067: _mesa_reference_renderbuffer: Afirmación «oldRb->Magic == 0xaabbccdd» fallida.
wine: Assertion failed at address 0x6ca2d832 (thread 001d), starting debugger..
```

I think it is trying to load a wrong video card as I don't use a nvidia agp card, I'm just using the onboard vga card. My motherboard is asus p5v-vm ultra, but it has also the option to add a pci express video card.

I'm sorry to be bothering here, but I'm very concerned as I can't execute any advanced graphics program on wine (just work for instance Adobe Photoshop, and others like those).

Can you please help me?

Thank you very much!

---

### Post by cogadh on 2010-12-30
First of all, if it is an old DOS game, it shouldn't use D3D at all and you really shouldn't use Wine to run it, you should use DOSBox instead.

As for the D3D error, it looks like you don't have a video card capable of DirectX, so you are very likely out of luck on that front. If you could provide a specific make/model for your onboard chipset, we could probably confirm that or provide much better advice.

---

### Post by El Potro on 2010-12-31
Thanks **cogadh**.

I need to use wine for this game as it only runs on WIN95.

Motherboard model is **Asus P5V-VM Ultra** and the on-board video chipset is **l VIA P4M890**. Is that the problem? **How can I fix it?**

I think it is a compatibility problem, because these games run perfectly on this computer with windows xp for instance. But my goal is to run them on ubuntu and finally erase windows.

Thank you very much.

---

### Post by ronnielsen1 on 2010-12-31
I was trying to guess the game you're trying to run. A lot of win 95 games were Dos. Is it Theme Hospital? It appears to be dos and should run in dosbox

> The Windows port of *Theme Hospital* was actually a Win32 version  of the DOS version, but all display, mouse, keyboard and sound output  and input was performed using DirectX. Because of this, it still had a  Low Resolution mode, despite the fact that it could only simulate it.  Also, some dos applications were still installed with it (including  MIDIFORM.EXE for converting midi files, and the companion batch file).
[http://en.wikipedia.org/wiki/Theme_Hospital](http://en.wikipedia.org/wiki/Theme_Hospital)

[http://www.dosbox.com/comp_list.php?showID=663&letter=T](http://www.dosbox.com/comp_list.php?showID=663&letter=T)

> Theme Hospital - Bullfrog (1997)
Tested By: zefo

                           runnable  -  playable  -  supported                      [IMG]http://www.dosbox.com/site_images/supported.png[/IMG]                              DOSBox version: 0.73 (supported)

---

### Post by ronnielsen1 on 2010-12-31
Also, you don't say what version of photoshop you're trying to run but always google winehq and the software you're trying to run. If it's a dos game, use dosbox

[http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17)

---

### Post by El Potro on 2010-12-31
Hi, thanks **ronnielsen1** for helping!

I'm going to try it on dosbox too! I was saying that Photoshop 7.0 works fine on this computer with wine. But I'm concerned about the graphics card and d3d because I want to play some new games like the sims, counter strike, and **cogadh** said the on board video chipset may be not compatible. The chipset is the **VIA P4M890**. Do you know if it works or it doesn't work on wine1.2 on ubuntu 10.04? Please tell me what are the chances to fix it and get it working normally.

Once again, thank you very much for your help guys.

---

### Post by cogadh on 2010-12-31
That chipset is not going to work. It is essentially a basic display chipset that is not good for much more than rendering your desktop and really can't do anything hardware accelerated like Direct3D, especially through Wine. Wine is dependent on Linux having hardware accelerated drivers for your video solution and AFAIK, nothing like that exists for that chipset. Your only real solution would be to buy and install a dedicated graphics card that is fully DirectX capable and has Linux drivers, preferably an Nvidia card (Nvidia has better Linux support than any other hardware manufacturer).

---

### Post by El Potro on 2010-12-31
Thank you cogadh. I don't want to sound idiot, please forgive me for my ignorance, but why is this going on? I mean, if I installed windows xp on this computer with this video chipset all those games would work. Why on wine not? Is it because of the driver?

Once agian thank you very much, and I wish you a happy new year

---

### Post by cogadh on 2010-12-31
Frankly, I'd be really surprised if the games would work in Windows at all with that chipset and even if they did work, they would not work very well. Regardless, the problem does come down to the drivers. Wine accomplishes its DirectX functions by translating Direct3D calls into OpenGL calls. OpenGL support is primarily a function of the video card/chipset drivers and without Linux drivers with the proper OpenGL support, Wine can't do its translating.

---

