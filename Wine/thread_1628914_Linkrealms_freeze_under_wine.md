---
title: "Linkrealms freeze under wine"
date: 2010-11-23
forum: Wine
---

### Post by ilcontegis on 2010-11-23
Linkedrealms is a UO style game in closed beta.
I got an invitation but I can't even start the game.
I don't get any error, the game doesn't start (I think it freeze)
I get only this
```
teo@teo-vaio:~/.wine/drive_c/Programmi/Linkrealms$ wine LinkRealms.exe 
fixme:advapi:SetEntriesInAclA 1 0x33f710 (nil) 0x33f758
fixme:advapi:SetSecurityInfo stub
fixme:system:SetProcessDPIAware stub!
fixme:msxml:ConnectionPoint_Advise (0x1923b0)->(0xc8021c 0xc15f0c): stub
fixme:msxml:ConnectionPoint_Advise (0x192440)->(0xc80234 0xc15f74): stub
fixme:msxml:ConnectionPoint_Advise (0x1a81e8)->(0xc80324 0xc15f74): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f748,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats


```
Any idea what can I do?
I have ubuntu 10.10 64bit on a vaio tt laptop with a Intel video card.
I hope you can give me some suggestions
Regards

---

### Post by bobwyajnr on 2010-11-24
> **ilcontegis said:**
> 

I have ubuntu 10.10 64bit on a vaio tt laptop with a Intel video card.
I hope you can give me some suggestions
Regards

That's the 11.1" notebook model with an integrated Intel GMA 4500MHD GPU - right?

Even though your game (Linkrealms) is only DX8 it still may not be supported running, via Wine, with the Intel Linux MESA driver. Lack of pixelshader support??? :-k

:?: Help - is that correct :?:

BTW what version of Wine are you using?

Bob

---

### Post by ilcontegis on 2010-11-24
Solved.
I deleted the wine 1.3 and I installed 1.2
Everything perfect.
Thank you

---

