---
title: "Unreal Tournament bright screen."
date: 2009-05-04
forum: Wine
---

### Post by solidsnake204 on 2009-05-04
I have Unreal Tournament (Game of the Year Edition) installed and runs mostly fine under Wine.

But I get these two annoying problems.

One is that every now and then the game speeds up and I'm walking faster than usual for a few seconds.

Another problem is when I exit the game, my screen is left very bright, like a white overlay. I can only fix this if I log off and on again or restart the computer.

I'm running Ubuntu 9.04, I have a 1.8GHz Pentium Dual Core Processor, 2GB RAM, NVIDIA 9500GT 1GB using the NVIDIA Driver version 180.

I am using Wine 1.0.1 and it's configured like this:
*Applications Tab*
Windows Version: Windows XP

*Libraries Tab*
No DLL overrides

*Graphics Tab*
Allow DirectX apps to stop the mouse leaving their window - Disabled
Allow the window manager to decorate the windows - Enabled
Allow the window manager to control the windows - Enabled
Emulate a virtual desktop - Disabled
Vertex Shader Support: Hardware
Allow Pixel Shader - Enabled
Screen Resolution: 96 dpi

*Audio Tab*
ALSA Driver checked, other options unchecked.
Hardware Acceleration: Full
Default sample rate: 44100
Default bits per sample: 16
Driver emulation - Disabled

This is the terminal output when I ran UT from the terminal:
> fixme:process:GetProcessWorkingSetSize (0xffffffff,0x32f39c,0x32f398): stub
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32c608,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:keyboard:RegisterHotKey (0x1002c,49247,0x00000001,27): stub
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ole:CoGetClassObject class {92fa2c24-253c-11d2-90fb-006008a1f441} not registered
err:ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441} could be created for context 0x1
err:ole:CoGetClassObject class {d8f1eee0-f634-11cf-8700-00a0245d918b} not registered
err:ole:CoGetClassObject no class object {d8f1eee0-f634-11cf-8700-00a0245d918b} could be created for context 0x1
fixme:d3d_surface:IWineD3DBaseSurfaceImpl_Blt Can't handle WINEDDBLT_ASYNC flag right now.
fixme:dsound:DllCanUnloadNow (void): stub


In the UnrealTournament.ini file, under the [WinDrv.WindowsClient] section, I have added the following lines:
> FrameRateLimit=60
SwapInterval=1

---

### Post by CatKiller on 2009-05-04
There is a Linux-native client for Unreal Tournament.

---

### Post by u235sentinel on 2009-05-04
> **CatKiller said:**
> There is a Linux-native client for Unreal Tournament.

I recommend it.  It comes on the store bought cd but I had problems with some servers.  Upgrading to the latest (3369 I think) solved that problem.  You can download it from their site.

Haven't had a problem since.

---

### Post by solidsnake204 on 2009-05-04
I've downloaded the Linux setup for it...

...but it seems to require the original CD ROM? Which I don't have.

I've lost the CD-ROM, I only have the game files which I backed up.

---

### Post by diiphantom on 2009-06-17
download the iso :) good luck!

---

### Post by u235sentinel on 2009-06-17
> **diiphantom said:**
> download the iso :) good luck!

Yeah.  Not much we can do without the software :D

---

