---
title: "Is there a way to force wine to grab the mouse?"
date: 2009-04-13
forum: Wine
---

### Post by Vunutus on 2009-04-13
I've recently installed WarCraft 3 and got it working with Wine, but it has a problem. As with most RTS games, it scrolls the view when you move your mouse to the border of the screen. Under Wine, however, this is an issue. Whether in fullscreen mode or in windowed virtual desktop mode, the edge-of-screen behavior is horrible. In fullscreen, when the mouse hits the edge of the screen, it shows both the system mouse and the Warcraft mouse, as if it can't decide which I want to use. Side scrolling works some of the time here and cuts out other times, overall very frustrating. In virtual desktop mode (which I prefer since I can run it at at a normal aspect ratio since WC3 doesn't support widescreen), it just lets the mouse flow in and out of the window which makes it even harder to use than the full screen option.

What I would like is something to lock my mouse pointer inside the virtual desktop window, much in the same way you can lock your mouse inside of VirtualBox when you are running a guest OS. 

Also, before anyone mentions it, the "allow directX to keep the mouse within program borders" option doesn't work (at least in this case).

---

### Post by NightMKoder on 2009-04-13
I believe there is a registry option called MouseWarpOverride, which you may want to look into.

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

```

wine regedit

```

Browse to:
HKEY_CURRENT_USER\Software\Wine\DirectInput

(Create a new key called DirectInput if it doesn't exist)

Create a new string value, named "MouseWarpOverride" and set the value to "force".

---

### Post by Vunutus on 2009-04-13
> **NightMKoder said:**
> I believe there is a registry option called MouseWarpOverride, which you may want to look into.

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

```

wine regedit

```

Browse to:
HKEY_CURRENT_USER\Software\Wine\DirectInput

(Create a new key called DirectInput if it doesn't exist)

Create a new string value, named "MouseWarpOverride" and set the value to "force".

Tried it, didn't seem to change anything in either fullscreen or virtual desktop unfortunately.

---

### Post by asdfoo on 2009-04-13
There might be an unofficial patch to make it work, but if I'm not mistaken, currently the real reason this has been missing for the past several years is missing functionality in Xorg which is being worked on for the next version of Xorg which then Wine can take advantage of to grab the mouse pointer properly and also to do relative mouse movements.

---

### Post by NightMKoder on 2009-04-13
Hmm, incidentally I think there may be a way to fix the issue on the top of the screen for you (to an extent of the other sides). In winecfg->Graphics->Uncheck Allow the Window Manager to decorate the windows.

But asdfoo is right - wine is missing DXGrab functionality, and needs a new extension to the X server. If warcraft has an option to run in windowed mode (instead of virtual desktop), try doing that.

---

### Post by Vunutus on 2009-04-14
> **NightMKoder said:**
> Hmm, incidentally I think there may be a way to fix the issue on the top of the screen for you (to an extent of the other sides). In winecfg->Graphics->Uncheck Allow the Window Manager to decorate the windows.

But asdfoo is right - wine is missing DXGrab functionality, and needs a new extension to the X server. If warcraft has an option to run in windowed mode (instead of virtual desktop), try doing that.

Windowed mode was my initial idea, but for some reason it doesn't work for me so I resorted to attempting to lock the mouse.

Maybe somebody here can spot what I'm doing wrong on the windowed thing so as not to make another topic.

The official documentation says that I need to add "-window" to the shortcut target line to launch windowed mode. Obviously that was written with Windows in mind.

I changed my WC3 launcher to this:

```
env WINEPREFIX="/home/danny/.wine" wine "C:\Warcraft III\Frozen Throne.exe -window"
```

I assumed that would accomplish the same thing, but apparently not. Is there another way I'm supposed to pass parameters to programs with Wine?

---

### Post by NightMKoder on 2009-04-14
Just pass them as you would normally, except with the wine stuff in front. Wine itself doesn't have any arguments (for all intents and purposes).

So do:
```

env WINEPREFIX="/home/danny/.wine" wine "C:\Warcraft III\Frozen Throne.exe" -window

```
(outside the quotes)

---

### Post by Vunutus on 2009-04-14
> **NightMKoder said:**
> Just pass them as you would normally, except with the wine stuff in front. Wine itself doesn't have any arguments (for all intents and purposes).

So do:
```

env WINEPREFIX="/home/danny/.wine" wine "C:\Warcraft III\Frozen Throne.exe" -window

```
(outside the quotes)

For some reason, that doesn't work when I set it to the launcher target, but if I just paste it in a terminal it works fine. 
 
Unfortunately, that's irrelevant now because windowed mode doesn't fix the original problem either.

I guess I'm just stuck with booting into windows until Xorg is updated?

---

### Post by NightMKoder on 2009-04-14
As a last resort, consider checking "Allow directx apps to stop the mouse leaving their window" in winecfg graphics section. Also it seems to be suggested that you use the -opengl option (for fps). And lastly, if you do run windowed mode, there might be an option in warcraft that you need to enable to lock the mouse.

That's all I can tell you (never tried WC3 on wine). AppDB doesn't seem to mention this problem often (or ever, really, for that matter). 
[http://appdb.winehq.org/appview.php?versionId=1177](http://appdb.winehq.org/appview.php?versionId=1177)

EDIT: Oh, and almost forgot, try disabling your desktop effects (if they are running).

---

### Post by Vunutus on 2009-04-14
It seems that the scrolling problem is indeed related to the compiz cube.

I searched around a bit and found a fantastic guide for WC3 scrolling issues in Wine (which I somehow didn't find before I made this topic). Unfortunately, due to WC3 not supporting widescreen resolutions, I must still run in a somewhat distorted fullscreen view. At least it's playable this way, however!

[http://ubuntuforums.org/showthread.php?t=906957](http://ubuntuforums.org/showthread.php?t=906957)

---

