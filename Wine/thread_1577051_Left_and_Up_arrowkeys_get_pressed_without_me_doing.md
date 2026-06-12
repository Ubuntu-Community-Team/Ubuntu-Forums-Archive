---
title: "Left and Up arrowkeys get pressed without me doing anything"
date: 2010-09-18
forum: Wine
---

### Post by mickcy on 2010-09-18
Had to go into the custom.exe and select "No DirectInput pad".


When playing certain games(which have worked normally before on this exact computer), the Up and Left arrow keys get pressed down for some reason unknown to me.

So far I have deleted .wine and reinstalled wine, attempted to use native and built-in libraries required by these games.

The games in question are the Touhou Project games, I mainly use Embodiment of Scarlet Devil(Touhou 6) to test if something fixed the issue or not, since this game should be able to run. [Running Touhou In Linux]("http://touhou.wikia.com/wiki/Running_in_Linux")(link) is the wiki, though quite outdated since it states that Scarlet Weather Rhapsody and Hisoutensoku cannot run properly, which I managed to do about 6 months ago. Between then and now I reinstalled Ubuntu.[URL="http://appdb.winehq.org/objectManager.php?sClass=application&iId=6020"]
AppDb entry for EoSD[/URL](link)


I currently use Ubuntu 10.04, up-to-date. Wine version 1.3.2.
I had play-on-linux installed and also uninstalled, made no difference.

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f66c,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x169ae0,0x1699e0): stub
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
```Is the terminal output.

I run it under Windows XP and the following settings:

Window Settings:
Allow the window manager to decorate the windows
Allow the window manager to control the windows

Direct3D: Vertex Shader Support [Hardware]
Allow Pixel Shader(if supported by hardware)
Screen resolution: 96 dpi

Audio:
Sound Drivers: ALSA Driver
Wave Out Devices -> default
Wave In Devices -> default
MIDI Out Devices -> Midi Through Port-0
MIDI In Devices -> Midi Through Port-0
Mixer Devices -> HDA Intel

Libraries:
d3dx9_33 -> Native
d3dx9_36 -> Native


Specifications:
Ubuntu Lucid 10.04
Kernel Linux 2.6.32-25-generic-pae
GNOME 2.30.2
Intel Core2 QUAD CPU Q9550 @ 2.83GHz
Resolution: 1680x1050 pixels
nVidia GT200 [GeForce GTX 260]
4GB DDR3 RAM
[Microsoft Wired Keyboard 400]("http://www.microsoft.com/hardware/oempartners/ProductDetails.aspx?pid=104")


I think I mentioned everything that is relevant, if not please mention what I forgot.
I hope someone can help me with this, since I want to play my games. XD

---

