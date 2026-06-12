---
title: "Military History Commander - Europe at War Gold (workshop thread)"
date: 2009-03-23
forum: Wine
---

### Post by anlag on 2009-03-23
Slitherine's enhanced version of their "Commander - Europe at War" from 2007. Gold was initially released last Friday, on March 20th, in version 1.12 which is supposed to be compatible with the last version of the original CEAW game (1.07 I think.)

I pre-ordered the game, got it today and am currently trying to get it to work. Have had some success but not done yet, and figured I'd post up a bit here so that if anyone else is doing the same we might work together. I've also submitted the game on Wine's AppDB, but additional exposure can't hurt.

So, my progress, using wine 1.1.17 under a well-updated Ubuntu 8.10 Intrepid:

1. **Installation**. Works fine, once you start it through the Autorun.exe file on the disc. Trying to start with the ceaw_gold_setup.exe file didn't work for me.


2. **Game-starting scripts.** MHCEAW Gold doesn't have a single .exe in its directory to just run to start the game. The installation has however placed two links on the desktop: one .lnk, and one .desktop. Ignoring the former, simply double-clicking on the latter initiates the game. However, as I prefer to run things from the terminal (especially when they don't work - so I can get the error messages) I take the key line from the .desktop file and make my own shell script:

```
#!/bin/sh

wine "C:\\Program Files\\Military History Commander - Europe at War GOLD\\jre\\bin\\java.exe" -Xss20m -Xms400m -Xmx800m -classpath . CEAW 14100

exit 0
```

In order to run the script needs to be chmodded (to 755 for instance) and also placed in the game installation directory, something like: 

*~/.wine/drive_c/Program Files/Military History Commander - Europe at War GOLD*


3. **Starting the game.** Regardless of whether I use the desktop shortcut, or the shell script, the outcome is the same. After the screen messing about and changing resolution for a few seconds, the intro film plays in full screen. After it finishes, or is killed with Esc, the screen reverts to showing my Ubuntu desktop. However, the sound of the game is playing and h/top shows it's still taking considerable resources. It seems like the game is indeed running, and waiting at the main menu, only the graphics don't work so nothing is displayed on the screen.

It's worth noting again that MHCEAW Gold runs in java, so I'm guessing the problem is java connected. This might also explain why it doesn't crash outright, like you could expect when the application is unable to display... well, anything. One thing I tried in this regard was to remove the specific path to java.exe in the shell script - in order to try running the game with my 'Windows' installation's own java rather than the one bundled with the game, but it then fails to start complaining of some missing modules. Perhaps one needs to give a path to the game as additional input to java? I wouldn't know how.

Monitoring the terminal output, there are a lot of 'fixme' messages, but what stands out is the (once repeated) 'err' close to the very end, which appears just after the intro ends and the "menu music" starts:

*err:pidl:_ILCreateGuidFromStrW L"DelegateFolders" is not a GUID*


That's as far as I've got in my first night on the job. If anyone else has bought this game and is trying to get it to work - successfully or not - please make a reply and give your experiences. It would be great to get this game running.

Also, of course, regardless of whether you have the game or not, if anyone can tell me what the above error message means and how one might work around it that would be most appreciated.

Enclosing the full terminal output below, for reference. Cheers!




```
anlag@casper:~/.wine/drive_c/Program Files/Military History Commander - Europe at War GOLD$ ./ceaw 
fixme:win:EnumDisplayDevicesW ((null),0,0x31b93c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x31b93c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32c830,0x00000000), stub!
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:imm:ImmGetOpenStatus (0x49af1670): semi-stub
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCOMPOSITIONWINDOW
AudioPlayer.playAudioStream audio format: PCM_SIGNED 22050.0 Hz, 16 bit, mono, 2 bytes/frame, little-endian
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x49b59750,0x49b59670): stub
fixme:imm:ImmGetOpenStatus (0x49bdd180): semi-stub
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCOMPOSITIONWINDOW
AudioPlayer.playAudioStream audio format: PCM_SIGNED 22050.0 Hz, 16 bit, mono, 2 bytes/frame, little-endian
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x211a20,0x211f78): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x136680,0x136ea0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1366a0,0x136ea0): stub
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:win:EnumDisplayDevicesW ((null),0,0x45a2a83c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x45a2a83c,0x00000000), stub!
^[fixme:win:EnumDisplayDevicesW ((null),0,0x45a2a83c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x45a2a83c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x45a2a83c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x45a2a83c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x45a2a83c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x45a2a83c,0x00000000), stub!
Display Setting Count = 40

fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x45aa1288,0x45aa1210): stub
Checking C:\windows\profiles\anlag\My Documents//CEAW/data/scenario/1943.data
  ...found. loadable?
  ...checks out. skipping.
Checking C:\windows\profiles\anlag\My Documents//CEAW/data/scenario/1942.data
  ...found. loadable?
  ...checks out. skipping.
Checking C:\windows\profiles\anlag\My Documents//CEAW/data/scenario/1941.data
  ...found. loadable?
  ...checks out. skipping.
Checking C:\windows\profiles\anlag\My Documents//CEAW/data/scenario/1940.data
  ...found. loadable?
  ...checks out. skipping.
Checking C:\windows\profiles\anlag\My Documents//CEAW/data/scenario/1944.data
  ...found. loadable?
  ...checks out. skipping.
Checking C:\windows\profiles\anlag\My Documents//CEAW/data/scenario/1939.data
  ...found. loadable?
  ...checks out. skipping.
image map25_nogrid<>C:\Program Files\Military History Commander - Europe at War GOLD/image/background/
trying image data C:\Program Files\Military History Commander - Europe at War GOLD/image/background/map25_nogrid.dat
able to load image
Tile size: (256, 256)
Tile count: (9, 5)
image map50_nogrid<>C:\Program Files\Military History Commander - Europe at War GOLD/image/background/
trying image data C:\Program Files\Military History Commander - Europe at War GOLD/image/background/map50_nogrid.dat
able to load image
Tile size: (256, 256)
Tile count: (18, 10)
image map100_nogrid<>C:\Program Files\Military History Commander - Europe at War GOLD/image/background/
trying image data C:\Program Files\Military History Commander - Europe at War GOLD/image/background/map100_nogrid.dat
able to load image
Tile size: (256, 256)
Tile count: (36, 19)
**err:pidl:_ILCreateGuidFromStrW L"DelegateFolders" is not a GUID**
fixme:shell:DllCanUnloadNow stub
**err:pidl:_ILCreateGuidFromStrW L"DelegateFolders" is not a GUID**
fixme:shell:DllCanUnloadNow stub
^C

```

---

### Post by cogadh on 2009-03-23
If it is a Java game, could it be possible to just run it natively and remove Wine from the equation? I couldn't begin to tell you how to do that, but since Java is totally OS agnostic, it just seems logical that you could somehow do it.

---

### Post by anlag on 2009-03-23
That would of course be exceptionally beautiful, but I'm not sure it's possible. There are some files in the installation tree that look distrinctly Windows-like. Still, perhaps they could be worked around, and they are not many. 

Just as the simplest possible experiment I took the flags and arguments given to the bundled java by the startup script and tried to run it natively:

```
anlag@casper:~/.wine/drive_c/Program Files/Military History Commander - Europe at War GOLD$ java -Xss20m -Xms400m -Xmx800m -classpath . CEAW 14100
ERROR You have not installed the DLL named 'ICE_JNIRegistry.DLL'.
	no ICE_JNIRegistry in java.library.path
Exception in thread "main" java.lang.UnsatisfiedLinkError: com.ice.jni.registry.RegistryKey.openSubKey(Ljava/lang/String;I)Lcom/ice/jni/registry/RegistryKey;
	at com.ice.jni.registry.RegistryKey.openSubKey(Native Method)
	at com.ice.jni.registry.Registry.openSubkey(Registry.java:217)
	at CEAW.checkRegistry(CEAW.java:81)
	at CEAW.main(CEAW.java:189)

```

That .dll is obviously one of said Windows-specific files.

Also tried the wine-installed java in the same manner:

*anlag@casper:~/.wine/drive_c/Program Files/Military History Commander - Europe at War GOLD$ wine java.exe -Xss20m -Xms400m -Xmx800m -classpath . CEAW 14100*


Worked better now than before (was probably in the wrong directory) but still only gets as far as when running with the bundled, and with almost the same terminal output. Still, this should open up for using an upgraded java, just in case that might help.

---

### Post by anlag on 2009-03-24
The Wine AppDB page is now up as well:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16090](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16090)

Any suggestions on the significance of the pidl error message greatly appreciated!

---

### Post by anlag on 2009-03-31
And, sorted!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16090](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16090)


Wine needed to be set to run in a virtual desktop, and moreover one with sufficiently low resolution. 1024x768 works fine, so does 1280x1024 although the window reverts back to the former size anyway. I also upgraded my wine version today, to 1.1.18. This may have played a part.

Anyhow, game runs great now, no loss in performance whatsoever. Everything seems to work fine. Well, except fullscreen mode I suppose.

---

