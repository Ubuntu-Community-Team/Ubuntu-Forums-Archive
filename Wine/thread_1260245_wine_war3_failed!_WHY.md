---
title: "wine war3 failed! WHY?"
date: 2009-09-07
forum: Wine
---

### Post by ChipWolf on 2009-09-07
[SIZE=3]***@****s-laptop:~/.wine/dosdevices/c:/Program Files/Warcraft III$ wine War3.exe -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f67c,0x00000000), stub!

I have installed the latest [/SIZE][SIZE=-1][SIZE=3]graphical card driver(my card is GF8600gs notebook acer5520g)
I donot know what is the problem,please help.
Ubuntu 9.04 works almost perfect for me.
[/SIZE][/SIZE]

---

### Post by hikaricore on 2009-09-07
There are no errors there.  Can't even begin to make a guess as to what's wrong.

---

### Post by j7%&lt;RmUg on 2009-09-07
I can run my cracked version of wc3 TFT on 9.04 fine. I think it has worked for me since wine 1.1.23 or so.

---

### Post by beastrace91 on 2009-09-07
@nisshh - don't post just to tell the other person that "it works fine for me" its not helpful in the slightest and is really a spamish post.

@ChipWolf What version of Wine are you using, what GFX driver version do you have, and 64bit or 32bit Ubuntu?

~Jeff

---

### Post by ChipWolf on 2009-09-08
> **beastrace91 said:**
> @nisshh - don't post just to tell the other person that "it works fine for me" its not helpful in the slightest and is really a spamish post.

@ChipWolf What version of Wine are you using, what GFX driver version do you have, and 64bit or 32bit Ubuntu?

~Jeff
"really a spamish post"well said, thanks to Jeff!
         Linux ###-laptop 2.6.28-15-generic  9.04 32bit
         GFX diver version NVIDIA-Linux-x86-185.18.36-pkg1.run(It was downloaded from the NVIDIA official website , and I installed it myself)
         wine-1.1.29

---

### Post by Soulcage on 2009-09-08
Perhaps the problem is that your running the wrong exe file its wine Warcraft\ III.exe or wine Frozen\ Throne.exe

---

### Post by beastrace91 on 2009-09-08
@ChipWolf I'm not sure what is wrong from your configuration listed there. The only thing that slightly confuses me is the -opengl argument you are passing to Wine when running the exe perhaps try it without this as I am decently sure it is not needed. 

Also as hikaricore suggested there isn't an error message in the small bit of output you posted from terminal, is that the full text it out puts when the game dumps?

I haven't personally tried WC3 since upgrading to Wine 1.1.29 but I'll give it a go later this afternoon to double check that it isn't a regression in the new package.

~Jeff

---

### Post by ChipWolf on 2009-09-08
> **beastrace91 said:**
> @ChipWolf I'm not sure what is wrong from your configuration listed there. 
~Jeff
Maybe I am not a lucky man, it is all the information from the terminal, anyway thank you guys!

---

### Post by ChipWolf on 2009-09-08
> **Soulcage said:**
> Perhaps the problem is that your running the wrong exe file its wine Warcraft\ III.exe or wine Frozen\ Throne.exe
I tried but didn't work!

---

### Post by beastrace91 on 2009-09-08
Alrighty, I am running Wine 1.1.29, Jaunty 64, and nVidia 190.25 drivers - I run the exact same commands as you I get: ```
jeff@sager-lintop:~/Data/Warcraft III$ wine war3.exe -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f270,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f608,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f640,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x146868,0x14d128): stub

```

And the game loads. If yours is dumping there should be some form of error in terminal (or does the screen flicker or anything like it is at least attempting to load?) Perhaps you could open your winecfg and set it to run war3.exe in a virtual desktop and see if that helps at all (for some odd reason it does on and off with some programs) Also changing what Windows version you are running in can help with some apps.

~Jeff

---

### Post by ChipWolf on 2009-09-08
> **beastrace91 said:**
> Alrighty, I am running Wine 1.1.29, Jaunty 64, and nVidia 190.25 drivers - I run the 
exact same commands as you I get: ```
jeff@sager-lintop:~/Data/Warcraft III$ wine war3.exe -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f270,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f608,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f640,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x146868,0x14d128): stub

```And the game loads. If yours is dumping there should be some form of error in terminal (or does the screen 
flicker or anything like it is at least attempting to load?) Perhaps you could open your winecfg and set it to run 
war3.exe in a virtual desktop and see if that helps at all (for some odd reason it does on and off with some 
programs) Also changing what Windows version you are running in can help with some apps.
 
~Jeff
yes, there is something more:
 
the terminal:
###@###-laptop:~/.wine/dosdevices/c:/Program Files/Warcraft III$ wine Warcraft\ III.exe 
errle:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f260,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f638,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f244,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
 
i did see the loading window and the loading image, but the loading process was terminated by some reason, and came 
out a small window wrote :"____III____Windows_" and a OK button,
after press OK button, another small window came out ,it wrote "??????III?????" and two buttons Retry, Cancel.
Then nothing.
 
(it seems i can't upload images from local?)

---

### Post by dal on 2009-09-09
The windows you're seeing sound vaguely reminiscent of the "Insert your Warcraft III CD" dialog I saw on occasion under windows when I set warcraft up with a nocd patch that didn't work. It is worth noting that some nocd patches will work fine under windows but not at all with wine - I've run into that playing from my windows hard drive and/or copying over game directories, and have either had to find another nocd patch or go back to dragging out the game cd whenever I want to play it (annoying). See if changing nocd patches helps :)

---

### Post by beastrace91 on 2009-09-10
Thats a very good point. Is this a legal copy of WC3? If it is just go download the latest patch for it (search wc3 patch download on google) and then it no longer needs a disc.

And if its not a legal copy... Well go buy the game, its one worth owning and then it will work fine ;)

~Jeff

---

### Post by ChipWolf on 2009-09-10
the question does not lie in the law problem,
the game ran OK in the windows, so it should run OK in Ubuntu.
and there is no patch for 1.20d version (I need 1.20 version to play with others),

I want to say thanks to all of you that try to give me a solution, especially Jeff~;but this thread should be closed now.

---

### Post by beastrace91 on 2009-09-13
> **ChipWolf said:**
> the game ran OK in the windows, so it should run OK in Ubuntu.

Just as an fyi this is rarely if ever the case with Wine, some applications it runs just fine others not so much - and small changes like 3rd party No-CD patches change the playing field alot.

~Jeff

---

