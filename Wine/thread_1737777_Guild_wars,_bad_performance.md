---
title: "Guild wars, bad performance"
date: 2011-04-23
forum: Wine
---

### Post by GridLynx on 2011-04-23
Greetings

I recently tried to run GW under wine. Needless to say  the performance was not the expected as you can witness on the following  screenshot.

- Laptop's Specs:
1.6 Ghz Centrino Duo
2gbs ram
128 mbs video memory
intel mobile graphics 945gm

Wine version: 1.2.2
Ubuntu: 10.10

Winecfg:
- Windows Version XP
- Allow the Windw manager to decorate windows
- Allow the Window manager to control the windows
- Emulate a Virtual desktop
- Vertex Shader Support: Hardware
- Allow Pixel Shader

Winedit:
- DirectDrawRenderer = opengl
- UseGLSL = enabled
- VideoMemorySize = 128
-VideoPciDeviceID 0x27a2
-VideoPciVendorID 0x8086

Terminal Output

[email]gridlynx@gridlynx-MX8720M:~/.wine[/email]/dosdevices/c:/Program Files/Guild Wars$ ./Gw.exe
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32e94c,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32e98c,0x00000000), stub!
fixme:imm:ImmDisableTextFrameService Stub
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1af1688,0x1e73b8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e74f0,0x1e73f0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e74f0,0x1e73f0): stub
fixme:d3d:state_vertexblend_w Vertex blend flags 0x100 not supported.
fixme:d3d:state_zfunc D3DCMP_NOTEQUAL and D3DCMP_EQUAL do not work correctly yet

Your help would be greatly appreciated!

( I included a screen shot of the regedit just to see if i was inputting it correctly)

---

### Post by handy on 2011-04-24
It looks like your Intel graphics card (or its drivers) are letting you down.

---

### Post by GridLynx on 2011-04-24
Seems like it, but if they are sort of " Supported " with analogue drivers for linux distributions... shouldn't they like work but with lesser performance? Maybe there is something that  i am not doing..

---

### Post by handy on 2011-04-24
You may find something of use here:

[http://www.guildwarsguru.com/forum/guide-permanent-fix-for-unrecoverable-t10408301.html?p=4905012](http://www.guildwarsguru.com/forum/guide-permanent-fix-for-unrecoverable-t10408301.html?p=4905012)

---

### Post by GridLynx on 2011-04-24
No sir.. didn't affect it much... I am wondering if the values i applied for the graphic card are correct ( When it comes to the registry)

00:02.0 0300: 8086:27a2 (rev 03)

According to a guide, 0300 means a VGA peripherial/card and 8086 should be the ID vendor for Intel... and obviously 27a2 should be the ID of the device.

Thanks for the tip tho! 

Hope someone can give us another lead tho

---

### Post by handy on 2011-04-24
> **GridLynx said:**
> ...
Hope someone can give us another lead tho

If I were you I'd be going through everything I could find that relates to your card & GW via Google.

There are obviously some people experiencing difficulties getting your card to work when running Windows. So knowing everything about the problem from that side would be my first step.

After knowing & applying where possible that understanding, then comes the Wine side of the problem.

Anyway, I hope it all works out for you as it is a great game, I spent years playing it in the past.

Looking forward to the release of GW2. :)

***[edit:]** I just had a thought; you could give the Crossover Games trial a go, to see what results you get, they also have a great forum that the dev's monitor quite closely. They are the prime Wine developers too (in case you didn't know that).*

---

### Post by brpylko on 2011-04-24
I've found some applications suffer greatly from having GLSL enabled, try disabling it and then see how it goes.

---

### Post by GridLynx on 2011-04-25
> If I were you I'd be going through everything I could find that relates to your card & GW via Google.

There are obviously some people experiencing difficulties getting your  card to work when running Windows. So knowing everything about the  problem from that side would be my first step.

Yeah, i think i will start googling those in specifical. The odd thing is, that while using XP and the very same video device, i could get up to 30-35 fps. I am aware tho of the limitations of using drivers destined for Linux kernel based OS and how they are " Not as adequate" as their propietary counterpats but i didn't expect that much of a hassle.. Nevertheless, i won't give up on on the search! :D

Also, i am also thinking of giving Cross Overs a twirl! good thing you reminded me about it :P

> I've found some applications suffer greatly from having GLSL enabled, try disabling it and then see how it goes. 	

Yep, I just disabled it but i have the very same effect on my game: No background, whiteish polygonal characters and very poor FPS performance.  Thanks for the tip tho!

---

### Post by handy on 2011-04-25
In the early days of my playing GW, I used Cedega (yuk!), then I went over to Crossover, which worked great (the Codeweavers team had the opposite attitude in comparison to that of the Transgaming team) under both Linux & OS X. 

I ended up using Crossover under OS X, for GW, as the graphics drivers for my ATi HD2600 Pro, were better than any of those available for Linux (at that time anyway).

---

### Post by GridLynx on 2011-04-25
I am in the worst of lucks it seems! 

I tried crossover games yesterday and nope! i have the very same problem i experienced when i tried GW with just wine...

If the problem is the drivers.. is there a way to activate the propietary ones even if they don't appear in the additional drivers manaer in the system tab?

---

### Post by handy on 2011-04-25
> **GridLynx said:**
> I am in the worst of lucks it seems! 

I tried crossover games yesterday and nope! i have the very same problem i experienced when i tried GW with just wine...

If the problem is the drivers.. is there a way to activate the proprietary ones even if they don't appear in the additional drivers manner in the system tab?

I don't think there are any. I've read that some people got better results in the past using the 915 driver?

You could take a chance & try the following:

**sudo apt-get install xserver-xorg-video-intel**

---

### Post by GridLynx on 2011-04-26
> **handy said:**
> I don't think there are any. I've read that some people got better results in the past using the 915 driver?

You could take a chance & try the following:

**sudo apt-get install xserver-xorg-video-intel**

~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

This was the console feed back

---

### Post by handy on 2011-04-26
Sorry mate, I've reached the end of the line. I don't know what else to offer you.

It must be a total pain in the butt.

Perhaps the only way you will get to play GW on that machine is if you dual boot the dreaded XP.

Which I know I wouldn't be happy about doing, but sometimes we are left with no other choice.

---

### Post by GridLynx on 2011-04-26
That's about right.. it's been a while since i last booted it but.. i guess it will be for a good cause haha.

Thanks for all the tips and support, Handy!

---

### Post by handy on 2011-04-26
> **GridLynx said:**
> That's about right.. it's been a while since i last booted it but.. i guess it will be for a good cause haha.

Thanks for all the tips and support, Handy!

My pleasure. :)

---

### Post by disabledaccount on 2011-04-26
I'm not playing Guild Wars, but it's marked Platinium on Wine AppDB, so... have You tried this:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)
I mean different commad line switches for GW (like -dx_8 ), disabling GLSL for Intel etc?

---

### Post by GridLynx on 2011-04-26
> **tomazzi said:**
> I'm not playing Guild Wars, but it's marked Platinium on Wine AppDB, so... have You tried this:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)
I mean different commad line switches for GW (like -dx_8 ), disabling GLSL for Intel etc?

Yep... every single possible fix was tried, Tomazzi.

I guess i will have no choice but to dual boot, and imight also consider posting my experiences at that web, just to see if anybody knows anything else.. but i don't have my hopes up  :P

---

### Post by -=- Mr. Tux -=- on 2011-07-05
goto wine cfg

in graphics menu 

set from hardware to emulation

i had this happen too fixes it 

try it let me know

---

