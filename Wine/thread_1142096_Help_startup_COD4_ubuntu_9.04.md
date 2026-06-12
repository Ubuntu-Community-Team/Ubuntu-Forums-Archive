---
title: "Help startup COD4/ ubuntu 9.04"
date: 2009-04-28
forum: Wine
---

### Post by Userstein on 2009-04-28
hey, in first place sorry for my bad english xP

when i start cod4 with wine its appear a error in the console
```
err:module:import_dll Library d3dx8.dll (which is needed by L"C:\\windows\\system32\\d3dx9_36.dll") not found
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXGetShaderOutputSemantics' used by L"C:\\windows\\system32\\d3dx9_34.dll"
```i search the d3dx8.dll in windows folders but i cant found it :confused:
wine-1.0.1
i hope u can help me pls :) thank you very much

pd: this is my first time using ubuntu

---

### Post by u235sentinel on 2009-04-29
> **Userstein said:**
> hey, in first place sorry for my bad english xP

when i start cod4 with wine its appear a error in the console
```
err:module:import_dll Library d3dx8.dll (which is needed by L"C:\\windows\\system32\\d3dx9_36.dll") not found
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXGetShaderOutputSemantics' used by L"C:\\windows\\system32\\d3dx9_34.dll"
```i search the d3dx8.dll in windows folders but i cant found it :confused:
wine-1.0.1
i hope u can help me pls :) thank you very much

pd: this is my first time using ubuntu

I've had varied success with making this work.  I'm running 1.1.18 and upgrading to 1.1.20.  haven't tested it yet but 1.0.1 won't work without a patch.  Something about the hdr not rendering properly I think they said.

I would recommend looking under winehq.com and following their directions.  You might have better luck than me.

---

### Post by newubunt on 2009-06-19
do you have solved your problem yet?

---

### Post by Sealbhach on 2009-06-19
Try installing it under PlayonLinux.

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

It uses Wine but it uses special scripts for installing each game. COD4 worked for me that way. 

.

---

### Post by newubunt on 2009-06-19
do it work online too...you know i'm a big cod4 online gamer

---

### Post by Sealbhach on 2009-06-19
> **newubunt said:**
> do it work online too...you know i'm a big cod4 online gamer

Punkbuster doesn't work online, but you can find servers that don't have Punkbuster enabled, and yes, the multiplayer online version works. But because you're using wine, the game in general feels a little bit, just a little bit slower than it should be.

Make sure you disable "soften smoke edges" and "depth of field" in the graphics settings.


.

---

### Post by newubunt on 2009-06-19
thx..btw...do you get drivers for your sony vaio? i have one too and searching for drivers, so everything works...

to punkbuster....evenbalance offers you a linux version download...why it won't work online?

don't be mad at my stupid questions but i'm pretty new to ubuntu

---

### Post by Sealbhach on 2009-06-19
> **newubunt said:**
> thx..btw...do you get drivers for your sony vaio? i have one too and searching for drivers, so everything works...

My webcam doesn't work. Brightness keys don't work. I use the Nvidia driver for graphics. Sounds works fine after I add an option in /etc/modprobe.d/alsa-base.conf 

> **newubunt said:**
> 

to punkbuster....evenbalance offers you a linux version download...why it won't work online?

I don't know anything about this.

> **newubunt said:**
> 
don't be mad at my stupid questions but i'm pretty new to ubuntu

They're not stupid questions, why should I be mad?  If you have problems with your Vaio start a new thread explaining what the issues are.

.

---

### Post by newubunt on 2009-06-20
So I finally  install COD4 under Ubuntu 9.04! THX for your help...Playonlinux is very useful...i just have one new question if you are a cod4 gamer as well..i can't open the console of COD4..i tried this button "^" but it doesn't work... can u help?

---

### Post by newubunt on 2009-06-20
So i get it worked...i updated Punkbuster for COD4 via bpsetup.exe and wine! If someone want to know about me just ask...its not that hard...i'm also just a newbie to ubuntu!!!

---

### Post by Sealbhach on 2009-06-21
That's great! Thanks for letting us know. So you got Punkbuster working? Can you play multiplayer in servers where Punkbuster is enabled? I kept getting kicked out after about a minute.

.

---

### Post by xenogia on 2009-06-28
I installed COD4 using PlayonLinux, the game loads fine, but once the actually gameplay starts none of the 3d graphics actually display only the 2d hud.  I am currently using Ubuntu 9.04 x64 with a 8800GTS 512mb.  Any ideas why this is doing it?

---

### Post by AsusEEEPC on 2009-06-29
Disable "Soften Smoke edges" and "Dept of field" graphics options.

---

### Post by xenogia on 2009-06-29
I did do that but I am still having no luck whatsover.

---

