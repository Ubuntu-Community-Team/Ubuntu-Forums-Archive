---
title: "Battlefield 2 Staticmesh.fx Error"
date: 2010-11-18
forum: Wine
---

### Post by doctorzeus on 2010-11-18
Hi I've been trying to get BF2 working for a week now and have been encountering various texture problems and crashes. I decided to start BF2 via "wine (location to bf2.exe)" so I can see the output. However trying to start the game via command line I get the error:

```

Shaders/StaticMesh.fx not found!!! _Do_check your working directory, _AND_sync your shaders folder before calling upon your local rendering programmmer/GP. (really!)

```

Heres my wine terminal output:

```

fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13b390,0x137c30): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e2b4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dcf0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dde0,0x00000000), stub!
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class obje****ct {da4e3da0-d07d-11d0-bd50-00a0c911ce86} could be created for context 0x1
err:ole:CoGetClassObject no class object {71985f4b-1ca1-11d3-9cc8-00c04f7971e0} could be created for context 0x1
err:ole:CoGetClassObject no class object {a2e3074f-6c3d-11d3-b653-00c04f79498e} could be created for context 0x1
err:ole:CoGetClassObject class {cc7bfb41-f175-11d1-a392-00e0291f3959} not registered
err:ole:CoGetClassObject no class object {cc7bfb41-f175-11d1-a392-00e0291f3959} could be created for context 0x1
err:ole:CoGetClassObject class {cc7bfb46-f175-11d1-a392-00e0291f3959} not registered
err:ole:CoGetClassObject no class object {cc7bfb46-f175-11d1-a392-00e0291f3959} could be created for context 0x1
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @85! (XRandR)

```

Does anyone have any idea how to solve this?!?

Thanks

Doctorzeus**[B]**[/B]

---

### Post by doctorzeus on 2010-11-20
Anyone?

I really need help with this please!

---

### Post by bobwyajnr on 2010-11-24
[LIST=2]
[*]
> **doctorzeus said:**
> 
```

Shaders/StaticMesh.fx not found!!! _Do_check your working directory, _AND_sync your shaders folder before calling upon your local rendering programmmer/GP. (really!)

```


You have to have the working directory set to where the BF2.exe is stored, e.g. easiest way:
```

cd "~/.wine/drive_c/Program Files/Electronic Arts/Battlefield 2/"
wine ./BF2.exe

```
just substitute your own path to the executable (e.g. if you are using a Wine prefix).

[*]
> **doctorzeus said:**
> 
```

err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @85! (XRandR)

```


You have a problem in that your xorg.conf is (probably) misconfigured. Your X-Server is not supporting a fullscreen mode of 800x600. You can confirm this is the case by trying to run the game in a Virtual Desktop of size 800x600 (using Winecfg). It should run OK.

Check out this thread for how I fixed my xorg.conf file:
[WineHQ Forums : supporting 800x600 startup screenmode for BF2/2142]("http://forum.winehq.org/viewtopic.php?t=10243&highlight=battlefield")

Perhaps you could post your xorg.conf file on this thread and someone can dissect it for you! Also what graphics card do you have and what driver version? How is/are your monitor(s) hooked up (DVI, VGA, HDMI, etc.)?
[/LIST]

**[COLOR="DarkRed"]Just remember that messing about with your xorg.conf can easily break your X-Server!! Back up your current configuration file and ensure you are comfortable with the commandline process to restore the original xorg.conf file - should something go wrong![/COLOR]**

Hope that helps!! :popcorn:

Bob

---

