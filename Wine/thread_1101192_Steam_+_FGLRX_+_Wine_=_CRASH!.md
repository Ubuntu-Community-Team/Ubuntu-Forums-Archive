---
title: "Steam + FGLRX + Wine = CRASH!"
date: 2009-03-20
forum: Wine
---

### Post by drelyn86 on 2009-03-20
This is a very big problem I've been having ever since Ubuntu Gutsy, and I would really LOVE to get it resolved. 

Whenever I play ANY steam game (under wine) for a few minutes, my X server completely crashes. This includes all Source games AND CS 1.6, Half-Life, etc (even using OpenGL). 

However... I've also tested WoW and Wolfenstein: Enemy Territory using Wine, and had absolutely no problems!

I've tried changing all different Windows Versions, disabling hardware Vertex and Shader support, changing between ALSA and OSS, changing to emulation sound drivers, the "UseFastTLS" tweak, newer versions of Wine, older versions of Wine, disabling in-game community, newer versions of FGLRX, older versions of FLRX, Ubuntu Gutsy, Ubuntu Hardy, Ubuntu Intrepid, ETC!!!

I've tried running Steam in console... it reports nothing relevant before the inevitable crash. I've even tried redirecting the console output to a file... but the file never saves, because I have to do a hard reboot when the X server crashes. 

Right now, I'm clueless... please help!!!

------------------

Current (relevant) specs:

CPU: AMD X2 5000+ Black Edition
GPU: Diamond ATI HD3850 256MB
MOBO: Asus M2N-SLI Deluxe
OS: Ubuntu Intrepid 32-bit
FGLRX: "OpenGL version string: 2.1.8087 Release" (not sure which version that is... whatever is in the repositories)
Wine: 1.1 (repositories)

---

### Post by drelyn86 on 2009-03-20
BUMP!

Come on guys, this would make a huge impact on my complete switch from Windows.

---

### Post by typiCAL_ on 2009-09-16
not to bring this back from the dead if it's already been solved, but google led me here and i'm wondering if anyone else has/had the same problem with source games on steam.

basically cs:s for example will start and get to the menu, but that's as far as i get.  anytime i try to do anything that renders graphics or sounds (besides the menu), i'm conveniently brought back to my desktop.  this includes video stress test and even speakers test from the audio menu!
as for hl2, while the menu is "loading..." as shown at the bottom right the same thing happens and i'm brought back to my desktop.

ftr i'm using:
linuxmint7/jaunty 9.04
radeon hd 4570
wine 1.0.1
below is what i find to be the last relevant messages from the console for each game:

```

CS:S

Backtrace:
=>1 0x0df2b423 in datacache (+0xb423) (0x00000002)
  2 0x00000000 (0x00000000)
utlmemory.h (322) : Assertion Failed: IsIdxValid(i)

``````

HL2

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
err:alsa:ALSA_copyFormat calculated 50 bytes, capping to 40 bytes
err:ntdll:RtlpWaitForCriticalSection section 0xa745ec "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0xa745ec "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)

```

so far from googling these have NOT worked:
disabling all desktop related compositing (desktop effects, compiz, gnome compositing, etc)
disabling steam community in-game
launching games with options -novid -dxlvl 80/70

i also have an all-alsa setup, i have pulseaudio disabled completely and winecfg is set to use only alsa.

:confused:

---

### Post by drelyn86 on 2009-09-16
> **typiCAL_ said:**
> not to bring this back from the dead if it's already been solved, but google led me here and i'm wondering if anyone else has/had the same problem with source games on steam.

basically cs:s for example will start and get to the menu, but that's as far as i get.  anytime i try to do anything that renders graphics or sounds (besides the menu), i'm conveniently brought back to my desktop.  this includes video stress test and even speakers test from the audio menu!
as for hl2, while the menu is "loading..." as shown at the bottom right the same thing happens and i'm brought back to my desktop.

ftr i'm using:
linuxmint7/jaunty 9.04
radeon hd 4570
wine 1.0.1
below is what i find to be the last relevant messages from the console for each game:

```

CS:S

Backtrace:
=>1 0x0df2b423 in datacache (+0xb423) (0x00000002)
  2 0x00000000 (0x00000000)
utlmemory.h (322) : Assertion Failed: IsIdxValid(i)

``````

HL2

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
err:alsa:ALSA_copyFormat calculated 50 bytes, capping to 40 bytes
err:ntdll:RtlpWaitForCriticalSection section 0xa745ec "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0xa745ec "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)

```

so far from googling these have NOT worked:
disabling all desktop related compositing (desktop effects, compiz, gnome compositing, etc)
disabling steam community in-game
launching games with options -novid -dxlvl 80/70

i also have an all-alsa setup, i have pulseaudio disabled completely and winecfg is set to use only alsa.

:confused:

lol yeah this thread is pretty old... since my last bump, I switched to Arch Linux (and still had the same results). However, once I switched my card to an nvidia 9600gt... no more problems.

---

### Post by typiCAL_ on 2009-09-16
> **drelyn86 said:**
> lol yeah this thread is pretty old... since my last bump, I switched to Arch Linux (and still had the same results). However, once I switched my card to an nvidia 9600gt... no more problems.

safe to assume it IS an ATI thing then, im curious if it's limited to the proprietary closed source drivers or if it's an issue with the opens source drivers too.  it's a shame it's been going on this long though and hasn't been fixed yet.  ain't too easy to replace an integrated gpu in my laptop, but i'm glad you were able to find a sort of solution :-|

---

### Post by Duskao on 2009-09-16
Part of the problem is the FGLRX driver in it's self. The driver in the repositories isn't all that fantastic in intrepid. In fact the driver in Jaunty isn't much better either. I was having similar issues with my card HD 4850. But Ati is making good headway with their drivers, but you have to download them from the ati site and install them. The current driver is catalyst 9.9 and it's very stable on my machine and there is a large performance boost from the driver you are trying to use the the repository.

---

### Post by typiCAL_ on 2009-09-16
> **Duskao said:**
> Part of the problem is the FGLRX driver in it's self. The driver in the repositories isn't all that fantastic in intrepid. In fact the driver in Jaunty isn't much better either. I was having similar issues with my card HD 4850. But Ati is making good headway with their drivers, but you have to download them from the ati site and install them. The current driver is catalyst 9.9 and it's very stable on my machine and there is a large performance boost from the driver you are trying to use the the repository.

oops, i suppose i omitted that part in my original post, as i mentioned it in another thread instead.  i am currently using the 9.9 catalyst driver i downloaded from ati/amd.  the driver that came with jaunty doesn't even support 3d compositing at all!  it took a few headaches but i do have the catalyst driver and it works extremely well too, but steam/source-based games are still not working properly ](*,)

---

### Post by drelyn86 on 2009-09-17
> **typiCAL_ said:**
> oops, i suppose i omitted that part in my original post, as i mentioned it in another thread instead.  i am currently using the 9.9 catalyst driver i downloaded from ati/amd.  the driver that came with jaunty doesn't even support 3d compositing at all!  it took a few headaches but i do have the catalyst driver and it works extremely well too, but steam/source-based games are still not working properly ](*,)

The Catalyst drivers that were included with 8.10, 9.04, and now 9.10 are all beta-release drivers made specifically for Canonical, due to AMD's inability to keep up with Xorg releases and kernel updates.

---

### Post by typiCAL_ on 2009-09-17
> **drelyn86 said:**
> The Catalyst drivers that were included with 8.10, 9.04, and now 9.10 are all beta-release drivers made specifically for Canonical, due to AMD's inability to keep up with Xorg releases and kernel updates.

Well that at least explains the lack of 3D support, though it's still a shame AMD hasn't been able to keep up with the linux support.  I was going to try and downgrade my catalyst version to 9.8 as from what I've been reading it's considered more stable and powerful than the 9.9, but it seems AMD took it off their site because I keep getting a 404 for that version, and the 9.7 is pre Mobility Radeon HD support so it's out of the question as well.. :(

---

