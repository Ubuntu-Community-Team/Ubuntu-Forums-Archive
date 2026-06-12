---
title: "Fallout New Vegas"
date: 2010-10-20
forum: Wine
---

### Post by MikeSpearman on 2010-10-20
Can anyone get New Vegas to work with Ubuntu?
I got it all to download and it should work but when I try to use the application it just loads for a while and then stops.

---

### Post by Jebtrix on 2010-10-20
Should work is very optimistic of you. What version of Wine you trying?

---

### Post by MikeSpearman on 2010-10-21
1.3.5 i believe. do you think i should use the stable version?

---

### Post by OgreProgrammer on 2010-10-21
Do you mean that you succeeded in the install process, and it fails when you try to start the game, or you cannot install it?

---

### Post by MikeSpearman on 2010-10-21
i installed it and when i click on the shortcut it downloaded to my desktop, the mouse does its loading thing for like 30 seconds and then nothing happens.

---

### Post by OgreProgrammer on 2010-10-25
Ok, so what you need to do is get some error messages. As anyone who has used linux knows, the terminal is the best way to do that. 

edit the shortcut and get the wine load string from that, and paste it into terminal. This should get some errors showing. I dont know if I can help with that, but I will try.

---

### Post by robeast on 2010-10-25
There are bugs popping up on the Wine bug tracker: [http://bugs.winehq.org/show_bug.cgi?id=24831](http://bugs.winehq.org/show_bug.cgi?id=24831)

That one has a patch you can apply to the Wine source before you build that might help. I'm trying it now.

---

### Post by robeast on 2010-10-28
For anyone searching around, they have added a fix to be released in wine 1.3.6 that will fix the error loading gamebryo renderer. 

If you are using Steam you need to make a backup of GameOverlayRenderer.dll in your Steam directory and remove it after launching steam and before launching the game, or else it will immediately crash because the Steam in-game community stuff doesn't work. 

I'm only able to play the game reliably if it is windowed at the lowest resolution possible (800x500) with the lowest possible graphics settings. I even went into the Fallout.ini and Falloutprefs.ini and turned off a bunch of stuff that the lowest settings from the launcher won't disable. If I try higher settings the game will either crash on loading the game world, or if it gets past that point, when I look at the pip boy, go to the game menu, or load a new area of the world but entering or exiting a building. 

I'm using the latest Nvidia drivers with Ubuntu 10.04. At the moment I'm using a patched compile of wine 1.3.5 that works around the gamebryo renderer error.

GeForce GTS 160M/PCI/SSE2
Core2 Duo @ 2.8GHz
4GB RAM
Kernel: 2.6.32-25-generic

---

### Post by MikeSpearman on 2010-11-07
well i got this
```
mike@mike-laptop:~$ '/home/mike/.wine/dosdevices/c:/Program Files/Bethesda Softworks/Fallout New Vegas/FalloutNV.exe'
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2b4,0x00000000), stub!
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Fallout New Vegas\\FalloutNVLauncher.exe") not found
mike@mike-laptop:~$ err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Fallout New Vegas\\FalloutNVLauncher.exe" failed, status c0000135

```

---

### Post by Yeeha on 2010-11-27
i got game to work using wine 1.3.8 and winetricks vcrun2008 cc580 d3dx9 but game crashes after 10 minutes or so with:
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x212a7790 stub tag
fixme:gstreamer:event_sink 0x212a7828 stub tag
fixme:gstreamer:event_sink 0x212a7600 stub tag
fixme:gstreamer:got_data_sink Triggering 0x212aa718 0xfcb0
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:no_more_pads Done

Any ideas how to fix this?

---

### Post by denisvv on 2010-11-27
> **Yeeha said:**
> i got game to work using wine 1.3.8 and winetricks vcrun2008 cc580 d3dx9 but game crashes after 10 minutes or so with:
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x212a7790 stub tag
fixme:gstreamer:event_sink 0x212a7828 stub tag
fixme:gstreamer:event_sink 0x212a7600 stub tag
fixme:gstreamer:got_data_sink Triggering 0x212aa718 0xfcb0
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:no_more_pads Done

Any ideas how to fix this?

run winecfg. Under libraries, find winegstreamer in the "new override for library" dropdown, add it, click edit, select disable.

---

### Post by Yeeha on 2010-11-28
Thanks that worked. Sadly there was a tradeoff, it seems gstreamer is needed for Directsound Hardware emulation so i had to set it to full hardware acceleration but with that sound is stuttering but unleast i can play.

---

### Post by Yeeha on 2010-12-03
Finally, no sound problems or crashes. I set sound driver from alsa to jack. When trying to launch game from launcher, game will have no sound but using falloutNV.exe sounds work perfectly. Thats odd because alsa is best supported driver in wine? Using alsa with hardware acceleration full has never worked for me without stuttering.

---

### Post by SHOTANG on 2010-12-07
I seem to have the same problem as the OP, (to him/her) how did you get the alsa driver to "jack"? I have a p7811-fx with 10.04 Lucid. It supposedly has a conexant HDA card. I have tried numerous ways to get the alsa drivers installed but my sound device has never showed up as anything but "internal audio". I hope I'm not snafuing by posting in someone else's thread but we seem to have the same issue (background sounds work but not gameplay). Thanks!

---

### Post by Yeeha on 2010-12-08
You can select what wine uses for audio from winecfg. You need to install jack2d package for it to work. But jack is sound server like pulseaudio so underneath it still uses alsa so if alsa cant handle your soundcard then using jack wont help i fear.

---

### Post by SHOTANG on 2010-12-09
You would think that linuxant would cover my sound card but I've yet to get through the .deb installer without errors and doing the alsa project command style install (get, unpack, cd, clean, make, install...for driver,lib, utils, and then firmware) always gives me trouble on either the utils or lib part. I'll play around with it more when my attention span accommodates. It's more of a novelty factor for me to play games on linux but I've got a smallish SSD so it would be nice to switch to a less bloated primary OS like Ubuntu.

Thanks for the sugestions.

---

### Post by alaukikyo on 2010-12-09
inthe newest version of playonlinux there is a experimental script for instalations

---

### Post by SHOTANG on 2010-12-10
In POL, there's an installer script for Linux packages or wine/windows stuff? Either way, I'll check it out, thanks alaukikyo

---

### Post by monteagus on 2011-03-30
i have a similar problem  i installed it with playonlinux from a mounted iso
and when i clik to launch the game nothing happens .So i copy the launch exe file to my desktop and launched... all i got is a fats windows that opens with a blue background and goes out fast.
so i tried pasting that on the terminal and all i got is this
i dont understand a this...

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library steam_api.dll (which is needed by L"Z:\\home\\agustin\\Escritorio\\Enlace hacia FalloutNVLauncher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\agustin\\Escritorio\\Enlace hacia FalloutNVLauncher.exe" failed, status c0000135

any clues? :confused:

---

### Post by seicean on 2011-08-12
Hello

I just installed Fallout New Vegas in WINE 1.2.2 and i don't get sound... doe anyone have the same issue?

Fallout New Vegas 1.0 Update 7 running on Core 2 Duo 2.0GHz, 3GB ram, nvidia 9300M and intel HD soundcard

thanks

---

