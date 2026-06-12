---
title: "ePSXe isn't working in Wine, Jaunty"
date: 2009-05-22
forum: Wine
---

### Post by ikacer on 2009-05-22
I'm having trouble getting ePSXe 1.70 to run in Wine.

ePSXe starts up fine, but when I try to run an iso it gives me a blank window. I'm using Pete's OpenGL2 and Eternal's sound plugins. when i run an iso I get this output:

```
$ wine ePSXe.exe
 * Running ePSXe emulator version 1.7.0. 
 * Running ePSXe emulator version 1.7.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [bios\SCPH1001.BIN]. 
 * Loading ISO Format [MDF/BIN/IMG2352] ok
 * First/Last track: 1 1
 * Track 1: (DATA)  - Start 1: (00,02,00) -  Length 61:27
 * NTSC cdrom detected. (SLU__000.00) 
 * Doing init gpu[0]... 
 * Gpu open[0]... 
 * Direct input init ok. 
 * Doing spu init... 
 * Spu open... 
fixme:wgl:X11DRV_wglBindTexImageARB partial stub!
```

at this point ePSXe is trying to run the game but only shows a black screen, with the plugin reporting 0.000FPS. Also the process is running at this point and uses all the available cpu. AppDB says it runs fine with these plugins under Intrepid and Hardy. I'm running Wine 1.1.21 in Jaunty.

Does anyone have any ideas on how to get this working? Also, if anyone has ePSXe working in wine on jaunty, could you please tell me what plugins/settings/wine version/etc you are using?

thanks

---

### Post by asdfoo on 2009-05-22
> **ikacer said:**
> I'm having trouble getting ePSXe 1.70 to run in Wine.

ePSXe starts up fine, but when I try to run an iso it gives me a blank window. I'm using Pete's OpenGL2 and Eternal's sound plugins. when i run an iso I get this output:

```
$ wine ePSXe.exe
 * Running ePSXe emulator version 1.7.0. 
 * Running ePSXe emulator version 1.7.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [bios\SCPH1001.BIN]. 
 * Loading ISO Format [MDF/BIN/IMG2352] ok
 * First/Last track: 1 1
 * Track 1: (DATA)  - Start 1: (00,02,00) -  Length 61:27
 * NTSC cdrom detected. (SLU__000.00) 
 * Doing init gpu[0]... 
 * Gpu open[0]... 
 * Direct input init ok. 
 * Doing spu init... 
 * Spu open... 
fixme:wgl:X11DRV_wglBindTexImageARB partial stub!
```

at this point ePSXe is trying to run the game but only shows a black screen, with the plugin reporting 0.000FPS. Also the process is running at this point and uses all the available cpu. AppDB says it runs fine with these plugins under Intrepid and Hardy. I'm running Wine 1.1.21 in Jaunty.

Does anyone have any ideas on how to get this working? Also, if anyone has ePSXe working in wine on jaunty, could you please tell me what plugins/settings/wine version/etc you are using?

thanks

does using a dx plugin instead of opengl change anything?

---

### Post by ikacer on 2009-05-22
I get the same error with the DirectX plugins as well as a few other OpenGL plugins I've tried. Changing the sound plugin or bios doesn't have any effect. I've had ePSXe running in Windows on this same computer before without any problems.

This is the output I get with Pete's D3D plugin (the dx7 version):
```
wine ePSXe.exe
 * Running ePSXe emulator version 1.7.0. 
 * Running ePSXe emulator version 1.7.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [bios\SCPH1001.BIN]. 
 * Loading ISO Format [MDF/BIN/IMG2352] ok
 * First/Last track: 1 1
 * Track 1: (DATA)  - Start 1: (00,02,00) -  Length 61:27
 * NTSC cdrom detected. (SLU__000.00) 
 * Doing init gpu[0]... 
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2c0,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
 * Gpu open[0]... 
 * Direct input init ok. 
 * Doing spu init... 
 * Spu open...
```

The savestate, disable framelimit, and such commands done by the F1, F2,... keys still seem to work as they will show up in the terminal output.

---

### Post by bikodog on 2009-05-23
I am trying to get epsxe running in wine as well and it is freezing on the black screen too.

Here is my terminal output:

```

```
ej-studio@ej-studio:~/epsxe_wine/epsxe170$ wine ePSXe.exe
fixme:mixer:ALSA_MixerInit No master control found on MidiSport 2x2, disabling mixer
 * Running ePSXe emulator version 1.7.0. 
 * Running ePSXe emulator version 1.7.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [bios\scph1001.bin]. 
 * Loading ISO Format [MDF/BIN/IMG2352] ok
 * First/Last track: 1 1
 * Track 1: (DATA)  - Start 1: (00,02,00) -  Length 13:52
Warning: ISORead overflow
 * NTSC cdrom detected. (SLU__000.00) 
 * Doing init gpu[0]... 
 * Gpu open[0]... 
 * Direct input init ok. 
 * Init core spu ...  ok 
```

```

Any thoughts?

---

### Post by fukr on 2009-05-23
I'm curious why you're trying to run PSX emulation under Wine in Linux. Unless you have some obscure cause to do it in this roundabout way, try the Linux Playstation emulator [pSX]("http://psxemulator.gazaxian.com/"). I've used pSX and ePSXe (Linux version) with the [wah!cade]("http://www.anti-particle.com/wahcade.shtml") frontend in both Debian 5 and Ubuntu 8.10. Really worth checking out -- it works as a frontend to any emulator you want to use. Here's a nice video demonstrating [wah!cade in Yellow Dog Linux on a PS3 :popcorn:]("http://www.youtube.com/watch?v=2Y8WrkDRMuI").

Once you get that going, the possibilities are endless: arcade cabinets, joysticks, bluetooth controllers, multi-emulator gaming consoles...it only depends on how far you'd like to go with it ;)

---

### Post by hikaricore on 2009-05-23
> **fukr said:**
> I'm curious why you're trying to run PSX emulation under Wine in Linux. Unless you have some obscure cause to do it in this roundabout way, try the Linux Playstation emulator [pSX]("http://psxemulator.gazaxian.com/"). I've used pSX and ePSXe (Linux version) with the [wah!cade]("http://www.anti-particle.com/wahcade.shtml") frontend in both Debian 5 and Ubuntu 8.10. Really worth checking out -- it works as a frontend to any emulator you want to use. Here's a nice video demonstrating [wah!cade in Yellow Dog Linux on a PS3 :popcorn:]("http://www.youtube.com/watch?v=2Y8WrkDRMuI").

Once you get that going, the possibilities are endless: arcade cabinets, joysticks, bluetooth controllers, multi-emulator gaming consoles...it only depends on how far you'd like to go with it ;)

You forgot pcsx-df: [http://pcsx-df.sourceforge.net/](http://pcsx-df.sourceforge.net/)

---

### Post by ikacer on 2009-05-23
why am I trying to do this in wine? well, I've tried pSX in the past it found it wasn't compatible with a lot of games. Also I like to tweak the gpu settings and use custom shaders to improve the graphics, which you can't do in pSX. Unfortunately the Linux version of ePSXe is outdated and is really inferior to the windows one, as are the available plugins.

Getting back on topic now. I've tried a few more things, none of which have worked. I thought it the problem might be with the way the program handles iso files so I tried Mooby's cdr plugin and let that handle the iso instead, but I got the same error. Also mounting the iso and running it that way also gave the same error.

One interesting error I've encountered occurs when I try to run a bios I've posted the output and attached a png of the window that popped up.

```
$ wine ./ePSXe.exe
 * Running ePSXe emulator version 1.7.0. 
 * Running ePSXe emulator version 1.7.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [C:\Program Files\epsxe170\bios\SCPH1001.BIN]. 
 * Init cdrom ... ok
wine: Unhandled page fault on read access to 0x00000004 at address 0x1218265 (thread 0009), starting debugger...
```

---

### Post by BoyOfDestiny on 2009-05-25
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12203](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12203)
The rating is for an older version of wine...

Downgrade your version of wine, and you should be golden.
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Hopefully the intrepid package for wine 1.1.5 will work with jaunty.

---

### Post by raj7095 on 2009-11-07
use the linux version of epsxe instead. You can get it from epsxe official website. It comes without any plugins. So, here's a website where you can get them: [http://www.pbernert.com/]("http://www.pbernert.com/")
Once you've downloaded the plugins, extract them and rename the gpu plugin to libgpu.so and spu to libspu.so and paste them to the plugins directory. Then, paste the .cfg file and cfg(something) to the cfg directory. That's it.;)

---

### Post by raj7095 on 2009-11-07
Oh, forgot to mention one thing, for running it, put the epsxe directory into your home folder. Now, go to terminal and type in > ./epsxe/epsxe
After that I think you know what to do.:D

---

