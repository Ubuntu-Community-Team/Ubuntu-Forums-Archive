---
title: "Ubuntu Wine+world of warcraft yielding errors"
date: 2009-08-10
forum: Wine
---

### Post by flapjacks on 2009-08-10
I downloaded WoW from blizzards website using their update manager thing. But typing wine "C:\Program Files\World of Warcraft\WoW.exe" in terminal only gives me this:

err:wineboot:pendingRename couldn't get file attributes (2)
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed84,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec74,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f278,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f124,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x32efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f124,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
Killed

After which WoW boots for a couple seconds then gives me a 132 error.
Clicking the launcher doesn't work either. It just shows the launcher with the news and stuff for a couple seconds then leads me back to the installation screen, though WoW is already installed. Halp?

OH I should also add that I rebooted and tried again, on on my third try I could start the game and watch the intro movie and log in but it said I had to download a patch. I click ok and it wants me to accept some license agreement, but I can't because the "agree" box is greyed out even when I scroll to the bottom of the page.

---

### Post by hikaricore on 2009-08-10
You're gonna have to provide more info.
For example what kinda video hardware are you using nvidia or ati?
Are your drivers properly installed? And so on.

---

### Post by flapjacks on 2009-08-10
Card: NVIDIA GeForce Go 8600M GT with 256MB GDDR3
Driver: nvidia accelerated graphics driver version 180 (I'm pretty sure it's up to date, maybe not)
6 gigs of ram, intel core 2 duo processor.

I think it's just a patching problem. I'm manually downloading patches now to see if it'll work.

---

### Post by 8Kuula on 2009-08-11
> **flapjacks said:**
>  OH I should also add that I rebooted and tried again, on on my third try I could start the game and watch the intro movie and log in but it said I had to download a patch. I click ok and it wants me to accept some license agreement, but I can't because the "agree" box is greyed out even when I scroll to the bottom of the page.

Using newest wine version, atm v1.1.27? That "agree" box grayed bug was in some older wine versions :roll:

---

