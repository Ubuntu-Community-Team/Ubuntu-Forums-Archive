---
title: "Wine and Magic Workstation"
date: 2009-02-03
forum: Wine
---

### Post by Snic on 2009-02-03
Okay, I've done some poking about here and on Google and haven't found anything regarding this issue. For Magic Workstation, Deck editor seems to work fine, but whenever I load MWSPlay.exe I get an access violation in GDIPlus.dll. I tried going into the config and setting a DLL over ride for this to native, same error. Tried in Wine 1.1.13 and 1.1.14 with winetricks as specified in the appdb. I'm running in Ubuntu 8.10 x86 release, has anyone else seen this or have further ideas on what may be bringing this up?

Terminal output when run is
```
 
$ wine /home/username/.wine/drive_c/Program\ Files/Magic\ Workstation/MWSPlay.exe 
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/username/.wine' has been updated.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f6b8,0x00000000), stub!
fixme:dciman:DCICreatePrimary 0x404 0xe2129c

```

---

### Post by Rarensu on 2009-08-08
I have a similar error.

Terminal:
```

$ wine /home/username/.wine/drive_c/Program\ Files/Magic\ Workstation/MWSplay.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f6b8,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x172100,0x172000): stub
fixme:dciman:DCICreatePrimary 0x404 0xe212a4
```

Then MWSPlay starts and I get an unending chain of error messages:

Access violation at address 70D09697 in module "gdiplus.dll'. Read of address 00000048.

Additional information. This error code appears to me when I run MWS on windows, but it only appears only occasionally, and only one at a time, instead of a huge flood every time I start the program. Furthermore, this is a recent development for me. I was able to run MWSPlay for several days under Wine before it broke: the error code appeared (often as a result of the program recieving a click to an area of the window that doesn't have any click properties), but it didn't cause the program to be totally useless. I would just close the message and carry on as before.

---

### Post by Rarensu on 2009-08-16
OK, I have an update... 

I suspected that the problem might have started when I upgraded from wine 1.1.26 to wine 1.1.27. I did regression testing on wine-git. Unfortunately, the error doesn't vanish no matter how many patches I revert. So it's probably not Wine's fault.

HMM.

---

### Post by NightMKoder on 2009-08-16
Did you get gdiplus through winetricks? (that's how you should have gotten it)

---

### Post by Lilu on 2009-10-12
Hi everybody!

I have the same error with MWSPlay.exe and GDIPlus.dll. Tried to get gdiplus through winetricks but it doesn't help.
Does anyone know how to fix it?

---

