---
title: "Hoyle Card Games 2008 - no fullscreen under 64-bit Jaunty"
date: 2009-08-05
forum: Wine
---

### Post by tgeer43 on 2009-08-05
I run both 32-bit Jaunty and recently 64-bit Jaunty on a triple boot with 32-bit Vista.
Hoyle Card Games 2008 installed without a hitch and runs just fine under 32-bit Jaunty but not quite so under 64-bit.

For starters, just to get the game to run I had to add the following files in the game's main directory:

msvcr80.dll
msvcm80.dll
msvcp80.dll
Microsoft.VC80.CRT.manifest

Now it runs just fine but _without any fullscreen mode_. It insists on being 800x600 even when sitting on a larger virtual desktop. I added the app in winecfg and tried the same settings as used under 32-bit as well as every other combination of graphics options but still no fullscreen mode. Rather sucks playing it at 800x600 on my 1440x900 desktop.

Here's the terminal output:
------------------------------------------------------------------------------------
tgeer@tgeer:~$ env WINEPREFIX="/home/tgeer/.wine" wine "C:\Program Files\Encore\Hoyle Card Games 2008\Hoyle Card Games.exe" 
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x142c60,0x142ba8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x142c60,0x142ba8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x5c9f310,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x5c9f2ec,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x24 @0! (desktop)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
-----------------------------------------------------------------------------------
Running wine v.1.1.26 under 9.04 64-bit Jaunty (fully updated) with Nvidia driver v180.

I suspect it can work properly in fullscreen mode since everything works so well under 32-bit Jaunty but don't know what else to try.

Ideas anyone?

Thanks in advance,

tgeer

---

