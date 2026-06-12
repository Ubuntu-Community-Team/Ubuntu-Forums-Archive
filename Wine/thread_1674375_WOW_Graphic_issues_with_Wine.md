---
title: "WOW Graphic issues with Wine"
date: 2011-01-23
forum: Wine
---

### Post by kenrerd on 2011-01-23
Hey I'm trying to run World of warcraft through wine, i have it installed through window on my external harddrive and want to run it from there. I've got wine 1.2.1 on Ubuntu 10.10.

I've managed to get wow to run using the terminal with commands:

wine "/media/elements/world of warcraft/wow.exe" -opengl

However when it opens the graphics are all mangled, the sign in screen flashes coloured triangles and stuff and when i've signed on it doesn't show my character, only their floating armour. I was just wondering if there's anything I could do to correct this?
Thanks.

---

### Post by cwwilson721 on 2011-01-23
What graphics hardware?

---

### Post by kenrerd on 2011-01-23
I'm not sure sorry, I'm not too good with computers and don't know where to find out.

I'm on an HP Compaq Presario CQ60-219TU 1.83 Ghz Dual core laptop.
It originally came with windows vista and wow worked fine on that, but my harddrive died so I installed a new one and ran ubuntu, I still had wow on my external harddrive though. 
I thought wow would run fine seeing as i didn't have any graphics issues on windows.
Sorry if that doesn't help >.<

---

### Post by Halzen on 2011-01-23
There is a lot of gray space in your problem, so I'll suggest a couple of ideas off the top of my head. If neither point us to the issue, I'll need to find out more about your setup.

1. We need to know if your video driver and setup has direct rendering (or DRI) enabled. Without it, you're going to have a lot of trouble running most 3D applications. To figure this out, please enter the following code into your Terminal:
```
glxinfo | grep rendering
```

If your Terminal returns "direct rendering: Yes", you're safe there. If not, let me know and we'll see what we can do.


2. If your direct rendering returns a "yes", we can move on from your immediate graphics configuration and try another possible quick fix. Find the file called Config.wtf in your World of Warcraft's WTF folder. You'll need to have logged in at least once with this installation for the document to exist. Open the Config.wtf in a text editor and add the following line:
```
Set UIFaster "2"
```

---

### Post by kenrerd on 2011-01-23
Ok i got the "Direct rendering: YES" response, but then adding that command in the wtf file didn't change anything sorry.

---

### Post by kenrerd on 2011-01-23
Did you want me to post what comes up in terminal before it opens, after I put in the open command?

---

### Post by Halzen on 2011-01-23
> **kenrerd said:**
> Did you want me to post what comes up in terminal before it opens, after I put in the open command?

You had more in response to the glxinfo query then the line I posted? If so, I'd love to see it.

Moving on, I believe we need to ensure that your video acceleration is set up and working properly. First, I need to know what sort of video device you have. Please run the following code into your Terminal to try to identify your graphics device:

```
sudo lshw -C video
```

The output should include a couple lines similar to the following:
```
description: VGA compatible controller
product: GT200 [GeForce GTX 260]
```

The above was my example, so what yours actually lists will obviously vary.

---

### Post by kenrerd on 2011-01-23
No sorry, when I did the glxinfo I just got the Yes thing that you wanted.
I meant when I put int he command to run wow through wine it outputs a long list of things then eventually wow opens witht he graphical problems, I thought maybe the problem might be listed then? 

As for the video device lines, my output was: 

*-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:90000000-903fffff memory:80000000-8fffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:92500000-925fffff

---

### Post by Halzen on 2011-01-23
Oh, dear, my fear has been realized: you're using Intel integrated graphics.

First off, many Intel drivers do not play nice with WoW in OpenGL mode. Try removing the -opengl parameter when running WoW.

If that doesn't fix it, we need to do some Regedit editing. First, enter the following into your Terminal:
```
wine regedit
```
This'll open Regedit under Wine. Do not close your Terminal while using Regedit, cuz that'll likely freeze or close Regedit as well.

Navigate to the following key: HKEY_CURRENT_USER/Software/Wine/Direct3D

Click on Direct3D to gain access to the strings to the right. We need to add the following strings, or edit them if any exist:

```

 "OffscreenRenderingMode" = "backbuffer"
 "PixelShaderMode" = "disabled"
 "UseGLSL" = "enabled"
 "VertexShaderMode" = "hardware"

```
Make sure that all of the keys are text value.

Now we're going to edit the Config.wtf we were working with before. You'll be adding some of these configs at the end of the document, or you'll be editing any that already exist (Gedit's find function will make this easy):

```
SET SoundOutputSystem "1"
 SET SoundBufferSize "150"
 SET gxApi "d3d"
 SET ffxGlow "0"
 SET readTOS "1"
 SET readEULA "1"
```

Once this is all done, let me know how WoW behaves.

---

### Post by kenrerd on 2011-01-23
There is no Direct3D folder or file in the wine directory. Only: Debug, FileOpenAssociations, Fonts, Menufiles, MSHTML, Temporary System Parameters and WineDbg.

---

### Post by Halzen on 2011-01-23
> **kenrerd said:**
> There is no Direct3D folder or file in the wine directory. Only: Debug, FileOpenAssociations, Fonts, Menufiles, MSHTML, Temporary System Parameters and WineDbg.

Okay, then add a key to the Wine directory and call it Direct3D. Then, add the strings and parameters that I listed.

---

### Post by kenrerd on 2011-01-23
I'm not too sure if i'm adding the strings correctly sorry, I right click in the field>new>string value
Then there's a name and a data part, what do I type in where? is the name the first bit and the data the stuff after the =?

---

### Post by Halzen on 2011-01-23
> **kenrerd said:**
> I'm not too sure if i'm adding the strings correctly sorry, I right click in the field>new>string value
Then there's a name and a data part, what do I type in where? is the name the first bit and the data the stuff after the =?

Precisely. For example, "OffscreenRenderingMode" = "backbuffer" means that the name should be "OffscreenRenderingMode" and the data should be "backbuffer", without the quotes. Make sure to match case; most backend data strings are case-sensitive.

---

### Post by kenrerd on 2011-01-23
That's definately working better, I can see characters now.
however, Underneath all the characters in game however the terrain is black, not everywhere just underneath my characters and other characters/npcs. and if I move the camera angle the terrain will jump in and out of black/normal so I often get completely black screens.

---

### Post by Halzen on 2011-01-24
> **kenrerd said:**
> That's definately working better, I can see characters now.
however, Underneath all the characters in game however the terrain is black, not everywhere just underneath my characters and other characters/npcs. and if I move the camera angle the terrain will jump in and out of black/normal so I often get completely black screens.

If you can, force all of your in-game graphics settings to Fair. Turn off multisampling, vertical sync, and projected textures.

---

### Post by Halzen on 2011-01-24
Oh, and disable shadows, texture filtering, and the other advanced effects completely.

---

### Post by kenrerd on 2011-01-24
OK did all that and still no go sorry.

---

### Post by _outlawed_ on 2011-01-24
I'm sorry to say this, but you aren't going to be able to play WoW all that well with an integrated intel card/chip. They are the worst of the 3 (nVidia->ATI->Intel) as far as linux graphics go.

You would be better off dual booting Windows to play most games on.

---

### Post by kenrerd on 2011-01-24
Yeah i've come to realise that haha ah well, might fiddle around with it a bit more then try dual booting or something. thanks anyway guys.

---

### Post by cwwilson721 on 2011-01-24
One quick addendum:

After adding '-opengl' to your command, the newest versions of WoW (4.0.3a) adds ```
SET gxApi "OpenGL"
```to the config.wtf file. So even if you remove the appended command, it will still run in opengl mode. 

If you wish to run in D3D, you must remove both the '-opengl' appendage, and the "SET gxApi "OpenGL"" in config.wtf

Just something I've noticed.

---

