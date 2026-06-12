---
title: "Graphics are garbaged in EVE Online"
date: 2009-07-23
forum: Wine
---

### Post by Dinchamion on 2009-07-23
Hi,

my problem with EVE is that the graphics are garbaged:

[http://www.dinchamion.net/storage/eve_garbage1.png](http://www.dinchamion.net/storage/eve_garbage1.png)
[http://www.dinchamion.net/storage/eve_garbage2.png](http://www.dinchamion.net/storage/eve_garbage2.png)
[http://www.dinchamion.net/storage/eve_garbage3.png](http://www.dinchamion.net/storage/eve_garbage3.png)

Console output:

```
dinchamion@daedalus:~$ wine "C:\Program Files\CCP\EVE\eve.exe" 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x8d0000 0 0x33fcac 4
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x338f04,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #4:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #8:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #12:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #16:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #19:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x30032 0x00000000
fixme:imm:ImmReleaseContext (0x30032, 0x13eec0): stub
dinchamion@daedalus:~$ fixme:reg:GetNativeSystemInfo (0x33b778) using GetSystemInfo()
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #23:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #20:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #26:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #24:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #30:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #27:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #33:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #31:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #37:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #34:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #41:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #38:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #45:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #42:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #46:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #50:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #48:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #54:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x30032
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
```

I'm running Ubuntu 9.04 (64-bit) with 9.6 ATI drivers (installed manually, the one from the repos is unusable for me) on a HD3850 card, and using Wine 1.1.26 (although the same effect appears on 1.1.24 and 25 too). Windowed mode, 1280x1024 (desktop is 1600x1200)

Any suggestions would be appreciated.

---

### Post by Askar450 on 2009-07-23
I've never played EVE before so I don't know what I'm looking at, is it the overlapping in the text or the map diagram? What are you using when you load eve? just Wine /path/?

---

### Post by Dinchamion on 2009-07-23
It is supposed to look like this:

[http://img7.imageshack.us/img7/2616/20090220025034ku2.jpg](http://img7.imageshack.us/img7/2616/20090220025034ku2.jpg)
[http://i2.photobucket.com/albums/y31/SwitchbladeUK/tengoops.jpg](http://i2.photobucket.com/albums/y31/SwitchbladeUK/tengoops.jpg)
[http://s3-llnw-screenshots.wegame.com/9050277644798796/9050277644798796_l.jpg](http://s3-llnw-screenshots.wegame.com/9050277644798796/9050277644798796_l.jpg)
[http://s3-llnw-screenshots.wegame.com/5-2809119399719077/2809119399719077_l.jpg](http://s3-llnw-screenshots.wegame.com/5-2809119399719077/2809119399719077_l.jpg)

The elements (like window borders, buttons, etc) are not rendered correctly.

I'm using it with a shortcut on my desktop, the command is ```
env WINEPREFIX="/home/dinchamion/.wine" wine "C:\Program Files\CCP\EVE\eve.exe"
```

But I tried without the wineprefix, from console as well as editing the shortcut, but didn't help.

Since it is faster that way, I used winecfg to specify a virtual desktop of 1280x1024 in winecfg for EVE, and ingame it is set to "fullscreen". (I started out running it with no virtual desktop and set in "windowed" mode, but as I was messing with the settings to get rid of the problem, I found it's faster this way)

---

### Post by Askar450 on 2009-07-23
What are your specs and what are you running under?

---

### Post by poosietgp on 2009-07-23
i believe you should look at this :)
[http://www.macworld.com/article/138764/2009/02/evelinux.html](http://www.macworld.com/article/138764/2009/02/evelinux.html)

---

### Post by Dinchamion on 2009-07-23
> **Askar450 said:**
> What are your specs and what are you running under?

Intel P4 3GHz, 2GB RAM, Ubuntu 9.04 (64-bit) with default kernel (didn't have time to do a custom build, but I'm planning to), Wine 1.1.26 from repos, ATI Radeon HD3850 card (512MB) with 9.6 Catalyst fglrx driver (manually installed following [this](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually) - the automatic thing Ubuntu did wasn't working for me really, it was slow, basically locked my computer up, etc. This one works)

> **poosietgp said:**
> i believe you should look at this :)
[http://www.macworld.com/article/1387.../evelinux.html](http://www.macworld.com/article/1387.../evelinux.html)

I know they don't have a linux client any more, I tried it a while ago, but it was still faster and easier in Wine, so never really used it. :) If your suggestion was that there are some hints in the comments, I'll go through them later (I'm at work atm :(). ;)

---

### Post by Askar450 on 2009-07-23
[Dinchamion]("http://ubuntuforums.org/member.php?u=39407") do you have MSN?

---

### Post by Dinchamion on 2009-07-23
> **Askar450 said:**
> [Dinchamion]("http://ubuntuforums.org/member.php?u=39407") do you have MSN?

I do: dinchamion(at)gmail(dot)com

But I can't use it at work, only when I get home in the evening. :(

---

### Post by Askar450 on 2009-07-23
Send me an IM at [email]snake45073@live.com[/email].

---

### Post by NightMKoder on 2009-07-24
Hey look, an ATI card! Have fun with that.

Try setting offscreenrenderingmode = backbuffer. Can also try updating to the latest drivers. Other than that, I suggest complaining to ATI.

---

### Post by ArcticCloud on 2009-07-25
> **Dinchamion said:**
> Hi,

my problem with EVE is that the graphics are garbaged:

[http://www.dinchamion.net/storage/eve_garbage1.png](http://www.dinchamion.net/storage/eve_garbage1.png)
[http://www.dinchamion.net/storage/eve_garbage2.png](http://www.dinchamion.net/storage/eve_garbage2.png)
[http://www.dinchamion.net/storage/eve_garbage3.png](http://www.dinchamion.net/storage/eve_garbage3.png)

Console output:

```
dinchamion@daedalus:~$ wine "C:\Program Files\CCP\EVE\eve.exe" 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x8d0000 0 0x33fcac 4
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x338f04,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #4:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #8:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #12:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #16:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #19:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x30032 0x00000000
fixme:imm:ImmReleaseContext (0x30032, 0x13eec0): stub
dinchamion@daedalus:~$ fixme:reg:GetNativeSystemInfo (0x33b778) using GetSystemInfo()
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #23:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #20:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #26:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #24:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #30:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #27:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #33:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #31:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #37:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #34:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [0] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [1] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [2] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #41:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #38:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #45:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #42:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #46:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #50:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #48:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked, vertex shader(s) linked. 
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log     WARNING: built-in varying gl_TexCoord [5] defined in Vertex shader and not used in Fragment shader
fixme:d3d_shader:print_glsl_info_log      
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #54:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x30032
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
```I'm running Ubuntu 9.04 (64-bit) with 9.6 ATI drivers (installed manually, the one from the repos is unusable for me) on a HD3850 card, and using Wine 1.1.26 (although the same effect appears on 1.1.24 and 25 too). Windowed mode, 1280x1024 (desktop is 1600x1200)

Any suggestions would be appreciated.

I have tried three versions of wine starting with 1.1.26 and I have found that version 1.1.24 is the most current and stable development copy.  I have been running version 24 for several days now with zero crashes and pretty good graphics.

---

### Post by Dinchamion on 2009-08-04
I didn't have time to test it recently, but on the weekend I had to do a complete wipe and fresh install of everything, and now it works like a charm. I updated to 9.7 drivers, but otherwise same specs. Everything is fine.

---

