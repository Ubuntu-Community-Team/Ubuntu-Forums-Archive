---
title: "The Iconoclasts"
date: 2011-04-27
forum: Wine
---

### Post by barkerson on 2011-04-27
So, I picked up a game called "[Ivory Springs]("http://www.konjak.org/index.php?folder=9&file=27")". Then I found out that he had abandoned the project and a while after that started to make a remake of it, called "[The Iconoclasts]("http://www.youtube.com/watch?v=QgSwUHjwyKY")"(not my video) *[download here]("http://www.konjak.org/iconoclasts.zip")*, it's only a demo but I want to play it. Does anyone know how to open this, in wine it says it's an unexpected error. Please help.

---

### Post by cogadh on 2011-04-27
We need more details, like the full Wine error output, not just a paraphrasing of the error message. Wine version and perhaps hardware specs would help as well.

---

### Post by barkerson on 2011-04-28
> **cogadh said:**
> We need more details, like the full Wine error output, not just a paraphrasing of the error message. Wine version and perhaps hardware specs would help as well.
wine 1.3.18
error message:
An unexpected error occurred and the application was terminated. We
apologise for the inconvenience.

Please report this problem to the application developer.

---

### Post by cogadh on 2011-04-28
That's not the Wine error output, that's just the gui element that pops up when an error occurs. You need to run the application from the terminal and post the detailed error messages that are output to the terminal.

---

### Post by barkerson on 2011-04-28
> **cogadh said:**
> That's not the Wine error output, that's just the gui element that pops up when an error occurs. You need to run the application from the terminal and post the detailed error messages that are output to the terminal.
sorry, don't know how to do it, tell me

---

### Post by orzechowskid on 2011-04-28
> **barkerson said:**
> sorry, don't know how to do it, tell me

Applications > Accessories > Terminal

then browse to the directory containing the program you're trying to run.  For example, if it's in your Downloads folder, type

cd Downloads/

at the prompt.  If it lives on your desktop, type

cd Desktop/

instead.  If you downloaded the program to your home directory, you don't have to do anything; that's where you start off when you open a new terminal session.

Once you're in the right directory, type

wine program.exe

at the prompt, where "program.exe" is the name of the program you're trying to run.  WINE will print a lot of stuff out while it tries to run your program; that's what we need to troubleshoot your problem.

---

### Post by barkerson on 2011-04-28
> **orzechowskid said:**
> Applications > Accessories > Terminal

then browse to the directory containing the program you're trying to run.  For example, if it's in your Downloads folder, type

cd Downloads/

at the prompt.  If it lives on your desktop, type

cd Desktop/

instead.  If you downloaded the program to your home directory, you don't have to do anything; that's where you start off when you open a new terminal session.

Once you're in the right directory, type

wine program.exe

at the prompt, where "program.exe" is the name of the program you're trying to run.  WINE will print a lot of stuff out while it tries to run your program; that's what we need to troubleshoot your problem.
```
emil@emil-desktop:~/Skrivbord/Iconoclasts$ wine Iconoclasts.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32d694,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d63c,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3dx:ID3DXLineImpl_SetAntialias (0x1eda10)->(1): stub
fixme:d3dx:D3DXCreateEffectEx (0x13d810, 0x107543c, 1112, (nil), (nil), (nil), 0, (nil), 0x9294850, 0x32dab8): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 2 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000003
fixme:d3dx:skip_dword_unknown     0x00000004
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x4dad001
```
I have no idea what this mean

---

### Post by cogadh on 2011-04-28
Looks like it is a known bug in Wine, though it was very recently reported:
[http://bugs.winehq.org/show_bug.cgi?id=26598](http://bugs.winehq.org/show_bug.cgi?id=26598)

According to that, the game is looking for one of the d3dx9_##.dll files that are part of DirectX (specifically the d3dx9_36.dll file). If you have a Windows installation handy, you can just copy that file from its system32 directory and place in the system32 of Wine's "fake Windows" directory (found in /home/<username>/.wine/drive_c/windows), or, IIRC, you can use [winetricks]("http://wiki.winehq.org/winetricks") to take care of it for you.

---

### Post by barkerson on 2011-04-28
downdoading dll now...

EDIT: YES it works! Thank you all on ubuntu forums!!! especially you cogadh and orzechowskid!

EDIT: Now I just need the sound.

---

### Post by barkerson on 2011-04-29
Now I want to get sound, it's dead silent!:sad:

---

### Post by cogadh on 2011-04-29
Do you have sound working in your system outside of Wine? What sound settings are you using in Wine?

---

### Post by barkerson on 2011-04-29
> **cogadh said:**
> Do you have sound working in your system outside of Wine? What sound settings are you using in Wine?
Every sound work outside of wine, in ivory springs i get sound-effects but no music.
I don't have anything checked in the sound-settings except ALSA-plugin.

---

### Post by cogadh on 2011-04-29
Try setting the audio driver in Wine to OSS, then run the game like this:
```
cd /path/to/game
padsp wine game.exe
```
Obviously, replace that path and .exe name with the correct information.

---

### Post by barkerson on 2011-04-29
> **cogadh said:**
> Try setting the audio driver in Wine to OSS, then run the game like this:
```
cd /path/to/game
padsp wine game.exe
```Obviously, replace that path and .exe name with the correct information.
sorry it didn't work but here is the terminal text:
```
emil@emil-desktop:~/Skrivbord/Iconoclasts$ padsp wine Iconoclasts.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32d694,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d63c,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
err:ole:CoGetClassObject class {b802058a-464a-42db-bc10-b650d6f2586a} not registered
err:ole:CoGetClassObject no class object {b802058a-464a-42db-bc10-b650d6f2586a} could be created for context 0x1
```

---

### Post by barkerson on 2011-05-04
do you know anything with this error? i shure don't, please help if you can.

---

### Post by barkerson on 2011-05-14
Come on, does anyone know what the error is? I need help!

---

### Post by barkerson on 2011-05-18
Pleeeeeeeeeease can i have help!!!

*cries loudly*

---

