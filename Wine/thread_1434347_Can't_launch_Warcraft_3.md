---
title: "Can't launch Warcraft 3"
date: 2010-03-20
forum: Wine
---

### Post by TheWatcher000 on 2010-03-20
Warcraft 3 is one of the few games I actually bought. I successfully installed the game through Wine, manually applied the newest patch (1.24e I think) so I can launch it without  cd in the drive (Its looooooooooud).

Sadly though, when I try to start it up through the terminal with -opengl, it doesn't really do a thing other than almost freezing up my laptop completely, the screen goes bright and almost completely white (there are a few weird lines).

I found a thread ([this thread]("http://ubuntuforums.org/showthread.php?p=5269543#post5269543")) with a suggestion about editing registry, but at me there was no Blizzard Entertainment in the Software group.

I uploaded the picture that shows what I see after trying to launch the game.

This is what was in the terminal:

```
root@niki-laptop:/home/niki# cd /home/niki/.wine/dosdevices/c:/Program\ Files/Warcraft\ III
root@niki-laptop:/home/niki/.wine/dosdevices/c:/Program Files/Warcraft III# wine "war3.exe" -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f384,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f684,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @75! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @70! (XRandR)
fixme:quartz:AVISplitter_InitializeStreams stream 1: frames found: 2172570, frames meant to be found: 2173350
fixme:win:EnumDisplayDevicesW ((null),0,0x33dfd8,0x00000000), stub!
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
err:wave:wodOpen Error open: Kimeneti/bemeneti hiba
fixme:dsound:mmErr Unknown MMSYS error 3
err:quartz:DSoundRender_create Cannot create Direct Sound object (80004005)
fixme:ole:CoCreateInstance no instance created for interface {56a86895-0ad4-11ce-b03a-0020af0ba770} of class {79376820-07d0-11cf-a24d-0020afd79767}, hres is 0x80004005
err:quartz:FilterGraph2_Render Unable to create filter (80004005), trying next one
err:ole:CoGetClassObject class {e30629d1-27e5-11ce-875d-00608cb78066} not registered
err:ole:CoGetClassObject no class object {e30629d1-27e5-11ce-875d-00608cb78066} could be created for context 0x1
err:quartz:FilterGraph2_Render Unable to create filter (80040154), trying next one
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
mmap() failed: Nem foglalható memória
err:wave:wodOpen Error open: Kimeneti/bemeneti hiba
fixme:dsound:mmErr Unknown MMSYS error 3
err:quartz:DSoundRender_create Cannot create Direct Sound object (80004005)
fixme:ole:CoCreateInstance no instance created for interface {56a86895-0ad4-11ce-b03a-0020af0ba770} of class {79376820-07d0-11cf-a24d-0020afd79767}, hres is 0x80004005
err:quartz:FilterGraph2_Render Unable to create filter (80004005), trying next one
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
err:ntdll:RtlpWaitForCriticalSection section 0x1451fc "videorenderer.c: VideoRendererImpl.csFilter" wait timed out in thread 0009, blocked by 001c, retrying (60 sec)
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
root@niki-laptop:/home/niki/.wine/dosdevices/c:/Program Files/Warcraft III# 


```It's in Hungarian, I think you still understand what the lines mean (if not, just tell me and I'll give you a translation (the best I can do)).

I would be grateful to anyone who can help, thanks in advance!


EDIT: wooooooooow, solved! I found another guide, it said I should rename the Movies folder in the warcraft 3 directory, the screen is messed up because it tries to play the intro video.
Wurks now !! hooray..

However, I still can't find that registry thing, I would be happy to increase performance...

---

### Post by _h_ on 2010-03-20
Just so you know your attachment image is severely distorted. :(

---

### Post by TheWatcher000 on 2010-03-20
Well that is what it used to look like : P
But now I can play it, I played a dota, but I had 10-20 fps, which actually cost us the game... bad ****.
So I need to speed it up somehow, as far as I can tell I have an 512 mb videocard, I should have no problem (my pc used to run it three times as good with less resources).

---

### Post by _h_ on 2010-03-20
What brand of card do you have? Updated drivers?

Also have you tried without the -opengl command, and use the Wine direct3d default?

---

### Post by TheWatcher000 on 2010-03-20
I get Fatal Error on launching without the -opengl part.

And the Direct3d appears to be allowed (Hardware (?))

I have an Intel card, Mobile 945GM/GMS, 943/940GMMML Express Integrated Graphics Controller.

The problem is I couldn't find drivers anywhere, not to mention I have no idea how to update them on ubuntu...
any help greatly appreciated

---

### Post by _h_ on 2010-03-20
> **TheWatcher000 said:**
> I have an Intel card, Mobile 945GM/GMS, 943/940GMMML Express Integrated Graphics Controller.

Sorry to say this, but you aren't going to get much performance out of Intel graphics cards on linux, sadly. :( (I've learned this too, having an integrated Intel GM965 graphics card.)

Their D3D and OpenGL capabilities are just...well...garbage on Linux.

I think that 15-20 FPS is pretty much the most you are going to get on Warcraft. :(

---

### Post by TheWatcher000 on 2010-03-20
Well there are a few suggestions around this forum to improve speed/fps on warcraft 3, plus I way playing on max detail... I really want to try everything possible

---

### Post by freeware2dl on 2010-03-20
i have the same trouble too

---

### Post by excelvou on 2010-10-15
I have the same trouble too but I think it's because the motherboard of my computer, hard to find the driver for the graphic card

---

### Post by Soulcage on 2010-10-15
I would just like to say you're not supposed to run wine as root.

---

