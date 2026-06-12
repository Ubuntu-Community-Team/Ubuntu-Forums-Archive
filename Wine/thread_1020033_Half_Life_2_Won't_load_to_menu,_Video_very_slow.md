---
title: "Half Life 2: Won't load to menu, Video very slow"
date: 2008-12-23
forum: Wine
---

### Post by Velleos on 2008-12-23
I'm having trouble with steam and, most importantly, steam games.  I was unable to get steam to work at all at first with Wine.  After a few hours of tweaking, Steam is working, but still buggy and slow, with scrollbars that constantly move, and sometimes I have to move the mouse away from what I'm trying to click in order to highlight it.  But, it DOES work, and I can deal with it.  

I was able to download a copy of Half Life 2: Deathmatch successfully, and launch it;however, it loads EXTREMELY slowly, with very choppy sound and choppy video.  After the Valve video at the beginning, it fades to a black screen that never turns into a game menu.  At least, it doesn't go to the menu in the 2-4 minutes I waited.


I'm using a Dell Dimension 4400 with 1.6 ghz cpu, 768 MB RAM,Nvidia GE Force 5500 video card,Ubuntu Hardy Heron, Wine 1.1.10


I came here because:

AppDB wasn't loading the pages I needed.

I haven't seen this topic answered in any other forum posts.


What I've done to try and fix the problem:

Read several how-tos.

Using restricted drivers boots back in low graphics mode, and the only way
to get my resolution back is to switch back.  Also, the restricted drivers didn't improve program function.

I've uninstalled and reinstalled Wine once already, and am reasonably sure it's up-to-date.  As well, I've tried using Crossover Games Trial, to the same effect as Wine.

I don't believe I've run Wine as sudo, but I may have executed a command involving Wine with sudo in terminal, but only if a guide said to.

Tried messing with the Sound configuration, and changing the compatibility for steam to XP, but I'm not sure if I even did it right.

Tried using Winetricks, but was unable to do anything at all with it.

Installed DirectX 9

I have spent several hours googling and surfing forums to try and fix this problem.

I also used a couple of commands in the terminal that I found on the internet.  Before I used these, steam was worse.

glxinfo | grep -i direct
sudo chmod a+rw /dev/nvidia*



Any help at all on this matter would be greatly appreciated.  I've begun to prefer Ubuntu over Windows, but if I can't play most games, I'll have to Dual-boot with Windows instead, relegating Ubuntu to a secondary and less important operating system.

---

### Post by Velleos on 2008-12-23
I tried starting steam in the terminal, and I have pasted what I was able to copy from it below.  This isn't all that showed up in the terminal, but some of the messages happened multiple times, and so fast that I couldn't catch everything.

Also, This code will take a few posts.  The forums tell me it has 21 images in it, and that I can only post 8, but there are NO images or links to images in it.(How annoying!)

Edit: Apparently some of the code WAS read by the forum as the same characters for smileys.  Weird.


CellID: Fetching server list from CSDS. . .
fixme: midi :OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme: process :SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: CSDS returned 211 servers.
CellID: Connecting to 114.80.71.99:27031. . .
CellID: Connect to 114.80.71.99:27031 took 260 MS
CellID: Nothing beat our old best time of 23 MS
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err: ole : CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err: ole : CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1

eIMMApp_OnDefWindowProc Stub (0x2003a 84 0 1a20291)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x200ac 81 0 32cf3c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x200ac 83 0 32ceec)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x200ac 1 0 32cf3c)

fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x2003a 84 0 bb011c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x2003a 84 0 b3011c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x2003a 84 0 1d5011d)


Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x100b8 1c 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x100aa 1c 0 0)

---

### Post by Velleos on 2008-12-23
err: ole :CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err: ole :CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err: ole :CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err: ole :CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1

---

### Post by Velleos on 2008-12-23
fixme:win:EnumDisplayDevicesW ((null ),0,0x32ceb8,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise ( 0x1d6688 )->(1 00000002 0x1212e18 )
fixme:shdocvw: PersistStreamInit_InitNew ( 0x1d6688 )
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1d6688 )->(ffffffff )
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x100b8 1c 0 0 )
fixme:shdocvw: OleInPlaceObject_InPlaceDeactivate (0x1d6688 )

---

### Post by Velleos on 2008-12-23
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1d6688 )
fixme:shdocvw:OleObject_Close (0x1d6688 )->(1)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x100b8 1c 0 0)
fixme:win:EnumDisplayDevicesW ((null),0,0x33e0a8,0x00000000), stub!
fixme: ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err: ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err: ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
err : x11settings : X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @60! (XRandR)
CellID: Connecting to 193.34.51.99:27031. . .
CellID: Connect to 193.34.51.99:27031 took 139 MS
CellID: Nothing beat our old best time of 23 MS

---

### Post by Velleos on 2008-12-23
I also found another error, probably sound-related, but that doesn't tell me why the game won't load properly, or the slow video.

err:wave:wodPlayer_WriteMaxFrags Error in writing wavehdr. Reason: Resource temporarily unavailable

---

### Post by Velleos on 2008-12-24
Bump

---

### Post by OrbJinzo on 2008-12-25
env WINEPREFIX="/home/usernamehere/.wine" wine "C:\Valve\Steam\steam.exe" -applaunch 220 -dxlevel 80 -novid -windowed

you gotta disable the video and lower the dxlevel to 80 or 81 just put that in a launcher and you should be able to get HL2 running.

---

### Post by Velleos on 2008-12-26
No luck

I tried putting this:

env WINEPREFIX="/home/velleos/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 220 -dxlevel 80 -novid -windowed

into terminal, steam login window came up, and crashed after trying to log in.

I copied what I thought were the errors that mattered.


fixme:win:RegisterDeviceNotificationA (hwnd=0x10090, filter=0x32df78,flags=0x00000004),
	returns a fake device notification handle!
CellID: Connect to 193.34.50.5:27031 took 127 MS
err: ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err: ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
CellID: Connecting to 119.167.242.114:27031. . .
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
NVIDIA: Direct rendering failed; attempting indirect rendering.
CellID: Connect to 119.167.242.114:27031 took 295 MS
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
NVIDIA: Direct rendering failed; attempting indirect rendering.
CellID: Connecting to 69.28.145.82:27031. . .
fixme:win:EnumDisplayDevicesW ((null),0,0x32bf38,0x00000000), stub!
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connect to 69.28.145.82:27031 took 74 MS
CellID: Connecting to 63.236.98.116:27031. . .
CellID: Connect to 63.236.98.116:27031 took 51 MS
CellID: Connecting to 114.80.71.106:27031. . .
CellID: Connect to 114.80.71.106:27031 took 261 MS
CellID: Connecting to 114.80.71.101:27031. . .
CellID: Connect to 114.80.71.101:27031 took 275 MS
CellID: Connecting to 62.118.240.141:27031. . .
CellID: Connect to 62.118.240.141:27031 took 290 MS
CellID: Connecting to 87.248.208.116:27031. . .
CellID: Connect to 87.248.208.116:27031 took 148 MS
CellID: Connecting to 208.111.156.52:27031. . .
CellID: Connect to 208.111.156.52:27031 took 55 MS
CellID: Connecting to 69.28.153.90:27031. . .
CellID: Connect to 69.28.153.90:27031 took 45 MS
CellID: Connecting to 68.142.116.2:27031. . .
CellID: Connect to 68.142.116.2:27031 took 96 MS
CellID: Connecting to 63.236.79.100:27031. . .
CellID: Connect to 63.236.79.100:27031 took 47 MS
CellID: Connecting to 87.248.196.198:27031. . .
CellID: Connect to 87.248.196.198:27031 took 184 MS
CellID: Connecting to 203.77.185.5:27031. . .
CellID: Connect to 203.77.185.5:27031 took 184 MS
CellID: Connecting to 193.34.49.3:27031. . .
CellID: Connect to 193.34.49.3:27031 took 152 MS
CellID: Connecting to 79.141.163.3:27031. . .
CellID: Connect to 79.141.163.3:27031 took 124 MS
CellID: Connecting to 119.167.242.111:27031. . .
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connect to 119.167.242.111:27031 took 280 MS
CellID: Connecting to 79.141.160.2:27031. . .
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connect to 79.141.160.2:27031 took 164 MS
CellID: Connecting to 203.66.135.29:27031. . .
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connect to 203.66.135.29:27031 took 230 MS
CellID: Connecting to 79.141.162.2:27031. . .
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
CellID: Connect to 79.141.162.2:27031 took 136 MS
CellID: !! Got Cell ID 50 from server 68.142.119.10:27031
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb

---

### Post by Velleos on 2008-12-27
Bump

---

### Post by soluphobe on 2008-12-27
Which nVidia driver are you using?  I've installed 177, but found that 173 works better on most things.  That might be a factor, especially since your display keeps getting messed up.

Have you tried adding -use11 (use one one, not use ell ell) to your terminal command?  A couple of people have told me it's the best thing ever.

---

### Post by emshains on 2008-12-27
Try running it with these preifxes:```

WINEDEBUG="fixme-all" wine /home/[username]/.wine/drive_c/Valve/Steam/steam.exe -applaunch 220 -dxlevel 70 -heapsize 512000 -w 1024 -novid

```

Making it run windowed sometimes will actually make it slower and for me, it allows my cursor to exit the window, no matter what I tick in the winecfg.

---

### Post by darklegion on 2008-12-27
I wouldn't even bother with that video card.Wine's performance has improved since wine-1.1.11 (which you should install) but I doubt a nvidia 5500 will give you decent performance.You really need at least a 7900GS/8600GT or higher to get good performance with wine, preferably a 9600GT/8800GT(S)/9800GT(X) or better.

---

### Post by darklegion on 2008-12-28
Also, check this out:
[http://bugs.winehq.org/show_bug.cgi?id=14451](http://bugs.winehq.org/show_bug.cgi?id=14451)

---

### Post by Wisp558 on 2008-12-28
You NEED the proprietary drivers, at this point, unfortunately.

That's the biggest problem.

If you can't use the "restricted" ubu drivers, download the ones from NVIDIA and install them yourself...

NOTE: You'll have to be running sans X server to install, I'd boot in recovery mode to do this... pretty easy if you extract everything beforehand.

Also, did you try BOTH restricted drivers? (At least I had 2 options...)

Also, I have an odd issue with hl2 where if Amarok is running, hl2 will just die at the menu screen... =/ kill all processes first

Another thing I find works well is to try using a minimal DE, like fluxbox or IceWM (I prefer FB).

-dxlevel 80 fails for me but -dxlevel 81 works OK.

I have a GeForce 8500 GT, for reference.

EDIT: Yeah, a 5500 is low in 'dows, and wine will run slower (to some degree) so... But definitely keep working on getting those drivers working.

---

### Post by Velleos on 2009-02-04
Sorry I haven't replied in a timely manner.  I understand now that my card isn't going to allow me to run HL2 on this linux machine.  Still, I've gotten a lot of useful advice about getting Wine to work better in general.

  Thank you for your help, everybody, I really appreciate it.

---

### Post by schnauzer93 on 2009-03-01
I have this same problem, except I have a 9600 series card. The Valve video that runs on launch is very slow, but the audio is normal speed. ```
err:wave:wodPlayer_WriteMaxFrags Error in writing wavehdr. Reason: Resource temporarily unavailable
```repeats on the terminal window, and it will not load to menu. Strange thing is, it worked this morning and I did not change any of my settings. My NVIDIA driver is 180.29.

---

### Post by kninnuG on 2009-03-14
I also have a nVidia FX 5500.
I added -novid on the command line, and it loads the menu. But the framerate in-game is horrible, the intro with the GMan only runs ok when the game is minimalized. I haven't gone further than the point you meet Alyx the first time, but even with lowest graphic settings that goes crap.
It runs smooth under Windows with highest graphic settings. I noticed that the CPU is used a lot when doing the simplest jobs, like showing the menus in Steam, I have feeling that it isn't using my graphics card at all, but doing everything with the CPU.
So far, the only game I can run with Wine is Half-Life 1...

More info:
AMD Athlon XP 1700+ (1.47Ghz), 1.5GiB RAM, Ubuntu 8.10

---

