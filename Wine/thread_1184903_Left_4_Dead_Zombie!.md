---
title: "Left 4 Dead Zombie!"
date: 2009-06-11
forum: Wine
---

### Post by 8Kuula on 2009-06-11
H!

L4D turns to zombie (need to get my shotgun?) at loading screen. Starting videos play fine. When loading screen comes, that "Loading..." at bottom right coner, L4D just freezes, on system monitor left4dead.exe status is zombie, and need end that process to get loading screen out.
After that steam is stuck too. But on system monitor it is sleeping.

Starting from console output is:
```

bunbun@triton:~/OS/Windows/Games/Steam/steamapps/common/left 4 dead# wine ./left4dead.exe -novid
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:win:EnumDisplayDevicesW ((null),0,0x32e1d0,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1280x1024x32 @60! (XRandR)
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x14c0c0) : stub
fixme:d3d:state_blendop Unrecognized/Unhandled D3DBLENDOP value 0

```On console try I started to tap ctrl+c, and it did quit left4dead.exe. Steam got stuck again too.

9.04 64bit, wine 1.1.23, nvidia 185.18.14, GeForce 8800 GT.

Any ideas? Im all out...  ](*,)

---

### Post by u235sentinel on 2009-06-11
> **8Kuula said:**
> H!

L4D turns to zombie (need to get my shotgun?) at loading screen. Starting videos play fine. When loading screen comes, that "Loading..." at bottom right coner, L4D just freezes, on system monitor left4dead.exe status is zombie, and need end that process to get loading screen out.
After that steam is stuck too. But on system monitor it is sleeping.

{snip}

9.04 64bit, wine 1.1.23, nvidia 185.18.14, GeForce 8800 GT.

Any ideas? Im all out...  ](*,)

I understand from the winehq apps database the application has performance problems.  The ONLY reason I haven't purchased it yet.  Once it hits gold then I'll consider it.  Until then I think you may be frustrated.

Sry.  Wish I could give you better news.  Perhaps another here has some insight that will help.

---

### Post by 8Kuula on 2009-06-11
> **u235sentinel said:**
> I understand from the winehq apps database the application has performance problems.  The ONLY reason I haven't purchased it yet.  Once it hits gold then I'll consider it.  Until then I think you may be frustrated.

Sry.  Wish I could give you better news.  Perhaps another here has some insight that will help.

Yes it has, only runs 20-30fps on my comp. But last weekend it did start up and could play, now cant do even that :(

Only thing I have updated manualy is nvidia drivers to 185.18.14, that was last saturday, and on sunday-monday night I did play L4D last time. So cant be that update since it did work with them.

---

### Post by linux.is.skynet on 2009-06-11
My install of Left4Dead does the same thing : 




fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x147ac0) : stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a6e40,0x1a73b0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a6e40,0x1a73b0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a6e40,0x1a73b0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a6e40,0x1a73b0): stub
fixme:d3d:state_blendop Unrecognized/Unhandled D3DBLENDOP value 0
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.



NOTE: wtf is up with the please enable coredumps? A bad MSCOREE.DLL? Tried adding one to system32 but no luck... :(  

This ran for a few hours in Cedega and then started doing the same....

---

### Post by Jorenko on 2009-06-11
This is happening to me too ever since the kernel update this morning. Both TF2 and L4D have the same problem. They've both worked fine for months previously.

---

### Post by 8Kuula on 2009-06-12
```
bonbon@triton:~# uname -a
Linux triton 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux
```That one?

edit:
```
Linux triton 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:31:32 UTC 2009 x86_64 GNU/Linux
```
Do not work with that kernel either.

Seems steam client has updated too at June 10th, [http://store.steampowered.com/news/2569/](http://store.steampowered.com/news/2569/) (have not noticed)
My steam version is:
 Built: Jun 9 2009, at 15:43:20
 Steam API: v008
 Steam package versions: 54 / 872

---

### Post by Klinke on 2009-06-12
same here

Linux djiin 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686 GNU/Linux

wine 1.1.23

nvidia 180.44

exactly the same output. Counter Strike Source and other wine games still run perfectly

Updated: Linux djiin 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux
same problem

---

### Post by 8Kuula on 2009-06-12
Did try start steam from console:
```

bunbun@triton:~# env WINEPREFIX="/home/bunbun/.wine" env WINEDEBUG=fixme-all wine "D:\Games\Steam\Steam.exe"
CellID: Fetching server list from CSDS. . .
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
CellID: CSDS returned 173 servers.
CellID: Connecting to 68.142.81.5:27031. . .
CellID: Connect to 68.142.81.5:27031 took 149 MS
CellID: Nothing beat our old best time of 0 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ntdll:RtlpWaitForCriticalSection section 0xbd6e64 "?" wait timed out in thread 0022, blocked by 0023, retrying (60 sec)
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[1bb760]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[1bb760]: NPN Logging Active!
0[1bb760]: General Plugin Logging Active! (nsPluginHostImpl::ctor)
0[1bb760]: NPP Logging Active!
0[1bb760]: nsPluginHostImpl::ctor
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.
zsh: killed     env WINEPREFIX="/home/bunbun/.wine" env WINEDEBUG=fixme-all wine 

```start steam -> start l4d from steam game menu.
Well do not say anything to me that but maybe to some guru it does :D

Steam games: 
 starts up: hl2, hl2e1, hl2e2 and css
 do not start up: l4d, portal and tf2

---

### Post by 8Kuula on 2009-06-12
Seems Wine gurus have noticed this problem, and trying to fix it.
[http://bugs.winehq.org/show_bug.cgi?id=18900](http://bugs.winehq.org/show_bug.cgi?id=18900)

Meanwhile :popcorn: for me then.

---

### Post by asdfoo on 2009-06-12
8Kuula: WHY ARE YOU RUNNING WINE AS ROOT?

---

### Post by Jorenko on 2009-06-12
Reverting to wine 1.0.1-ubuntu6 from the ubuntu repos fixed the problem for me. Looks like there's a patch for 1.1.23 in that bug's comments but it'll probably be 2 more releases til it's merged in, if ever.

---

### Post by 8Kuula on 2009-06-13
Yeah reverting to 1.0.1 fixes problem here too, thou now l4d runs with ~10fps :D
Oh well, seems need hope wine gurus put that patch to 1.1.24 (or what ever version comes out next).

---

### Post by asdfoo on 2009-06-13
> **asdfoo said:**
> 8Kuula: WHY ARE YOU RUNNING WINE AS ROOT?

if you don't stop running as root you risk trashing your entire system

---

### Post by Jorenko on 2009-06-20
> **8Kuula said:**
> Yeah reverting to 1.0.1 fixes problem here too, thou now l4d runs with ~10fps :D
Oh well, seems need hope wine gurus put that patch to 1.1.24 (or what ever version comes out next).

Indeed, same here. But yes, they have included the patch in 1.1.24 which is now released! The official ubuntu build should be showing up in Scott Ritchie's repos any time now...

---

### Post by plinydogg on 2009-06-20
I hope the release of 1.1.24 fixes the problem as I am experiencing the same thing!

---

### Post by trey85stang on 2009-06-20
> **asdfoo said:**
> if you don't stop running as root you risk trashing your entire system

he's running it on a personal desktop not a server... Not a big deal.

I'm having the same problem even with cedega 7.3.0

---

### Post by 8Kuula on 2009-06-21
> **asdfoo said:**
> if you don't stop running as root you risk trashing your entire system

What makes you belive that I run wine as root? :confused:

---

### Post by plinydogg on 2009-06-21
Updating to the latest version of Wine worked for me!

---

### Post by trey85stang on 2009-06-23
> **8Kuula said:**
> What makes you belive that I run wine as root? :confused:

in one of your quotes: bunbun@triton:~#  the "#" gives it away.

---

### Post by trey85stang on 2009-06-23
> **plinydogg said:**
> Updating to the latest version of Wine worked for me!

Good to know!

---

### Post by 8Kuula on 2009-06-24
> **trey85stang said:**
> in one of your quotes: bunbun@triton:~#  the "#" gives it away.

Ok, my prompt is "bunbun@triton:~(_!_)"  now. Am I runing wine as ***? :o

1 character dont mean that command is ran as root #-o

---

