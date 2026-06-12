---
title: "wine and Frets on fire"
date: 2009-06-05
forum: Wine
---

### Post by X1R1 on 2009-06-05
ok here is my question, hope you guys can help me out.

I have Fofix final installed on my pc, no problems at all with that. The problem is that I have 2 operating systems in this machine, Xp64 bit pro AND Ubuntu Jaunty 9.04 64 bit. I have played FoF for a long time now and I would like to have fof in both operating systems with same settings and scores and all. So I figured that WINE would work. I just open the FretsOnFire.exe with wine and work done. WRONG as soon as it opens it stays on the "Loading" screen and hangs. it just stays there....

How can I make this work? what am I doing wrong?

thank you all for the help!

PS. Of course I know there is a linux version for FoF, its only that I dont want to have 2 different installations for the same game. And this way the scores would be synchronized and wont matter if I play on Xp or ubuntu :D

Wine info:
Version 1.0.1
all settings default, no personal dlls
sound alsa

Terminal output
x1r1@DESKTOP:/media/XP64/Program Files (x86)/Frets on Fire$ wine FretsOnFire.exe

fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f16c,0x00000000), stub!
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList

---

### Post by asdfoo on 2009-06-05
Last I looked frets on fire does something weird with OpenGL that Wine doesn't like causing it to crash.

Just use the native version. ps. "Wine"

---

### Post by X1R1 on 2009-06-05
> **asdfoo said:**
> Just use the native version. ps. "Wine"

what do you mean? is that a file or something that I need to load on to wine? please explain a little more....

thanks for the help!

---

### Post by pluckypigeon on 2009-06-05
> **X1R1 said:**
> what do you mean? is that a file or something that I need to load on to wine? please explain a little more....

thanks for the help!

Share the settings using symlinks from xp to home folder and install fretsonfire from synaptic

---

### Post by X1R1 on 2009-06-05
> **pluckypigeon said:**
> Share the settings using symlinks from xp to home folder and install fretsonfire from synaptic

my frets on fire installation is on ```
/media/XP64/Program Files (x86)/Frets on Fire
```

after I install fretsonfire via synaptic. what will the code be?

---

### Post by pluckypigeon on 2009-06-05
> **X1R1 said:**
> my frets on fire installation is on ```
/media/XP64/Program Files (x86)/Frets on Fire
```

after I install fretsonfire via synaptic. what will the code be?

I'm not sure exactly..

You could try looking for fretsonfire.ini in your xp partition and symlink it to ~/.fretsonfire/fretsonfire.ini

either by dragging it while holding down shift and ctrl or

```
ln -s /media/path/_to/_xp_/fretsonfire.ini ~/.fretsonfire/fretsonfire.ini
```

let me know how you get on

---

### Post by X1R1 on 2009-06-05
> **pluckypigeon said:**
> I'm not sure exactly..

You could try looking for fretsonfire.ini in your xp partition and symlink it to ~/.fretsonfire/fretsonfire.ini

either by dragging it while holding down shift and ctrl or

```
ln -s /media/path/_to/_xp_/fretsonfire.ini ~/.fretsonfire/fretsonfire.ini
```

let me know how you get on

important fact. the version of Frets on Fire I have installed is FoFix final, so maybe I should try and install that...then symlink the fretsonfire.ini AND all other folders (songs, themes, etc) in order to have same settings scores and themes on both systems.

I made a mistake, there no need to symlink the "songs" folder because in-game options you can choose the path. So it would be just the themes folder and others that I want to keep sync.

---

