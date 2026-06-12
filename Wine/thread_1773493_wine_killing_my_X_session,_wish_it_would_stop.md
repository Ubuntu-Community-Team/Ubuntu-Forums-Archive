---
title: "wine killing my X session, wish it would stop"
date: 2011-06-02
forum: Wine
---

### Post by DatBugler on 2011-06-02
I'm trying to run Rollercoaster Tycoon 3 under WINE, but after a seemingly random period of time somewhere in the 1-10 min time frame after I start building a rollercoaster in the rollercoaster design tool, I get a black screen and then am returned to the login manager. Some research has led me to conclude that WINE is most likely exposing a disagreement among the game's DirectX 9, the proprietary NVidia graphics driver for my GTS 450, and X11.

I am running Kubuntu 10.10 x64 with fully updated packages and drivers. I regularly use non-3D applications under WINE with no problems. I also routinely run native Linux 3D (OpenGL) applications with no problems.

I have tested running the game in Windows XP and Windows 7 mode, windowed and fullscreen, and both with and without a virtual desktop, with the same result. I have also tried reinstalling the NVidia driver and turning off compositing, to no effect.

Here is my Xorg.conf:
```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "InputClass"
        Identifier  "Marble Mouse"
        MatchProduct "Logitech USB Trackball"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "ButtonMapping" "1 2 3 4 5 6 7 8 9"
        Option "EmulateWheel" "true"
        Option "EmulateWheelButton" "8"
        Option "ZAxisMapping" "4 5"
        Option  "XAxisMapping" "6 7"
        Option  "Emulate3Buttons" "true"
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

Here is the spew from running the game under WINE from the command line:
```

fixme:win:EnumDisplayDevicesW ((null),0,0x184e254,0x00000000), stub!
wineserver: file_set_error() can't map error: Function not implemented
fixme:d3d:IWineD3DImpl_CheckDeviceFormatConversion iface 0x13d148, adapter_idx 0, device_type WINED3DDEVTYPE_HAL, src_format WINED3DFMT_B8G8R8A8_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1280x768x0 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1280x800x0 @0! (XRandR)
fixme:mixer:ALSA_MixerInit No master control found on M Audio Audiophile 24/96, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on TASCAM US-X2Y, disabling mixer
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x3e12b58,0x3e12ab8): stub

```

All of that spew happens at the game's initial loading. I've tried redirecting the output to a log file, to see if it catches an error message when the X server crashes, but the log turned up empty. I guess the game itself doesn't actually crash, just X11.

After the last X11 crash, a file turned up in my home directory entitled "GraphFix.log" with the following contents:
```

Driver          : nv4_disp.dll
Description     : NVIDIA GeForce 8300 GS
DeviceName      : \\.\DISPLAY1
VendorID     (*): 4318
DeviceID     (*): 1059
SubSysID        : 0
Revision        : 0
WHQLLevel       : 1
DriverVersion(*): 0x0008000F000B2611

```

It looks like nv4_disp.dll is the culprit in some way, but I'm unsure how to proceed from here. Is there a different version of the file I should try having WINE use instead? Or am I on the wrong track altogether?

---

### Post by bobwyajnr on 2011-06-03
Hi

Whats with the **nv4_disp.dll**?? That's part of the Windows version of the Nvidia drivers?!! Has no place in Linux :popcorn:

I presume you have Desktop effects disabled (in the KVM Setting Manager) for full-screen applications. I think you said this was the case...

What Nvidia driver are you using - 270.xx I presume?

What Wine version and what .dll/library over-rides do you have in place? What else have you installed in the same WINEPREFIX?

Personally I've only seen Wine locking up my Desktop manager (in recent times). But I can't remember the last time I had to reboot as a result (normally I can just hope to a TTY console and kill the offending process).

Bob

---

### Post by Shikiru on 2011-06-05
I can't really help on this issue but I waned to say that I am having the same problem and would like to help if I can. I don't know if any cross-referencing would help but hey, thought I'd offer and I do hope this gets fixed :)

~Critter

PS, I'm using Ubuntu 11.04

---

### Post by Shikiru on 2011-06-10
So installing dev release of  Wine 1.3.21 solved my issue :)

---

